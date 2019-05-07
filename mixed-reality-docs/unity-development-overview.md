---
title: Общие сведения о разработке Unity
description: Начало создания приложениях смешанной реальности в Unity.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Смешанный реальность, разработка, Приступая к работе, новый проект, перенос, возможность, камеры, моделирования, эмуляции, документация по Unity
ms.openlocfilehash: 2cdcd5e997ab7e3f6d340377464e453a8e7c025c
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2019
ms.locfileid: "64874004"
---
# <a name="unity-development-overview"></a>Общие сведения о разработке Unity

Самый быстрый путь к стандартных [приложением смешанной реальности](app-views.md) с [Unity](http://aka.ms/HoloLensUnity). Рекомендуется, чтобы тратить время на изучение [учебники Unity](https://unity3d.com/learn/tutorials). Если вам нужна активы, Unity имеет исчерпывающий [Asset Store](https://www.assetstore.unity3d.com/). После создания копии базовое представление о Unity, вы можете посетить [учебники](tutorials.md) Дополнительные особенности разработки смешанной реальности, с помощью Unity. Не забудьте посетить [форумы смешанной реальности Unity](http://forum.unity3d.com/forums/hololens.102/) для привлечения остальным членам сообщества создавать приложения смешанной реальности в Unity и поиск решений проблем, вы можете столкнуться.


Чтобы приступить к созданию приложений смешанной реальности в Unity, сначала [установить средства](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Новый проект Unity с помощью набора средств для смешанной реальности 

Самый простой способ разработки в Unity — с помощью средств управления смешанной реальности. Он поможет с проектом установки автоматически и предоставляют набор функций смешанной реальности, чтобы ускорить разработку. Ознакомьтесь со сведениями [смешанной реальности Toolkit v2](mrtk-getting-started.md) Дополнительные сведения и приступить к работе. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Перенос существующего приложения Unity в Windows Mixed Reality

Если у вас есть существующий проект Unity, который вы переносите в Windows Mixed Reality, выполните вместе с [руководство по переносу Unity](porting-guides.md) Чтобы приступить к работе.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Настройка нового проекта Unity для Windows Mixed Reality

Если вы хотите создать новый проект Unity без импорта смешанной реальности Toolkit, есть небольшой набор параметров Unity, вам потребуется вручную измените для смешанной реальности Windows, чтобы разделить на две категории: отдельных проектов и на сцене. Здесь приведены пошаговые инструкции для [настроить новый Unity проекта для Windows Mixed Reality](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Добавление возможности смешанной реальности и входные данные

Когда вы настроили MRTK V2 с проектом или настройки проекта, как описано выше, стандартные объекты игры Unity (например, камеры) работают и сразу же для **сидели высококлассные возможности**, с позиции камеры обновлены автоматически как пользователь перемещает их головах по всему миру.

Добавлена поддержка функций Windows Mixed Reality, такие как [пространственных этапы](coordinate-systems.md#spatial-coordinate-systems), [жесты, контроллеры движения](gestures-and-motion-controllers-in-unity.md) или [голоса](voice-input-in-unity.md) достигается с помощью API-интерфейсы, построенные непосредственно в Unity. 

Прежде всего следует просмотреть [возникнуть шкал](coordinate-systems.md) , предназначенных для приложения:
* Если вы хотите создать **только для ориентации** или **сидели высококлассные возможности**, необходимо задать тип пространства для отслеживания Unity [стационарные](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Если вы хотите создать **положение шкалы** или **комнаты высококлассные возможности**, вам потребуется убедиться Unity отслеживания тип пространства успешно присвоено [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Если вы хотите создать **высококлассные world** взаимодействия на HoloLens, позволяя пользователям перемещаться за пределы 5 м, вам потребуется использовать [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) компонента.

Все основные строительные блоки для смешанной реальности приложений, представлены в форме, совместимой с другими интерфейсами API Unity. Они также доступны в этой смешанной реальности Toolkit.
* [Камера](camera-in-unity.md)
* [Системы координат](coordinate-systems-in-unity.md)
* [Взгляд](gaze-in-unity.md)
* [Жестов и контроллеры движения](gestures-and-motion-controllers-in-unity.md)
* [Голосовой ввод](voice-input-in-unity.md)
* [Сохраняемость](persistence-in-unity.md)
* [Пространственный звук](spatial-sound-in-unity.md)
* [Пространственное сопоставление](spatial-mapping-in-unity.md)

Существуют другие ключевые функции, что во многих приложениях смешанной реальности будете использовать, также предоставляются для приложений Unity:
* [Общие возможности](shared-experiences-in-unity.md)
* [Камера с определяемым местоположением](locatable-camera-in-unity.md)
* [Точку фокуса](focus-point-in-unity.md)
* [Отслеживание потери](tracking-loss-in-unity.md)
* [Клавиатура](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Запуск проекта Unity на физическое или виртуальное устройство

После того, как проект Unity holographic готовы протестировать, ваш следующий шаг — [экспорта и сборки решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md).

С помощью этого решения VS в наличии затем запуском приложения в одном из трех способов, с помощью физическое или виртуальное устройство:
* [Развертывание на реальных HoloLens или Windows Mixed Reality иммерсивных гарнитуры](using-visual-studio.md)
* [Развертывание в эмуляторе HoloLens](using-the-hololens-emulator.md)
* [Развертывание в симуляторе иммерсивных гарнитуры смешанной реальности Windows](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Документация по Unity

В дополнение к этой документации доступны в центре разработки для Windows Unity устанавливает документации для функциональных возможностей Windows Mixed Reality совместно с редактором Unity. Unity при условии, что документация включает два отдельных разделах:
1. **Справочник по написанию скриптов Unity**
    * Этот раздел документации содержит сведения о Unity предоставляет API для выполнения сценариев.
    * Доступ из редактора Unity через **Справка > Справочник по написанию скриптов**
2. **Unity вручную**
    * Это руководство разработано для информации об использовании Unity, от простейших до самых сложных методов.
    * Доступ из редактора Unity через **Справка > вручную**

## <a name="see-also"></a>См. также
* [Смешанной реальности Toolkit v2](mrtk-getting-started.md)
* [100. Основы смешанной реальности: начало работы с Unity](holograms-100.md)
* [Рекомендуемые параметры для Unity](recommended-settings-for-unity.md)
* [Рекомендации по производительности для Unity](performance-recommendations-for-unity.md)
* [Экспорт и разработка решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Использование пространства имен Windows с приложениями Unity для HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Рекомендации по работе с Unity и Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Режим воспроизведения в Unity](unity-play-mode.md)
* [Руководства по переносу](porting-guides.md)
