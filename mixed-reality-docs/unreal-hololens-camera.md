---
title: Камера HoloLens в Unreal
description: Руководство по работе с камерой HoloLens в Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, камера третья камера, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840123"
---
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="c9e38-104">Камера HoloLens в Unreal</span><span class="sxs-lookup"><span data-stu-id="c9e38-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="c9e38-105">Третья камера для съемки смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="c9e38-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="c9e38-106">Третья камера для съемки смешанной реальности (MRC) позволяет визуализировать изображение смешанной реальности с точки зрения камеры, установленной на видоискателе HoloLens, вместо позиции текстур глаз.</span><span class="sxs-lookup"><span data-stu-id="c9e38-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="c9e38-107">Это улучшает соответствие между реальным миром и голограммами в видеороликах MRC.</span><span class="sxs-lookup"><span data-stu-id="c9e38-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="c9e38-108">Чтобы включить применение третьей камеры MRC, вызовите SetEnabledMixedRealityCamera и ResizeMixedRealityCamera с указанием нужного разрешения видео.</span><span class="sxs-lookup"><span data-stu-id="c9e38-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![Третья камера](images/unreal-camera-3rd.PNG)

<span data-ttu-id="c9e38-110">Затем запишите видеоролик MRC на портале устройств HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c9e38-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="c9e38-111">Фото-/видеокамера</span><span class="sxs-lookup"><span data-stu-id="c9e38-111">PV Camera</span></span>

<span data-ttu-id="c9e38-112">Текстуру веб-камеры также можно также получить во время игры.</span><span class="sxs-lookup"><span data-stu-id="c9e38-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="c9e38-113">Чтобы получить текстуру веб-камеры в HoloLens, для начала установите флажок Webcam (Камера) в разделе Project Settings (Параметры проекта) > Platform (Платформа) > HoloLens > Capabilities (Возможности) редактора Unreal.</span><span class="sxs-lookup"><span data-stu-id="c9e38-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="c9e38-114">Включите использование веб-камеры во время выполнения с помощью функции StartCameraCapture.</span><span class="sxs-lookup"><span data-stu-id="c9e38-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="c9e38-115">Для остановки записи примените функцию StopCameraCapture.</span><span class="sxs-lookup"><span data-stu-id="c9e38-115">Stop capturing with the StopCameraCapture function.</span></span> 

![Запуск и остановка камеры](images/unreal-camera-startstop.PNG)

<span data-ttu-id="c9e38-117">Чтобы отображать изображение камеры, сначала создайте экземпляр динамического материала на основе материала из проекта.</span><span class="sxs-lookup"><span data-stu-id="c9e38-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="c9e38-118">В нашем примере это материал с именем PVCamMat.</span><span class="sxs-lookup"><span data-stu-id="c9e38-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="c9e38-119">Сохраните это значение в переменную с типом Material Instance Dynamic Object Reference (Ссылка на динамический объект экземпляра материала).</span><span class="sxs-lookup"><span data-stu-id="c9e38-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="c9e38-120">Затем в качестве материала для того объекта в сцене, который будет отображать поток с камеры, укажите новый экземпляр динамического материала и запустите таймер, который будет использоваться для привязки изображения с камеры к материалу.</span><span class="sxs-lookup"><span data-stu-id="c9e38-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![Отрисовка камеры](images/unreal-camera-render.PNG)

<span data-ttu-id="c9e38-122">Создайте для этого таймера новую функцию (в нашем примере это MaterialTimer) и вызовите функцию GetARCameraImage, чтобы получить текстуру от веб-камеры.</span><span class="sxs-lookup"><span data-stu-id="c9e38-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="c9e38-123">Если эта текстура допустима, присвойте это изображение параметру текстуры в шейдере.</span><span class="sxs-lookup"><span data-stu-id="c9e38-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="c9e38-124">В противном случае снова запустите таймер обновления материала.</span><span class="sxs-lookup"><span data-stu-id="c9e38-124">Otherwise, start the material timer again.</span></span> 

![Текстура от камеры](images/unreal-camera-texture.PNG)

<span data-ttu-id="c9e38-126">Для материала нужно создать в SetTextureParameterValue параметр с таким же именем, который привязан к записи цвета, чтобы выводимое камерой изображение отображалось правильно.</span><span class="sxs-lookup"><span data-stu-id="c9e38-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![Текстура от камеры](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="c9e38-128">См. также статью</span><span class="sxs-lookup"><span data-stu-id="c9e38-128">See also</span></span>
* [<span data-ttu-id="c9e38-129">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="c9e38-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="c9e38-130">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="c9e38-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
