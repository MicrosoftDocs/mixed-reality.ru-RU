---
layout: LandingPage
title: Изучите инструменты и архитектуру.
description: Документация для разработчиков приложений смешанной реальности для HoloLens и иммерсивных гарнитур.
author: grbury
ms.author: grbury
ms.date: 04/27/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Смешанная реальность, создание, разработка, HoloLens, Unity, Unreal, DirectX
ms.openlocfilehash: 97a6e130af45a9444ead5e6ed40168351c4dbbf6
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835293"
---
# <a name="learn-the-tools-and-architecture"></a>Изучите инструменты и архитектуру.

![Абстрактная трехмерная сфера](images/07_Development.png)

## <a name="expand-your-design-process"></a>[Расширение процесса разработки](case-study-expanding-the-design-process-for-mixed-reality.md)

Когда корпорация Майкрософт представила HoloLens аудитории нетерпеливых разработчиков в 2016 году, наша группа уже сотрудничала со студиями в корпорации Майкрософт и сторонними студиями для разработки средств запуска устройств. Эти команды учились, открывая новые возможности и сталкиваясь с проблемами в новой области проектирования смешанной реальности. [Подробнее](case-study-expanding-the-design-process-for-mixed-reality.md)


<br>

---


## <a name="what-technology-path-are-you-interested-in"></a>Какая технология вас интересует? 


:::row:::   
    :::column:::    
       [![Unity](images/unity_logo.png)](development.md#unity)<br>
        **[Unity](development.md#unity)**<br>   
        Unity позволяет создать кроссплатформенное полнофункциональное приложение смешанной реальности.
    :::column-end:::    
    :::column:::    
        [![Unreal](images/Unreal_logo.png)](development.md#unreal)<br>
        **[Unreal](development.md#unreal)**<br> 
        В Unreal Engine привлекательные возможности смешанной реальности сочетаются с поддержкой рабочей среды. 
    :::column-end:::
    :::column:::    
        [![JavaScript](images/web-logo.png)](development.md#javascript)<br>
        **[JavaScript](development.md#javascript)**<br>
        API устройства JavaScript и WebXR — это открытая спецификация, которая позволяет работать со смешанной реальностью в браузере на любой платформе.    
    :::column-end:::        
    :::column:::    
        [![Собственные решения](images/VisualStudio-small_logo.png)](development.md#native)<br>
        **[Собственные решения](development.md#native)**<br> 
        Создавайте приложения смешанной реальности, непосредственно используя в коде интерфейсы API Windows Mixed Reality. 
    :::column-end:::    
:::row-end:::

<br>

---

## <a name="unity"></a>Unity


### <a name="unity-development-overview"></a>[Обзор разработки в Unity](unity-development-overview.md)
Рекомендуется потратить некоторое время на изучение руководств по Unity. Если вам нужны ресурсы, в Unity есть исчерпывающий портал Asset Store. 

<br>

### <a name="microsofts-mixed-reality-toolkit-mrtk-for-unity"></a>[Mixed Reality Toolkit (MRTK) для Unity от корпорации Майкрософт](mrtk-getting-started.md)
MRTK версии 2 для Unity — это кроссплатформенный пакет SDK с открытым кодом, предназначенный для приложений смешанной реальности. MRTK версии 2 используется для ускорения разработки приложений, нацеленных на Microsoft HoloLens, иммерсивные гарнитуры (гарнитур виртуальной реальности) Windows Mixed Reality и платформу OpenVR.

<br>

### <a name="open-source-sample-apps-and-step-by-step-tutorials"></a>[Примеры приложений с открытым кодом и пошаговые руководства](tutorials.md)
Руководства по HoloLens 2 призваны помочь разработчикам в изучении методик и рекомендаций по разработке приложений смешанной реальности. Эти руководства основаны на Mixed Reality Toolkit 2.0 (MRTK 2.0).

<br>

### <a name="hand-interaction-examples-scene-mrtk-for-unity"></a>[Пример сцены для взаимодействия с помощью рук (МРТК) для Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#open-and-run-the-handinteractionexamples-scene-in-editor)
Пример сцены HandInteractionExamples.unity содержит различного вида взаимодействия и элементы управления пользовательского интерфейса, выделяемые при вводе с помощью рук.
>[!NOTE]
>Требует установки пакета МРТК Foundation и пакета примеров для Unity.

### <a name="eye-tracking-examples-mrtk-for-unity"></a>[Примеры с отслеживанием глаз (МРТК) для Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_ExamplesOverview.html)
На этой странице описывается, как быстро приступить к работе с отслеживанием глаз в МРТК, взяв за основу предоставленные примеры с отслеживанием глаз для МРТК.
>[!NOTE]
>Требует установки пакета МРТК Foundation и пакета примеров для Unity.

<br>

---

## <a name="unreal"></a>Unreal

### <a name="unreal-development-overview"></a>[Обзор разработки для Unreal](unreal-development-overview.md)
Узнайте, как создать приложение смешанной реальности на платформе Unreal.

<br>

### <a name="microsofts-mixed-reality-toolkit-mrtk-for-unreal"></a>[Набор средств для смешанной реальности для Unreal, созданный корпорацией Майкрософт](https://github.com/microsoft/MixedRealityToolkit-Unreal)
Набор средств смешанной реальности для Unreal (MRTK-Unreal) представляет собой набор таких компонентов, как подключаемые модули, примеры и документы, созданных для ускорения разработки приложений смешанной реальности с использованием Unreal Engine.

<br>

### <a name="open-source-sample-apps-and-a-step-by-step-tutorial"></a>[Примеры приложений с открытым кодом и пошаговые руководства](unreal-uxt-ch1.md)
В руководстве по началу разработки систем смешанной реальности в Unreal описан полный процесс создания приложения HoloLens 2 с использованием [средств разработки пользовательского интерфейса (UX) для Unreal версии 0.8](https://github.com/microsoft/MixedReality-UXTools-Unreal).

<br>

---

## <a name="javascript"></a>JavaScript   

### <a name="javascript-development-overview"></a>[Обзор разработки в JavaScript](javascript-development-overview.md)   
Узнайте, как создать приложение смешанной реальности для любой платформы с помощью JavaScript.

<br>

---

## <a name="native"></a>Собственный


### <a name="native-development-overview"></a>[Обзор разработки для собственной платформы](directx-development-overview.md)
Самый быстрый способ создать собственное приложение смешанной реальности.

<br>

### <a name="directx-uwp-app-templates-for-mixed-reality"></a>[Шаблоны приложений UWP с использованием DirectX для смешанной реальности](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)
Все необходимое, чтобы начать создание приложения смешанной реальности с помощью DirectX.

<br>

---


## <a name="what-would-you-like-to-do-next"></a>Что бы вы хотели сделать дальше?


:::row:::
    :::column:::
       [![Изучение основ](images/icon-lightbulb.png)](index.md#understand-the-basics)<br>
        **[Изучение основ](index.md#understand-the-basics)**<br>
        Получите более полное представление о том, что определяет смешанную реальность и как она используется.
    :::column-end:::
    :::column:::
        [![Станьте автором](images/icon-design.jpg)](design.md)<br>
         **[Станьте автором](design.md)**<br>
        Изучите основные понятия, необходимые для начала разработки и создания прототипов.
    :::column-end:::
    :::column:::
        [![Установка инструментов](images/icon-developer.jpg)](install-the-tools.md)<br>
         **[Установка инструментов](install-the-tools.md)**<br>
        Используйте контрольный список установки, чтобы получить инструменты, необходимые для создания приложений для HoloLens и смешанной реальности.
    :::column-end:::
    :::column:::
        [![Посетите мероприятие](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[Посетите мероприятие](sf-academy-events.md)**<br>
        Ознакомьтесь с оборудованием и получите практическое руководство по созданию первого приложения HoloLens 2.
    :::column-end:::
:::row-end:::


<br>

<br>
