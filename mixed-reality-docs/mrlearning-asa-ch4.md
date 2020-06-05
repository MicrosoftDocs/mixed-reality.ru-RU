---
title: Руководства по Пространственным привязкам Azure, часть 4 Пространственные привязки Azure для Android и iOS
description: В этом руководстве показано, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: смешанная реальность, unity, руководство, курс, hololens, azure, пространственные привязки
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867626"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="54c22-105">4. Пространственные привязки Azure для Android и iOS</span><span class="sxs-lookup"><span data-stu-id="54c22-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="54c22-106">В этом руководстве показано, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="54c22-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="54c22-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="54c22-107">Objectives</span></span>

* <span data-ttu-id="54c22-108">Узнайте, как выполнить сборку проекта на устройстве Android с помощью пакетов Unity AR Foundation и ARCore XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="54c22-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="54c22-109">Узнайте, как выполнить сборку проекта на устройстве iOS с помощью пакетов Unity AR Foundation и ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="54c22-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

[!NOTE] <span data-ttu-id="54c22-110">Для работы с этим руководством необходимо сначала изучить [руководство по началу работы с Пространственными привязками Azure](mrlearning-asa-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="54c22-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="54c22-111">Добавление встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="54c22-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="54c22-112">В этом разделе показано, как установить встроенные в Unity пакеты AR Foundation, ARCore XR Plugin и ARKit XR Plugin, требуемые для включения поддержки устройств Android и iOS.</span><span class="sxs-lookup"><span data-stu-id="54c22-112">In this section, you will install Unity's inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="54c22-113">Убедитесь, что установлена правильная версия следующих пакетов Unity:</span><span class="sxs-lookup"><span data-stu-id="54c22-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="54c22-114">**AR Foundation 2.1.4;**</span><span class="sxs-lookup"><span data-stu-id="54c22-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="54c22-115">**ARCore XR Plugin 2.2.0 (предварительная версия 2);**</span><span class="sxs-lookup"><span data-stu-id="54c22-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="54c22-116">**ARKit XR Plugin 2.1.1.**</span><span class="sxs-lookup"><span data-stu-id="54c22-116">**ARKit XR plugin 2.1.1**</span></span>

[!NOTE] <span data-ttu-id="54c22-117">Если вы разрабатываете проект для Android, устанавливать пакет ARKit XR Plugin не нужно.</span><span class="sxs-lookup"><span data-stu-id="54c22-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="54c22-118">Если вы разрабатываете проект для iOS, устанавливать пакет ARCore XR Plugin также не нужно.</span><span class="sxs-lookup"><span data-stu-id="54c22-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="54c22-119">В меню Unity последовательно выберите **Window** > **Диспетчер пакетов**:</span><span class="sxs-lookup"><span data-stu-id="54c22-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="54c22-121">Для отображения всех пакетов в списке может потребоваться несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="54c22-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="54c22-122">Чтобы увидеть предварительные версии пакетов, откройте дополнительные параметры и щелкните **Show preview packages** (Показать предварительные версии пакетов).</span><span class="sxs-lookup"><span data-stu-id="54c22-122">Display preview packages by clicking on Advanced option and select "**Show preview packages.**"</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="54c22-124">В окне диспетчера пакетов выберите **AR Foundation**. В полном списке версий выберите 2.1.4 и обновите пакет, нажав кнопку **Update to 2.1.4** (Обновить до версии 2.1.4).</span><span class="sxs-lookup"><span data-stu-id="54c22-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select version 2.1.4 and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="54c22-126">Для включения поддержки устройств Android выполните такую же процедуру, чтобы импортировать пакет ARCore XR Plugin 2.2.0, предварительная версия 2.</span><span class="sxs-lookup"><span data-stu-id="54c22-126">To support Android devices, follow the same process to import ARCore XR Plugin 2.2.0 preview 2.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="54c22-128">Для включения поддержки устройств iOS необходимо импортировать пакет **ARKit XR Plugin 2.1.1** для Unity из диспетчера пакетов.</span><span class="sxs-lookup"><span data-stu-id="54c22-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="54c22-130">Настройка MRTK для включения поддержки камеры AR Foundation</span><span class="sxs-lookup"><span data-stu-id="54c22-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="54c22-131">Настройте параметры MRTK для поддержки AR Foundation, выбрав MixedRealityToolKit в окне Hierarchy (Иерархия) и нажав кнопку **Clone** (Клонировать) в наборе средств для Смешанной реальности MRTK в окне Inspector (Инспектор).</span><span class="sxs-lookup"><span data-stu-id="54c22-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="54c22-133">Если нажать кнопку **Clone** (Клонировать), появится окно Clone Profile (Клонировать профиль). Нажмите кнопку Clone (Клонировать) еще раз, чтобы клонировать профиль DefaultMixedRealityToolkitProfile.</span><span class="sxs-lookup"><span data-stu-id="54c22-133">When you click the **Clone** button, a new Clone Profile window will appear, click on the Clone button again to clone the DefaultMixedRealityToolkitProfile.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="54c22-135">Аналогичным образом клонируйте профиль камеры в окне Inspector (Инспектор), присвойте профилю имя UnityARConfigurationProfile и нажмите кнопку **Clone** (Клонировать).</span><span class="sxs-lookup"><span data-stu-id="54c22-135">Similarly, clone the camera profile in the Inspector window and rename the profile to “UnityARConfigurationProfile” and click on the **Clone** button.</span></span> <span data-ttu-id="54c22-136">В окне Inspector (Инспектор) найдите MixedReality, выберите вкладку Camera (Камера), разверните поставщиков параметров камеры в окне Inspector (Инспектор) и щелкните **+Add Camera Setting Provider** (+Добавить поставщика параметров камеры). Затем разверните пункт **New data provider 1** (Новый поставщик данных 1), выберите для параметра Type (Тип) значение **None** (Нет), после чего выберите **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** и **UnityARCameraSettings**.</span><span class="sxs-lookup"><span data-stu-id="54c22-136">In the Inspector window, locate the MixedReality, select the Camera tab Expand the camera setting providers in the inspector window and click on **+Add Camera Setting Provider** > expand **New data provider 1**> select Type **None** >select **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** > Select **UnityARCameraSettings**.</span></span>


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="54c22-138">Выбрав объект MixedRealityToolKit в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) добавьте вспомогательные скрипты, нажав кнопку **Add component** (Добавить компонент), введите AR Reference Point Manager и выберите скрипт.</span><span class="sxs-lookup"><span data-stu-id="54c22-138">With the MixedRealityToolKit object selected in the Hierarchy window, in the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="54c22-139">При добавлении скрипта AR Reference Point Manager в окне Inspector (Инспектор) также будет автоматически добавлен скрипт AR Session Origin.</span><span class="sxs-lookup"><span data-stu-id="54c22-139">Adding the  "AR Reference Point Manager" script will automatically add "AR session origin" along with it in the Inspector window.</span></span> <span data-ttu-id="54c22-140">После добавления вспомогательных скриптов окно Inspector (Инспектор) должно выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="54c22-140">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a><span data-ttu-id="54c22-142">Создание приложения на устройстве Android</span><span class="sxs-lookup"><span data-stu-id="54c22-142">Build application to Android device</span></span>

<span data-ttu-id="54c22-143">Чтобы создать приложение на устройстве Android, щелкните **File** (Файл) в верхней части окна и выберите **Build Settings** (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="54c22-143">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="54c22-144">В открывшемся окне выберите **Android** и щелкните **Switch Platform** (Сменить платформу).</span><span class="sxs-lookup"><span data-stu-id="54c22-144">A new window will appear on the screen, select **Android,** and click on the **Switch Platform**.</span></span> <span data-ttu-id="54c22-145">Переключение платформы займет несколько минут.</span><span class="sxs-lookup"><span data-stu-id="54c22-145">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="54c22-146">После перехода на платформу Android щелкните **Add Open Scenes** (Добавить открытые сцены) и убедитесь, что текущая сцена является единственной выбранной сценой в списке **Scenes In Build** (Сцены в сборке).</span><span class="sxs-lookup"><span data-stu-id="54c22-146">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="54c22-148">Закройте окно **Build Settings** (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="54c22-148">Close the **Build Settings** window.</span></span> <span data-ttu-id="54c22-149">В меню Unity выберите **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств Смешанной реальности > Утилиты > Настроить проект Unity) и нажмите кнопку **Apply** (Применить), чтобы настроить проект Unity для платформы Android.</span><span class="sxs-lookup"><span data-stu-id="54c22-149">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="54c22-151">В меню Unity выберите **Edit** > **Project Settings** (Правка > Параметры проекта), чтобы открыть окно Project Settings (Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="54c22-151">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="54c22-152">В окне Project Settings (Параметры проекта) выберите вкладку **Player** (Проигрыватель), разверните раздел Other Settings (Другие параметры), а затем выберите и удалите **Vulkan**, щелкнув значок -.</span><span class="sxs-lookup"><span data-stu-id="54c22-152">In the Project Settings, window selects the **Player** tab, expand the Other Settings section, select **Vulkan,** and remove it by clicking the "-" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="54c22-154">Закройте окно Player Settings (Параметры проигрывателя) и снова откройте окно Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="54c22-154">Close the Player Settings window and open the Build Settings window again.</span></span> <span data-ttu-id="54c22-155">Затем с помощью USB-кабеля подключите устройство Android к компьютеру и выберите устройство в раскрывающемся списке **Build and Run on** (Выполнить сборку и запустить на), а затем щелкните **Build And Run** (Выполнить сборку и запустить).</span><span class="sxs-lookup"><span data-stu-id="54c22-155">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run on** the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="54c22-156">Вам будет предложено сохранить APK-файл, для которого можно выбрать любое имя.</span><span class="sxs-lookup"><span data-stu-id="54c22-156">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="54c22-158">Если в окне консоли Unity появится сообщение об ошибке, связанной с модулями пакетов SDK, NDK или JDK для Android, необходимо открыть Unity Hub и установить соответствующие модули пакетов SDK, NDK и JDK для модуля Android Build Support.</span><span class="sxs-lookup"><span data-stu-id="54c22-158">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="54c22-159">По завершении сборки приложения должны автоматически загрузиться на устройство Android.</span><span class="sxs-lookup"><span data-stu-id="54c22-159">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-application-to-ios-device"></a><span data-ttu-id="54c22-160">Создание приложения на устройстве iOS</span><span class="sxs-lookup"><span data-stu-id="54c22-160">Build application to iOS Device</span></span>

<span data-ttu-id="54c22-161">Чтобы создать приложение на устройстве iOS, щелкните **File** (Файл) в верхней части окна и выберите **Build Settings** (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="54c22-161">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="54c22-162">В открывшемся окне выберите **iOS** и щелкните **Switch Platform** (Сменить платформу).</span><span class="sxs-lookup"><span data-stu-id="54c22-162">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="54c22-164">Закройте окно **Build Settings** (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="54c22-164">Close the **Build Settings** window.</span></span> <span data-ttu-id="54c22-165">В меню Unity выберите **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств Смешанной реальности > Утилиты > Настроить проект Unity) и нажмите кнопку **Apply** (Применить), чтобы настроить проект Unity для платформы iOS.</span><span class="sxs-lookup"><span data-stu-id="54c22-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="54c22-167">Чтобы выполнить сборку проекта iOS XCode, перейдите к настройкам сборки и щелкните **Build** (Выполнить сборку).</span><span class="sxs-lookup"><span data-stu-id="54c22-167">To build the iOS XCode project, go to Build Settings and, click on **Build**.</span></span>

<span data-ttu-id="54c22-168">Изучите [это руководство](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project), чтобы узнать, как развернуть этот проект на своем устройстве iOS.</span><span class="sxs-lookup"><span data-stu-id="54c22-168">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="54c22-169">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="54c22-169">Congratulations</span></span>

<span data-ttu-id="54c22-170">Из этого руководства вы узнали, как создать проект для устройств Android и iOS.</span><span class="sxs-lookup"><span data-stu-id="54c22-170">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="54c22-171">Вы также узнали, как использовать пакеты AR Foundation, ARCore XR Plugin и ARKit XR Plugin для выполнения проекта на устройствах Android и iOS.</span><span class="sxs-lookup"><span data-stu-id="54c22-171">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>