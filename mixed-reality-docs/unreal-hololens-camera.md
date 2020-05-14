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
# <a name="hololens-camera-in-unreal"></a>Камера HoloLens в Unreal

## <a name="third-camera-mixed-reality-capture"></a>Третья камера для съемки смешанной реальности

Третья камера для съемки смешанной реальности (MRC) позволяет визуализировать изображение смешанной реальности с точки зрения камеры, установленной на видоискателе HoloLens, вместо позиции текстур глаз.  Это улучшает соответствие между реальным миром и голограммами в видеороликах MRC. 

Чтобы включить применение третьей камеры MRC, вызовите SetEnabledMixedRealityCamera и ResizeMixedRealityCamera с указанием нужного разрешения видео. 

![Третья камера](images/unreal-camera-3rd.PNG)

Затем запишите видеоролик MRC на портале устройств HoloLens. 

## <a name="pv-camera"></a>Фото-/видеокамера

Текстуру веб-камеры также можно также получить во время игры.  Чтобы получить текстуру веб-камеры в HoloLens, для начала установите флажок Webcam (Камера) в разделе Project Settings (Параметры проекта) > Platform (Платформа) > HoloLens > Capabilities (Возможности) редактора Unreal. 

Включите использование веб-камеры во время выполнения с помощью функции StartCameraCapture.  Для остановки записи примените функцию StopCameraCapture. 

![Запуск и остановка камеры](images/unreal-camera-startstop.PNG)

Чтобы отображать изображение камеры, сначала создайте экземпляр динамического материала на основе материала из проекта.  В нашем примере это материал с именем PVCamMat.  Сохраните это значение в переменную с типом Material Instance Dynamic Object Reference (Ссылка на динамический объект экземпляра материала).  Затем в качестве материала для того объекта в сцене, который будет отображать поток с камеры, укажите новый экземпляр динамического материала и запустите таймер, который будет использоваться для привязки изображения с камеры к материалу. 

![Отрисовка камеры](images/unreal-camera-render.PNG)

Создайте для этого таймера новую функцию (в нашем примере это MaterialTimer) и вызовите функцию GetARCameraImage, чтобы получить текстуру от веб-камеры.  Если эта текстура допустима, присвойте это изображение параметру текстуры в шейдере.  В противном случае снова запустите таймер обновления материала. 

![Текстура от камеры](images/unreal-camera-texture.PNG)

Для материала нужно создать в SetTextureParameterValue параметр с таким же именем, который привязан к записи цвета, чтобы выводимое камерой изображение отображалось правильно. 

![Текстура от камеры](images/unreal-camera-material.PNG)

## <a name="see-also"></a>См. также статью
* [Камера с определяемым местоположением](locatable-camera.md)
* [Съемка смешанной реальности для разработчиков](mixed-reality-capture-for-developers.md)
