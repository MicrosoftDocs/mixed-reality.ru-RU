---
title: Обзор разработки в Unity
description: Приступите к созданию приложений смешанной реальности в Unity.
author: thetuvix
ms.author: kurtie
ms.date: 07/29/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, смешанная реальность, разработка, приступая к работе, новый проект, перенос, возможность, камера, имитация, эмуляция, документация
ms.openlocfilehash: 4679e1a2b58a7e0d77e6b295803624a4de1fac19
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476716"
---
# <a name="unity-development-overview"></a>Обзор разработки в Unity

Самым быстрым средством создания [приложения смешанной реальности](app-views.md) является [Unity](https://unity.com). Рекомендуется потратить некоторое время на изучение [руководств по Unity](https://unity3d.com/learn/tutorials). Если вам нужны ресурсы, в Unity есть исчерпывающий портал [Asset Store](https://www.assetstore.unity3d.com/). Изучив основы Unity, вы можете перейти к [руководствам](tutorials.md), чтобы изучить особенности разработки смешанной реальности с помощью Unity. Обязательно посетите [форумы по смешанной реальности Unity](https://forum.unity3d.com/forums/hololens.102/), чтобы присоединиться к остальным участникам сообщества разработчиков приложений смешанной реальности в Unity и находить решения проблем, с которыми вы можете столкнуться.

Чтобы приступить к созданию приложений смешанной реальности с помощью Unity, сначала [установите инструменты](install-the-tools.md).

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Создание проекта Unity с помощью набора средств для смешанной реальности (MRTK) 

Проще всего разрабатывать приложения в Unity с помощью Mixed Reality Toolkit, который обеспечит автоматическую настройку проекта и предоставит набор функций смешанной реальности, позволяющих ускорить разработку. Чтобы узнать больше и приступить к работе, ознакомьтесь с [Mixed Reality Toolkit версии 2](mrtk-getting-started.md). 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Перенос существующего приложения Unity в Windows Mixed Reality

Если у вас есть проект Unity, который нужно перенести в Windows Mixed Reality, следуйте указаниям в [руководстве по переносу в Unity](porting-guides.md), чтобы приступить к работе.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Настройка нового проекта Unity для Windows Mixed Reality

Если вы хотите создать проект Unity без импорта Mixed Reality Toolkit, то вам потребуется настроить несколько параметров Unity для Windows Mixed Reality. Они делятся на две категории: параметры проекта и параметры сцены. Пошаговые инструкции приведены в разделе [Настройка нового проекта Unity для Windows Mixed Reality](Configure-Unity-Project.md).

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Добавление возможностей и средств ввода смешанной реальности

После настройки MRTK версии 2 для проекта или настройки проекта согласно приведенным выше инструкциям немедленно активируются стандартные игровые объекты Unity (например, камера) в **режиме сидящего оператора**. При этом положение камеры изменяется автоматически, когда пользователь двигает головой.

Добавление поддержки функций Windows Mixed Reality, таких как [пространственные сцены](coordinate-systems.md#spatial-coordinate-systems), [жесты, контроллеры движений](gestures-and-motion-controllers-in-unity.md) или [голосовой ввод](voice-input-in-unity.md), возможно благодаря интерфейсам API, встроенным непосредственно в Unity. 

Сначала изучите целевой [масштаб взаимодействия](coordinate-systems.md) для приложения.
* Если вы хотите реализовать только поддержку **определения направления** или **режима сидящего оператора**, необходимо будет задать для пространства отслеживания Unity тип [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Если вы хотите реализовать поддержку **режима стоящего оператора** или **виртуального помещения**, необходимо убедиться, что для пространства отслеживания Unity задан тип [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Если вы хотите реализовать **виртуальный мир** в HoloLens, который позволяет пользователям перемещаться дальше чем на 5 метров, потребуется использовать компонент [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience).

Все основные стандартные блоки для приложений смешанной реальности предоставляются так же, как и другие интерфейсы API Unity. Они также доступны в наборе средств для смешанной реальности.
* [Камера](camera-in-unity.md)
* [Системы координат](coordinate-systems-in-unity.md)
* [Взгляд](gaze-in-unity.md)
* [Жесты и контроллеры движений](gestures-and-motion-controllers-in-unity.md)
* [Голосовой ввод](voice-input-in-unity.md)
* [Сохраняемость](persistence-in-unity.md)
* [Пространственный звук](spatial-sound-in-unity.md)
* [Пространственное сопоставление](spatial-mapping-in-unity.md)

Существуют и другие ключевые функции для приложений Unity, которые потребуются многим приложениям смешанной реальности:
* [общие возможности](shared-experiences-in-unity.md);
* [Камера с определяемым местоположением](locatable-camera-in-unity.md)
* [точка фокусировки](focus-point-in-unity.md);
* [потеря слежения](tracking-loss-in-unity.md);
* [Клавиатура](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Запуск проекта Unity на физическом или имитированном устройстве

После подготовки голографического проекта Unity к тестированию следующим шагом является [экспорт и сборка решения Unity в Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md).

С помощью этого решения Visual Studio можно будет запустить приложение одним из трех способов, используя физическое или имитированное устройство:
* [развертывание на физической иммерсивной гарнитуре HoloLens или Windows Mixed Reality](using-visual-studio.md);
* [развертывание в эмуляторе HoloLens](using-the-hololens-emulator.md);
* [развертывание в симуляторе иммерсивной гарнитуры Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md).

## <a name="unity-documentation"></a>Документация по Unity

Помимо этой документации, доступной на сайте docs.microsoft.com, вместе с редактором Unity платформа устанавливает документацию по функциям Windows Mixed Reality. Предоставленная документация по Unity включает в себя два раздела:
1. **Справочник по сценариям Unity**.
    * В этом разделе документации содержатся сведения об API сценариев, предоставляемых Unity.
    * Чтобы перейти к нему, следует открыть редактор Unity и выбрать **Help (Справка) > Scripting Reference (Справочник по сценариям)** .
2. **Руководство по Unity**.
    * Это руководство призвано помочь вам научиться использовать Unity — от простых до усложненных методик.
    * Чтобы перейти к нему, следует открыть редактор Unity и выбрать **Help (Справка) > Manual (Руководство)** .

## <a name="see-also"></a>См. также статью
* [Набор средств для смешанной реальности версии 2](mrtk-getting-started.md)
* [100. Основы смешанной реальности: начало работы с Unity](holograms-100.md)
* [Рекомендуемые параметры для Unity](recommended-settings-for-unity.md)
* [Рекомендации по производительности для Unity](performance-recommendations-for-unity.md)
* [Экспорт и разработка решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Использование пространства имен Windows с приложениями Unity для HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Рекомендации по работе с Unity и Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Режим воспроизведения в Unity](unity-play-mode.md)
* [Руководства по переносу приложений](porting-guides.md)
