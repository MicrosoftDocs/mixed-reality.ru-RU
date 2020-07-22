---
title: Руководства по Пространственным привязкам Azure, часть 1 Введение
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6a015b4c9f6a5c1a92697ef9909443234a98ab09
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306022"
---
# <a name="1-introduction"></a><span data-ttu-id="0535f-105">1. Введение</span><span class="sxs-lookup"><span data-stu-id="0535f-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="0535f-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="0535f-106">Overview</span></span>

<span data-ttu-id="0535f-107">Добро пожаловать в руководства по Пространственным привязкам Azure!</span><span class="sxs-lookup"><span data-stu-id="0535f-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="0535f-108">Из этой серии руководств вы узнаете о <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Пространственных привязках Azure</a> (ASA) и о том, как использовать возможности смешанной реальности в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="0535f-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="0535f-109">Вы также узнаете, как развернуть проект в Android и iOS.</span><span class="sxs-lookup"><span data-stu-id="0535f-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="0535f-110">Руководства в этой серии:</span><span class="sxs-lookup"><span data-stu-id="0535f-110">Tutorials in this series:</span></span>

1. [<span data-ttu-id="0535f-111">Введение</span><span class="sxs-lookup"><span data-stu-id="0535f-111">Introduction</span></span>](mr-learning-asa-01.md)
2. [<span data-ttu-id="0535f-112">Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="0535f-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="0535f-113">Сохранение, получение и совместное использование Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="0535f-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="0535f-114">Отображение сведений о Пространственных привязках Azure</span><span class="sxs-lookup"><span data-stu-id="0535f-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="0535f-115">Пространственные привязки Azure для Android и iOS</span><span class="sxs-lookup"><span data-stu-id="0535f-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="0535f-116">Задачи</span><span class="sxs-lookup"><span data-stu-id="0535f-116">Objectives</span></span>

* <span data-ttu-id="0535f-117">Узнать, как создавать пространственные привязки и получать их из Azure.</span><span class="sxs-lookup"><span data-stu-id="0535f-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="0535f-118">Узнать, как обеспечить пространственное выравнивание в сеансах приложения.</span><span class="sxs-lookup"><span data-stu-id="0535f-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="0535f-119">Узнать, как реализовать пространственное выравнивание на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="0535f-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="0535f-120">Узнать, как подготовить, создать и развернуть проект в Android и iOS.</span><span class="sxs-lookup"><span data-stu-id="0535f-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0535f-121">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="0535f-121">Prerequisites</span></span>

* <span data-ttu-id="0535f-122">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0535f-122">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="0535f-123">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="0535f-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="0535f-124">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="0535f-124">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="0535f-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="0535f-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="0535f-126">Выполненные инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) статьи [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="0535f-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="0535f-127">Знакомство с серией [руководств по началу работы](mr-learning-base-01.md) или базовый опыт работы с Unity и MRTK.</span><span class="sxs-lookup"><span data-stu-id="0535f-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="0535f-128">Знакомство с серией [руководств по Пространственным привязкам Azure](mr-learning-asa-01.md) или опыт создания учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="0535f-128">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or previous experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="0535f-129">Если планируется развертывание на устройствах Android и HoloLens</span><span class="sxs-lookup"><span data-stu-id="0535f-129">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="0535f-130">Устройство Android с <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">включенными возможностями разработки</a> и <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">поддержкой ARCore</a>, подключенное через USB к компьютеру Windows или macOS.</span><span class="sxs-lookup"><span data-stu-id="0535f-130">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="0535f-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем Android Build Support.</span><span class="sxs-lookup"><span data-stu-id="0535f-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="0535f-132">Если планируется развертывание на устройствах iOS и HoloLens</span><span class="sxs-lookup"><span data-stu-id="0535f-132">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="0535f-133">Компьютер macOS с последней версией <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> и <a href="https://cocoapods.org" target="_blank">CocoaPods</a>.</span><span class="sxs-lookup"><span data-stu-id="0535f-133">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="0535f-134"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">Совместимое с ARKit</a> устройство iOS, подключенное через USB к компьютеру macOS.</span><span class="sxs-lookup"><span data-stu-id="0535f-134">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="0535f-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем iOS Build Support.</span><span class="sxs-lookup"><span data-stu-id="0535f-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="0535f-136">Рекомендуемая версия набора средств для Смешанной реальности для этой серии руководств — МРТК 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="0535f-136">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="0535f-137">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="0535f-137">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="0535f-138">Это заменяет все требования к версии Unity, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="0535f-138">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="0535f-139">Следующее руководство: 2. Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="0535f-139">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
