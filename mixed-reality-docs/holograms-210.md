---
title: Входные данные MR 210 - взглядом
description: Выполните пошаговое руководство по использованию Unity, Visual Studio и HoloLens Дополнительные сведения о концепции взглядом кодирования.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, руководства, взглядом academy
ms.openlocfilehash: 63c55e8a7a348f2a3e0cc29a9795d7fabcef5df0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599376"
---
>[!NOTE]
><span data-ttu-id="7e559-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="7e559-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7e559-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="7e559-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7e559-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7e559-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7e559-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="7e559-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7e559-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7e559-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7e559-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="7e559-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="7e559-110">Входные данные MR 210: Взгляд</span><span class="sxs-lookup"><span data-stu-id="7e559-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="7e559-111">[Помощи](gaze.md) — это первая форма входных данных, а также обсуждаются цели и осведомленности пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e559-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="7e559-112">210 MR входных данных (также называемые обозревателе проектов) — это подробные сведения о связанных с взглядом основные понятия для смешанной реальности Windows.</span><span class="sxs-lookup"><span data-stu-id="7e559-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="7e559-113">Мы добавим отслеживание контекста курсора и голограммы, преимуществами знает о взглядом пользователя приложения.</span><span class="sxs-lookup"><span data-stu-id="7e559-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="7e559-114">У нас есть понятное космонавты здесь помогут вам сведения о концепциях взглядом.</span><span class="sxs-lookup"><span data-stu-id="7e559-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="7e559-115">В [101 основы MR](holograms-101.md), у нас было, просто за ваши взглядом простом курсоре.</span><span class="sxs-lookup"><span data-stu-id="7e559-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="7e559-116">Сегодня переходим на шаг опережает простой курсор:</span><span class="sxs-lookup"><span data-stu-id="7e559-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="7e559-117">Мы вносим курсор и наши голограммы поддержкой взглядом: как будет меняться в зависимости от где смотрит пользователь - или где пользователь является *не* поиска.</span><span class="sxs-lookup"><span data-stu-id="7e559-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="7e559-118">Это делает их учетом контекста.</span><span class="sxs-lookup"><span data-stu-id="7e559-118">This makes them context-aware.</span></span>
* <span data-ttu-id="7e559-119">Мы будем добавлять отзывы наших курсора и голограммы дать пользователю дополнительный контекст на то, что целевая.</span><span class="sxs-lookup"><span data-stu-id="7e559-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="7e559-120">Эти отзывы можно Аудио- и visual.</span><span class="sxs-lookup"><span data-stu-id="7e559-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="7e559-121">Мы покажем нацеливания методы, чтобы пользователи связываются с меньше целевых объектов.</span><span class="sxs-lookup"><span data-stu-id="7e559-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="7e559-122">Мы покажем, как привлечь внимание пользователя к вашей голограммы с индикатором направления.</span><span class="sxs-lookup"><span data-stu-id="7e559-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="7e559-123">Мы расскажут способы занять вашей голограммы с пользователем, так как она перемещается в ваш мир.</span><span class="sxs-lookup"><span data-stu-id="7e559-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="7e559-124">Видео, внедренных в каждой главы ниже были записаны с использованием более старой версии Unity и смешанной реальности Toolkit.</span><span class="sxs-lookup"><span data-stu-id="7e559-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="7e559-125">Хотя пошаговые инструкции и точной и актуальной, может появиться скрипты и визуальные элементы в соответствующих видео, становятся недействительными.</span><span class="sxs-lookup"><span data-stu-id="7e559-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="7e559-126">Видеоролики остаются включены перемешаны и поскольку рассматриваются основные понятия по-прежнему применяются.</span><span class="sxs-lookup"><span data-stu-id="7e559-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="7e559-127">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="7e559-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7e559-128">Курс</span><span class="sxs-lookup"><span data-stu-id="7e559-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7e559-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7e559-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7e559-130"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="7e559-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="7e559-131">Входные данные MR 210: Взгляд</span><span class="sxs-lookup"><span data-stu-id="7e559-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="7e559-132">✔️</span><span class="sxs-lookup"><span data-stu-id="7e559-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7e559-133">✔️</span><span class="sxs-lookup"><span data-stu-id="7e559-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="7e559-134">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="7e559-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7e559-135">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="7e559-135">Prerequisites</span></span>

* <span data-ttu-id="7e559-136">ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="7e559-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="7e559-137">Основные C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="7e559-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="7e559-138">Необходимо завершить [101 основы MR](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="7e559-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="7e559-139">Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="7e559-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="7e559-140">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="7e559-140">Project files</span></span>

* <span data-ttu-id="7e559-141">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) требуемые для проекта.</span><span class="sxs-lookup"><span data-stu-id="7e559-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="7e559-142"> Требуется компонент Unity 2017.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="7e559-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="7e559-143">Удаление архива файлы рабочего стола или других легко положения.</span><span class="sxs-lookup"><span data-stu-id="7e559-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="7e559-144">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="7e559-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="7e559-145">Список ошибок и примечания</span><span class="sxs-lookup"><span data-stu-id="7e559-145">Errata and Notes</span></span>

* <span data-ttu-id="7e559-146">В Visual Studio «Только мой код» должен быть отключено (флажок не установлен), в разделе Сервис -> Параметры -> "Отладка" для точки останова в коде.</span><span class="sxs-lookup"><span data-stu-id="7e559-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="7e559-147">Глава 1 - Установка Unity</span><span class="sxs-lookup"><span data-stu-id="7e559-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="7e559-148">Цели</span><span class="sxs-lookup"><span data-stu-id="7e559-148">Objectives</span></span>

* <span data-ttu-id="7e559-149">Оптимизация Unity для разработки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e559-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="7e559-150">Импорт ресурсов и настроить сцены.</span><span class="sxs-lookup"><span data-stu-id="7e559-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="7e559-151">Просмотрите космонавты HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e559-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="7e559-152">Инструкция</span><span class="sxs-lookup"><span data-stu-id="7e559-152">Instructions</span></span>

1. <span data-ttu-id="7e559-153">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="7e559-153">Start Unity.</span></span>
2. <span data-ttu-id="7e559-154">Выберите **новый проект**.</span><span class="sxs-lookup"><span data-stu-id="7e559-154">Select **New Project**.</span></span>
3. <span data-ttu-id="7e559-155">Назовите проект **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="7e559-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="7e559-156">Введите расположение как **помощи** папку вы ранее не архивные.</span><span class="sxs-lookup"><span data-stu-id="7e559-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="7e559-157">Убедитесь, что проект присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="7e559-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="7e559-158">Нажмите кнопку **Создание проекта**.</span><span class="sxs-lookup"><span data-stu-id="7e559-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="7e559-159">Параметры Unity для HoloLens</span><span class="sxs-lookup"><span data-stu-id="7e559-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="7e559-160">Нужно сообщить Unity известно, что следует создать приложение, мы пытаемся Экспорт [иммерсивных представление](app-views.md) вместо двухмерном виде.</span><span class="sxs-lookup"><span data-stu-id="7e559-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="7e559-161">Для этого, добавив HoloLens в качестве устройств виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="7e559-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="7e559-162">Перейдите к **изменить > Параметры проекта > проигрывателя**.</span><span class="sxs-lookup"><span data-stu-id="7e559-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="7e559-163">В **панели Инспектора** параметры проигрывателя, выбор **Windows Store** значок.</span><span class="sxs-lookup"><span data-stu-id="7e559-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="7e559-164">Разверните **XR параметры** группы.</span><span class="sxs-lookup"><span data-stu-id="7e559-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="7e559-165">В **визуализации** установите флажок **поддерживается виртуальной реальности** флажок, чтобы добавить новый **виртуальной реальности SDK** списка.</span><span class="sxs-lookup"><span data-stu-id="7e559-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="7e559-166">Убедитесь, что **Windows Mixed Reality** появится в списке.</span><span class="sxs-lookup"><span data-stu-id="7e559-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="7e559-167">Если это не так, выберите **+** кнопку в нижней части списка и выберите **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="7e559-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="7e559-168">Далее нам нужно присвоить сценариев серверную часть .NET.</span><span class="sxs-lookup"><span data-stu-id="7e559-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="7e559-169">Перейдите к **изменить > Параметры проекта > проигрывателя** (по-прежнему возможно, это на предыдущем шаге).</span><span class="sxs-lookup"><span data-stu-id="7e559-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="7e559-170">В **панели Инспектора** параметры проигрывателя, выбор **Windows Store** значок.</span><span class="sxs-lookup"><span data-stu-id="7e559-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="7e559-171">В **другие параметры** конфигурации раздела, убедитесь, что **сценариев серверной части** присваивается **.NET**</span><span class="sxs-lookup"><span data-stu-id="7e559-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="7e559-172">Наконец мы обновим наши настройки качества достижение высокой производительности на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e559-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="7e559-173">Перейдите к **изменить > Параметры проекта > качества**.</span><span class="sxs-lookup"><span data-stu-id="7e559-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="7e559-174">Щелкните стрелку вниз в **по умолчанию** строки под значком Windows Store.</span><span class="sxs-lookup"><span data-stu-id="7e559-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="7e559-175">Выберите **быстрый** для **Windows Store Apps**.</span><span class="sxs-lookup"><span data-stu-id="7e559-175">Select **Fastest** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="7e559-176">Импорт ресурсов проекта</span><span class="sxs-lookup"><span data-stu-id="7e559-176">Import project assets</span></span>

1. <span data-ttu-id="7e559-177">Щелкните правой кнопкой мыши **активы** папку в **проекта** панели.</span><span class="sxs-lookup"><span data-stu-id="7e559-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="7e559-178">Щелкните **Импорт пакета > пользовательского пакета**.</span><span class="sxs-lookup"><span data-stu-id="7e559-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="7e559-179">Перейдите к файлам проекта, который вы скачали и щелкните **ModelExplorer.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="7e559-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="7e559-180">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="7e559-180">Click **Open**.</span></span>
5. <span data-ttu-id="7e559-181">После загрузки пакета, щелкните **импорта** кнопки.</span><span class="sxs-lookup"><span data-stu-id="7e559-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="7e559-182">Программа установки сцены</span><span class="sxs-lookup"><span data-stu-id="7e559-182">Setup the scene</span></span>

1. <span data-ttu-id="7e559-183">В иерархии, удалите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="7e559-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="7e559-184">В **HoloToolkit** откройте **ввода** папку, затем откройте **Prefabs** папки.</span><span class="sxs-lookup"><span data-stu-id="7e559-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="7e559-185">Перетаскивание **MixedRealityCameraParent** prefab из **Prefabs** папку в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="7e559-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="7e559-186">Щелкните правой кнопкой мыши **направленный свет** в иерархии и выберите **удалить**.</span><span class="sxs-lookup"><span data-stu-id="7e559-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="7e559-187">В **голограммы** папки, перетаскивать перечисленные ниже ресурсы в корне **иерархии**:</span><span class="sxs-lookup"><span data-stu-id="7e559-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="7e559-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="7e559-188">**AstroMan**</span></span>
    * <span data-ttu-id="7e559-189">**источники света**</span><span class="sxs-lookup"><span data-stu-id="7e559-189">**Lights**</span></span>
    * <span data-ttu-id="7e559-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="7e559-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="7e559-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="7e559-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="7e559-192">Запуск **режим воспроизведения** ▶ для просмотра-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="7e559-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="7e559-193">Нажмите кнопку **режим воспроизведения** ▶ еще раз, чтобы **остановить**.</span><span class="sxs-lookup"><span data-stu-id="7e559-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="7e559-194">В **голограммы** папки, найти **Fitbox** активов и перетащите его в корневой каталог **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="7e559-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="7e559-195">Выберите **Fitbox** в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="7e559-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="7e559-196">Перетащите **AstroMan** коллекции из **иерархии** для **голограмма коллекции** свойство Fitbox в **инспектор** панели.</span><span class="sxs-lookup"><span data-stu-id="7e559-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="7e559-197">Сохраните проект</span><span class="sxs-lookup"><span data-stu-id="7e559-197">Save the project</span></span>

1. <span data-ttu-id="7e559-198">Сохраните новую сцену: **Файл > Сохранить сцену как**.</span><span class="sxs-lookup"><span data-stu-id="7e559-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="7e559-199">Нажмите кнопку **новую папку** и назовите папку **сцены**.</span><span class="sxs-lookup"><span data-stu-id="7e559-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="7e559-200">Назовите файл «**ModelExplorer**"и сохраните его в **сцены** папки.</span><span class="sxs-lookup"><span data-stu-id="7e559-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="7e559-201">Построение проекта</span><span class="sxs-lookup"><span data-stu-id="7e559-201">Build the project</span></span>

1. <span data-ttu-id="7e559-202">В Unity, выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="7e559-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="7e559-203">Нажмите кнопку **добавьте откройте сцены** Добавление сцены.</span><span class="sxs-lookup"><span data-stu-id="7e559-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="7e559-204">Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="7e559-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="7e559-205">Если вы разрабатываете специально для HoloLens, задайте **целевое устройство** для **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="7e559-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="7e559-206">В противном случае оставьте его на **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="7e559-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="7e559-207">Убедитесь, **построение** присваивается **D3D** и **SDK** имеет значение **самую новую установленную** (которое должно быть SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="7e559-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="7e559-208">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="7e559-208">Click **Build**.</span></span>
7. <span data-ttu-id="7e559-209">Создание **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="7e559-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="7e559-210">Одним щелчком мыши **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="7e559-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="7e559-211">Нажмите клавишу **выберите папку**.</span><span class="sxs-lookup"><span data-stu-id="7e559-211">Press **Select Folder**.</span></span>

<span data-ttu-id="7e559-212">По завершении Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="7e559-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="7e559-213">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="7e559-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="7e559-214">Откройте **решение ModelExplorer в Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7e559-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="7e559-215">Если развертывание HoloLens:</span><span class="sxs-lookup"><span data-stu-id="7e559-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="7e559-216">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x86**.</span><span class="sxs-lookup"><span data-stu-id="7e559-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="7e559-217">Щелкните стрелку раскрывающегося списка рядом с кнопкой на локальном компьютере и выберите **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="7e559-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="7e559-218">Введите **IP-адрес устройства HoloLens** и задайте режим проверки подлинности **универсальный (незашифрованный протокол)**.</span><span class="sxs-lookup"><span data-stu-id="7e559-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="7e559-219">Нажмите кнопку **выберите**.</span><span class="sxs-lookup"><span data-stu-id="7e559-219">Click **Select**.</span></span> <span data-ttu-id="7e559-220">Если вы не знаете IP-адрес устройства, найдите в **параметры > сеть и Интернет > Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="7e559-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="7e559-221">В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="7e559-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="7e559-222">Если это при первом развертывании к устройству, необходимо будет [свяжите его с помощью Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="7e559-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="7e559-223">Когда приложение будет развернуто, закрыть **Fitbox** с **выберите жест**.</span><span class="sxs-lookup"><span data-stu-id="7e559-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="7e559-224">Если развертывание иммерсивных гарнитура:</span><span class="sxs-lookup"><span data-stu-id="7e559-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="7e559-225">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x64**.</span><span class="sxs-lookup"><span data-stu-id="7e559-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="7e559-226">Убедитесь, что целевой объект развертывания присваивается **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="7e559-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="7e559-227">В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="7e559-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="7e559-228">Когда приложение будет развернуто, закрыть **Fitbox** , потянув триггер на контроллере движения.</span><span class="sxs-lookup"><span data-stu-id="7e559-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="7e559-229">Глава 2 - курсора и целевой объект обратной связи</span><span class="sxs-lookup"><span data-stu-id="7e559-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="7e559-230">Цели</span><span class="sxs-lookup"><span data-stu-id="7e559-230">Objectives</span></span>

* <span data-ttu-id="7e559-231">Курсор визуального проектирования и поведение.</span><span class="sxs-lookup"><span data-stu-id="7e559-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="7e559-232">Обратная связь на основе взглядом курсора.</span><span class="sxs-lookup"><span data-stu-id="7e559-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="7e559-233">Голограмма основе взглядом обратной связи.</span><span class="sxs-lookup"><span data-stu-id="7e559-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="7e559-234">Мы будем строить свою работу на некоторые принципы проектирования курсора, а именно:</span><span class="sxs-lookup"><span data-stu-id="7e559-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="7e559-235">Курсор всегда присутствует.</span><span class="sxs-lookup"><span data-stu-id="7e559-235">The cursor is always present.</span></span>
* <span data-ttu-id="7e559-236">Позаботьтесь, чтобы получить слишком мал или большой курсор.</span><span class="sxs-lookup"><span data-stu-id="7e559-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="7e559-237">Избегайте приложения препятствуют работе содержимого.</span><span class="sxs-lookup"><span data-stu-id="7e559-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="7e559-238">Инструкция</span><span class="sxs-lookup"><span data-stu-id="7e559-238">Instructions</span></span>

1. <span data-ttu-id="7e559-239">В **HoloToolkit\Input\Prefabs** папки, найти **InputManager** активов.</span><span class="sxs-lookup"><span data-stu-id="7e559-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="7e559-240">Перетаскивание **InputManager** на **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="7e559-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="7e559-241">В **HoloToolkit\Input\Prefabs** папки, найти **курсор** активов.</span><span class="sxs-lookup"><span data-stu-id="7e559-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="7e559-242">Перетаскивание **курсор** на **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="7e559-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="7e559-243">Выберите **InputManager** объекта в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="7e559-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="7e559-244">Перетащите **курсор** объекта из **иерархии** в InputManager **SimpleSinglePointerSelector** **курсор** поле в конец **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="7e559-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Простота установки единичный выбор указателя](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="7e559-246">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="7e559-246">Build and Deploy</span></span>

1. <span data-ttu-id="7e559-247">Перестройте приложение из **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="7e559-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="7e559-248">Откройте **папки приложения**.</span><span class="sxs-lookup"><span data-stu-id="7e559-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="7e559-249">Откройте **решение ModelExplorer в Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7e559-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="7e559-250">Нажмите кнопку **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="7e559-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="7e559-251">Обратите внимание, как курсор рисуется, и ее внешний вид, если оно касается голограмма.</span><span class="sxs-lookup"><span data-stu-id="7e559-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="7e559-252">Инструкция</span><span class="sxs-lookup"><span data-stu-id="7e559-252">Instructions</span></span>

1. <span data-ttu-id="7e559-253">В **иерархии** панели, разверните узел **AstroMan**->**GEO_G**->**Back_Center** объекта.</span><span class="sxs-lookup"><span data-stu-id="7e559-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="7e559-254">Дважды щелкните **Interactible.cs** чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7e559-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="7e559-255">Раскомментируйте в **IFocusable.OnFocusEnter()** и **IFocusable.OnFocusExit()** обратные вызовы в **Interactible.cs**.</span><span class="sxs-lookup"><span data-stu-id="7e559-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="7e559-256">Они называются по InputManager смешанной реальности набор средств, когда фокус (или взглядом по контроллер указывает) вводит и выходит из определенных GameObject collider.</span><span class="sxs-lookup"><span data-stu-id="7e559-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="7e559-257">Мы используем `EnableKeyword` и `DisableKeyword` выше.</span><span class="sxs-lookup"><span data-stu-id="7e559-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="7e559-258">Чтобы использовать их в собственное приложение с помощью стандартных шейдера из набора средств, вам потребуется выполнить [Unity, касающиеся доступа к материалам с помощью скрипта](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="7e559-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="7e559-259">В этом случае мы уже включили [три варианта выделенный материал](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) в папку «ресурсы» (найдите три материалы с выделением в имени).</span><span class="sxs-lookup"><span data-stu-id="7e559-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="7e559-260">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="7e559-260">Build and Deploy</span></span>

1. <span data-ttu-id="7e559-261">Как и раньше постройте проект и разверните HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e559-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="7e559-262">Обратите внимание, что происходит, когда взглядом предназначен для объекта и если он недопустим.</span><span class="sxs-lookup"><span data-stu-id="7e559-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="7e559-263">Глава 3 - предназначенные для методов</span><span class="sxs-lookup"><span data-stu-id="7e559-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="7e559-264">Цели</span><span class="sxs-lookup"><span data-stu-id="7e559-264">Objectives</span></span>

* <span data-ttu-id="7e559-265">Упростить голограммы целевой объект.</span><span class="sxs-lookup"><span data-stu-id="7e559-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="7e559-266">Стабилизация естественным головной перемещений.</span><span class="sxs-lookup"><span data-stu-id="7e559-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="7e559-267">Инструкция</span><span class="sxs-lookup"><span data-stu-id="7e559-267">Instructions</span></span>

1. <span data-ttu-id="7e559-268">В **иерархии** панели, выберите **InputManager** объекта.</span><span class="sxs-lookup"><span data-stu-id="7e559-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="7e559-269">В **инспектор** панели, найти **помощи стабилизатор** скрипта.</span><span class="sxs-lookup"><span data-stu-id="7e559-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="7e559-270">Если требуется просмотреть, щелкните его, чтобы открыть в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7e559-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="7e559-271">Этот сценарий выполняет итерацию по выборок данных Raycast и позволяет стабилизировать взглядом пользователя для нацеливания на точность.</span><span class="sxs-lookup"><span data-stu-id="7e559-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="7e559-272">В **инспектор**, можно изменить **хранятся образцы стабильность** значение.</span><span class="sxs-lookup"><span data-stu-id="7e559-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="7e559-273">Это значение представляет количество выборок, стабилизатор перемещается на вычисления стабилизации значения.</span><span class="sxs-lookup"><span data-stu-id="7e559-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="7e559-274">Глава 4 – направленных индикаторов</span><span class="sxs-lookup"><span data-stu-id="7e559-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="7e559-275">Цели</span><span class="sxs-lookup"><span data-stu-id="7e559-275">Objectives</span></span>

* <span data-ttu-id="7e559-276">Добавление индикатора направления на курсор для поиска голограммы.</span><span class="sxs-lookup"><span data-stu-id="7e559-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="7e559-277">Инструкция</span><span class="sxs-lookup"><span data-stu-id="7e559-277">Instructions</span></span>

<span data-ttu-id="7e559-278">Мы будем использовать **DirectionIndicator.cs** файла, который:</span><span class="sxs-lookup"><span data-stu-id="7e559-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="7e559-279">Отображение индикатора направления, если пользователь не gazing в голограммы.</span><span class="sxs-lookup"><span data-stu-id="7e559-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="7e559-280">Скрыть индикатора направления, если пользователь gazing в голограммы.</span><span class="sxs-lookup"><span data-stu-id="7e559-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="7e559-281">Обновите индикатора направления, чтобы он указывал голограммы.</span><span class="sxs-lookup"><span data-stu-id="7e559-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="7e559-282">Начнем.</span><span class="sxs-lookup"><span data-stu-id="7e559-282">Let's get started.</span></span>

1. <span data-ttu-id="7e559-283">Щелкните **AstroMan** объекта в **иерархии** панели и **щелкните стрелку** чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="7e559-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="7e559-284">В **иерархии** панели, выберите **DirectionalIndicator** объекта под **AstroMan**.</span><span class="sxs-lookup"><span data-stu-id="7e559-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="7e559-285">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="7e559-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="7e559-286">В меню, введите в поле поиска **индикатором направления**.</span><span class="sxs-lookup"><span data-stu-id="7e559-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="7e559-287">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="7e559-287">Select the search result.</span></span>
5. <span data-ttu-id="7e559-288">В **иерархии** панели перетащите **курсор** объекта на **курсор** свойство в **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="7e559-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="7e559-289">В **проекта** на панели **голограммы** папку путем перетаскивания **DirectionalIndicator** активов на **индикатора направления**свойство в **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="7e559-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="7e559-290">Сборка и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="7e559-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="7e559-291">Посмотрите, как объект индикатора направления помогает найти-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="7e559-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="7e559-292">Глава 5 - биллбординга</span><span class="sxs-lookup"><span data-stu-id="7e559-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="7e559-293">Цели</span><span class="sxs-lookup"><span data-stu-id="7e559-293">Objectives</span></span>

* <span data-ttu-id="7e559-294">Используйте биллбординга для голограммы всегда лицевой стороной к себе.</span><span class="sxs-lookup"><span data-stu-id="7e559-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="7e559-295">Мы будем использовать **Billboard.cs** файла сохранить объект GameObject, ориентированного таким образом, чтобы все время лицевой пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e559-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="7e559-296">В **иерархии** панели, выберите **AstroMan** объекта.</span><span class="sxs-lookup"><span data-stu-id="7e559-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="7e559-297">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="7e559-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="7e559-298">В меню, введите в поле поиска **элемент с объявлением**.</span><span class="sxs-lookup"><span data-stu-id="7e559-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="7e559-299">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="7e559-299">Select the search result.</span></span>
4. <span data-ttu-id="7e559-300">В **инспектор** задать **оси поворота** для **Y**.</span><span class="sxs-lookup"><span data-stu-id="7e559-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="7e559-301">Попробуйте!</span><span class="sxs-lookup"><span data-stu-id="7e559-301">Try it!</span></span> <span data-ttu-id="7e559-302">Создавайте и развертывайте приложения прямо в приложении.</span><span class="sxs-lookup"><span data-stu-id="7e559-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="7e559-303">См. в разделе, как элемент с объявлением объекта лица, которые независимо от того, как изменить точки зрения.</span><span class="sxs-lookup"><span data-stu-id="7e559-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="7e559-304">Удалите скрипт из **AstroMan** сейчас.</span><span class="sxs-lookup"><span data-stu-id="7e559-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="7e559-305">Глава 6 - Tag-Along</span><span class="sxs-lookup"><span data-stu-id="7e559-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="7e559-306">Цели</span><span class="sxs-lookup"><span data-stu-id="7e559-306">Objectives</span></span>

* <span data-ttu-id="7e559-307">Используйте Tag-Along для наших голограммы следите за нашими новостями вокруг комнате.</span><span class="sxs-lookup"><span data-stu-id="7e559-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="7e559-308">Как мы работаем над этой проблемы, мы будем руководствоваться следующие ограничения на проект:</span><span class="sxs-lookup"><span data-stu-id="7e559-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="7e559-309">Содержимое всегда должно быть быстро немедленно.</span><span class="sxs-lookup"><span data-stu-id="7e559-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="7e559-310">Содержимое не должно быть так.</span><span class="sxs-lookup"><span data-stu-id="7e559-310">Content should not be in the way.</span></span>
* <span data-ttu-id="7e559-311">Блокировка HEAD содержимое доставляет неудобства.</span><span class="sxs-lookup"><span data-stu-id="7e559-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="7e559-312">Используемый здесь решение является использование подхода «tag-along».</span><span class="sxs-lookup"><span data-stu-id="7e559-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="7e559-313">Объект tag-along никогда полностью не оставляет представление пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e559-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="7e559-314">Можно представить вложенные tag-along как объект, ластики head пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e559-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="7e559-315">При перемещении, содержимое будет оставаться в пределах просто быстро, перемещая к краю представления, не покидая полностью.</span><span class="sxs-lookup"><span data-stu-id="7e559-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="7e559-316">При пользователь gazes к tag-along объекта, предоставляется более полно в представление.</span><span class="sxs-lookup"><span data-stu-id="7e559-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="7e559-317">Мы будем использовать **SimpleTagalong.cs** файла, который:</span><span class="sxs-lookup"><span data-stu-id="7e559-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="7e559-318">Определения, является ли объект Tag-Along в пределах границ камеры.</span><span class="sxs-lookup"><span data-stu-id="7e559-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="7e559-319">В противном случае внутри усеченная разместить Tag-Along для частично в усеченная.</span><span class="sxs-lookup"><span data-stu-id="7e559-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="7e559-320">В противном случае установите Tag-Along расстоянию по умолчанию от пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e559-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="7e559-321">Чтобы сделать это, мы сначала необходимо изменить **Interactible.cs** скрипта для вызова **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="7e559-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="7e559-322">Изменить **Interactible.cs** , выполнив кодирования Упражнение 6.a (84 к 87 раскомментирование строки).</span><span class="sxs-lookup"><span data-stu-id="7e559-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="7e559-323">**InteractibleAction.cs** скрипт, сопряженные с **Interactible.cs** выполняет пользовательские действия при касании на голограммы.</span><span class="sxs-lookup"><span data-stu-id="7e559-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="7e559-324">В этом случае мы будем использовать его специально для tag-along.</span><span class="sxs-lookup"><span data-stu-id="7e559-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="7e559-325">В **сценарии** щелкните папку **TagalongAction.cs** активов, чтобы открыть в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7e559-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="7e559-326">Упражнения кодирования или изменить его на следующий:</span><span class="sxs-lookup"><span data-stu-id="7e559-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="7e559-327">В верхней части **иерархии**, в строке поиска введите **ChestButton_Center** и выберите результат.</span><span class="sxs-lookup"><span data-stu-id="7e559-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="7e559-328">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="7e559-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="7e559-329">В меню, введите в поле поиска **свои действия**.</span><span class="sxs-lookup"><span data-stu-id="7e559-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="7e559-330">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="7e559-330">Select the search result.</span></span>
  * <span data-ttu-id="7e559-331">В **голограммы** найти папку **свои** активов.</span><span class="sxs-lookup"><span data-stu-id="7e559-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="7e559-332">Выберите **ChestButton_Center** объекта в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="7e559-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="7e559-333">Перетаскивание **свои** объекта из **проекта** на панель **инспектор** в **объекта к свои** свойство.</span><span class="sxs-lookup"><span data-stu-id="7e559-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="7e559-334">Перетащите **свои действия** объекта из **инспектор** в **Interactible действие** на **Interactible** скрипта.</span><span class="sxs-lookup"><span data-stu-id="7e559-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="7e559-335">Дважды щелкните **TagalongAction** скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7e559-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible настройки](images/holograms210-interactible.png)

<span data-ttu-id="7e559-337">Нам нужно добавить следующее:</span><span class="sxs-lookup"><span data-stu-id="7e559-337">We need to add the following:</span></span>

* <span data-ttu-id="7e559-338">Функция PerformAction в скрипте TagalongAction (наследуется от InteractibleAction) расширяют функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="7e559-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="7e559-339">Добавьте биллбординга объекту gazed при и задайте оси поворота для x и y.</span><span class="sxs-lookup"><span data-stu-id="7e559-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="7e559-340">Затем добавьте простой Tag-Along объекта.</span><span class="sxs-lookup"><span data-stu-id="7e559-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="7e559-341">Вот наше решение из **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="7e559-341">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="7e559-342">Попробуйте!</span><span class="sxs-lookup"><span data-stu-id="7e559-342">Try it!</span></span> <span data-ttu-id="7e559-343">Сборка и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="7e559-343">Build and deploy the app.</span></span>
* <span data-ttu-id="7e559-344">Посмотрите, как содержимое соответствует центру точки взглядом, но не непрерывно и не блокируя его.</span><span class="sxs-lookup"><span data-stu-id="7e559-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
