---
title: 1. Начало работы
description: Часть 1 руководства по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств разработки пользовательского интерфейса (UX) из набора средств для смешанной реальности
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, средства разработки пользовательского интерфейса, средства UX, документация
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840133"
---
# <a name="1-getting-started"></a><span data-ttu-id="ad108-104">1. Начало работы</span><span class="sxs-lookup"><span data-stu-id="ad108-104">1. Getting started</span></span>

<span data-ttu-id="ad108-105">В этом пошаговом руководстве показано, как создать интерактивное приложение для игры в шахматы для HoloLens 2 с помощью Unreal Engine 4.</span><span class="sxs-lookup"><span data-stu-id="ad108-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="ad108-106">Вы также узнаете, как подключаемый модуль средств разработки пользовательского интерфейса (UX) из набора средств смешанной реальности позволяет ускорить разработку.</span><span class="sxs-lookup"><span data-stu-id="ad108-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="ad108-107">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="ad108-107">Prerequisites</span></span>

* <span data-ttu-id="ad108-108">Windows 10 1809 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ad108-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="ad108-109">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="ad108-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="ad108-110">Unreal Engine 4.25 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ad108-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="ad108-111">Устройство Microsoft HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode), или эмулятор.</span><span class="sxs-lookup"><span data-stu-id="ad108-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="ad108-112">Visual Studio 2019 (с перечисленными ниже рабочими нагрузками и компонентами).</span><span class="sxs-lookup"><span data-stu-id="ad108-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="ad108-113">Установка Visual Studio 2019, рабочих нагрузок и компонентов</span><span class="sxs-lookup"><span data-stu-id="ad108-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="ad108-114">Установите последнюю версию Visual Studio 2019 или выполните обновление до этой версии.</span><span class="sxs-lookup"><span data-stu-id="ad108-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="ad108-115">Скачать Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ad108-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="ad108-116">Установите следующие рабочие нагрузки:</span><span class="sxs-lookup"><span data-stu-id="ad108-116">Install the following workloads:</span></span>
* <span data-ttu-id="ad108-117">"Разработка классических приложений на C++";</span><span class="sxs-lookup"><span data-stu-id="ad108-117">Desktop development with C++</span></span>
* <span data-ttu-id="ad108-118">"Разработка классических приложений .NET";</span><span class="sxs-lookup"><span data-stu-id="ad108-118">.NET desktop development</span></span>
* <span data-ttu-id="ad108-119">"Разработка приложений для универсальной платформы Windows".</span><span class="sxs-lookup"><span data-stu-id="ad108-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="ad108-120">Установите следующие дополнительные компоненты:</span><span class="sxs-lookup"><span data-stu-id="ad108-120">Install the following individual components:</span></span>
* <span data-ttu-id="ad108-121">компиляторы, средства сборки и среды выполнения > средства сборки MSVC v142 — VS 2019 C++ ARM64 (последняя версия).</span><span class="sxs-lookup"><span data-stu-id="ad108-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="ad108-122">Следующий раздел: 2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="ad108-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)