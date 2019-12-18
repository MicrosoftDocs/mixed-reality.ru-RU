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
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="74e39-105">Добавление пространственного звука в проект Unity</span><span class="sxs-lookup"><span data-stu-id="74e39-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="74e39-106">Добро пожаловать в пространственное аудио тутиорал для Unity на HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="74e39-106">Welcome to the spatial audio tutioral for Unity on HoloLens2.</span></span> <span data-ttu-id="74e39-107">В этой последовательности учебников показано следующее:</span><span class="sxs-lookup"><span data-stu-id="74e39-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="74e39-108">Как использовать разгрузку ХРТФ в HoloLens 2 в Unity</span><span class="sxs-lookup"><span data-stu-id="74e39-108">How to use HRTF offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="74e39-109">Включение переглагола при использовании разгрузки ХРТФ</span><span class="sxs-lookup"><span data-stu-id="74e39-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="74e39-110">В [репозитории Microsoft Спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity) есть завершенный проект Unity этой последовательности руководств.</span><span class="sxs-lookup"><span data-stu-id="74e39-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="74e39-111">Рекомендации по спатиализеи звуков см. в статье как использовать [Пространственный звук](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="74e39-111">For our recommendations on when it can be helpful to spatialize sounds, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="objectives"></a><span data-ttu-id="74e39-112">Задачи</span><span class="sxs-lookup"><span data-stu-id="74e39-112">Objectives</span></span>
<span data-ttu-id="74e39-113">В этой первой главе вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="74e39-113">In this first chapter, you'll:</span></span>
* <span data-ttu-id="74e39-114">Создание проекта Unity и импорт МРТК</span><span class="sxs-lookup"><span data-stu-id="74e39-114">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="74e39-115">Импорт подключаемого модуля Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="74e39-115">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="74e39-116">Включение подключаемого модуля Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="74e39-116">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="74e39-117">Включение пространственного звука на рабочей станции разработчика</span><span class="sxs-lookup"><span data-stu-id="74e39-117">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="74e39-118">Создание проекта и добавление NuGet для Unity</span><span class="sxs-lookup"><span data-stu-id="74e39-118">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="74e39-119">Начните с пустого проекта Unity, а затем добавьте и настройте NuGet для Unity:</span><span class="sxs-lookup"><span data-stu-id="74e39-119">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="74e39-120">Скачайте последнюю версию [нужетфорунити. пакет unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="74e39-120">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="74e39-121">В строке меню Unity щелкните **активы-> импортировать пакет-> пользовательский пакет...** и установите пакет нужетфорунити:</span><span class="sxs-lookup"><span data-stu-id="74e39-121">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Импорт пользовательского пакета](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="74e39-123">Добавление пакета Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="74e39-123">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="74e39-124">Поддержка Windows Mixed Reality в Unity 2019 и более поздних версиях содержится в необязательном пакете.</span><span class="sxs-lookup"><span data-stu-id="74e39-124">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="74e39-125">Чтобы добавить его в проект, откройте **окно Диспетчер пакетов >** в строке меню Unity:</span><span class="sxs-lookup"><span data-stu-id="74e39-125">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Меню диспетчера пакетов](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="74e39-127">Затем найдите и установите пакет **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="74e39-127">Then find and install the **Windows Mixed Reality** package:</span></span>

![Окно диспетчера пакетов](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="74e39-129">Установка МРТК и Microsoft Спатиализер</span><span class="sxs-lookup"><span data-stu-id="74e39-129">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="74e39-130">Используя NuGet для Unity, установите подключаемые модули МРТК и Microsoft Спатиализер.</span><span class="sxs-lookup"><span data-stu-id="74e39-130">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="74e39-131">В строке меню Unity щелкните **NuGet-> Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="74e39-131">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![Управление пакетами NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="74e39-133">В поле **поиска** введите "Microsoft. Микседреалити. Toolkit" и установите пакет мртк Core: **Microsoft. микседреалити. Toolkit. Foundation** .</span><span class="sxs-lookup"><span data-stu-id="74e39-133">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Пакет NuGet МРТК](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="74e39-135">[Пакет NuGet мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) имеет дополнительный контекст и сведения.</span><span class="sxs-lookup"><span data-stu-id="74e39-135">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="74e39-136">В поле **поиска** введите "Microsoft. спатиалаудио" и установите пакет Microsoft Спатиализер: **Microsoft. спатиалаудио. спатиализер. Unity.**</span><span class="sxs-lookup"><span data-stu-id="74e39-136">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![NuGet подключаемого модуля спатиализер](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="74e39-138">Настройка МРТК в проекте</span><span class="sxs-lookup"><span data-stu-id="74e39-138">Set up MRTK in your project</span></span>

1. <span data-ttu-id="74e39-139">Откройте окно параметры сборки, выбрав **файл-> параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="74e39-139">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="74e39-140">Выберите _универсальная платформа Windows_ и нажмите кнопку **Переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="74e39-140">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="74e39-141">Щелкните **Параметры проигрывателя** в **окне сборка** , чтобы открыть свойства **параметров проигрывателя** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="74e39-141">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="74e39-142">В разделе **Параметры XR**установите флажок **Поддерживаемые виртуальные реальность** .</span><span class="sxs-lookup"><span data-stu-id="74e39-142">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="74e39-143">В разделе **Параметры XR**измените **режим отображения стерео** на **один экземпляр однопроходного экземпляра**.</span><span class="sxs-lookup"><span data-stu-id="74e39-143">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="74e39-144">В разделе **Параметры публикации**установите флажок **пространственное восприятие** в разделе **возможности** .</span><span class="sxs-lookup"><span data-stu-id="74e39-144">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="74e39-145">В строке меню щелкните **набор средств для смешанной реальности — > добавить в сцену и настроить..**</span><span class="sxs-lookup"><span data-stu-id="74e39-145">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="74e39-146">чтобы добавить МРТК в сцену.</span><span class="sxs-lookup"><span data-stu-id="74e39-146">to add MRTK to your scene.</span></span>

<span data-ttu-id="74e39-147">Дополнительные рекомендации, включая создание приложения и развертывание в HoloLens 2, см. в [главе 1 базового модуля MR Learning](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="74e39-147">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="74e39-148">Включение подключаемого модуля Microsoft Спатиализер</span><span class="sxs-lookup"><span data-stu-id="74e39-148">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="74e39-149">Включите подключаемый модуль **Microsoft спатиализер** .</span><span class="sxs-lookup"><span data-stu-id="74e39-149">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="74e39-150">Откройте **> параметры проекта-> аудио**и измените **подключаемый модуль Спатиализер** на "Microsoft спатиализер".</span><span class="sxs-lookup"><span data-stu-id="74e39-150">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="74e39-151">Теперь раздел **аудио** в **параметрах проекта** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="74e39-151">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Параметры проекта, отображающие подключаемый модуль спатиализер](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="74e39-153">Включение пространственного звука на рабочей станции</span><span class="sxs-lookup"><span data-stu-id="74e39-153">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="74e39-154">В настольных версиях Windows Пространственный звук по умолчанию отключен.</span><span class="sxs-lookup"><span data-stu-id="74e39-154">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="74e39-155">Включите его, щелкнув значок тома правой кнопкой мыши на панели задач.</span><span class="sxs-lookup"><span data-stu-id="74e39-155">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="74e39-156">Чтобы получить лучшее представление о том, что вы услышите в HoloLens 2, выберите **Пространственный звук — > Windows Sonic для наушников**.</span><span class="sxs-lookup"><span data-stu-id="74e39-156">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Параметры пространственного звука рабочего стола](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="74e39-158">Этот параметр требуется только в том случае, если планируется тестирование проекта в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="74e39-158">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="74e39-159">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="74e39-159">Next steps</span></span>
<span data-ttu-id="74e39-160">Переходите к [пространственному аудио разделу Unity 2](unity-spatial-audio-ch2.md) до кнопки спатиализе (звуки).</span><span class="sxs-lookup"><span data-stu-id="74e39-160">Continue on to [Unity spatial audio chapter 2](unity-spatial-audio-ch2.md) to spatialize button interaction sounds.</span></span>

