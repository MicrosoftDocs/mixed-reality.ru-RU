---
title: Настройка проекта Unity для Windows Mixed Reality
description: Настройка проекта Unity без MRTK
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, смешанный реальность, разработка, Приступая к работе, новый проект
ms.openlocfilehash: 4ee81eca25109da428d7b3addf59e102ddc5c5cf
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993540"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="4b878-104">Настройка проекта Unity для Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4b878-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="4b878-105">(пропустите, если вы уже импортировали MRTK v2 в проект Unity)</span><span class="sxs-lookup"><span data-stu-id="4b878-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="4b878-106">Если вы хотите создать новый проект Unity без импорта смешанной реальности Toolkit, есть небольшой набор параметров Unity, вам потребуется вручную измените для смешанной реальности Windows, чтобы разделить на две категории: отдельных проектов и на сцене.</span><span class="sxs-lookup"><span data-stu-id="4b878-106">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="4b878-107">Параметры для отдельных проектов</span><span class="sxs-lookup"><span data-stu-id="4b878-107">Per-project settings</span></span>

<span data-ttu-id="4b878-108">Для смешанной реальности Windows, необходимо сначала настроить проект Unity, чтобы экспортировать в виде приложения универсальной платформы Windows:</span><span class="sxs-lookup"><span data-stu-id="4b878-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span>
1. <span data-ttu-id="4b878-109">Выберите **файл > Параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="4b878-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="4b878-110">Выберите **универсальной платформы Windows** на платформу в списке и нажмите кнопку **изменить платформу**</span><span class="sxs-lookup"><span data-stu-id="4b878-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="4b878-111">Задайте **SDK** для **универсальной 10**</span><span class="sxs-lookup"><span data-stu-id="4b878-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="4b878-112">Задайте **целевое устройство** для **любого устройства** для поддержки иммерсивную или переключиться в режим **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="4b878-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="4b878-113">Задайте **Тип_сборки** для **D3D**</span><span class="sxs-lookup"><span data-stu-id="4b878-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="4b878-114">Задайте **универсальной платформы Windows SDK** для **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="4b878-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="4b878-115">Затем нужно сообщить Unity известно, что следует создать приложение, мы пытаемся Экспорт [иммерсивных представление](app-views.md) вместо двухмерном виде.</span><span class="sxs-lookup"><span data-stu-id="4b878-115">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="4b878-116">Это сделать, включив «Поддерживается виртуальной реальности»:</span><span class="sxs-lookup"><span data-stu-id="4b878-116">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="4b878-117">Из **параметры сборки...**  открытое окно **параметры проигрывателя...**</span><span class="sxs-lookup"><span data-stu-id="4b878-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="4b878-118">Выберите **параметры для универсальной платформы Windows** вкладку</span><span class="sxs-lookup"><span data-stu-id="4b878-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="4b878-119">Разверните **XR параметры** группы</span><span class="sxs-lookup"><span data-stu-id="4b878-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="4b878-120">В **параметры XR** установите флажок **поддерживается виртуальной реальности** флажок, чтобы добавить **устройств виртуальной реальности** списка.</span><span class="sxs-lookup"><span data-stu-id="4b878-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="4b878-121">В **параметры XR** группе, убедитесь, что **«Windows Mixed Reality»** указана как поддерживаемое устройство.</span><span class="sxs-lookup"><span data-stu-id="4b878-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="4b878-122">(это может отображаться как «Windows Holographic» в более старых версиях Unity)</span><span class="sxs-lookup"><span data-stu-id="4b878-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="4b878-123">Приложение теперь можно выполнять основные holographic отрисовки и пространственных входных данных.</span><span class="sxs-lookup"><span data-stu-id="4b878-123">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="4b878-124">Чтобы пойти дальше и воспользоваться преимуществами некоторых возможностей, приложения необходимо объявить соответствующие возможности в манифесте.</span><span class="sxs-lookup"><span data-stu-id="4b878-124">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="4b878-125">Манифеста объявления можно сделать в Unity, поэтому они будут включены в каждый проект последующих экспорта.</span><span class="sxs-lookup"><span data-stu-id="4b878-125">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="4b878-126">Этот параметр можно найти в **параметры проигрывателя > Параметры для универсальной платформы Windows > Параметры публикации > возможности**.</span><span class="sxs-lookup"><span data-stu-id="4b878-126">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="4b878-127">Ниже приведены применимые возможности по включению часто используемые интерфейсы API Unity для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="4b878-127">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="4b878-128">Возможности</span><span class="sxs-lookup"><span data-stu-id="4b878-128">Capability</span></span>  |  <span data-ttu-id="4b878-129">API, требующие возможности</span><span class="sxs-lookup"><span data-stu-id="4b878-129">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="4b878-130">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="4b878-130">SpatialPerception</span></span>  |  <span data-ttu-id="4b878-131">SurfaceObserver (доступ к [пространственное сопоставление](spatial-mapping.md) сетки на HoloLens)&mdash;*отсутствует возможность для общего пространственных отслеживание гарнитура*</span><span class="sxs-lookup"><span data-stu-id="4b878-131">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="4b878-132">Веб-камера</span><span class="sxs-lookup"><span data-stu-id="4b878-132">WebCam</span></span>  |  <span data-ttu-id="4b878-133">PhotoCapture и VideoCapture</span><span class="sxs-lookup"><span data-stu-id="4b878-133">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="4b878-134">PicturesLibrary или VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="4b878-134">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="4b878-135">PhotoCapture или VideoCapture, соответственно (при хранении записанного содержимого)</span><span class="sxs-lookup"><span data-stu-id="4b878-135">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="4b878-136">Микрофон</span><span class="sxs-lookup"><span data-stu-id="4b878-136">Microphone</span></span>  |  <span data-ttu-id="4b878-137">VideoCapture (при записи аудио), DictationRecognizer, GrammarRecognizer и KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="4b878-137">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="4b878-138">internetClient</span><span class="sxs-lookup"><span data-stu-id="4b878-138">InternetClient</span></span>  |  <span data-ttu-id="4b878-139">DictationRecognizer (и использовать Unity Profiler)</span><span class="sxs-lookup"><span data-stu-id="4b878-139">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="4b878-140">**Параметры качества Unity**</span><span class="sxs-lookup"><span data-stu-id="4b878-140">**Unity quality settings**</span></span>

<span data-ttu-id="4b878-141">![Параметры качества Unity](images/unityqualitysettings-350px.png)</span><span class="sxs-lookup"><span data-stu-id="4b878-141">![Unity quality settings](images/unityqualitysettings-350px.png)</span></span><br>
<span data-ttu-id="4b878-142">*Параметры качества Unity*</span><span class="sxs-lookup"><span data-stu-id="4b878-142">*Unity quality settings*</span></span>

<span data-ttu-id="4b878-143">HoloLens имеет графический Процессор mobile класса.</span><span class="sxs-lookup"><span data-stu-id="4b878-143">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="4b878-144">Если приложение предназначено для HoloLens, вам понадобится параметры качества отображения быстрый производительностью убедитесь, что мы поддерживаем полный частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="4b878-144">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="4b878-145">Выберите **изменить > Параметры проекта > качества**</span><span class="sxs-lookup"><span data-stu-id="4b878-145">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="4b878-146">Выберите **раскрывающийся список** под **Windows Store** логотип и выберите **очень низкий**.</span><span class="sxs-lookup"><span data-stu-id="4b878-146">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="4b878-147">Вы будете знать, применяется параметр правильно при поле в столбце Windows Store и **очень низкий** строки отображается зеленым цветом.</span><span class="sxs-lookup"><span data-stu-id="4b878-147">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="4b878-148">Параметры сцену</span><span class="sxs-lookup"><span data-stu-id="4b878-148">Per-scene settings</span></span>

<span data-ttu-id="4b878-149">**Параметры камеры Unity**</span><span class="sxs-lookup"><span data-stu-id="4b878-149">**Unity camera settings**</span></span>

<span data-ttu-id="4b878-150">![Параметры камеры Unity](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="4b878-150">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="4b878-151">*Параметры камеры Unity*</span><span class="sxs-lookup"><span data-stu-id="4b878-151">*Unity camera settings*</span></span>

<span data-ttu-id="4b878-152">После включения флажок «Поддерживается виртуальной реальности», [камеры Unity](camera-in-unity.md) дескрипторы компонент [головного отслеживания "и" stereoscopic отрисовка](rendering.md).</span><span class="sxs-lookup"><span data-stu-id="4b878-152">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="4b878-153">Нет необходимости заменить его с помощью пользовательских камеры, чтобы сделать это.</span><span class="sxs-lookup"><span data-stu-id="4b878-153">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="4b878-154">Если приложение предназначено для HoloLens в частности, существует ряд параметров, которые должны быть изменены для оптимизации для прозрачного дисплеям устройств, поэтому приложения будут видны сквозь для физического мира.</span><span class="sxs-lookup"><span data-stu-id="4b878-154">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="4b878-155">В **иерархии**выберите **Main Camera**</span><span class="sxs-lookup"><span data-stu-id="4b878-155">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="4b878-156">В **инспектор** панели, задайте преобразование **позиции** для **0, 0, 0** , расположение заголовка пользователей начинается в начале координат world Unity.</span><span class="sxs-lookup"><span data-stu-id="4b878-156">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="4b878-157">Изменение **очистить флаги** для **Одноцветная**.</span><span class="sxs-lookup"><span data-stu-id="4b878-157">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="4b878-158">Изменение **фона** цвет **RGBA 0,0,0,0**.</span><span class="sxs-lookup"><span data-stu-id="4b878-158">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="4b878-159">Выполняет визуализацию черный как прозрачный в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4b878-159">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="4b878-160">Изменение **обрезки плоскостей - практически** для [HoloLens рекомендуется](camera-in-unity.md#clip-planes) 0,85 (метров).</span><span class="sxs-lookup"><span data-stu-id="4b878-160">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="4b878-161">Если удалить и создать новую камеру, убедитесь, что ваша камера **метка** как **MainCamera**.</span><span class="sxs-lookup"><span data-stu-id="4b878-161">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="4b878-162">См. также</span><span class="sxs-lookup"><span data-stu-id="4b878-162">See also</span></span>
* [<span data-ttu-id="4b878-163">Смешанной реальности Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="4b878-163">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="4b878-164">Общие сведения о разработке Unity</span><span class="sxs-lookup"><span data-stu-id="4b878-164">Unity Development Overview</span></span>](unity-development-overview.md)