---
title: Общие сведения о разработке DirectX
description: Создание на базе DirectX смешанной реальности engine непосредственно с помощью API-интерфейсов смешанной реальностью Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic визуализации, приложение native собственных приложений, WinRT, WinRT, интерфейсы API, пользовательской подсистемы платформы по промежуточного слоя
ms.openlocfilehash: 60c4de7025099f38f0902e2ff24579e7088835a6
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628997"
---
# <a name="directx-development-overview"></a>Общие сведения о разработке DirectX

Приложения используют Windows Mixed Reality [holographic отрисовки](rendering.md), [помощи](gaze.md), [жест](gestures.md), [контроллера движения](motion-controllers.md), [голоса ](voice-input.md) и [пространственное сопоставление](spatial-mapping.md) API-интерфейсы для создания [смешанной реальности](mixed-reality.md) возможности для HoloLens и иммерсивную. Вы можете создавать приложения смешанной реальности, с помощью надежной подсистемы 3D, такие как [Unity](unity-development-overview.md), или вы можете писать код непосредственно для смешанной реальности интерфейсы API Windows с помощью DirectX 11 или DirectX 12. Если вы используете непосредственно платформы, вы будете по сути разрабатывать собственные по промежуточного слоя или платформы. API-интерфейсы Windows поддерживает приложения, написанные в обоих C++ и C#. Если вы хотите использовать C#, приложения могут использовать [SharpDX](http://sharpdx.org/) библиотека программного обеспечения с открытым кодом.

Поддерживает Windows Mixed Reality [два вида приложений](app-views.md):
* **Приложениях смешанной реальности** (UWP или Win32), которых используют [HolographicSpace API](getting-a-holographicspace.md) для подготовки к просмотру [иммерсивных представление](app-views.md) пользователю, который заполняет гарнитура отображения.
* **2D приложений** (UWP), которые используют DirectX, XAML или других платформ для отрисовки [2D представлений](app-views.md#2d-views) на портативные ПК в Windows Mixed Reality home.

Различия между разработкой DirectX для [2D и иммерсивных представления](app-views.md) являются в основном связаны с holographic отрисовки и пространственных входных данных. Приложения UWP [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) или приложение Win32 HWND по-прежнему необходимы и остаются во многом так же, как интерфейсы API WinRT, доступной для приложения. Однако чтобы воспользоваться преимуществами функций holographic использовать другое подмножество этих API-интерфейсов. Например, цепочки буферов управляется системой для holographic приложений и работы с HolographicSpace API, а не DXGI выполнять [представить кадров](rendering-in-directx.md).

Чтобы приступить к разработке мощных приложений:
* Для **приложений универсальной платформы Windows**, [создайте новый проект универсальной платформы Windows с помощью шаблонов в Visual Studio](creating-a-holographic-directx-project.md). В зависимости от вашего языка **Visual C++**  или **Visual C#** , вы найдете шаблоны универсальной платформы Windows в разделе **универсальной Windows**  >   **Holographic**.
* Для **приложения Win32**, [запуск из *BasicHologram* пример Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Это отличный способ получить код, необходимо добавить поддержку holographic отрисовки для существующего приложения или ядра. Код и основные понятия представлены в шаблоне способом, который знакома любому разработчику в режиме реального времени интерактивные программного обеспечения.

## <a name="getting-started"></a>Начало работы

В следующих разделах рассматриваются основные требования добавления поддержки Windows Mixed Reality на основе DirectX по промежуточного слоя:
* [Создание проекта holographic DirectX](creating-a-holographic-directx-project.md): Шаблон holographic приложения, в сочетании с документации мы покажем различия между что вы привыкли и особых требований, представленное в устройство, которое разработано с учетом необходимости функционирование над головой.
* [Начало HolographicSpace](getting-a-holographicspace.md): Необходимо сначала создать HolographicSpace, который предоставит в ваше приложение последовательность HolographicFrame объекты, представляющие каждый головной позиции, из которого будет готовятся к просмотру.
* [Подготовка к просмотру в DirectX](rendering-in-directx.md): Так как цепочку обмена holographic имеет два целевых объектов отрисовки, вы скорее всего, потребуется внести некоторые изменения в представление приложения.
* [Системы координат в DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality изучает и обновляет его, понимание мира проверки пользователя, предоставляя пространственных координатных системах, использующих приложения делать выводы о окружения пользователя, включая пространственных привязки и определенных пространственных рабочей области пользователя.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Добавление возможности смешанной реальности и входные данные

Чтобы обеспечить максимальное удобство для пользователей иммерсивных приложений, вам понадобится для поддержки следующих ключей стандартных блоках.
* [HEAD и глаз взглядом в DirectX](gaze-in-directx.md)
* [Руки и контроллеры движения в DirectX](hands-and-motion-controllers-in-directx.md)
* [Голосовой ввод в DirectX](voice-input-in-directx.md)
* [Пространственный звук в DirectX](spatial-sound-in-directx.md)
* [Пространственное сопоставление в DirectX](spatial-mapping-in-directx.md)

Существуют другие ключевые функции, которые многие мощных приложений будет использоваться, которые также предоставляются для приложений DirectX:
* [Общие пространственные привязки в DirectX](shared-spatial-anchors-in-directx.md)
* [Камера с определяемым местоположением в DirectX](locatable-camera-in-directx.md)
* [Ввод с помощью клавиатуры, мыши и контроллера в DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>См. также
* [Модель приложений](app-model.md)
* [Представления приложений](app-views.md)
