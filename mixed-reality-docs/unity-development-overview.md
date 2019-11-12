---
title: Общие сведения о разработке Unity
description: Начало работы по созданию приложений смешанной реальности в Unity.
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
keywords: Unity, Mixed Reality, разработка, начало работы, новый проект, перенос, возможность, Камера, моделирование, Эмуляция, документация
ms.openlocfilehash: f9b314bfc7c58e72b11ecfd76fe7293ef2f6c11e
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926697"
---
# <a name="unity-development-overview"></a>Общие сведения о разработке Unity

Самым быстрым путем создания [приложения смешанной реальности](app-views.md) является [Unity](https://unity.com). Для изучения [учебников по Unity](https://unity3d.com/learn/tutorials)рекомендуется пройти некоторое время. Если вам нужны активы, в Unity есть исчерпывающее [хранилище активов](https://www.assetstore.unity3d.com/). После создания базового понимания Unity вы можете посетить [учебники](tutorials.md) , чтобы изучить особенности разработки смешанной реальности с Unity. Не забудьте посетить [форумы Unity Mixed Reality](https://forum.unity3d.com/forums/hololens.102/) , чтобы привлечь внимание к остальным участникам сообщества, создающим приложения смешанной реальности в Unity, и найти решения проблем, с которыми вы можете столкнуться.

Чтобы приступить к созданию приложений смешанной реальности с помощью Unity, сначала [установите средства](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Новый проект Unity с набором средств Mixed Reality 

Самым простым способом разработки в Unity является набор средств Mixed Reality. Это поможет вам автоматически настроить проект и предоставить набор функций смешанной реальности для ускорения разработки. Ознакомьтесь с [набором средств для смешанной реальности версии 2](mrtk-getting-started.md) , чтобы узнать больше и приступить к работе. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Перенос существующего приложения Unity на Windows Mixed Reality

Если у вас есть проект Unity, перенесенный в Windows Mixed Reality, следуйте указаниям в разделе Руководство по [переносу Unity](porting-guides.md) , чтобы приступить к работе.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Настройка нового проекта Unity для Windows Mixed Reality

Если вы хотите создать новый проект Unity без импорта набора средств для смешанной реальности, существует небольшой набор параметров Unity, которые потребуется вручную изменить для Windows Mixed Reality. Они делятся на две категории: на проект и на сцену. Ознакомьтесь с пошаговым руководством по [настройке нового проекта Unity для Windows Mixed Reality](Configure-Unity-Project.md) .

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Добавление возможностей и входных данных смешанной реальности

После настройки МРТК v2 с помощью проекта или настройки проекта, как описано выше, стандартные объекты игры Unity (например, Камера) немедленно становятся недоступными для **работы с возможностями масштабирования**, при этом расположение камеры автоматически обновляется как пользователь перемещает свой заголовок по всему миру.

Добавление поддержки функций Windows Mixed Reality, таких как [пространственные этапы](coordinate-systems.md#spatial-coordinate-systems), [жесты, контроллеры движения](gestures-and-motion-controllers-in-unity.md) или [Ввод голоса](voice-input-in-unity.md) , достигается с помощью API, встроенных непосредственно в Unity. 

Сначала ознакомьтесь с [возможностями масштабирования](coordinate-systems.md) , которые могут ориентироваться в приложении.
* Если вы хотите создать **интерфейс**, предназначенный **только для ориентации** или установки, необходимо установить тип пространства отслеживания Unity в положение " [стационарный](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)".
* Если вы собираетесь создать интерфейс масштабирования в фиксированном **масштабе или на** **уровне комнаты**, необходимо убедиться, что тип пространства отслеживания Unity успешно установлен в [румскале](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Если вы хотите создать в HoloLens интерфейс по **всему миру** , который позволит пользователям перемещаться за пределы 5 метров, необходимо использовать компонент [ворлданчор](coordinate-systems-in-unity.md#building-a-world-scale-experience) .

Все основные стандартные блоки для приложений смешанной реальности предоставляются способом, согласованным с другими API Unity. Они также доступны в наборе средств Mixed Reality.
* [Камера](camera-in-unity.md)
* [Системы координат](coordinate-systems-in-unity.md)
* [Взгляд](gaze-in-unity.md)
* [Жесты и контроллеры движения](gestures-and-motion-controllers-in-unity.md)
* [Голосовой ввод](voice-input-in-unity.md)
* [Сохраняемости](persistence-in-unity.md)
* [Пространственный звук](spatial-sound-in-unity.md)
* [Пространственное сопоставление](spatial-mapping-in-unity.md)

Существуют и другие ключевые функции, которые многие приложения смешанной реальности будут использовать в приложениях Unity.
* [Общие возможности](shared-experiences-in-unity.md)
* [Камера с определяемым местоположением](locatable-camera-in-unity.md)
* [Фокусная точка](focus-point-in-unity.md)
* [Отслеживание потерь](tracking-loss-in-unity.md)
* [Клавиатура](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Запуск проекта Unity на реальном или имитируемом устройстве

После того, как проект "holographic Unity" готов к тестированию, вы можете выполнить [Экспорт и сборку решения Unity Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md).

С помощью этого решения VS можно запустить приложение одним из трех способов, используя реальное или имитацию устройства:
* [Развертывание на реальной виртуальной гарнитуре HoloLens или Windows Mixed Reality](using-visual-studio.md)
* [Развертывание в эмуляторе HoloLens](using-the-hololens-emulator.md)
* [Развертывание в симуляторе гарнитуры Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Документация по Unity

Помимо этой документации, доступной в docs.microsoft.com, Unity устанавливает документацию по функциям Windows Mixed Reality вместе с редактором Unity. Предоставленная документация по Unity включает два отдельных раздела:
1. **Справочник по скриптам Unity**
    * В этом разделе документации содержатся сведения о API скриптов, предоставляемых Unity.
    * Доступ к редактору Unity с помощью **справки > Справочник по сценариям**
2. **Руководство по Unity**
    * Это руководство призвано помочь вам научиться использовать Unity — от базовых до продвинутых методик.
    * Доступ к редактору Unity с помощью **справки > вручную**

## <a name="see-also"></a>См. также
* [Набор средств Mixed Reality версии 2](mrtk-getting-started.md)
* [Основные сведения о MR 100: Начало работы с Unity](holograms-100.md)
* [Рекомендуемые параметры для Unity](recommended-settings-for-unity.md)
* [Рекомендации по производительности для Unity](performance-recommendations-for-unity.md)
* [Экспорт и разработка решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Использование пространства имен Windows с приложениями Unity для HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Рекомендации по работе с Unity и Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Режим воспроизведения в Unity](unity-play-mode.md)
* [Руководства по переносу](porting-guides.md)
