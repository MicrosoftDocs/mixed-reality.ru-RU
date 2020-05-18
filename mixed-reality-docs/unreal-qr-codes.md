---
title: QR-коды в Unreal
description: Введение в использование QR-кодов в Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, QR-коды
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342662"
---
# <a name="qr-codes-in-unreal"></a>QR-коды в Unreal

HoloLens умеет находить QR-коды в абсолютном пространстве и отображать голограммы на известных позициях в реальном мире.  Это позволяет, помимо прочего, визуализировать голограммы на нескольких устройствах в одном и том же расположении, чтобы создать единое взаимодействие. 

Чтобы включить обнаружение QR-кодов в HoloLens, установите флажок Webcam (Веб-камера) в разделе Project Settings (Параметры проекта) > Platform (Платформа) > HoloLens > Capabilities (Возможности) редактора Unreal.  

Включите отслеживание QR-кодов в Unreal, запустив сеанс ARSession с функцией StartARSession. 

QR-коды выводятся в виде отслеживаемого изображения через отслеживаемую геометрическую систему дополненной реальности Unreal.  Чтобы использовать эту возможность, добавьте к субъекту Blueprint (Схема) компонент AR Trackable Notify. 

![AR Trackable Notify для QR-кодов](images/unreal-spatialmapping-artrackablenotify.PNG)

Затем перейдите к сведениям об этом компоненте и зелеными кнопками "+" выберите события для отслеживания.  

![События QR-кодов](images/unreal-spatialmapping-events.PNG)

В нашем примере мы подписались на событие OnUpdateTrackedImage, чтобы отображать точку в центре QR-кода и выводить закодированные в QR-коде данные. 

![Пример отрисовки QR-кода](images/unreal-qr-render.PNG)

Сначала приведите отслеживаемое изображение к типу ARTrackedQRCode и убедитесь, что текущее обновленное изображение содержит QR-код.  Затем вы сможете получить закодированные данные через переменную QRCode.  Левый верхний край QR-кода можно получить по расположению GetLocalToWorldTransform.  Размеры кода можно получить из свойства GetEstimateSize. 

Каждый QR-код также имеет уникальный код GUID: 

![GUID для QR-кода](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>См. также статью
* [Отслеживание QR-кода](qr-code-tracking.md)
