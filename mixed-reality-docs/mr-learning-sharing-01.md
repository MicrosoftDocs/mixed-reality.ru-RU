---
title: Руководства по многопользовательским возможностям, часть 1. Введение
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: eff600ba6388732ab9aa200ce41494cac1dddf35
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306799"
---
# <a name="1-introduction"></a><span data-ttu-id="94e0a-105">1. Введение</span><span class="sxs-lookup"><span data-stu-id="94e0a-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="94e0a-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="94e0a-106">Overview</span></span>

<span data-ttu-id="94e0a-107">Приветствуем в руководствах по многопользовательским возможностям!</span><span class="sxs-lookup"><span data-stu-id="94e0a-107">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="94e0a-108">Из этой серии руководств вы узнаете об основных принципах создания многопользовательских взаимодействий с помощью <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span><span class="sxs-lookup"><span data-stu-id="94e0a-108">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="94e0a-109">PUN — это одна из нескольких сетевых платформ, на основе которых разработчики смешанной реальности могут создавать совместные взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="94e0a-109">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="94e0a-110">Руководства в этой серии:</span><span class="sxs-lookup"><span data-stu-id="94e0a-110">Tutorials in this series:</span></span>

* [<span data-ttu-id="94e0a-111">Настройка Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="94e0a-111">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="94e0a-112">Подключение нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="94e0a-112">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="94e0a-113">Предоставление разным пользователям общего доступа к перемещениям объекта</span><span class="sxs-lookup"><span data-stu-id="94e0a-113">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="94e0a-114">Интеграция Пространственных привязок Azure в общее взаимодействие</span><span class="sxs-lookup"><span data-stu-id="94e0a-114">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="94e0a-115">Задачи</span><span class="sxs-lookup"><span data-stu-id="94e0a-115">Objectives</span></span>

* <span data-ttu-id="94e0a-116">Узнать, как создать приложение PUN и подключить к нему проект Unity.</span><span class="sxs-lookup"><span data-stu-id="94e0a-116">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="94e0a-117">Подключение нескольких пользователей к общему взаимодействию</span><span class="sxs-lookup"><span data-stu-id="94e0a-117">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="94e0a-118">Узнать, как предоставлять разным пользователям общий доступ к перемещениям объекта.</span><span class="sxs-lookup"><span data-stu-id="94e0a-118">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="94e0a-119">Узнать, как реализовать пространственное выравнивание на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="94e0a-119">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94e0a-120">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="94e0a-120">Prerequisites</span></span>

* <span data-ttu-id="94e0a-121">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="94e0a-121">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="94e0a-122">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="94e0a-122">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="94e0a-123">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="94e0a-123">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="94e0a-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="94e0a-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="94e0a-125">Выполненные инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) статьи [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="94e0a-125">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="94e0a-126">Знакомство с серией [руководств по началу работы](mr-learning-base-01.md) или базовый опыт работы с Unity и MRTK.</span><span class="sxs-lookup"><span data-stu-id="94e0a-126">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="94e0a-127">Знакомство с серией [руководств по Пространственным привязкам Azure](mr-learning-asa-01.md) или опыт создания учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="94e0a-127">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="94e0a-128">Если планируется развертывание на устройствах Android и HoloLens</span><span class="sxs-lookup"><span data-stu-id="94e0a-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="94e0a-129">Устройство Android с <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">включенными возможностями разработки</a> и <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">поддержкой ARCore</a>, подключенное через USB к компьютеру Windows или macOS.</span><span class="sxs-lookup"><span data-stu-id="94e0a-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="94e0a-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем Android Build Support.</span><span class="sxs-lookup"><span data-stu-id="94e0a-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="94e0a-131">Если планируется развертывание на устройствах iOS и HoloLens</span><span class="sxs-lookup"><span data-stu-id="94e0a-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="94e0a-132">Компьютер macOS с последней версией <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> и <a href="https://cocoapods.org" target="_blank">CocoaPods</a>.</span><span class="sxs-lookup"><span data-stu-id="94e0a-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="94e0a-133"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">Совместимое с ARKit</a> устройство iOS, подключенное через USB к компьютеру macOS.</span><span class="sxs-lookup"><span data-stu-id="94e0a-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="94e0a-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем iOS Build Support.</span><span class="sxs-lookup"><span data-stu-id="94e0a-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="94e0a-135">Рекомендуемая версия набора средств для смешанной реальности для этой серии руководств — МРТК 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="94e0a-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="94e0a-136">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="94e0a-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="94e0a-137">Это заменяет все требования к версии Unity, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="94e0a-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="94e0a-138">Следующее руководство: 2. Настройка Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="94e0a-138">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
