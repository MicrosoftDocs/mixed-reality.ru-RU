---
title: Пространственные аудио учебники — 3. Спатиализинг аудио из видео
description: Импортируйте видео-ресурс в проект Unity и спатиализе звук из видео.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182751"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="9d90e-105">Спатиализинг аудио из видео</span><span class="sxs-lookup"><span data-stu-id="9d90e-105">Spatializing audio from a video</span></span>
<span data-ttu-id="9d90e-106">В этой третьей главе, посвященной пространственному аудио модулю в учебниках по Unity в HoloLens 2, вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="9d90e-106">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="9d90e-107">Импорт видео и добавление видеопроигрывателя</span><span class="sxs-lookup"><span data-stu-id="9d90e-107">Import a video and add a Video Player</span></span>
* <span data-ttu-id="9d90e-108">Воспроизведение видео на куадрангле</span><span class="sxs-lookup"><span data-stu-id="9d90e-108">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="9d90e-109">Перенаправление звука с видео на куадрангле и спатиализе звук</span><span class="sxs-lookup"><span data-stu-id="9d90e-109">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="9d90e-110">Импорт видео и добавление видеопроигрывателя</span><span class="sxs-lookup"><span data-stu-id="9d90e-110">Import a video and add a Video Player</span></span>

<span data-ttu-id="9d90e-111">Перетащите видеофайл в область **проекта** в проекте Unity.</span><span class="sxs-lookup"><span data-stu-id="9d90e-111">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="9d90e-112">[Это видео](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) можно использовать из примера проекта пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="9d90e-112">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Папка Assets с видео](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="9d90e-114">Настройка параметров качества видеоклипа обеспечивает плавное воспроизведение в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9d90e-114">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="9d90e-115">Щелкните видеофайл в области **проекта** .</span><span class="sxs-lookup"><span data-stu-id="9d90e-115">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="9d90e-116">Затем на панели **инспектора** для видеофайла Переопределите параметры приложений для Магазина Windows и:</span><span class="sxs-lookup"><span data-stu-id="9d90e-116">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="9d90e-117">Включить **перекодировать**</span><span class="sxs-lookup"><span data-stu-id="9d90e-117">Enable **Transcode**</span></span>
* <span data-ttu-id="9d90e-118">Задать для **кодека** H264 Single bitrate</span><span class="sxs-lookup"><span data-stu-id="9d90e-118">Set **Codec** to H264</span></span>
* <span data-ttu-id="9d90e-119">Установите низкий **режим** скорости</span><span class="sxs-lookup"><span data-stu-id="9d90e-119">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="9d90e-120">Установка среднего значения **пространственного качества**</span><span class="sxs-lookup"><span data-stu-id="9d90e-120">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="9d90e-121">После выполнения этих корректировок панель **инспектора** для файла видео будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9d90e-121">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Панель свойств видео](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="9d90e-123">Затем добавьте объект **видеопроигрывателя** в **иерархию** , щелкнув правой кнопкой мыши панель **Иерархия** и выбрав **видео-> видеопроигрыватель**:</span><span class="sxs-lookup"><span data-stu-id="9d90e-123">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![Видеопроигрыватель в иерархии](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="9d90e-125">Воспроизведение видео на куадрангле</span><span class="sxs-lookup"><span data-stu-id="9d90e-125">Play video onto a quadrangle</span></span>
<span data-ttu-id="9d90e-126">Объекту **видеопроигрывателя** требуется текстурированный объект Game, на котором будет отображаться видео.</span><span class="sxs-lookup"><span data-stu-id="9d90e-126">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="9d90e-127">Во-первых, добавьте к своей **иерархии** « **четыре** », щелкнув правой кнопкой мыши панель « **Иерархия** » и выбрав « **объемные объекты», > «четыре»** :</span><span class="sxs-lookup"><span data-stu-id="9d90e-127">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![Добавить Quad в иерархию](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="9d90e-129">Чтобы гарантировать, что **четыре** части появляются перед пользователем при запуске приложения, задайте **для свойства "значение"** **Quad** равным (0, 0, 2) и свойству **Scale** значение (1,28, 0,72, 1).</span><span class="sxs-lookup"><span data-stu-id="9d90e-129">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="9d90e-130">После внесения этих изменений компонент **преобразования** на панели **инспектора** для **четырех** компонентов будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9d90e-130">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Четыре преобразования](images/spatial-audio/quad-transform.png)

<span data-ttu-id="9d90e-132">Чтобы создать текстуру **Quad** с видео, создайте новую **текстуру рендеринга**.</span><span class="sxs-lookup"><span data-stu-id="9d90e-132">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="9d90e-133">В области **проекта** щелкните правой кнопкой мыши и выберите **Создать-> рендеринг текстуры**:</span><span class="sxs-lookup"><span data-stu-id="9d90e-133">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![Создать текстуру рендеринга](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="9d90e-135">На панели **инспектора** **текстуры рендеринга**присвойте свойству **size** значение, совпадающее с разрешением 1280 x 720 в собственном разрешении видео.</span><span class="sxs-lookup"><span data-stu-id="9d90e-135">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="9d90e-136">Затем, чтобы обеспечить хорошую производительность отрисовки в HoloLens 2, задайте для свойства **буфера глубины** значение не **менее 16 бит**.</span><span class="sxs-lookup"><span data-stu-id="9d90e-136">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="9d90e-137">После этих параметров панель **инспектора** для **текстуры рендеринга** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9d90e-137">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Прорисовка свойств текстуры](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="9d90e-139">Затем используйте новую **текстуру рендеринга** в качестве текстуры для **четырех**:</span><span class="sxs-lookup"><span data-stu-id="9d90e-139">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="9d90e-140">Перетащите **текстуру рендеринга** из области **проекта** на **четыре** части **иерархии**</span><span class="sxs-lookup"><span data-stu-id="9d90e-140">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="9d90e-141">Чтобы обеспечить хорошую производительность в HoloLens 2, на панели **инспектора** для **четырех**выберите **стандартный шейдер набора средств Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="9d90e-141">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="9d90e-142">С этими параметрами компонент **текстуры** на панели **инспектора** для **четырех** компонентов будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9d90e-142">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Свойства с четырьмя текстурами](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="9d90e-144">Чтобы задать новый **видеопроигрыватель** и **визуализировать текстуру** для воспроизведения видеоклипа, откройте панель **инспектора** для **видеопроигрывателя** и:</span><span class="sxs-lookup"><span data-stu-id="9d90e-144">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="9d90e-145">Задайте для свойства "видеоклип **видео** " видеофайл</span><span class="sxs-lookup"><span data-stu-id="9d90e-145">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="9d90e-146">Установите флажок " **цикл** "</span><span class="sxs-lookup"><span data-stu-id="9d90e-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="9d90e-147">Задать **целевую текстуру** для новой текстуры рендеринга</span><span class="sxs-lookup"><span data-stu-id="9d90e-147">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="9d90e-148">Панель **инспектора** для **видеопроигрывателя** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9d90e-148">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Свойства проигрывателя видео](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="9d90e-150">Спатиализе звук из видео</span><span class="sxs-lookup"><span data-stu-id="9d90e-150">Spatialize the audio from the video</span></span>
<span data-ttu-id="9d90e-151">На панели **инспектора** для « **четырех**» создайте **источник аудио** , в который вы направите звук из видео:</span><span class="sxs-lookup"><span data-stu-id="9d90e-151">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="9d90e-152">Щелкните **Добавить компонент** в нижней части панели.</span><span class="sxs-lookup"><span data-stu-id="9d90e-152">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="9d90e-153">Добавление **источника звука**</span><span class="sxs-lookup"><span data-stu-id="9d90e-153">Add an **Audio Source**</span></span>

<span data-ttu-id="9d90e-154">Затем на **источнике аудио**:</span><span class="sxs-lookup"><span data-stu-id="9d90e-154">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="9d90e-155">Задание **выходных данных** для микшера</span><span class="sxs-lookup"><span data-stu-id="9d90e-155">Set **Output** to your mixer</span></span>
* <span data-ttu-id="9d90e-156">Установите флажок **спатиализе**</span><span class="sxs-lookup"><span data-stu-id="9d90e-156">Check the **Spatialize** box</span></span>
* <span data-ttu-id="9d90e-157">Переместить ползунок **пространственного смешения** в 1 (объемный)</span><span class="sxs-lookup"><span data-stu-id="9d90e-157">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="9d90e-158">После внесения этих изменений компонент " **источник звука** " на панели **инспектора** будет **выглядеть** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9d90e-158">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Проводник с четырьмя звуковыми источниками](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="9d90e-160">Чтобы настроить **видеопроигрыватель** для направления звука в **источник звука** **, откройте**панель **инспектора** для **видеопроигрывателя** и:</span><span class="sxs-lookup"><span data-stu-id="9d90e-160">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="9d90e-161">Установите для **режима вывода звука** значение "источник звука".</span><span class="sxs-lookup"><span data-stu-id="9d90e-161">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="9d90e-162">Задайте для свойства **источник звука** значение четыре</span><span class="sxs-lookup"><span data-stu-id="9d90e-162">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="9d90e-163">После внесения этих изменений панель **инспектора** для **видеопроигрывателя** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9d90e-163">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Выбор источника звука видеопроигрывателя](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="9d90e-165">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="9d90e-165">Next steps</span></span>
<span data-ttu-id="9d90e-166">Попробуйте приложение в HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="9d90e-166">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="9d90e-167">Вы увидите и услышите видео, и звук из видео будет пространственно.</span><span class="sxs-lookup"><span data-stu-id="9d90e-167">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

<span data-ttu-id="9d90e-168">Перейдите к [главе 4](unity-spatial-audio-ch4.md) , чтобы включить и отключить пространственность во время выполнения с помощью кнопки.</span><span class="sxs-lookup"><span data-stu-id="9d90e-168">Continue to [Chapter 4](unity-spatial-audio-ch4.md) to use the button to enable and disable spatialization at run time.</span></span>

