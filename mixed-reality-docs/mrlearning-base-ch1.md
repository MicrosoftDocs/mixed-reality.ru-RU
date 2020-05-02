---
title: Руководства по началу работы Инициализация проекта и первое приложение
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 56adb4bfc66768684c8269c0f0cafd70c486ea8a
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376211"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="1035f-105">2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="1035f-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="1035f-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="1035f-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="1035f-107">B этом первом руководстве описаны некоторые возможности <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">набора средств для Смешанной реальности (MRTK)</a>. Также вы узнаете, как запустить свое первое приложение для HoloLens 2 и развернуть его на устройстве.</span><span class="sxs-lookup"><span data-stu-id="1035f-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="1035f-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="1035f-108">Objectives</span></span>

* <span data-ttu-id="1035f-109">Настройка Unity для разработки решений для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1035f-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="1035f-110">Импорт ресурсов и настройка сцены.</span><span class="sxs-lookup"><span data-stu-id="1035f-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="1035f-111">Визуализация сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="1035f-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1035f-112">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="1035f-112">Prerequisites</span></span>

* <span data-ttu-id="1035f-113">Компьютер с Windows 10, настроенный с требуемыми [установленными инструментами](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1035f-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="1035f-114">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="1035f-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="1035f-115">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="1035f-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="1035f-116">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="1035f-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="1035f-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="1035f-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1035f-118">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="1035f-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="1035f-119">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="1035f-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="1035f-120">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="1035f-120">Create new Unity project</span></span>

<span data-ttu-id="1035f-121">Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты) и щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):</span><span class="sxs-lookup"><span data-stu-id="1035f-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="1035f-123">Выберите версию Unity, указанную в разделе с [предварительными требованиями](#prerequisites) выше.</span><span class="sxs-lookup"><span data-stu-id="1035f-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="1035f-125">В окне Create a new project (Создание нового проекта) сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="1035f-125">In the Create a new project window:</span></span>

* <span data-ttu-id="1035f-126">Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="1035f-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="1035f-127">Укажите понятное **имя проекта**, например _MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="1035f-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="1035f-128">Выберите подходящее **расположение** для хранения проекта, например _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="1035f-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="1035f-129">Нажмите кнопку **Create** (Создать), чтобы создать и запустить новый проект Unity.</span><span class="sxs-lookup"><span data-stu-id="1035f-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="1035f-131">В Windows для переменной MAX_PATH есть ограничение в 255 символов.</span><span class="sxs-lookup"><span data-stu-id="1035f-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="1035f-132">Так как эти ограничения распространяются и на Unity, может произойти сбой компиляции, если длина пути к файлу превысит 255 символов.</span><span class="sxs-lookup"><span data-stu-id="1035f-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="1035f-133">Поэтому настоятельно рекомендуется хранить проект Unity как можно ближе к корневому каталогу диска.</span><span class="sxs-lookup"><span data-stu-id="1035f-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="1035f-134">Подождите, пока Unity создаст проект:</span><span class="sxs-lookup"><span data-stu-id="1035f-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="1035f-136">Настройка проекта Unity для Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1035f-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="1035f-137">В этом разделе описано, как переключить платформу сборки, включить виртуальную реальность и настроить возможность пространственного восприятия.</span><span class="sxs-lookup"><span data-stu-id="1035f-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="1035f-138">1. Переключение платформы сборки</span><span class="sxs-lookup"><span data-stu-id="1035f-138">1. Switch build platform</span></span>

<span data-ttu-id="1035f-139">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="1035f-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="1035f-141">В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):</span><span class="sxs-lookup"><span data-stu-id="1035f-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="1035f-143">Подождите, пока Unity переключит платформу:</span><span class="sxs-lookup"><span data-stu-id="1035f-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="1035f-145">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="1035f-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="1035f-147">2. Включение виртуальной реальности</span><span class="sxs-lookup"><span data-stu-id="1035f-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="1035f-148">Включение виртуальной реальности также распространяется на гарнитуры дополненной и смешанной реальности, так как при этом включается стереоскопическое изображение (отрисовка разных изображений для каждого глаза).</span><span class="sxs-lookup"><span data-stu-id="1035f-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="1035f-149">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:</span><span class="sxs-lookup"><span data-stu-id="1035f-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="1035f-151">В окне параметров проекта щелкните **Player** > **XR Settings** (Проигрыватель >Параметры XR), чтобы развернуть окно параметров XR:</span><span class="sxs-lookup"><span data-stu-id="1035f-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="1035f-153">В окне параметров XR установите флажок **Virtual Reality Supported** (Поддерживаемая виртуальная реальность), чтобы включить виртуальную реальность, а затем щелкните значок **+** и выберите **Windows Mixed Reality**, чтобы добавить пакет SDK для Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="1035f-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="1035f-155">Подождите, пока Unity добавит пакет SDK:</span><span class="sxs-lookup"><span data-stu-id="1035f-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="1035f-157">Когда Unity добавит пакет SDK, оптимизируйте параметры XR следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1035f-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="1035f-158">В Windows Mixed Reality задайте для параметра **Depth Format** (Формат глубины) значение **16-bit depth** (16-разрядная глубина).</span><span class="sxs-lookup"><span data-stu-id="1035f-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="1035f-159">В Windows Mixed Reality установите флажок **Enable Depth Sharing** (Совместное использование глубины).</span><span class="sxs-lookup"><span data-stu-id="1035f-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="1035f-160">Для параметра **Stereo Rendering Mode\*** (Режим стереоскопической отрисовки) задайте значение **Single Pass Instanced** (Однопроходная отрисовка экземпляра).</span><span class="sxs-lookup"><span data-stu-id="1035f-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="1035f-162">См. сведения об оптимизации Unity для Windows Mixed Reality в документации по [рекомендуемым параметрам для Unity](recommended-settings-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="1035f-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="1035f-163">3. Включение пространственного восприятия</span><span class="sxs-lookup"><span data-stu-id="1035f-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="1035f-164">Пространственное восприятие позволяет визуализировать сетку пространственного сканирования на устройствах Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1035f-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="1035f-165">В окне параметров проекта щелкните **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), чтобы развернуть окно параметров публикации:</span><span class="sxs-lookup"><span data-stu-id="1035f-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="1035f-167">В окне параметров публикации прокрутите вниз до раздела **Capabilities** (Возможности) и установите флажок **Spatial Perception** (Пространственное восприятие).</span><span class="sxs-lookup"><span data-stu-id="1035f-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="1035f-169">Закройте окно параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="1035f-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="1035f-170">Импорт требуемых ресурсов TextMesh Pro</span><span class="sxs-lookup"><span data-stu-id="1035f-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="1035f-171">Мы импортируем этот пакет, так как он требуется для работы элементов пользовательского интерфейса набора средств Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1035f-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="1035f-172">В меню Unity щелкните **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP):</span><span class="sxs-lookup"><span data-stu-id="1035f-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="1035f-174">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="1035f-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="1035f-176">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="1035f-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="1035f-177">Скачайте пользовательский пакет Unity:</span><span class="sxs-lookup"><span data-stu-id="1035f-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="1035f-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="1035f-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

<span data-ttu-id="1035f-179">В меню Unity щелкните **Assets** > **Import Package** > **Custom Package** (Ресурсы > Импорт пакетов > Пользовательский пакет), чтобы открыть окно импорта пакетов:</span><span class="sxs-lookup"><span data-stu-id="1035f-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="1035f-181">В окне импорта пакетов выберите скачанный пакет **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** и нажмите кнопку **Open** (Открыть):</span><span class="sxs-lookup"><span data-stu-id="1035f-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="1035f-183">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="1035f-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="1035f-185">Настройка проекта Unity для набора средств для Смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="1035f-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="1035f-186">После импорта пакета должно отобразиться окно конфигуратора проекта МРТК.</span><span class="sxs-lookup"><span data-stu-id="1035f-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="1035f-187">В противном случае откройте это окно, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для Смешанной реальности > Служебные программы > Настроить проект Unity) в меню Unity.</span><span class="sxs-lookup"><span data-stu-id="1035f-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="1035f-189">В окне конфигуратора проектов МРТК разверните раздел **Modify Configurations** (Изменение конфигураций), <u>снимите флажок</u> **Enable MSBuild for Unity** (Включить MSBuild для Unity), убедитесь, что настроены остальные параметры, и нажмите кнопку **Apply** (Применить), чтобы применить эти параметры:</span><span class="sxs-lookup"><span data-stu-id="1035f-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="1035f-191">Так как MSBuild для Unity может поддерживать не все пакеты SDK, которые будут использоваться, с отключением могут быть проблемы.</span><span class="sxs-lookup"><span data-stu-id="1035f-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="1035f-192">Поэтому настоятельно рекомендуется не включать MSBuild для Unity.</span><span class="sxs-lookup"><span data-stu-id="1035f-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="1035f-193">Настройка набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="1035f-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="1035f-194">В меню Unity щелкните **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для Смешанной реальности > Добавить в сцену и настроить), чтобы добавить набор средств для Смешанной реальности в текущую сцену:</span><span class="sxs-lookup"><span data-stu-id="1035f-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="1035f-196">Выбрав объект MixedRealityToolkit в окне иерархии, измените профиль конфигурации набора средств для Смешанной реальности на **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="1035f-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, verify the Mixed Reality Toolkit configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> <span data-ttu-id="1035f-198">Как правило, при разработке для HoloLens 2 используется DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="1035f-198">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens 2.</span></span> <span data-ttu-id="1035f-199">Но при работе с этим руководством вы будете использовать DefaultMixedRealityToolkitConfigurationProfile, а затем при работе со следующим руководством по [созданию пользовательского интерфейса и настройке набора Средств смешанной реальности](mrlearning-base-ch2.md) — DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="1035f-199">However, for the purpose of this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="1035f-200">В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:</span><span class="sxs-lookup"><span data-stu-id="1035f-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="1035f-202">В окне сохранения сцены перейдите к папке **Scenes** проекта, присвойте сцене понятное имя, например _GettingStarted_, и нажмите кнопку **Save** (Сохранить), чтобы сохранить сцену:</span><span class="sxs-lookup"><span data-stu-id="1035f-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="1035f-204">Разработка приложения для устройства</span><span class="sxs-lookup"><span data-stu-id="1035f-204">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="1035f-205">1. Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="1035f-205">1. Build the Unity project</span></span>

<span data-ttu-id="1035f-206">В меню Unity щелкните **File** > **Build Settings** (Файл > Параметры сборки), чтобы открыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="1035f-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="1035f-207">В окне параметров сборки нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке), а затем нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки универсальной платформы Windows:</span><span class="sxs-lookup"><span data-stu-id="1035f-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="1035f-209">В окне сборки универсальной платформы Windows выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_, создайте папку и присвойте ей понятное имя, например _GettingStarted_, а затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="1035f-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="1035f-211">Подождите, пока Unity завершит сборку:</span><span class="sxs-lookup"><span data-stu-id="1035f-211">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="1035f-213">2. Сборка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="1035f-213">2. Build and deploy the application</span></span>

<span data-ttu-id="1035f-214">По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой.</span><span class="sxs-lookup"><span data-stu-id="1035f-214">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="1035f-215">Перейдите в папку и дважды щелкните файл решения, чтобы открыть его в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="1035f-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="1035f-217">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по [установке средств](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1035f-217">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="1035f-218">Настройте Visual Studio для устройства HoloLens 2, выбрав конфигурацию **Ведущий** или **Выпуск**, архитектуру **ARM** и целевой объект **Устройство**:</span><span class="sxs-lookup"><span data-stu-id="1035f-218">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

> [!NOTE]
> <span data-ttu-id="1035f-220">Если устройство не отображается как вариант, возможно, придется изменить проект запуска по умолчанию, указав вместо проекта IC2Lpp проект UWP.</span><span class="sxs-lookup"><span data-stu-id="1035f-220">If you don't see Device as an option you may need to change the default start up project from the IC2Lpp project to your UWP Project.</span></span> <span data-ttu-id="1035f-221">В **обозревателе решений** щелкните правой кнопкой мыши **имя_проекта (Universal Windows)** и выберите **Set as StartUp Project** (Назначить запускаемым проектом).</span><span class="sxs-lookup"><span data-stu-id="1035f-221">In the **Solution Explorer**, right click on **yourprojectname (Universal Windows)** and select **Set as StartUp Project**.</span></span> 

<span data-ttu-id="1035f-222">Подключите HoloLens 2 к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="1035f-222">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1035f-223">Перед выполнением сборки устройство нужно перевести в режим разработчика и связать с компьютером разработки.</span><span class="sxs-lookup"><span data-stu-id="1035f-223">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="1035f-224">Оба эти действия можно выполнить, следуя [этим инструкциям](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1035f-224">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="1035f-225">Завершающий шаг — это сборка и развертывание на вашем устройстве. Для этого щелкните **Отладка** > **Запуск без отладки**:</span><span class="sxs-lookup"><span data-stu-id="1035f-225">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="1035f-227">Хотя в этих инструкциях предполагается, что вы будете развертывать приложение на устройстве HoloLens 2, вы можете также развернуть его на [эмуляторе HoloLens 2](using-the-hololens-emulator.md) или создать [пакет приложения для передачи данных на другое локальное устройство](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="1035f-227">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="1035f-228">Выбор параметра "Запуск без отладки" приведет к немедленному запуску приложения на вашем устройстве после успешной сборки, но без подключения отладчика и отображения сведений об отладке в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1035f-228">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="1035f-229">Это также означает, что вы можете отсоединить USB-кабель во время выполнения приложения на устройстве HoloLens 2, не прерывая его работу.</span><span class="sxs-lookup"><span data-stu-id="1035f-229">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="1035f-230">Кроме того, вы можете выбрать "Сборка" > "Развернуть решение", чтобы развернуть решение на устройстве без автоматического запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="1035f-230">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="1035f-231">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1035f-231">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="1035f-232">Вы развернули свое первое приложение HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1035f-232">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="1035f-233">Перемещаясь, вы увидите, как пространственная сетка сопоставления покрывает все поверхности, воспринятые HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1035f-233">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="1035f-234">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="1035f-234">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="1035f-235">Это лишь некоторые из основополагающих компонентов, входящих в комплект поставки набора средств для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1035f-235">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="1035f-236">В следующих руководствах описано, как добавлять содержимое и интерактивные средства в сцену, чтобы в полной мере изучить возможности HoloLens 2 и набора средств для Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1035f-236">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="1035f-237">При работе приложения можно заметить, что профилировщик диагностики позволяет переключать видимость с помощью команды **Toggle Diagnostics** (Переключить диагностику).</span><span class="sxs-lookup"><span data-stu-id="1035f-237">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="1035f-238">Но обычно рекомендуется не закрывать профилировщик во время разработки. Так вы сможете определить, влияют ли изменения приложения на производительность (например, приложение HoloLens 2 должно [непрерывно выполняться с частотой 60 кадров в секунду](understanding-performance-for-mixed-reality.md)).</span><span class="sxs-lookup"><span data-stu-id="1035f-238">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="1035f-239">Следующее руководство: 3. Создание пользовательского интерфейса и настройка набора средств для Смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="1035f-239">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
