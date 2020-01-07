---
title: Пространственные аудио учебники — 1. Добавление пространственного звука в проект
description: Добавьте подключаемый модуль Microsoft Спатиализер в проект Unity, чтобы получить доступ к аппаратной разгрузке HoloLens 2 ХРТФ.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182801"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Добавление пространственного звука в проект Unity

Добро пожаловать в пространственное аудио тутиорал для Unity на HoloLens2. В этой последовательности учебников показано следующее:
* Как использовать разгрузку ХРТФ в HoloLens 2 в Unity
* Включение переглагола при использовании разгрузки ХРТФ

В [репозитории Microsoft Спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity) есть завершенный проект Unity этой последовательности руководств. 

Рекомендации по спатиализеи звуков см. в статье как использовать [Пространственный звук](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).

## <a name="objectives"></a>Задачи
В этой первой главе вы выполните следующие действия:
* Создание проекта Unity и импорт МРТК
* Импорт подключаемого модуля Microsoft спатиализер
* Включение подключаемого модуля Microsoft спатиализер
* Включение пространственного звука на рабочей станции разработчика

## <a name="create-a-project-and-add-nuget-for-unity"></a>Создание проекта и добавление NuGet для Unity
Начните с пустого проекта Unity, а затем добавьте и настройте NuGet для Unity:
1. Скачайте последнюю версию [нужетфорунити. пакет unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. В строке меню Unity щелкните **активы-> импортировать пакет-> пользовательский пакет...** и установите пакет нужетфорунити:

![Импорт пользовательского пакета](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Добавление пакета Windows Mixed Reality
Поддержка Windows Mixed Reality в Unity 2019 и более поздних версиях содержится в необязательном пакете. Чтобы добавить его в проект, откройте **окно Диспетчер пакетов >** в строке меню Unity:

![Меню диспетчера пакетов](images/spatial-audio/package-manager-menu.png)

Затем найдите и установите пакет **Windows Mixed Reality** .

![Окно диспетчера пакетов](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>Установка МРТК и Microsoft Спатиализер
Используя NuGet для Unity, установите подключаемые модули МРТК и Microsoft Спатиализер.
1. В строке меню Unity щелкните **NuGet-> Управление пакетами NuGet**.

![Управление пакетами NuGet](images/spatial-audio/manage-nuget-packages.png)

2. В поле **поиска** введите "Microsoft. Микседреалити. Toolkit" и установите пакет мртк Core: **Microsoft. микседреалити. Toolkit. Foundation** .

![Пакет NuGet МРТК](images/spatial-audio/mrtk-nuget-package.png)

[Пакет NuGet мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) имеет дополнительный контекст и сведения.

4. В поле **поиска** введите "Microsoft. спатиалаудио" и установите пакет Microsoft Спатиализер: **Microsoft. спатиалаудио. спатиализер. Unity.**

![NuGet подключаемого модуля спатиализер](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>Настройка МРТК в проекте

1. Откройте окно параметры сборки, выбрав **файл-> параметры сборки**.

2. Выберите _универсальная платформа Windows_ и нажмите кнопку **Переключить платформу**.

3. Щелкните **Параметры проигрывателя** в **окне сборка** , чтобы открыть свойства **параметров проигрывателя** на панели **инспектора** .
    * В разделе **Параметры XR**установите флажок **Поддерживаемые виртуальные реальность** .
    * В разделе **Параметры XR**измените **режим отображения стерео** на **один экземпляр однопроходного экземпляра**.
    * В разделе **Параметры публикации**установите флажок **пространственное восприятие** в разделе **возможности** .

4. В строке меню щелкните **набор средств для смешанной реальности — > добавить в сцену и настроить..** чтобы добавить МРТК в сцену.

Дополнительные рекомендации, включая создание приложения и развертывание в HoloLens 2, см. в [главе 1 базового модуля MR Learning](mrlearning-base-ch1.md).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Включение подключаемого модуля Microsoft Спатиализер
Включите подключаемый модуль **Microsoft спатиализер** . Откройте **> параметры проекта-> аудио**и измените **подключаемый модуль Спатиализер** на "Microsoft спатиализер". Теперь раздел **аудио** в **параметрах проекта** будет выглядеть следующим образом:

![Параметры проекта, отображающие подключаемый модуль спатиализер](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Включение пространственного звука на рабочей станции
В настольных версиях Windows Пространственный звук по умолчанию отключен. Включите его, щелкнув значок тома правой кнопкой мыши на панели задач. Чтобы получить лучшее представление о том, что вы услышите в HoloLens 2, выберите **Пространственный звук — > Windows Sonic для наушников**.

![Параметры пространственного звука рабочего стола](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> Этот параметр требуется только в том случае, если планируется тестирование проекта в редакторе Unity.

## <a name="next-steps"></a>Дальнейшие действия
Переходите к [пространственному аудио разделу Unity 2](unity-spatial-audio-ch2.md) до кнопки спатиализе (звуки).
