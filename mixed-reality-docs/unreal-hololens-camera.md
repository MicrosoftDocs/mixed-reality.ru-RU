---
title: Фото- и видеокамера HoloLens в Unreal
description: Руководство по работе с фото- и видеокамерой HoloLens в Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, камера, PV-камера, MRC
ms.openlocfilehash: e15ea593283a22dc31cd496de596159035d83799
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720330"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="95664-104">Фото- и видеокамера HoloLens в Unreal</span><span class="sxs-lookup"><span data-stu-id="95664-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="95664-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="95664-105">Overview</span></span>

<span data-ttu-id="95664-106">Устройство HoloLens оснащено фото- и видеокамерой, которая используется для съемки смешанной реальности (MRC) и может также использоваться приложением для доступа к визуальным элементам реального мира.</span><span class="sxs-lookup"><span data-stu-id="95664-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="95664-107">Отрисовка с фото- и видеокамеры для MRC</span><span class="sxs-lookup"><span data-stu-id="95664-107">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="95664-108">Для этого требуется **Unreal Engine версии 4.25** и выше.</span><span class="sxs-lookup"><span data-stu-id="95664-108">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="95664-109">Системные и пользовательские средства MRC производят съемку смешанной реальности, совмещая изображение с фото- и видеокамеры и голограммы, которые отрисовываются иммерсивным приложением.</span><span class="sxs-lookup"><span data-stu-id="95664-109">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="95664-110">По умолчанию для съемки смешанной реальности используется голографический вывод правого глаза.</span><span class="sxs-lookup"><span data-stu-id="95664-110">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="95664-111">В иммерсивном приложении можно вместо этого выбрать [отрисовку с фото- и видеокамеры](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in).</span><span class="sxs-lookup"><span data-stu-id="95664-111">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="95664-112">Это улучшает соответствие между реальным миром и голограммами в видеороликах MRC.</span><span class="sxs-lookup"><span data-stu-id="95664-112">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="95664-113">Чтобы включить отрисовку с фото- и видеокамеры (по умолчанию она выключена):</span><span class="sxs-lookup"><span data-stu-id="95664-113">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="95664-114">Вызовите функции **SetEnabledMixedRealityCamera** и **ResizeMixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="95664-114">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="95664-115">Задайте размеры видеоизображения с помощью параметров **Size X** (Размер по X) и **Size Y** (Размер по Y).</span><span class="sxs-lookup"><span data-stu-id="95664-115">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Третья камера](images/unreal-camera-3rd.PNG)

<span data-ttu-id="95664-117">После этого Unreal будет обрабатывать запросы от MRC на отрисовку с точки зрения фото- и видеокамеры.</span><span class="sxs-lookup"><span data-stu-id="95664-117">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="95664-118">Приложению будет даваться команда на отрисовку с точки зрения фото- и видеокамеры только в том случае, если активирована [съемка смешанной реальности](mixed-reality-capture.md).</span><span class="sxs-lookup"><span data-stu-id="95664-118">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="95664-119">Использование фото- и видеокамеры</span><span class="sxs-lookup"><span data-stu-id="95664-119">Using the PV Camera</span></span>

<span data-ttu-id="95664-120">Текстуру с веб-камеры можно получить в игре во время выполнения, но эту возможность необходимо включить в разделе **Edit > Project Settings** (Правка > Параметры проекта) редактора:</span><span class="sxs-lookup"><span data-stu-id="95664-120">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="95664-121">Выберите **Platforms > HoloLens > Capabilities** (Платформы > HoloLens > Возможности) и установите флажок **Webcam** (Веб-камера).</span><span class="sxs-lookup"><span data-stu-id="95664-121">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="95664-122">Чтобы начать запись с веб-камеры во время выполнения, вызовите функцию **StartCameraCapture**, а чтобы остановить запись, вызовите функцию **StopCameraCapture**.</span><span class="sxs-lookup"><span data-stu-id="95664-122">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Запуск и остановка камеры](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="95664-124">Отрисовка изображения</span><span class="sxs-lookup"><span data-stu-id="95664-124">Rendering an image</span></span>
<span data-ttu-id="95664-125">Для отрисовки изображения с камеры:</span><span class="sxs-lookup"><span data-stu-id="95664-125">To render the camera image:</span></span>
1. <span data-ttu-id="95664-126">Создайте динамический экземпляр материала на основе материала **PVCamMat** из проекта (см. снимок экрана ниже).</span><span class="sxs-lookup"><span data-stu-id="95664-126">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="95664-127">Сохраните новый динамический экземпляр материала в переменной **Material Instance Dynamic Object Reference** (Ссылка на динамический объект экземпляра материала).</span><span class="sxs-lookup"><span data-stu-id="95664-127">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="95664-128">Выберите этот динамический экземпляр материала в качестве материала объекта в сцене, где будет отрисовываться изображение с камеры.</span><span class="sxs-lookup"><span data-stu-id="95664-128">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="95664-129">Запустите таймер, по которому будет выполняться привязка изображения с камеры будет к материалу.</span><span class="sxs-lookup"><span data-stu-id="95664-129">Start a timer that will be used to bind the camera image to the material.</span></span> 

![Отрисовка камеры](images/unreal-camera-render.PNG)

4. <span data-ttu-id="95664-131">Создайте для этого таймера новую функцию (в нашем примере это **MaterialTimer**) и вызовите функцию **GetARCameraImage**, чтобы получить текстуру с веб-камеры.</span><span class="sxs-lookup"><span data-stu-id="95664-131">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="95664-132">Если эта текстура допустима, установите это изображение в качестве значения параметра текстуры в шейдере.</span><span class="sxs-lookup"><span data-stu-id="95664-132">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="95664-133">В противном случае снова запустите таймер обновления материала.</span><span class="sxs-lookup"><span data-stu-id="95664-133">Otherwise, start the material timer again.</span></span> 

![Текстура от камеры](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="95664-135">У материала должен быть параметр с таким же именем, как имя параметра функции **SetTextureParameterValue**, привязанное к записи о цвете.</span><span class="sxs-lookup"><span data-stu-id="95664-135">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="95664-136">Без этого изображение с камеры не может быть правильно отображено.</span><span class="sxs-lookup"><span data-stu-id="95664-136">Without this, the camera image can't be properly displayed.</span></span>

![Текстура от камеры](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="95664-138">См. также статью</span><span class="sxs-lookup"><span data-stu-id="95664-138">See also</span></span>
* [<span data-ttu-id="95664-139">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="95664-139">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="95664-140">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="95664-140">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
