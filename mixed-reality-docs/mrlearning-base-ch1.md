---
title: Руководства по началу работы Инициализация проекта и первое приложение
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: смешанная реальность, unity, руководство, hololens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334418"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="17a30-105">2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="17a30-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="17a30-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="17a30-106">Overview</span></span>

<span data-ttu-id="17a30-107">На этом первом уроке вы узнаете о некоторых возможностях <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">набора средств для смешанной реальности (MRTK)</a>, запустите свое первое приложение для HoloLens 2 и развернете его на устройстве.</span><span class="sxs-lookup"><span data-stu-id="17a30-107">In this first lesson, you'll learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="17a30-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="17a30-108">Objectives</span></span>

* <span data-ttu-id="17a30-109">Настройка Unity для разработки решений для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="17a30-109">Configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="17a30-110">Импорт ресурсов и настройка сцены.</span><span class="sxs-lookup"><span data-stu-id="17a30-110">Import assets and set up the scene.</span></span>
* <span data-ttu-id="17a30-111">Визуализация пространственной сетки сопоставления, виртуальных рук и счетчика частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="17a30-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="17a30-112">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="17a30-112">Create new Unity project</span></span>

1. <span data-ttu-id="17a30-113">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="17a30-113">Start Unity.</span></span>

2. <span data-ttu-id="17a30-114">Выберите **New** (Создать).</span><span class="sxs-lookup"><span data-stu-id="17a30-114">Select **New**.</span></span>

    ![Урок 1, раздел 1, шаг 2](images/mrlearning-base-ch1-1-step2.JPG)

3. <span data-ttu-id="17a30-116">Введите название проекта (например, MixedRealityBase).</span><span class="sxs-lookup"><span data-stu-id="17a30-116">Enter a project name (e.g. "MixedRealityBase").</span></span>

    ![Урок 1, раздел 1, шаг 3](images/mrlearning-base-ch1-1-step3.JPG)

4. <span data-ttu-id="17a30-118">Укажите расположение, где будет сохранен проект.</span><span class="sxs-lookup"><span data-stu-id="17a30-118">Enter a location to save your project.</span></span>

    ![Урок 1, раздел 1, шаг 4](images/mrlearning-base-ch1-1-step4.JPG)

5. <span data-ttu-id="17a30-120">Задайте для проекта значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="17a30-120">Make sure the project is set to **3D**.</span></span>

    ![Урок 1, раздел 1, шаг 5](images/mrlearning-base-ch1-1-step5.JPG)

6. <span data-ttu-id="17a30-122">Щелкните **Create Project** (Создать проект).</span><span class="sxs-lookup"><span data-stu-id="17a30-122">Click **Create Project**.</span></span>

    ![Урок 1, раздел 1, шаг 6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="17a30-124">Настройка проекта Unity для Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="17a30-124">Configure the Unity project for Windows Mixed Reality</span></span>

1. <span data-ttu-id="17a30-125">Откройте окно *Build Settings* (Параметры сборки), выбрав **File (Файл)**   >  **Build Settings (Параметры сборки)** .</span><span class="sxs-lookup"><span data-stu-id="17a30-125">Open the *Build Settings* window by going to **File** > **Build Settings**.</span></span>

    ![Урок 1, раздел 2, шаг 1](images/mrlearning-base-ch1-2-step1.JPG)

2. <span data-ttu-id="17a30-127">Выберите *Universal Windows Platform* (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу), чтобы переключить платформу.</span><span class="sxs-lookup"><span data-stu-id="17a30-127">Select the *Universal Windows Platform* and click the **Switch Platform** button to switch platforms.</span></span> <span data-ttu-id="17a30-128">С HoloLens 2 должны использоваться приложения, совместимые с универсальной платформой Windows (UWP).</span><span class="sxs-lookup"><span data-stu-id="17a30-128">Applications running on HoloLens 2 are required to be Universal Windows Platform (UWP) compatible.</span></span>

    ![Урок 1, раздел 2, шаг 2](images/mrlearning-base-ch1-2-step2.JPG)

3. <span data-ttu-id="17a30-130">Включите виртуальную реальность, щелкнув **Player Settings** (Параметры проигрывателя) в окне сборки, а затем на панели инспектора установите флажок *Virtual Reality Supported* (Поддержка виртуальной реальности) в разделе "XR Settings" (Параметры XR), как показано на приведенном ниже рисунке.</span><span class="sxs-lookup"><span data-stu-id="17a30-130">Enable virtual reality by clicking the **Player Settings** button in the Build Window, and enable the *Virtual Reality Supported* checkbox under XR Settings from the inspector panel, as shown in the image below.</span></span> <span data-ttu-id="17a30-131">Обратите внимание на то, что может потребоваться перетащить окно *Build Settings* (Параметры сборки) в сторону, чтобы увидеть панель инспектора.</span><span class="sxs-lookup"><span data-stu-id="17a30-131">Note that you might need to drag the *Build Settings* window out of the way in order to see the inspector panel.</span></span> <span data-ttu-id="17a30-132">Флажок *Virtual Reality Supported* (Поддержка виртуальной реальности) также применяется к гарнитурам дополненной и смешанной реальности, так как он включает стереоскопическое изображение (отрисовка разных изображений для каждого глаза).</span><span class="sxs-lookup"><span data-stu-id="17a30-132">The *Virtual Reality Supported* checkbox also applies to Mixed Reality and Augmented Reality headsets because it refers to the enabling of stereoscopic vision (rendering different images for each eye.)</span></span>

    ![Урок 1, раздел 2, шаг 3](images/mrlearning-base-ch1-2-step3.JPG)

4. <span data-ttu-id="17a30-134">Кроме того, в разделе "XR Settings" (Параметры XR) измените режим *Stereo Rendering Mode* (Режим стереоскопической отрисовки) на *Single Pass Instanced* (Однопроходная отрисовка экземпляра).</span><span class="sxs-lookup"><span data-stu-id="17a30-134">Also under XR Settings, change the *Stereo Rendering Mode* to *Single Pass Instanced*.</span></span> <span data-ttu-id="17a30-135">Этот [стиль конвейера отрисовки](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) обычно является наиболее производительным для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="17a30-135">This [rendering pipeline style](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) is generally most performant for HoloLens 2.</span></span> <span data-ttu-id="17a30-136">Если вас интересуют другие производительные конфигурации для среды Unity, следуйте [этим инструкциям](recommended-settings-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="17a30-136">If interested in other performant configurations for your Unity environment, follow [these instructions](recommended-settings-for-unity.md).</span></span>

    ![Урок 1, раздел 2, шаг 4](images/mrlearning-base-ch1-2-step4.jpg)

5. <span data-ttu-id="17a30-138">На той же панели инспектора в области возможностей раздела *Publishing Settings* (Параметры публикации) убедитесь, что установлен флажок *Spatial Perception* (Пространственное восприятие).</span><span class="sxs-lookup"><span data-stu-id="17a30-138">From the same inspector panel, ensure that the *Spatial Perception* checkbox in the capabilities section is enabled under *Publishing Settings*.</span></span> <span data-ttu-id="17a30-139">Пространственное восприятие позволяет визуализировать сетку пространственного сопоставления на устройстве смешанной реальности, таком как HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="17a30-139">Spatial Perception allows us to visualize the spatial mapping mesh on a mixed reality device, such as HoloLens 2.</span></span> <span data-ttu-id="17a30-140">Раздел параметров публикации находится на панели инспектора над областью "XR Settings" (Параметры XR) в разделе "Other Settings" (Другие параметры).</span><span class="sxs-lookup"><span data-stu-id="17a30-140">Publishing Settings are found in the inspector panel, above XR Settings and under Other Settings.</span></span>

    ![Урок 1, раздел 2, шаг 5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    ><span data-ttu-id="17a30-142">Вы можете включить и другие распространенные функции (хотя в этом разделе они не используются), например *Microphone* (для голосовых команд) и *InternetClient* (для подключения к службам, для которых требуется сетевое подключение).</span><span class="sxs-lookup"><span data-stu-id="17a30-142">While not used in this section, some other common capabilities you might want to enable include the *Microphone* for voice commands, and *InternetClient* for connecting to services requiring a network connection.</span></span>

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="17a30-143">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="17a30-143">Import the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="17a30-144">Скачайте [пакет платформы Unity версии 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) для [набора средств для смешанной реальности](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) (Mixed Reality Toolkit) и сохраните его в папке на своем компьютере.</span><span class="sxs-lookup"><span data-stu-id="17a30-144">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) and save it to a folder on your PC.</span></span>

2. <span data-ttu-id="17a30-145">Импортируйте пакет *набора средств для смешанной реальности*, скачанный на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="17a30-145">Import the *Mixed Reality Toolkit* package that you downloaded in the previous step.</span></span> <span data-ttu-id="17a30-146">Щелкните **Assets** (Ресурсы)  > **Import** (Импортировать)  > **Custom Package** (Пользовательский пакет), выберите *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* и откройте его, чтобы начать процесс импорта.</span><span class="sxs-lookup"><span data-stu-id="17a30-146">Start by clicking on **Assets** > **Import** > **Custom Package**, select *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* and open it to begin the importing process.</span></span> <span data-ttu-id="17a30-147">Процесс импорта может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="17a30-147">Allow a few minutes for the importing process to complete.</span></span>

    ![Урок 1, раздел 3, шаг 2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![Урок 1, раздел 3, шаг 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. <span data-ttu-id="17a30-150">В следующем всплывающем окне щелкните **Import** (Импортировать), чтобы начать импорт выбранного пакета в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="17a30-150">In the next pop-up window, click **Import** to begin importing the selected package into the Unity project.</span></span> <span data-ttu-id="17a30-151">Убедитесь, что все параметры выбраны, как показано на приведенном ниже рисунке.</span><span class="sxs-lookup"><span data-stu-id="17a30-151">Ensure all items are checked as shown in the image.</span></span>

    ![Урок 1, раздел 3, шаг 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > <span data-ttu-id="17a30-153">Если появится всплывающее диалоговое окно с запросом на применение параметров по умолчанию для набора средств для смешанной реальности, щелкните **Apply** (Применить).</span><span class="sxs-lookup"><span data-stu-id="17a30-153">If you see a pop-up dialog box asking to apply the Mixed Reality Toolkit default settings, click **Apply**.</span></span> <span data-ttu-id="17a30-154">При импорте MRTK анализирует ваш проект, выявляя пропущенные рекомендуемые параметры, чтобы обеспечить автоматическую настройку.</span><span class="sxs-lookup"><span data-stu-id="17a30-154">MRTK analyzes your project for any missing recommended settings when imported for automated setup.</span></span> <span data-ttu-id="17a30-155">В зависимости от выбранных параметров всплывающее окно может выглядеть иначе, чем на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="17a30-155">Depending on your settings, the pop-up might look different than the image below.</span></span>

    ![Урок 1, раздел 3, шаг 4, примечание 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="17a30-157">Настройка набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="17a30-157">Configure the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="17a30-158">Добавьте *набор средств для смешанной реальности* в текущую сцену, выбрав **Mixed Reality Toolkit** (Набор средств для смешанной реальности)  > **Add to Scene and Configure** (Добавить в сцену и настроить)</span><span class="sxs-lookup"><span data-stu-id="17a30-158">Add the *Mixed Reality Toolkit* to your current scene by selecting **Mixed Reality Toolkit** > **Add to Scene and Configure..**</span></span> <span data-ttu-id="17a30-159">в строке меню.</span><span class="sxs-lookup"><span data-stu-id="17a30-159">from the menu bar.</span></span> <span data-ttu-id="17a30-160">Если после импорта набора средств для смешанной реальности этот пункт меню не отображается, перезапустите Unity.</span><span class="sxs-lookup"><span data-stu-id="17a30-160">If you don't see this menu item after importing the mixed reality toolkit, restart Unity.</span></span>

    ![Урок 1, раздел 4, шаг 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > <span data-ttu-id="17a30-162">Может появиться всплывающее диалоговое окно для выбора [профиля для набора средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span><span class="sxs-lookup"><span data-stu-id="17a30-162">You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="17a30-163">Выберите профиль *DefaultHoloLens2ConfigurationProfile*, дважды щелкнув его.</span><span class="sxs-lookup"><span data-stu-id="17a30-163">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

2. <span data-ttu-id="17a30-164">В сцене появится несколько новых элементов и изменений.</span><span class="sxs-lookup"><span data-stu-id="17a30-164">Your scene will have several new items and modifications.</span></span> <span data-ttu-id="17a30-165">Сохраните сцену под другим именем, щелкнув **File** (Файл)  > **Save As** (Сохранить как) и укажите имя для сцены, например *BaseScene*.</span><span class="sxs-lookup"><span data-stu-id="17a30-165">Save your scene under a different name by clicking **File** > **Save As...**, and give your scene a name, such as *BaseScene*.</span></span> <span data-ttu-id="17a30-166">Сохраните сцену в папке *Scenes* в папке *Assets* проекта, чтобы все сцены хранились в одном месте.</span><span class="sxs-lookup"><span data-stu-id="17a30-166">Keep your scene organized by saving it to the *Scenes* folder in your project’s *Assets* folder.</span></span>

    ![Урок 1, раздел 4, шаг 2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![Урок 1, раздел 4, шаг 2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="17a30-169">Разработка приложения для устройства</span><span class="sxs-lookup"><span data-stu-id="17a30-169">Build your application to your device</span></span>

1. <span data-ttu-id="17a30-170">Если вы закрыли окно *Build Settings* (Параметры сборки), открытое в предыдущих разделах, снова откройте его, выбрав **File** (Файл)  > **Build Settings** (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="17a30-170">If you closed the *Build Settings* window from the previous sections, open the *Build Settings* window again by going to **File** > **Build Settings**.</span></span>

    ![Урок 1, раздел 5, шаг 1](images/mrlearning-base-ch1-5-step1.JPG)

2. <span data-ttu-id="17a30-172">Убедитесь, что созданная сцена указана в списке *Scenes in Build* (Сцены в сборке), нажав кнопку **Add Open Scenes** (Добавить открытые сцены). Эта сцена должна быть открыта в Unity.</span><span class="sxs-lookup"><span data-stu-id="17a30-172">Ensure the scene you just created is in the *Scenes in Build* list by clicking on the **Add Open Scenes** button while your scene is open in Unity.</span></span>

3. <span data-ttu-id="17a30-173">Нажмите кнопку **Build** (Сборка), чтобы начать процесс сборки.</span><span class="sxs-lookup"><span data-stu-id="17a30-173">Press the **Build** button to begin the build process.</span></span>

    ![Урок 1, раздел 5, шаг 3](images/mrlearning-base-ch1-5-step3.JPG)

4. <span data-ttu-id="17a30-175">Создайте папку для приложения и укажите для нее название.</span><span class="sxs-lookup"><span data-stu-id="17a30-175">Create and name a new folder for your application.</span></span> <span data-ttu-id="17a30-176">На приведенном ниже изображении для хранения приложения была создана папка App.</span><span class="sxs-lookup"><span data-stu-id="17a30-176">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="17a30-177">Щелкните **Select Folder** (Выбор папки), чтобы начать создание приложения в новой папке.</span><span class="sxs-lookup"><span data-stu-id="17a30-177">Click **Select Folder** to begin building to the newly created folder.</span></span> <span data-ttu-id="17a30-178">После завершения создания вы можете закрыть окно *Build Settings* (Параметры сборки) в Unity.</span><span class="sxs-lookup"><span data-stu-id="17a30-178">After the build has completed, you can close the *Build Settings* window in Unity.</span></span>

    ![Урок 1, раздел 5, шаг 4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    ><span data-ttu-id="17a30-180">Если сборка завершилась сбоем, попробуйте выполнить ее заново или перезапустите Unity и повторите попытку.</span><span class="sxs-lookup"><span data-stu-id="17a30-180">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="17a30-181">Может отобразиться ошибка, например "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?) (Ошибка: CS0246 = не удалось найти тип или имя пространства имен XX (возможно, отсутствует директива using или ссылка на сборку)).</span><span class="sxs-lookup"><span data-stu-id="17a30-181">If you see an error, such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="17a30-182">В этом случае может потребоваться установить [пакет SDK Windows 10 (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="17a30-182">If so, you might need to install [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span></span>

5. <span data-ttu-id="17a30-183">После завершения сборки откройте созданную папку, содержащую файлы только что созданного приложения.</span><span class="sxs-lookup"><span data-stu-id="17a30-183">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="17a30-184">Дважды щелкните решение *MixedRealityBase.sln* (или соответствующее имя, если вы использовали альтернативное имя для своего проекта), чтобы открыть файл решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17a30-184">Double-click on the *MixedRealityBase.sln* solution, or the corresponding name, if you used an alternative name for your project, to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="17a30-185">Обязательно откройте созданную папку (т. е. папку *App*, если вы следовали соглашениям об именовании из предыдущих шагов), так как за пределами этой папки будет находиться SLN-файл с аналогичным именем. Не перепутайте его с SLN-файлом, содержащимся в папке сборки.</span><span class="sxs-lookup"><span data-stu-id="17a30-185">Be sure to open the newly created folder (i.e. the *App* folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder, that is not to be confused with the .sln file inside the build folder.</span></span> <span data-ttu-id="17a30-186">Структура папок должна выглядеть примерно так, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="17a30-186">The folder structure should look similar to the image below.</span></span>
    >
    ><span data-ttu-id="17a30-187">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано на [этой странице](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="17a30-187">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

    ![Урок 1, раздел 5, шаг 5](images/mrlearning-base-ch1-5-step5.JPG)

6. <span data-ttu-id="17a30-189">Подключите HoloLens 2 к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="17a30-189">Connect your HoloLens 2 into your PC.</span></span> <span data-ttu-id="17a30-190">Хотя в данных инструкциях предполагается, что вы будете развертывать приложение на устройстве HoloLens 2, вы можете также развернуть его на [эмуляторе HoloLens 2](using-the-hololens-emulator.md) или создать [пакет приложения для передачи данных на другое локальное устройство](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="17a30-190">While these instructions assume you will be deploying to a HoloLens 2 device, you might also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="17a30-191">Перед выполнением сборки на устройстве его нужно перевести в *режим разработчика* и связать с компьютером разработки.</span><span class="sxs-lookup"><span data-stu-id="17a30-191">Before building to your device, the device must be in *Developer Mode* and paired with your development machine.</span></span> <span data-ttu-id="17a30-192">Большинство этих действий можно выполнить, следуя [данным инструкциям](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="17a30-192">Both of these steps can be completed by following [these instructions](using-visual-studio.md)</span></span>

7. <span data-ttu-id="17a30-193">Настройте Visual Studio для сборки на устройство HoloLens 2, выбрав конфигурацию *Выпуск* или *Ведущий*, архитектуру *ARM* и цель *Устройство*.</span><span class="sxs-lookup"><span data-stu-id="17a30-193">Configure Visual Studio for building to your HoloLens 2 by selecting the *Release* or *Master* configuration, the *ARM* architecture, and *Device* as target.</span></span>

    ![Урок 1, раздел 5, шаг 8](images/mrlearning-base-ch1-5-step7.JPG)

8. <span data-ttu-id="17a30-195">Завершающий шаг — это сборка и развертывание на вашем устройстве. Выберите **Отладка** > **Запуск без отладки**.</span><span class="sxs-lookup"><span data-stu-id="17a30-195">The final step is to build and deploy to your device by selecting **Debug** > **Start without debugging**.</span></span> <span data-ttu-id="17a30-196">Выбор *Запуск без отладки* приведет к немедленному запуску приложения на вашем устройстве после успешной сборки, но без подключения отладчика и отображения сведений об отладке в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17a30-196">Selecting *Start without Debugging* causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="17a30-197">Это также означает, что вы можете отсоединить USB-кабель во время выполнения приложения на устройстве HoloLens 2, не прерывая его работу.</span><span class="sxs-lookup"><span data-stu-id="17a30-197">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="17a30-198">Кроме того, вы можете выбрать **Сборка** > **Развернуть решение**, чтобы развернуть решение на устройстве без автоматического запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="17a30-198">You might also select **Build** > **Deploy Solution** to deploy to your device without having the application automatically start.</span></span>

    ![Урок 1, раздел 5, шаг 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a><span data-ttu-id="17a30-200">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="17a30-200">Congratulations</span></span>

<span data-ttu-id="17a30-201">Вы развернули свое первое приложение HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="17a30-201">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="17a30-202">Перемещаясь, вы увидите, как пространственная сетка сопоставления покрывает все поверхности, воспринятые HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="17a30-202">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="17a30-203">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="17a30-203">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="17a30-204">Это лишь некоторые из основополагающих компонентов, входящих в комплект поставки набора средств для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="17a30-204">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="17a30-205">На следующих уроках вы начнете добавлять больше содержимого и интерактивных средств в сцену, чтобы в полной мере изучить возможности HoloLens 2 и набора средств для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="17a30-205">In the lessons to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="17a30-206">В приложении вы можете заметить визуальный профилировщик.</span><span class="sxs-lookup"><span data-stu-id="17a30-206">In the app, you may notice the visual profiler.</span></span> <span data-ttu-id="17a30-207">Переключение счетчика частоты кадров с помощью голосовой команды описывается в [уроке 5](mrlearning-base-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="17a30-207">You will cover how to toggle the frame rate counter using a voice command in [Lesson 5](mrlearning-base-ch5.md).</span></span> <span data-ttu-id="17a30-208">Обычно рекомендуется постоянно отображать визуальный профилировщик во время разработки. Это позволит определить, если изменения кода повлияют на производительность.</span><span class="sxs-lookup"><span data-stu-id="17a30-208">It is generally recommended to keep the visual profiler visible at all times during development to understand when code changes may have impacted perf.</span></span> <span data-ttu-id="17a30-209">Приложение HoloLens 2 должно [непрерывно выполняться в режиме 60 кадров/с](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="17a30-209">HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="17a30-210">Следующий урок. 3. Создание пользовательского интерфейса и настройка набора средств для Смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="17a30-210">Next Lesson: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
