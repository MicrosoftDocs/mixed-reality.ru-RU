---
title: Руководства по началу работы Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4f72f70b9eaac159f7d9231e61f23d18d708d0c7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306277"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="c5883-105">2. Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="c5883-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="c5883-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="c5883-106">Overview</span></span>

<span data-ttu-id="c5883-107">Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">набора средств для смешанной реальности (MRTK)</a> и импортировать MRTK.</span><span class="sxs-lookup"><span data-stu-id="c5883-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="c5883-108">Вы также узнаете, как настроить, создать и развернуть базовую сцену примера Unity из Visual Studio в эмуляторе или HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c5883-108">You'll also walk through configuring, building, and deploying the basic Unity sample scene from Visual Studio to your HoloLens 2 or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="c5883-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="c5883-109">Objectives</span></span>

* <span data-ttu-id="c5883-110">Узнайте, как настроить Unity для разработки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c5883-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="c5883-111">Узнайте, как создать и развернуть приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c5883-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="c5883-112">Изучите возможности сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="c5883-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="c5883-113">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="c5883-113">Creating the Unity project</span></span>

<span data-ttu-id="c5883-114">Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты) и щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):</span><span class="sxs-lookup"><span data-stu-id="c5883-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="c5883-116">В раскрывающемся списке выберите **версию** Unity, указанную в разделе с [предварительными требованиями](mr-learning-base-01.md#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="c5883-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="c5883-118">Если конкретная версия Unity недоступна в Unity Hub, можно запустить установку из <a href="https://unity3d.com/get-unity/download/archive" target="_blank">архива загрузок</a> Unity.</span><span class="sxs-lookup"><span data-stu-id="c5883-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="c5883-119">В окне Create a new project (Создание нового проекта) сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="c5883-119">In the Create a new project window:</span></span>

* <span data-ttu-id="c5883-120">Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="c5883-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="c5883-121">Укажите понятное **имя проекта**, например _MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="c5883-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="c5883-122">Выберите подходящее **расположение** для хранения проекта, например _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="c5883-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="c5883-123">Нажмите кнопку **Create** (Создать), чтобы создать и запустить новый проект Unity.</span><span class="sxs-lookup"><span data-stu-id="c5883-123">Click the **Create** button to create and launch your new Unity project</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="c5883-125">В Windows для переменной MAX_PATH есть ограничение в 255 символов.</span><span class="sxs-lookup"><span data-stu-id="c5883-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="c5883-126">Поэтому следует сохранить проект Unity рядом с корневым каталогом диска.</span><span class="sxs-lookup"><span data-stu-id="c5883-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="c5883-127">Подождите, пока Unity создаст проект:</span><span class="sxs-lookup"><span data-stu-id="c5883-127">Wait for Unity to create the project:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="c5883-129">Переключение платформы сборки</span><span class="sxs-lookup"><span data-stu-id="c5883-129">Switching the build platform</span></span>

<span data-ttu-id="c5883-130">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="c5883-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="c5883-132">В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):</span><span class="sxs-lookup"><span data-stu-id="c5883-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="c5883-134">Подождите, пока Unity переключит платформу:</span><span class="sxs-lookup"><span data-stu-id="c5883-134">Wait for Unity to finish switching the platform:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="c5883-136">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="c5883-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="c5883-138">Импорт требуемых ресурсов TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="c5883-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="c5883-139">В меню Unity выберите **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP), чтобы открыть окно Import Unity Package (Импорт пакета Unity):</span><span class="sxs-lookup"><span data-stu-id="c5883-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="c5883-141">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="c5883-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="c5883-143">Ресурсы TextMeshPro требуются для элементов пользовательского интерфейса MRTK.</span><span class="sxs-lookup"><span data-stu-id="c5883-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="c5883-144">Этот шаг можно пропустить, если вы не планируете использовать элементы пользовательского интерфейса MRTK в проекте.</span><span class="sxs-lookup"><span data-stu-id="c5883-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="c5883-145">Импорт набора средств для смешанной реальности (MRTK)</span><span class="sxs-lookup"><span data-stu-id="c5883-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="c5883-146">Скачайте пользовательский пакет Unity:</span><span class="sxs-lookup"><span data-stu-id="c5883-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="c5883-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="c5883-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="c5883-148">В меню Unity щелкните **Assets** > **Import Package** > **Custom Package** (Ресурсы > Импорт пакетов > Пользовательский пакет), чтобы открыть окно импорта пакетов:</span><span class="sxs-lookup"><span data-stu-id="c5883-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="c5883-150">В окне импорта пакетов выберите скачанный пакет **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** и щелкните кнопку **Open** (Открыть):</span><span class="sxs-lookup"><span data-stu-id="c5883-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="c5883-152">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="c5883-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="c5883-154">Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="c5883-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="c5883-155">1. Применение параметров конфигуратора проекта MRTK</span><span class="sxs-lookup"><span data-stu-id="c5883-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="c5883-156">Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="c5883-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="c5883-157">Если этого не происходит, откройте окно Configurator (Конфигуратор), перейдя в меню Unity и выбрав **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для смешанной реальности > Служебные программы > Настроить проект Unity):</span><span class="sxs-lookup"><span data-stu-id="c5883-157">If it doesn't, open the Configurator window by going to the Unity menu and selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="c5883-159">В окне конфигуратора проектов MRTK разверните раздел **Modify Configurations** (Изменение конфигураций), убедитесь, что все флажки включены, и нажмите кнопку **Apply**(Применить), чтобы применить эти параметры:</span><span class="sxs-lookup"><span data-stu-id="c5883-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="c5883-161">2. Настройка дополнительных параметров проекта</span><span class="sxs-lookup"><span data-stu-id="c5883-161">2. Configure additional project settings</span></span>

<span data-ttu-id="c5883-162">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:</span><span class="sxs-lookup"><span data-stu-id="c5883-162">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="c5883-164">В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), щелкните значок **+** и выберите Windows Mixed Reality, чтобы добавить пакет SDK для Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="c5883-164">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="c5883-166">Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="c5883-166">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="c5883-167">Если этого не произошло, откройте его в меню Unity.</span><span class="sxs-lookup"><span data-stu-id="c5883-167">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="c5883-168">В окне конфигуратора проектов MRTK откройте раскрывающийся список **Audio spatializer** (Аудио спатиалайзер), чтобы выбрать **MS HRTF Spatializer** (Спатиалайзер MS HRTF), а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:</span><span class="sxs-lookup"><span data-stu-id="c5883-168">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="c5883-170">В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), а затем в раскрывающемся списке **Depth Format** (Формат глубины) выберите **16-bit depth** (16-разрядная глубина):</span><span class="sxs-lookup"><span data-stu-id="c5883-170">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="c5883-172">В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="c5883-172">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="c5883-174">Package name (Имя пакета) — это уникальный идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="c5883-174">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="c5883-175">Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.</span><span class="sxs-lookup"><span data-stu-id="c5883-175">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="c5883-176">Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c5883-176">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="c5883-177">Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.</span><span class="sxs-lookup"><span data-stu-id="c5883-177">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="c5883-178">Создание и настройка сцены</span><span class="sxs-lookup"><span data-stu-id="c5883-178">Creating and configuring the scene</span></span>

<span data-ttu-id="c5883-179">Чтобы создать сцену, в меню Unity выберите **File** > **New Scene** (Файл > Новая сцена):</span><span class="sxs-lookup"><span data-stu-id="c5883-179">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="c5883-181">В меню Unity щелкните **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для смешанной реальности > Добавить в сцену и настроить), чтобы добавить MRTK в текущую сцену:</span><span class="sxs-lookup"><span data-stu-id="c5883-181">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="c5883-183">Выбрав объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), убедитесь, что профиль конфигурации **MixedRealityToolkit** имеет значение **DefaultMixedRealityToolkitConfigurationProfile** в окне Inspector (Инспектор):</span><span class="sxs-lookup"><span data-stu-id="c5883-183">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="c5883-185">Как правило, при разработке для HoloLens используется DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="c5883-185">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="c5883-186">Но при работе с этим учебником вы будете использовать DefaultMixedRealityToolkitConfigurationProfile, а затем при работе со следующим учебником [по настройке профилей MRTK](mr-learning-base-03.md) — DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="c5883-186">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="c5883-187">В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:</span><span class="sxs-lookup"><span data-stu-id="c5883-187">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="c5883-189">В окне сохранения сцены перейдите к папке **Scenes** проекта, присвойте сцене понятное имя, например _GettingStarted_, и нажмите кнопку **Save** (Сохранить), чтобы сохранить сцену:</span><span class="sxs-lookup"><span data-stu-id="c5883-189">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="c5883-191">Создание приложения в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c5883-191">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="c5883-192">1. Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="c5883-192">1. Build the Unity project</span></span>

<span data-ttu-id="c5883-193">В меню Unity щелкните **File** > **Build Settings** (Файл > Параметры сборки), чтобы открыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="c5883-193">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="c5883-194">В окне параметров сборки нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке), а затем нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки универсальной платформы Windows:</span><span class="sxs-lookup"><span data-stu-id="c5883-194">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="c5883-196">В окне сборки универсальной платформы Windows выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_, создайте папку и присвойте ей понятное имя, например _GettingStarted_, а затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="c5883-196">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="c5883-198">Подождите, пока Unity завершит сборку:</span><span class="sxs-lookup"><span data-stu-id="c5883-198">Wait for Unity to finish the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="c5883-200">2. Сборка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="c5883-200">2. Build and deploy the application</span></span>

<span data-ttu-id="c5883-201">По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой.</span><span class="sxs-lookup"><span data-stu-id="c5883-201">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="c5883-202">Перейдите в папку и дважды щелкните файл решения, чтобы открыть его в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="c5883-202">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="c5883-204">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по **[установке средств](install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="c5883-204">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="c5883-205">Настройте Visual Studio для устройства HoloLens, выбрав конфигурацию **Master** (Ведущий) или **Release** (Выпуск), архитектуру **ARM64** и целевой объект **Device** (Устройство):</span><span class="sxs-lookup"><span data-stu-id="c5883-205">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="c5883-207">Если выполняется развертывание в HoloLens (первое поколение), выберите архитектуру **x86**.</span><span class="sxs-lookup"><span data-stu-id="c5883-207">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="c5883-208">В HoloLens обычно выполняется сборка для архитектуры ARM.</span><span class="sxs-lookup"><span data-stu-id="c5883-208">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="c5883-209">Однако в Unity 2019.3 существует <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>известная проблема</strong></a>, которая вызывает ошибки при выборе ARM в качестве архитектуры сборки в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5883-209">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="c5883-210">Рекомендуемое решение — выполните сборку для ARM64.</span><span class="sxs-lookup"><span data-stu-id="c5883-210">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="c5883-211">Если такой вариант неприемлем, выберите **Edit > Project Settings > Player > Other Settings** (Изменить > Параметры проекта > Проигрыватель > Другие параметры) и отключите **графические задания**.</span><span class="sxs-lookup"><span data-stu-id="c5883-211">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="c5883-212">Если выбранное устройство не отображается как целевой объект, может потребоваться изменить загружаемый проект для решения Visual Studio из проекта IL2CPP на UWP.</span><span class="sxs-lookup"><span data-stu-id="c5883-212">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="c5883-213">Для этого в обозревателе решений щелкните правой кнопкой мыши имя_проекта (Universal Windows) и выберите **Set as StartUp Project** (Назначить запускаемым проектом).</span><span class="sxs-lookup"><span data-stu-id="c5883-213">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="c5883-214">Подключите HoloLens к компьютеру, а затем выберите **Debug** > **Start Without Debugging** (Отладка >Запуск без отладки), чтобы выполнить сборку и развертывание на устройстве:</span><span class="sxs-lookup"><span data-stu-id="c5883-214">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="c5883-216">Перед выполнением сборки устройство нужно перевести в режим разработчика и связать с компьютером разработки.</span><span class="sxs-lookup"><span data-stu-id="c5883-216">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="c5883-217">Оба эти действия можно выполнить, следуя [этим инструкциям](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c5883-217">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="c5883-218">Кроме того, можно выполнить развертывание в [эмуляторе HoloLens](using-the-hololens-emulator.md) или создать [пакет приложения](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) для загрузки неопубликованных приложений.</span><span class="sxs-lookup"><span data-stu-id="c5883-218">You can also deploy to the [HoloLens Emulator](using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="c5883-219">Использование параметра запуска без отладки автоматически запускает приложение на устройстве без присоединения отладчика Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5883-219">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="c5883-220">Выберите **Build > Deploy Solution** (Сборка > Развернуть решение), чтобы развернуть решение на устройстве без автоматического запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="c5883-220">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="c5883-221">В приложении можно заметить профилировщик диагностики, который можно включать или выключать с помощью голосовой команды **Toggle Diagnostics** (Переключить диагностику).</span><span class="sxs-lookup"><span data-stu-id="c5883-221">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="c5883-222">В процессе разработки рекомендуется отображать профилировщик основную часть времени. Это позволит определить, повлияют ли изменения приложения на производительность.</span><span class="sxs-lookup"><span data-stu-id="c5883-222">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="c5883-223">Например, приложения HoloLens должны [непрерывно выполняться с частотой 60 кадров/с](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="c5883-223">For example, HoloLens apps should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="c5883-224">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="c5883-224">Congratulations</span></span>

<span data-ttu-id="c5883-225">Вы развернули свое первое приложение HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c5883-225">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="c5883-226">Перемещаясь, вы увидите, как пространственная сетка сопоставления покрывает поверхности, воспринятые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c5883-226">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="c5883-227">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="c5883-227">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="c5883-228">Эти функции — лишь немногие из новых базовых компонентов, входящих в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="c5883-228">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="c5883-229">В следующих учебниках вы добавите содержимое в сцену, чтобы исследовать возможности HoloLens и MRTK.</span><span class="sxs-lookup"><span data-stu-id="c5883-229">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

[<span data-ttu-id="c5883-230">Следующее руководство: 3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="c5883-230">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
