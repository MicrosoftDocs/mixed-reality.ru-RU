---
title: Создание проекта holographic DirectX
description: В этой статье описывается создание нового holographic приложения на основе шаблона приложения Windows смешанной реальности.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Смешанная реальность Windows holographic приложения, новое приложение, приложение универсальной платформы Windows, приложения шаблона, голограммы, новый проект, пошаговое руководство, загрузки, пример кода
ms.openlocfilehash: 7d1ea0246cf823f74e68b4e67fbcfc275d081688
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605096"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="37548-104">Создание проекта holographic DirectX</span><span class="sxs-lookup"><span data-stu-id="37548-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="37548-105">Holographic приложения, создаваемые для HoloLens будут <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">приложения универсальной платформы Windows (UWP)</a>.</span><span class="sxs-lookup"><span data-stu-id="37548-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="37548-106">Если для рабочего стола Windows Mixed Reality гарнитуры, можно создать приложение универсальной платформы Windows или приложения Win32.</span><span class="sxs-lookup"><span data-stu-id="37548-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="37548-107">Шаблон приложения универсальной платформы Windows holographic DirectX 11 очень напоминает шаблон приложения универсальной платформы Windows DirectX 11; он включает в себя программы цикла (или «цикла игры»), **DeviceResources** класса для управления устройство Direct3D и контекста, а также класс упрощенный обработчик содержимого.</span><span class="sxs-lookup"><span data-stu-id="37548-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="37548-108">Есть также <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>точно так же, как любое другое приложение универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="37548-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="37548-109">Приложение смешанной реальности, однако имеет некоторые дополнительные возможности, которые не присутствуют в типичном приложении Direct3D 11 UWP.</span><span class="sxs-lookup"><span data-stu-id="37548-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="37548-110">Windows Holographic шаблон приложения возможность:</span><span class="sxs-lookup"><span data-stu-id="37548-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="37548-111">Обработка ресурсов устройства Direct3D, связанных с holographic камеры.</span><span class="sxs-lookup"><span data-stu-id="37548-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="37548-112">Получить камеры задние буферы из системы.</span><span class="sxs-lookup"><span data-stu-id="37548-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="37548-113">Обрабатывать [помощи](gaze.md) ввода и распознавания простой [жест](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="37548-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="37548-114">Перейти в режим полноэкранной отрисовке стерео.</span><span class="sxs-lookup"><span data-stu-id="37548-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="37548-115">Как начать работу?</span><span class="sxs-lookup"><span data-stu-id="37548-115">How do I get started?</span></span>

<span data-ttu-id="37548-116">Первый [установить средства](install-the-tools.md), следующие инструкции по скачиванию Visual Studio 2017 и в эмуляторе Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="37548-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2017 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="37548-117">Шаблоны holographic приложения включены в тот же установщик, что и эмулятор Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="37548-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="37548-118">Также убедитесь, что перед установкой выбран параметр, чтобы установить шаблоны.</span><span class="sxs-lookup"><span data-stu-id="37548-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="37548-119">Теперь вы готовы создать приложение DirectX 11 Windows смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="37548-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="37548-120">Обратите внимание на то, чтобы удалить этот пример содержимого, закомментируйте **DRAW_SAMPLE_CONTENT** директивы препроцессора в *pch.h*.</span><span class="sxs-lookup"><span data-stu-id="37548-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="37548-121">Создание проекта UWP</span><span class="sxs-lookup"><span data-stu-id="37548-121">Creating a UWP project</span></span>

<span data-ttu-id="37548-122">После установки средства можно затем создать holographic проекта DirectX UWP.</span><span class="sxs-lookup"><span data-stu-id="37548-122">Once the tools are installed you can then create a holographic DirectX UWP project.</span></span> <span data-ttu-id="37548-123">Чтобы создать новый проект:</span><span class="sxs-lookup"><span data-stu-id="37548-123">To create a new project:</span></span>
1. <span data-ttu-id="37548-124">Запуск **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="37548-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="37548-125">Из **файл** последовательно выберите пункты **New** и выберите **проекта** в контекстном меню.</span><span class="sxs-lookup"><span data-stu-id="37548-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="37548-126">**Новый проект** откроется диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="37548-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="37548-127">Разверните **установленные** слева и разверните **Visual C++**  узел языка.</span><span class="sxs-lookup"><span data-stu-id="37548-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="37548-128">Перейдите к **универсальной Windows > Holographic** узел и выберите **Holographic приложение DirectX 11 (универсальные Windows) (C++/WinRT)**.</span><span class="sxs-lookup"><span data-stu-id="37548-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="37548-129">Убедитесь, что имя шаблона проекта включает «(C++/WinRT)».</span><span class="sxs-lookup"><span data-stu-id="37548-129">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="37548-130">В противном случае у вас есть более старой версии holographic шаблонов проектов установки.</span><span class="sxs-lookup"><span data-stu-id="37548-130">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="37548-131">Чтобы получить последние шаблоны проекта, [установить последнюю эмулятор HoloLens](using-the-hololens-emulator.md).</span><span class="sxs-lookup"><span data-stu-id="37548-131">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="37548-132">Заполните **имя** и **расположение** текстовые поля и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="37548-132">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="37548-133">Создается проект holographic приложения.</span><span class="sxs-lookup"><span data-stu-id="37548-133">The holographic app project is created.</span></span>
6. <span data-ttu-id="37548-134">Для разработки приложений для различных версий только 2 HoloLens, убедитесь, что **целевой версии** и **Минимальная версия** присваивается **Windows 10, версия 1903**.</span><span class="sxs-lookup"><span data-stu-id="37548-134">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="37548-135">Если планируется также HoloLens (1-го поколения) или рабочего стола гарнитуры смешанной реальности Windows, можно задать **Минимальная версия** для **Windows 10, версия 1809** вместо этого, несмотря на то, что это потребует некоторых <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> проверки версий adapative</a> в коде при использовании новые возможности HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="37548-135">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adapative checks</a> in your code when using new features of HoloLens 2.</span></span>

<span data-ttu-id="37548-136">![Снимок экрана: шаблон проекта holographic приложения в Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="37548-136">![Screenshot of the holographic app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
<span data-ttu-id="37548-137">*Шаблон проекта holographic приложения в Visual Studio*</span><span class="sxs-lookup"><span data-stu-id="37548-137">*Holographic app project template in Visual Studio*</span></span>

<span data-ttu-id="37548-138">Шаблон создает проект с использованием <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, C ++ 17 языковых проекцию API среды выполнения Windows, которая поддерживает любой совместимый со стандартами C ++ 17 компилятор.</span><span class="sxs-lookup"><span data-stu-id="37548-138">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="37548-139">Проекта показано, как создать куб заблокирован для мира, помещенный два счетчика от пользователя.</span><span class="sxs-lookup"><span data-stu-id="37548-139">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="37548-140">Пользователь может [жест касания](gestures.md#air-tap) или нажать кнопку на контроллере, чтобы поместить куба в другое место, который задается параметром пользователя [помощи](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="37548-140">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="37548-141">Вы можете изменить этот проект для создания любого приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="37548-141">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="37548-142">Кроме того, можно создать новый проект с помощью **Visual C#**  шаблона holographic проекта, который основан на SharpDX.</span><span class="sxs-lookup"><span data-stu-id="37548-142">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="37548-143">Если ваш holographic C# проекта не запустилась из Windows Holographic шаблон приложения, вам потребуется скопировать файл ms.fxcompile.targets из Windows Mixed Reality C# шаблона проекта и импорта его в ваш .csproj файла для компиляции HLSL файлы, добавляемые в проект.</span><span class="sxs-lookup"><span data-stu-id="37548-143">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="37548-144">Просмотрите [с помощью Visual Studio для развертывания и отладки](using-visual-studio.md) сведения о том, как построение и развертывание примера в вашей HoloLens, ПК с иммерсивных устройство или эмулятор.</span><span class="sxs-lookup"><span data-stu-id="37548-144">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="37548-145">Остальная часть в инструкциях ниже предполагается, что вы используете C++ к сборке приложения.</span><span class="sxs-lookup"><span data-stu-id="37548-145">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="37548-146">Точка входа для приложения универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="37548-146">UWP app entry point</span></span>

<span data-ttu-id="37548-147">Запускает приложения универсальной платформы Windows holographic в **wWinMain** функции в AppView.cpp.</span><span class="sxs-lookup"><span data-stu-id="37548-147">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="37548-148">**WWinMain** функция создает приложения <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> и запускает <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> с ним.</span><span class="sxs-lookup"><span data-stu-id="37548-148">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="37548-149">Из **AppView.cpp**:</span><span class="sxs-lookup"><span data-stu-id="37548-149">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="37548-150">С этого момента AppView обрабатывает взаимодействие с Windows основные входные события CoreWindow события и обмена сообщениями и т. д.</span><span class="sxs-lookup"><span data-stu-id="37548-150">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="37548-151">Он также создаст HolographicSpace, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="37548-151">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="37548-152">Создание проекта Win32</span><span class="sxs-lookup"><span data-stu-id="37548-152">Creating a Win32 project</span></span>

<span data-ttu-id="37548-153">Самый простой способ приступить к созданию Win32, holographic проекта — адаптировать <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* пример Win32</a>.</span><span class="sxs-lookup"><span data-stu-id="37548-153">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="37548-154">В этом примере Win32 используется <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, C ++ 17 языковых проекцию API среды выполнения Windows, которая поддерживает любой совместимый со стандартами C ++ 17 компилятор.</span><span class="sxs-lookup"><span data-stu-id="37548-154">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="37548-155">Проекта показано, как создать куб заблокирован для мира, помещенный два счетчика от пользователя.</span><span class="sxs-lookup"><span data-stu-id="37548-155">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="37548-156">Пользователь может нажать кнопку на контроллере, чтобы поместить куба в другое место, который задается параметром пользователя [помощи](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="37548-156">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="37548-157">Вы можете изменить этот проект для создания любого приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="37548-157">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="37548-158">Точка входа приложения Win32</span><span class="sxs-lookup"><span data-stu-id="37548-158">Win32 app entry point</span></span>

<span data-ttu-id="37548-159">Запускает holographic приложения Win32 в **wWinMain** функции в AppMain.cpp.</span><span class="sxs-lookup"><span data-stu-id="37548-159">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="37548-160">**WWinMain** функция создает HWND приложения и запускает цикл сообщений.</span><span class="sxs-lookup"><span data-stu-id="37548-160">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="37548-161">Из **AppMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="37548-161">From **AppMain.cpp**:</span></span>

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

<span data-ttu-id="37548-162">С этого момента AppMain обрабатывает взаимодействие с основные окна сообщений и т. д.</span><span class="sxs-lookup"><span data-stu-id="37548-162">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="37548-163">Он также создаст HolographicSpace, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="37548-163">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="37548-164">Визуализации holographic содержимого</span><span class="sxs-lookup"><span data-stu-id="37548-164">Render holographic content</span></span>

<span data-ttu-id="37548-165">Проекта **содержимого** папка содержит классы для подготовки к просмотру голограммы в [holographic пространства](getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="37548-165">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="37548-166">Голограмма по умолчанию в шаблоне является вращающегося куба, который разместил два метров от пользователя.</span><span class="sxs-lookup"><span data-stu-id="37548-166">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="37548-167">Рисование этого куба реализуется в **SpinningCubeRenderer.cpp**, который имеет следующие основные методы:</span><span class="sxs-lookup"><span data-stu-id="37548-167">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="37548-168">Метод</span><span class="sxs-lookup"><span data-stu-id="37548-168">Method</span></span>  |  <span data-ttu-id="37548-169">Объяснение</span><span class="sxs-lookup"><span data-stu-id="37548-169">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="37548-170">Загружает шейдеры и создает сетку куба.</span><span class="sxs-lookup"><span data-stu-id="37548-170">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="37548-171">Помещает голограмма в расположении, указанном с использованием указанного <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span><span class="sxs-lookup"><span data-stu-id="37548-171">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="37548-172">Поворачивает куб и задает матрицы модели.</span><span class="sxs-lookup"><span data-stu-id="37548-172">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="37548-173">Прорисовывает кадр, с помощью шейдеров вершин и пикселей.</span><span class="sxs-lookup"><span data-stu-id="37548-173">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="37548-174">**Шейдеры** вложенная папка содержит четыре реализации шейдера по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="37548-174">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="37548-175">Построитель текстуры</span><span class="sxs-lookup"><span data-stu-id="37548-175">Shader</span></span>  |  <span data-ttu-id="37548-176">Объяснение</span><span class="sxs-lookup"><span data-stu-id="37548-176">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="37548-177">К серверу, который оставляет геометрии без изменений.</span><span class="sxs-lookup"><span data-stu-id="37548-177">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="37548-178">Проходит через данные о цвете.</span><span class="sxs-lookup"><span data-stu-id="37548-178">Passes through the color data.</span></span> <span data-ttu-id="37548-179">Данные о цвете интерполированные и заданы для точки на этапе растеризации.</span><span class="sxs-lookup"><span data-stu-id="37548-179">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="37548-180">Простой шейдер для обработки вершин в GPU.</span><span class="sxs-lookup"><span data-stu-id="37548-180">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="37548-181">Простой шейдер для обработки вершин в GPU, оптимизированный для смешанной реальности Windows стерео отрисовки.</span><span class="sxs-lookup"><span data-stu-id="37548-181">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="37548-182">`VertexShaderShared.hlsl` содержит код, общий между `VertexShader.hlsl` и `VPRTVertexShader.hlsl`.</span><span class="sxs-lookup"><span data-stu-id="37548-182">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="37548-183">Шейдеры компилируются при сборке проекта, и они загружены в **SpinningCubeRenderer::CreateDeviceDependentResources** метод.</span><span class="sxs-lookup"><span data-stu-id="37548-183">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="37548-184">Взаимодействовать с вашей голограммы</span><span class="sxs-lookup"><span data-stu-id="37548-184">Interact with your holograms</span></span>

<span data-ttu-id="37548-185">Ввод данных пользователем обрабатывается в **SpatialInputHandler** класса, который будет <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> экземпляра и подписывается на <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> событий.</span><span class="sxs-lookup"><span data-stu-id="37548-185">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="37548-186">Это позволяет, определение жеста жест касания и другие Пространственные входных событий.</span><span class="sxs-lookup"><span data-stu-id="37548-186">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="37548-187">Обновление содержимого holographic</span><span class="sxs-lookup"><span data-stu-id="37548-187">Update holographic content</span></span>

<span data-ttu-id="37548-188">Смешанная реальность обновлений в цикл игры, который по умолчанию реализуется в **обновление** метод в `AppMain.cpp`.</span><span class="sxs-lookup"><span data-stu-id="37548-188">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="37548-189">**Обновление** метод обновляет объектов сцены, например вращающегося куба и возвращает <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> объект, используемый для получения актуальной матриц представления и проекции и представлять цепочки буферов.</span><span class="sxs-lookup"><span data-stu-id="37548-189">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="37548-190">**Визуализации** метод в `AppMain.cpp` принимает <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> и прорисовывает текущий кадр для каждого holographic камеры, в соответствии с текущим приложением и пространственных позиционирования состояния.</span><span class="sxs-lookup"><span data-stu-id="37548-190">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="37548-191">См. также</span><span class="sxs-lookup"><span data-stu-id="37548-191">See also</span></span>
* [<span data-ttu-id="37548-192">Начало HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="37548-192">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="37548-193"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="37548-193"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="37548-194">Подготовка к просмотру в DirectX</span><span class="sxs-lookup"><span data-stu-id="37548-194">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="37548-195">С помощью Visual Studio для развертывания и отладки</span><span class="sxs-lookup"><span data-stu-id="37548-195">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="37548-196">Использование эмулятора HoloLens</span><span class="sxs-lookup"><span data-stu-id="37548-196">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="37548-197">Использование XAML holographic приложениях DirectX</span><span class="sxs-lookup"><span data-stu-id="37548-197">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
