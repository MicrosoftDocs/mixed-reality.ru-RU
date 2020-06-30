---
title: 1. Начало работы
description: Часть 1 (из 6) серии руководств по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств UX из набора средств для смешанной реальности
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, средства разработки пользовательского интерфейса, средства UX, документация
ms.openlocfilehash: 39e4e7218341dcc69eacf01f43b5e0721e76031b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720380"
---
# <a name="1-getting-started"></a>1. Начало работы

Как новичкам, так и опытным специалистам по разработке приложений смешанной реальности стоит начать работу с [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) и [Unreal Engine](https://www.unrealengine.com/en-US/) отсюда. В этой серии руководств даются пошаговые инструкции по созданию интерактивного приложения для игры в шахматы с помощью [подключаемого модуля средств UX](https://github.com/microsoft/MixedReality-UXTools-Unreal), входящего в состав [набора средств для смешанной реальности для Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). Этот подключаемый модуль содержит код, схемы и примеры, которые помогут вам реализовать распространенные функции пользовательского интерфейса в своих проектах. 

![Готовая сцена в окне просмотра](images/unreal-uxt/5-endscene.PNG)

К концу этой серии руководств вы получите практический опыт выполнения следующих задач:
* создание проекта;
* настройка проекта для смешанной реальности;
* работа с пользовательским вводом;
* добавление кнопок;
* воспроизведение на эмуляторе или устройстве.

Если у вас возникнут вопросы, ознакомьтесь с "[Обзором разработки в Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)".

## <a name="prerequisites"></a>Предварительные условия
Прежде чем приступать, обзаведитесь всем необходимым:
* Windows 10 1809 или более поздней версии.
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) версии 4.25 и выше.
* Устройство Microsoft HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode), или эмулятор.
* Visual Studio 2019 с указанными ниже рабочими нагрузками

### <a name="installing-visual-studio-2019"></a>Установка Visual Studio 2019
Последний шаг — установка Visual Studio:
1. Установите последнюю версию [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).
2. Установите следующие [рабочие нагрузки](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):
    * "Разработка классических приложений на C++";
    * "Разработка классических приложений .NET";
    * "Разработка приложений для универсальной платформы Windows".

3. Установите следующие [компоненты](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):
    * компиляторы, средства сборки и среды выполнения > средства сборки MSVC v142 — VS 2019 C++ ARM64 (последняя версия).

Вот и все! Можно приступать к проекту по созданию шахматного приложения.

[Следующий раздел: 2. Инициализация проекта и первое приложение](unreal-uxt-ch2.md)