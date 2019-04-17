---
title: С помощью WebVR в Microsoft Edge с Windows Mixed Reality
description: Общие сведения о использовании и разработке для WebVR в Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, веб-vr, веб-xr, веб-mr, веб-ar, 360, 360 видео 360 видео, 360 фотографий, 360 фотографий, 360 содержимое, иммерсивных web, immersiveweb IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604636"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>С помощью WebVR в Microsoft Edge с Windows Mixed Reality

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Создание содержимого WebVR для Windows смешанной реальности иммерсивную

WebVR 1.1 доступен в Microsoft Edge, начиная с Windows 10 Fall Creators Update. Разработчики теперь могут использовать этот API для создания мощных приложений виртуальной Реальности в Интернете.

WebVR API предоставляет данные поза HMD страницу, которая может использоваться для отображения сцены WebGL издавать HMD. Сведения о поддержке API можно найти в [странице состояние платформы Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/). Контактная зона WebVR API присутствует на все время в Microsoft Edge. Тем не менее вызов getVRDisplays() вернет только гарнитуры Если подсоединено гарнитуры или симуляторе был включен.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Просмотр содержимого WebVR в Windows Mixed Reality иммерсивную

Инструкции для доступа к содержимому WebVR в вашей иммерсивных гарнитура можно найти в [кого руководство](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).

## <a name="see-also"></a>См. также
* [Сведения о WebVR](http://webvr.info)
* [Спецификация WebVR](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [Игровой API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) и [расширения Gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Обработка потери контекста в WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [С помощью Babylon.js, чтобы включить WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

