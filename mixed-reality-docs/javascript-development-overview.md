---
title: Общие сведения о разработке JavaScript в смешанной реальности
description: Общие сведения о разработке смешанной реальности с использованием JavaScript для веб-, мобильных и высококачественных головных телефонов Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: Вебкср, Винмр, Вебар, Вебвр, Виндовсмикседреалити, HoloLens, Windows Mixed Reality, веб-VR, Web XR, Web MR, Web AR, 360, 360 Video, 360 видео, 360 Photo, 360 фотографии, 360 Content, иммерсивное веб-узел, иммерсивное веб-сайт, IW, иммерсивевеб
ms.openlocfilehash: a1288e8f477f42b0937e797623fb83fe8f63685c
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835613"
---
# <a name="mixed-reality-development-with-javascript-overview"></a>Обзор разработки смешанной реальности с использованием JavaScript

## <a name="mixed-reality-applications-on-the-web"></a>Приложения смешанной реальности в Интернете

Функции смешанной реальности доступны в Интернете с помощью [API-интерфейсов устройств вебкср](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) и [устаревших API вебвр](webxr-overview.md). Для браузеров, которые не поддерживают полные функции Вебкср, можно добавить [вебксрные заливки](https://github.com/immersive-web/webxr-polyfill) на веб-сайт.

## <a name="what-is-webxr-polyfill"></a>Что такое Вебксрная Заливка

Реализация API устройства Вебкср на JavaScript, а также модуль игровой планшет Вебкср. Эта Заливка позволяет разработчикам писать в соответствии с последней спецификацией, предоставляя поддержку при запуске в браузерах, которые реализуют спецификацию Вебвр 1,1, или на мобильных устройствах без поддержки Вебвр/Вебкср.

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>Библиотеки JavaScript для создания приложений смешанной реальности в Интернете

## <a name="babylonjs"></a>Бабилон. js

Бабилон — это трехмерный модуль JavaScript, который упрощает разработку трехмерного содержимого и впечатляющих приложений. Прежде чем приступить к работе с иммерсивное приложение, рекомендуется изучить основы разработки Бабилон. js.

Узнайте, как создать приложение смешанной реальности с помощью Бабилон в [разделе Приступая к работе](https://doc.babylonjs.com/). Воспроизводите трехмерные примеры и их исходный код с помощью [Бабилон Playground](https://doc.babylonjs.com/examples/). Познакомьтесь с разработкой смешанной реальности в [разделе вебкср](https://doc.babylonjs.com/how_to/introduction_to_webxr) документации. 

## <a name="a-frame"></a>A-кадр

A-Frame — это декларативная платформа JavaScript, позволяющая начать работу с Virtual Reality в Интернете. Ознакомьтесь с [документацией по кадрам,](https://aframe.io/) чтобы узнать больше.

## <a name="threejs"></a>Три JS

Три. js — популярная трехмерная библиотека для создания впечатляющих возможностей. Дополнительные сведения о [трех. js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) на странице документации и [примеры](https://threejs.org/examples/#webgl_animation_cloth)см. здесь.

## <a name="webgl"></a>WebGL

Доступ к API устройства Вебкср можно получить непосредственно с помощью API-интерфейсов WebGL. WebGL (Библиотека веб-графики) — это API JavaScript для визуализации высокопроизводительной интерактивной трехмерной и двухмерной графики в любом совместимом веб-браузере без использования подключаемых модулей. Дополнительные сведения об [интерфейсах API WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>Собственные мобильные приложения смешанной реальности с использованием JavaScript

С помощью нескольких библиотек JavaScript вы можете писать свои возможности смешанной реальности и развертывать их в Интернете и на собственных платформах, таких как гарнитуры Windows Mixed Reality, устройства Android и iOS.

## <a name="babylon-native"></a>Бабилон Native

[Бабилон собственная](https://www.babylonjs.com/native/) платформа позволяет любому пользователю взять свой код Бабилон. js и создать собственное приложение с ним, разблокируя возможности собственных технологий. Вы можете скачать [Бабилон Native на сайте GitHub](https://github.com/BabylonJS/BabylonNative) и прочесть дополнительные сведения о нем в [блоге Бабилон. js](https://medium.com/@babylonjs/babylon-native-821f1694fffc).

## <a name="react-native"></a>React Native

[Реакция на машинный код](https://reactnative.dev/) — это еще одна библиотека с открытым исходным кодом, которая позволяет разработчикам создавать с помощью JavaScript и развертывать на нескольких платформах Вы можете скачать [собственное реагирование на GitHub](https://github.com/facebook/react-native) и узнать больше о нем в блоге, посвященном [собственному реагированию](https://reactnative.dev/blog/).

## <a name="see-also"></a>См. также

* [Обзор Вебкср](webxr-overview.md)
* [Спецификация API устройства Вебкср](https://immersive-web.github.io/webxr/)
* [Документация по API устройства Вебкср](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Иммерсивевеб. dev](https://immersiveweb.dev/)
* [Примеры Вебкср](https://immersive-web.github.io/webxr-samples/)
* [Использование Бабилон. js для создания Вебксрных возможностей](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality и новая Microsoft ребро](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Иммерсивное веб-сайт W3C GitHub](https://github.com/immersive-web)
* [API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* Расширения [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) и [игровой](https://w3c.github.io/gamepad/extensions.html) планшета
* [Обзор Вебвр](webvr-overview.md)
