---
title: Общие сведения о разработке DirectX
description: Создание на базе DirectX смешанной реальности engine непосредственно с помощью API-интерфейсов смешанной реальностью Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic визуализации, приложение native собственных приложений, WinRT, WinRT, интерфейсы API, пользовательской подсистемы платформы по промежуточного слоя
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414386"
---
# <a name="directx-development-overview"></a>Общие сведения о разработке DirectX


Приложения Windows Mixed Reality использовать [holographic отрисовки](rendering.md), [помощи](gaze.md), [жест](gestures.md), [контроллера движения](motion-controllers.md), [голосовой](voice-input.md), и [пространственное сопоставление](spatial-mapping.md) API-интерфейсы для создания [смешанной реальности](mixed-reality.md) возможности для HoloLens и иммерсивную. Можно создавать с помощью надежной подсистемы 3D, таких как приложения смешанной реальности [Unity](unity-development-overview.md), или вы можете писать код непосредственно для смешанной реальности интерфейсы API Windows с помощью DirectX 11 или DirectX 12. Если вы используете непосредственно платформы, вы будете по сути разрабатывать собственные по промежуточного слоя или платформы. API-интерфейсы Windows поддерживают приложения, написанные в обоих C++ и C#. Если вы решили использовать C#, приложения могут использовать [SharpDX](http://sharpdx.org/) библиотека программного обеспечения с открытым кодом.


Поддерживает Windows Mixed Reality [два вида приложений](app-views.md):
* **Смешанных приложений реальности** (UWP или Win32), которые используют [HolographicSpace API](getting-a-holographicspace.md) для подготовки к просмотру [иммерсивных представление](app-views.md) пользователю, который заполняет гарнитура отображения.
* **2D приложений** (UWP), использующие DirectX, XAML или других платформ для подготовки к просмотру [2D представлений](app-views.md#2d-views) на портативные ПК в Windows Mixed Reality home.


Различия между разработкой DirectX для [2D и иммерсивных представления](app-views.md) являются в основном связаны с holographic отрисовки и пространственных входных данных. Приложение UWP [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) или приложение Win32 HWND являются обязательными, а остаются во многом так же, как интерфейсы API WinRT, доступными для приложения. Тем не менее необходимо использовать другое подмножество этих API-интерфейсов, чтобы воспользоваться преимуществами функций holographic. Например цепочки буферов управляется системой для holographic appslications. Работе с HolographicSpace API, а не DXGI выполнять [представить кадров](rendering-in-directx.md).

Чтобы приступить к разработке мощных приложений:
* Для **приложений универсальной платформы Windows**, [создайте новый проект универсальной платформы Windows с помощью шаблонов в Visual Studio](creating-a-holographic-directx-project.md). В зависимости от вашего языка **Visual C++**  или **Visual C#** , можно найти шаблоны универсальной платформы Windows в разделе **универсальной Windows**  >   **Holographic**.
* Для **приложений Win32**, [запуск из *BasicHologram* пример Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Это отличный способ получить код, который необходимо добавить поддержку holographic отрисовки для существующего приложения или ядра. Код и основные понятия представлены в шаблоне способом, который знакома любому разработчику в режиме реального времени интерактивные программного обеспечения.


## <a name="getting-started"></a>Начало работы

В следующих разделах рассматриваются основные требования добавления поддержки Windows Mixed Reality на основе DirectX по промежуточного слоя:

* [Создание проекта holographic DirectX](creating-a-holographic-directx-project.md): Шаблон holographic приложения, в сочетании с документации показаны различия между что вы привыкли, а также особые требования, представленное в устройство, которое разработано с учетом необходимости работать при наведении на голове.
* [Начало HolographicSpace](getting-a-holographicspace.md): Необходимо сначала создать HolographicSpace, предоставляющий приложения последовательность HolographicFrame объекты, представляющие каждый головной позиции, из которого будет готовятся к просмотру.
* [Подготовка к просмотру в DirectX](rendering-in-directx.md): Так как цепочку обмена holographic имеет два целевых объектов отрисовки, необходимо внести некоторые изменения в представление приложения.
* [Системы координат в DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality изучает и обновляет его основные сведения о мира когда пользователь выходит вокруг. Это обеспечивает Пространственные системы координат, что приложения используют делать выводы о окружения пользователя, в том числе пространственных привязки и пользователя определенные пространственных рабочей области.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Добавление возможности смешанной реальности и входные данные

Чтобы обеспечить максимальное удобство для пользователей вашей иммерсивных appslication, вам понадобится для поддержки следующих ключей стандартных блоках.

* [Направление головы и взгляда в DirectX](gaze-in-directx.md)
* [Контроллеры движения и жестов в DirectX](hands-and-motion-controllers-in-directx.md)
* [Голосовой ввод в DirectX](voice-input-in-directx.md)
* [Пространственный звук в DirectX](spatial-sound-in-directx.md)
* [Пространственное сопоставление в DirectX](spatial-mapping-in-directx.md)


Существуют другие ключевые функции, которые будут использовать многие иммерсивные приложения, которые также доступны в приложениях DirectX:

* [Общие пространственные привязки в DirectX](shared-spatial-anchors-in-directx.md)
* [Камера с определяемым местоположением в DirectX](locatable-camera-in-directx.md)
* [Ввод с помощью клавиатуры, мыши и контроллера в DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>См. также
* [Модель приложений](app-model.md)
* [Представления приложений](app-views.md)
