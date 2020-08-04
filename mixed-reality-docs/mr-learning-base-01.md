---
title: Серия руководств по началу работы, часть 1 Введение
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 330863d36abe051e8fe17b87ce913b1b110e2d3d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376436"
---
# <a name="1-introduction"></a><span data-ttu-id="5a865-105">1. Введение</span><span class="sxs-lookup"><span data-stu-id="5a865-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="5a865-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="5a865-106">Overview</span></span>

<span data-ttu-id="5a865-107">Приветствуем вас в серии руководств по началу работы!</span><span class="sxs-lookup"><span data-stu-id="5a865-107">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="5a865-108">Из этих руководств вы узнаете о наборе средств для смешанной реальности (MRTK) и некоторых его функциях.</span><span class="sxs-lookup"><span data-stu-id="5a865-108">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="5a865-109">Кроме того, вы создадите взаимодействие в смешанной реальности, чтобы пользователи могли рассмотреть голограмму, созданную по модели марсохода NASA Curiosity.</span><span class="sxs-lookup"><span data-stu-id="5a865-109">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="5a865-110">Пройдя эту серию, вы сможете уверенно работать с MRTK и ускорите процесс разработки.</span><span class="sxs-lookup"><span data-stu-id="5a865-110">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="5a865-111">Руководства в этой серии идут последовательно, поэтому изучайте их в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="5a865-111">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. [<span data-ttu-id="5a865-112">Введение</span><span class="sxs-lookup"><span data-stu-id="5a865-112">Introduction</span></span>](mr-learning-base-01.md)
2. [<span data-ttu-id="5a865-113">Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="5a865-113">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="5a865-114">Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="5a865-114">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="5a865-115">Размещение объектов в сцене</span><span class="sxs-lookup"><span data-stu-id="5a865-115">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="5a865-116">Создание динамического содержимого с помощью решателей</span><span class="sxs-lookup"><span data-stu-id="5a865-116">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="5a865-117">Создание пользовательских взаимодействий</span><span class="sxs-lookup"><span data-stu-id="5a865-117">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="5a865-118">Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="5a865-118">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="5a865-119">Использование функции отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="5a865-119">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="5a865-120">Использование голосовых команд</span><span class="sxs-lookup"><span data-stu-id="5a865-120">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="5a865-121">Задачи</span><span class="sxs-lookup"><span data-stu-id="5a865-121">Objectives</span></span>

* <span data-ttu-id="5a865-122">Узнать, как настроить Unity для MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a865-122">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="5a865-123">Узнать, как выполнять сборку и развертывание на устройстве.</span><span class="sxs-lookup"><span data-stu-id="5a865-123">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="5a865-124">Узнать, как использовать некоторые из основных функций MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a865-124">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="5a865-125">Создать полное взаимодействие смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5a865-125">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a865-126">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="5a865-126">Prerequisites</span></span>

* <span data-ttu-id="5a865-127">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5a865-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="5a865-128">[Пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="5a865-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="5a865-129">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="5a865-129">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="5a865-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="5a865-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="5a865-131">Рекомендуемая версия MRTK для этой серии руководств — MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="5a865-131">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="5a865-132">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="5a865-132">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="5a865-133">Это заменяет все требования к версии Unity, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="5a865-133">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="5a865-134">Следующее руководство: 2. Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="5a865-134">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
