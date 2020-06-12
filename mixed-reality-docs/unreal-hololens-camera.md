---
title: Фото- и видеокамера HoloLens в Unreal
description: Руководство по работе с фото- и видеокамерой HoloLens в Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, камера, PV-камера, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451339"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="f56ba-104">Фото- и видеокамера HoloLens в Unreal</span><span class="sxs-lookup"><span data-stu-id="f56ba-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="f56ba-105">Устройство HoloLens оснащено фото- и видеокамерой, которая используется для съемки смешанной реальности (MRC) и может также использоваться приложением для доступа к визуальным элементам реального мира.</span><span class="sxs-lookup"><span data-stu-id="f56ba-105">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="f56ba-106">Отрисовка с фото- и видеокамеры для MRC</span><span class="sxs-lookup"><span data-stu-id="f56ba-106">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="f56ba-107">Для этого требуется **Unreal Engine версии 4.25** и выше.</span><span class="sxs-lookup"><span data-stu-id="f56ba-107">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="f56ba-108">Системные и пользовательские средства MRC производят съемку смешанной реальности, совмещая изображение с фото- и видеокамеры и голограммы, которые отрисовываются иммерсивным приложением.</span><span class="sxs-lookup"><span data-stu-id="f56ba-108">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="f56ba-109">По умолчанию для съемки смешанной реальности используется голографический вывод правого глаза.</span><span class="sxs-lookup"><span data-stu-id="f56ba-109">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="f56ba-110">В иммерсивном приложении можно вместо этого выбрать [отрисовку с фото- и видеокамеры](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in).</span><span class="sxs-lookup"><span data-stu-id="f56ba-110">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="f56ba-111">Это улучшает соответствие между реальным миром и голограммами в видеороликах MRC.</span><span class="sxs-lookup"><span data-stu-id="f56ba-111">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="f56ba-112">Чтобы включить отрисовку с фото- и видеокамеры (по умолчанию она выключена):</span><span class="sxs-lookup"><span data-stu-id="f56ba-112">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="f56ba-113">Вызовите функции **SetEnabledMixedRealityCamera** и **ResizeMixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="f56ba-113">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="f56ba-114">Задайте размеры видеоизображения с помощью параметров **Size X** (Размер по X) и **Size Y** (Размер по Y).</span><span class="sxs-lookup"><span data-stu-id="f56ba-114">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Третья камера](images/unreal-camera-3rd.PNG)

<span data-ttu-id="f56ba-116">После этого Unreal будет обрабатывать запросы от MRC на отрисовку с точки зрения фото- и видеокамеры.</span><span class="sxs-lookup"><span data-stu-id="f56ba-116">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="f56ba-117">Приложению будет даваться команда на отрисовку с точки зрения фото- и видеокамеры только в том случае, если активирована [съемка смешанной реальности](mixed-reality-capture.md).</span><span class="sxs-lookup"><span data-stu-id="f56ba-117">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="f56ba-118">Использование фото- и видеокамеры</span><span class="sxs-lookup"><span data-stu-id="f56ba-118">Using the PV Camera</span></span>

<span data-ttu-id="f56ba-119">Текстуру с веб-камеры можно получить в игре во время выполнения, но эту возможность необходимо включить в разделе **Edit > Project Settings** (Правка > Параметры проекта) редактора:</span><span class="sxs-lookup"><span data-stu-id="f56ba-119">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="f56ba-120">Выберите **Platforms > HoloLens > Capabilities** (Платформы > HoloLens > Возможности) и установите флажок **Webcam** (Веб-камера).</span><span class="sxs-lookup"><span data-stu-id="f56ba-120">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="f56ba-121">Чтобы начать запись с веб-камеры во время выполнения, вызовите функцию **StartCameraCapture**, а чтобы остановить запись, вызовите функцию **StopCameraCapture**.</span><span class="sxs-lookup"><span data-stu-id="f56ba-121">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Запуск и остановка камеры](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="f56ba-123">Отрисовка изображения</span><span class="sxs-lookup"><span data-stu-id="f56ba-123">Rendering an image</span></span>
<span data-ttu-id="f56ba-124">Для отрисовки изображения с камеры:</span><span class="sxs-lookup"><span data-stu-id="f56ba-124">To render the camera image:</span></span>
1. <span data-ttu-id="f56ba-125">Создайте динамический экземпляр материала на основе материала **PVCamMat** из проекта (см. снимок экрана ниже).</span><span class="sxs-lookup"><span data-stu-id="f56ba-125">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="f56ba-126">Сохраните новый динамический экземпляр материала в переменной **Material Instance Dynamic Object Reference** (Ссылка на динамический объект экземпляра материала).</span><span class="sxs-lookup"><span data-stu-id="f56ba-126">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="f56ba-127">Выберите этот динамический экземпляр материала в качестве материала объекта в сцене, где будет отрисовываться изображение с камеры.</span><span class="sxs-lookup"><span data-stu-id="f56ba-127">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="f56ba-128">Запустите таймер, по которому будет выполняться привязка изображения с камеры будет к материалу.</span><span class="sxs-lookup"><span data-stu-id="f56ba-128">Start a timer that will be used to bind the camera image to the material.</span></span> 

![Отрисовка камеры](images/unreal-camera-render.PNG)

4. <span data-ttu-id="f56ba-130">Создайте для этого таймера новую функцию (в нашем примере это **MaterialTimer**) и вызовите функцию **GetARCameraImage**, чтобы получить текстуру с веб-камеры.</span><span class="sxs-lookup"><span data-stu-id="f56ba-130">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="f56ba-131">Если эта текстура допустима, установите это изображение в качестве значения параметра текстуры в шейдере.</span><span class="sxs-lookup"><span data-stu-id="f56ba-131">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="f56ba-132">В противном случае снова запустите таймер обновления материала.</span><span class="sxs-lookup"><span data-stu-id="f56ba-132">Otherwise, start the material timer again.</span></span> 

![Текстура от камеры](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="f56ba-134">У материала должен быть параметр с таким же именем, как имя параметра функции **SetTextureParameterValue**, привязанное к записи о цвете.</span><span class="sxs-lookup"><span data-stu-id="f56ba-134">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="f56ba-135">Без этого изображение с камеры не может быть правильно отображено.</span><span class="sxs-lookup"><span data-stu-id="f56ba-135">Without this, the camera image can't be properly displayed.</span></span>

![Текстура от камеры](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="f56ba-137">См. также статью</span><span class="sxs-lookup"><span data-stu-id="f56ba-137">See also</span></span>
* [<span data-ttu-id="f56ba-138">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="f56ba-138">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="f56ba-139">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="f56ba-139">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
