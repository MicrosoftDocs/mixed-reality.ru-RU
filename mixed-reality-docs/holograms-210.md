---
title: Ввод MR 210-взгляд
description: Выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы узнать о концепциях взгляда.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, Academy, учебник, взгляд
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434691"
---
>[!NOTE]
><span data-ttu-id="2717d-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2717d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2717d-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="2717d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2717d-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2717d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2717d-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="2717d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2717d-108">Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="2717d-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="2717d-109">Ввод MR 210: взгляд</span><span class="sxs-lookup"><span data-stu-id="2717d-109">MR Input 210: Gaze</span></span>

<span data-ttu-id="2717d-110">[Взгляните](gaze-and-commit.md) на первую форму входных данных и раскрывает намерение и осведомленность пользователя.</span><span class="sxs-lookup"><span data-stu-id="2717d-110">[Gaze](gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="2717d-111">MR-вход 210 (то есть обозреватель проектов) — это глубокое углубление концепций Windows Mixed Reality, связанных с взглядом.</span><span class="sxs-lookup"><span data-stu-id="2717d-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="2717d-112">Мы будем добавлять в курсор и голограммы сведения о контексте, используя все преимущества вашего приложения о взгляде пользователя.</span><span class="sxs-lookup"><span data-stu-id="2717d-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="2717d-113">У нас есть удобный-космонавтам, который поможет вам изучить концепции взгляда.</span><span class="sxs-lookup"><span data-stu-id="2717d-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="2717d-114">В статьях « [Основные сведения 101](holograms-101.md)» мы имели простой курсор, который только что проделал взгляд.</span><span class="sxs-lookup"><span data-stu-id="2717d-114">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="2717d-115">Сейчас мы перемещая шаг за пределы простого курсора:</span><span class="sxs-lookup"><span data-stu-id="2717d-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="2717d-116">Мы создаем курсор и наши самые голограммы: обе будут изменены в зависимости от того, где пользователь смотрит, или где пользователь *не* смотрит.</span><span class="sxs-lookup"><span data-stu-id="2717d-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="2717d-117">Это делает их контекстно-зависимым.</span><span class="sxs-lookup"><span data-stu-id="2717d-117">This makes them context-aware.</span></span>
* <span data-ttu-id="2717d-118">Мы добавим отзыв к нашим курсору и голограммам, чтобы дать пользователю больше контекста на то, что целевое.</span><span class="sxs-lookup"><span data-stu-id="2717d-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="2717d-119">Отзывы могут быть звуковыми и визуальными элементами.</span><span class="sxs-lookup"><span data-stu-id="2717d-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="2717d-120">Мы покажем, что вы научитесь использовать методы, чтобы помочь пользователям достичь меньшего объема целевых объектов.</span><span class="sxs-lookup"><span data-stu-id="2717d-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="2717d-121">Мы покажем, как привлечь внимание пользователя к голограммам с помощью индикатора направления.</span><span class="sxs-lookup"><span data-stu-id="2717d-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="2717d-122">Мы обсудим методы, с помощью которых пользователь перемещает свои голограммы по всему миру.</span><span class="sxs-lookup"><span data-stu-id="2717d-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="2717d-123">Видеоматериалы, внедренные в каждую из приведенных ниже глав, были записаны с использованием более старой версии Unity и набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2717d-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="2717d-124">Хотя пошаговые инструкции являются точными и актуальными, в соответствующих видеоматериалах могут отображаться сценарии и визуальные элементы, которые являются неактуальными.</span><span class="sxs-lookup"><span data-stu-id="2717d-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="2717d-125">Видеоматериалы по-прежнему включены в постерити, так как эти концепции все еще применимы.</span><span class="sxs-lookup"><span data-stu-id="2717d-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="2717d-126">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="2717d-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2717d-127">Хождение</span><span class="sxs-lookup"><span data-stu-id="2717d-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2717d-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2717d-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2717d-129"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="2717d-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="2717d-130">Ввод MR 210: взгляд</span><span class="sxs-lookup"><span data-stu-id="2717d-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="2717d-131">✔️</span><span class="sxs-lookup"><span data-stu-id="2717d-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2717d-132">✔️</span><span class="sxs-lookup"><span data-stu-id="2717d-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="2717d-133">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="2717d-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2717d-134">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="2717d-134">Prerequisites</span></span>

* <span data-ttu-id="2717d-135">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="2717d-135">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="2717d-136">Некоторые базовые C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="2717d-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="2717d-137">Вы должны были выполнить [Основные сведения о MR 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="2717d-137">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="2717d-138">Устройство HoloLens, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="2717d-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="2717d-139">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="2717d-139">Project files</span></span>

* <span data-ttu-id="2717d-140">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="2717d-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="2717d-141"> Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="2717d-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="2717d-142">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="2717d-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="2717d-143">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="2717d-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="2717d-144">Ошибки и примечания</span><span class="sxs-lookup"><span data-stu-id="2717d-144">Errata and Notes</span></span>

* <span data-ttu-id="2717d-145">В Visual Studio параметр "Только мой код" должен быть отключен (снят) в разделе Сервис-> Параметры — > Отладка для попадания в код точек останова в коде.</span><span class="sxs-lookup"><span data-stu-id="2717d-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="2717d-146">Глава 1. Установка Unity</span><span class="sxs-lookup"><span data-stu-id="2717d-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="2717d-147">Задачи</span><span class="sxs-lookup"><span data-stu-id="2717d-147">Objectives</span></span>

* <span data-ttu-id="2717d-148">Оптимизация Unity для разработки решений для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2717d-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="2717d-149">Импорт ресурсов и настройка сцены.</span><span class="sxs-lookup"><span data-stu-id="2717d-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="2717d-150">Просмотрите-космонавтам в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2717d-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="2717d-151">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2717d-151">Instructions</span></span>

1. <span data-ttu-id="2717d-152">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="2717d-152">Start Unity.</span></span>
2. <span data-ttu-id="2717d-153">Выберите **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="2717d-153">Select **New Project**.</span></span>
3. <span data-ttu-id="2717d-154">Назовите проект **моделексплорер**.</span><span class="sxs-lookup"><span data-stu-id="2717d-154">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="2717d-155">Введите расположение, в котором была отменена Архивация папки " **Взгляните** ".</span><span class="sxs-lookup"><span data-stu-id="2717d-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="2717d-156">Задайте для проекта значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="2717d-156">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="2717d-157">Щелкните **Create Project** (Создать проект).</span><span class="sxs-lookup"><span data-stu-id="2717d-157">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="2717d-158">Параметры Unity для HoloLens</span><span class="sxs-lookup"><span data-stu-id="2717d-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="2717d-159">Необходимо разрешить Unity знать, что приложение, которое мы пытаемся экспортировать, должно создать [иммерсивное представление](app-views.md) вместо 2D-представления.</span><span class="sxs-lookup"><span data-stu-id="2717d-159">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="2717d-160">Это можно сделать, добавив HoloLens в качестве устройства виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="2717d-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="2717d-161">Выберите **изменить > параметры проекта > Player**.</span><span class="sxs-lookup"><span data-stu-id="2717d-161">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="2717d-162">На **панели инспектора** для параметров проигрывателя выберите значок **Магазин Windows** .</span><span class="sxs-lookup"><span data-stu-id="2717d-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="2717d-163">Разверните группу **Параметры XR** .</span><span class="sxs-lookup"><span data-stu-id="2717d-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="2717d-164">В разделе " **Подготовка** " установите флажок " **Virtual Reality Supported** ", чтобы добавить новый список **пакетов SDK виртуальной реальности** .</span><span class="sxs-lookup"><span data-stu-id="2717d-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="2717d-165">Убедитесь, что в списке присутствует **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="2717d-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="2717d-166">В противном случае нажмите кнопку **+** в нижней части списка и выберите **Windows holographic**.</span><span class="sxs-lookup"><span data-stu-id="2717d-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="2717d-167">Далее необходимо задать для нашей серверной части скрипта .NET.</span><span class="sxs-lookup"><span data-stu-id="2717d-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="2717d-168">Перейдите в раздел **изменить > параметры проекта > проигрывателе** (возможно, это можно будет выполнить на предыдущем шаге).</span><span class="sxs-lookup"><span data-stu-id="2717d-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="2717d-169">На **панели инспектора** для параметров проигрывателя выберите значок **Магазин Windows** .</span><span class="sxs-lookup"><span data-stu-id="2717d-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="2717d-170">В разделе Настройка **других параметров** убедитесь, что для **серверной части скрипта** задано значение **.NET** .</span><span class="sxs-lookup"><span data-stu-id="2717d-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="2717d-171">Наконец, мы будем обновлять наши параметры качества, чтобы добиться высокой производительности HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2717d-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="2717d-172">Выберите **изменить > параметры проекта > качество**.</span><span class="sxs-lookup"><span data-stu-id="2717d-172">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="2717d-173">Щелкните стрелку вниз в строке **по умолчанию** под значком магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="2717d-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="2717d-174">Выберите **очень низкое** для **приложений Магазина Windows**.</span><span class="sxs-lookup"><span data-stu-id="2717d-174">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="2717d-175">Импорт ресурсов проекта</span><span class="sxs-lookup"><span data-stu-id="2717d-175">Import project assets</span></span>

1. <span data-ttu-id="2717d-176">Щелкните правой кнопкой мыши папку **активы** на панели **проект** .</span><span class="sxs-lookup"><span data-stu-id="2717d-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="2717d-177">Щелкните **Импорт пакета > настраиваемый пакет**.</span><span class="sxs-lookup"><span data-stu-id="2717d-177">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="2717d-178">Перейдите к скачанным файлам проекта и щелкните **моделексплорер. пакет unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="2717d-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="2717d-179">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="2717d-179">Click **Open**.</span></span>
5. <span data-ttu-id="2717d-180">После загрузки пакета нажмите кнопку " **Импорт** ".</span><span class="sxs-lookup"><span data-stu-id="2717d-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="2717d-181">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="2717d-181">Setup the scene</span></span>

1. <span data-ttu-id="2717d-182">В иерархии удалите **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="2717d-182">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="2717d-183">В папке **холотулкит** откройте **входную** папку, а затем откройте папку **Prefabs** .</span><span class="sxs-lookup"><span data-stu-id="2717d-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="2717d-184">Перетащите **микседреалитикамерапарент** prefab из папки **Prefabs** в **иерархию**.</span><span class="sxs-lookup"><span data-stu-id="2717d-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="2717d-185">Щелкните правой кнопкой мыши **направленный источник** в иерархии и выберите **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="2717d-185">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="2717d-186">В папке **голограмм** перетащите следующие ресурсы в корень **иерархии**:</span><span class="sxs-lookup"><span data-stu-id="2717d-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="2717d-187">**астроман**</span><span class="sxs-lookup"><span data-stu-id="2717d-187">**AstroMan**</span></span>
    * <span data-ttu-id="2717d-188">**Свет**</span><span class="sxs-lookup"><span data-stu-id="2717d-188">**Lights**</span></span>
    * <span data-ttu-id="2717d-189">**спацеаудиосаурце**</span><span class="sxs-lookup"><span data-stu-id="2717d-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="2717d-190">**спацебаккграунд**</span><span class="sxs-lookup"><span data-stu-id="2717d-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="2717d-191">Запустите **режим воспроизведения** ▶, чтобы просмотреть-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="2717d-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="2717d-192">Щелкните **режим воспроизведения** ▶ еще раз, чтобы **приостанавливаться**.</span><span class="sxs-lookup"><span data-stu-id="2717d-192">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="2717d-193">В папке **голограмм** найдите ресурс **фитбокс** и перетащите его в корень **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="2717d-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="2717d-194">Выберите **фитбокс** на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="2717d-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="2717d-195">Перетащите коллекцию **астроман** из **иерархии** в свойство **коллекции голограммы** фитбокс на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="2717d-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="2717d-196">Сохранение проекта</span><span class="sxs-lookup"><span data-stu-id="2717d-196">Save the project</span></span>

1. <span data-ttu-id="2717d-197">Сохраните новую сцену: **файл > сохранить сцену как**.</span><span class="sxs-lookup"><span data-stu-id="2717d-197">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="2717d-198">Щелкните **создать папку** и присвойте имя папке **сцены**.</span><span class="sxs-lookup"><span data-stu-id="2717d-198">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="2717d-199">Назовите файл «**моделексплорер**» и сохраните его в папке « **сцены** ».</span><span class="sxs-lookup"><span data-stu-id="2717d-199">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="2717d-200">Построение проекта</span><span class="sxs-lookup"><span data-stu-id="2717d-200">Build the project</span></span>

1. <span data-ttu-id="2717d-201">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="2717d-201">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="2717d-202">Щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="2717d-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="2717d-203">Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.</span><span class="sxs-lookup"><span data-stu-id="2717d-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="2717d-204">Если вы специально разрабатываете для HoloLens, задайте для параметра **целевое устройство** значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="2717d-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="2717d-205">В противном случае оставьте его на **любом устройстве**.</span><span class="sxs-lookup"><span data-stu-id="2717d-205">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="2717d-206">Убедитесь, что для **типа сборки** задано значение **D3D** и **пакет SDK** установлен в значение " **Последняя установленная версия** " (это должен быть пакет SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="2717d-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="2717d-207">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="2717d-207">Click **Build**.</span></span>
7. <span data-ttu-id="2717d-208">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="2717d-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="2717d-209">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="2717d-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="2717d-210">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="2717d-210">Press **Select Folder**.</span></span>

<span data-ttu-id="2717d-211">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="2717d-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="2717d-212">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="2717d-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="2717d-213">Откройте **решение Моделексплорер Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2717d-213">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="2717d-214">При развертывании в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="2717d-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="2717d-215">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="2717d-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="2717d-216">Щелкните стрелку раскрывающегося списка рядом с кнопкой локальный компьютер и выберите **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="2717d-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="2717d-217">Введите **IP-адрес устройства HoloLens** и задайте для режима проверки подлинности значение **универсальный (незашифрованный протокол)** .</span><span class="sxs-lookup"><span data-stu-id="2717d-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="2717d-218">Нажмите кнопку **выбрать**.</span><span class="sxs-lookup"><span data-stu-id="2717d-218">Click **Select**.</span></span> <span data-ttu-id="2717d-219">Если вы не узнаете IP-адрес устройства, проверьте **параметры > сеть & интернет > дополнительные параметры**.</span><span class="sxs-lookup"><span data-stu-id="2717d-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="2717d-220">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="2717d-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="2717d-221">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="2717d-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="2717d-222">После развертывания приложения закройте **фитбокс** с помощью **жеста выбора**.</span><span class="sxs-lookup"><span data-stu-id="2717d-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="2717d-223">При развертывании на иммерсивное головной телефон:</span><span class="sxs-lookup"><span data-stu-id="2717d-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="2717d-224">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.</span><span class="sxs-lookup"><span data-stu-id="2717d-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="2717d-225">Убедитесь, что для целевого объекта развертывания задано значение **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="2717d-225">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="2717d-226">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="2717d-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="2717d-227">После развертывания приложения закройте **фитбокс** , изменив триггер на контроллере движения.</span><span class="sxs-lookup"><span data-stu-id="2717d-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="2717d-228">Глава 2 — Обратная связь курсора и целевого объекта</span><span class="sxs-lookup"><span data-stu-id="2717d-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="2717d-229">Задачи</span><span class="sxs-lookup"><span data-stu-id="2717d-229">Objectives</span></span>

* <span data-ttu-id="2717d-230">Визуальное проектирование и поведение курсора.</span><span class="sxs-lookup"><span data-stu-id="2717d-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="2717d-231">Обратная связь курсора на основе взгляда.</span><span class="sxs-lookup"><span data-stu-id="2717d-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="2717d-232">Отзывы о голограммах на основе взгляда.</span><span class="sxs-lookup"><span data-stu-id="2717d-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="2717d-233">Мы собираемся основывать наши усилия на некоторых принципах проектирования курсоров, а именно:</span><span class="sxs-lookup"><span data-stu-id="2717d-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="2717d-234">Курсор всегда находится в наличии.</span><span class="sxs-lookup"><span data-stu-id="2717d-234">The cursor is always present.</span></span>
* <span data-ttu-id="2717d-235">Не дайте курсору быть слишком маленьким или большим.</span><span class="sxs-lookup"><span data-stu-id="2717d-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="2717d-236">Избегайте неблизкого содержимого.</span><span class="sxs-lookup"><span data-stu-id="2717d-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="2717d-237">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2717d-237">Instructions</span></span>

1. <span data-ttu-id="2717d-238">В папке **холотулкит\инпут\префабс** найдите ресурс **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="2717d-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="2717d-239">Перетащите **InputManager** в **иерархию**.</span><span class="sxs-lookup"><span data-stu-id="2717d-239">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="2717d-240">В папке **холотулкит\инпут\префабс** найдите ресурс **cursor** .</span><span class="sxs-lookup"><span data-stu-id="2717d-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="2717d-241">Перетащите **курсор** на **иерархию**.</span><span class="sxs-lookup"><span data-stu-id="2717d-241">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="2717d-242">Выберите объект **InputManager** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="2717d-242">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="2717d-243">Перетащите объект **cursor** из **иерархии** в поле **курсора** InputManager **симплесинглепоинтерселектор**в нижней части **инспектора**.</span><span class="sxs-lookup"><span data-stu-id="2717d-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Настройка простого единичного селектора указателя](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="2717d-245">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="2717d-245">Build and Deploy</span></span>

1. <span data-ttu-id="2717d-246">Перестройте приложение из **файла > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="2717d-246">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="2717d-247">Откройте **папку приложения**.</span><span class="sxs-lookup"><span data-stu-id="2717d-247">Open the **App folder**.</span></span>
3. <span data-ttu-id="2717d-248">Откройте **решение Моделексплорер Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2717d-248">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="2717d-249">Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="2717d-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="2717d-250">Обратите внимание на прорисовку курсора и на то, как он изменяет внешний вид, если он касается голограммы.</span><span class="sxs-lookup"><span data-stu-id="2717d-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="2717d-251">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2717d-251">Instructions</span></span>

1. <span data-ttu-id="2717d-252">На панели **Иерархия** разверните объект **астроман**->**GEO_G**->**Back_Center** .</span><span class="sxs-lookup"><span data-stu-id="2717d-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="2717d-253">Дважды щелкните **Interactible.CS** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2717d-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="2717d-254">Раскомментируйте строки в обратных вызовах **ифокусабле. онфокусентер ()** и **ифокусабле. онфокусексит ()** в **Interactible.CS**.</span><span class="sxs-lookup"><span data-stu-id="2717d-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="2717d-255">Они вызываются InputManager набора средств Mixed Reality, когда фокус (либо с помощью указателя мыши, либо с помощью контроллера) вводит и выходит из GameObjectа.</span><span class="sxs-lookup"><span data-stu-id="2717d-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="2717d-256">Мы используем `EnableKeyword` и `DisableKeyword` выше.</span><span class="sxs-lookup"><span data-stu-id="2717d-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="2717d-257">Чтобы использовать их в своем приложении с помощью стандартного шейдера набора средств, необходимо следовать [правилам Unity для доступа к материалам с помощью сценария](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="2717d-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="2717d-258">В этом случае мы уже включили [три варианта выделенного материала](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) , который требуется в папке ресурсов (Найдите три материала с выделенным именем).</span><span class="sxs-lookup"><span data-stu-id="2717d-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="2717d-259">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="2717d-259">Build and Deploy</span></span>

1. <span data-ttu-id="2717d-260">Как и ранее, выполните сборку проекта и разверните его в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2717d-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="2717d-261">Обратите внимание на то, что происходит, когда наблюдатель предназначен для объекта, а когда нет.</span><span class="sxs-lookup"><span data-stu-id="2717d-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="2717d-262">Глава 3-методы нацеливания</span><span class="sxs-lookup"><span data-stu-id="2717d-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="2717d-263">Задачи</span><span class="sxs-lookup"><span data-stu-id="2717d-263">Objectives</span></span>

* <span data-ttu-id="2717d-264">Упростить целевую голограмму.</span><span class="sxs-lookup"><span data-stu-id="2717d-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="2717d-265">Стабилизация естественных перемещений головок.</span><span class="sxs-lookup"><span data-stu-id="2717d-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="2717d-266">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2717d-266">Instructions</span></span>

1. <span data-ttu-id="2717d-267">На панели **Иерархия** выберите объект **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="2717d-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="2717d-268">На панели **инспектора** найдите скрипт **стабилизер** .</span><span class="sxs-lookup"><span data-stu-id="2717d-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="2717d-269">Щелкните его, чтобы открыть в Visual Studio, если вы хотите просмотреть его.</span><span class="sxs-lookup"><span data-stu-id="2717d-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="2717d-270">Этот сценарий выполняет перебор образцов данных Райкаст и помогает стабилизировать пользовательское определение точности для целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="2717d-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="2717d-271">В **инспекторе**можно изменить значение **сохраненных выборок стабильности** .</span><span class="sxs-lookup"><span data-stu-id="2717d-271">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="2717d-272">Это значение представляет число выборок, по которым стабилизер выполняет итерацию, чтобы вычислить значение "стабилизация".</span><span class="sxs-lookup"><span data-stu-id="2717d-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="2717d-273">Глава 4-направленный индикатор</span><span class="sxs-lookup"><span data-stu-id="2717d-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="2717d-274">Задачи</span><span class="sxs-lookup"><span data-stu-id="2717d-274">Objectives</span></span>

* <span data-ttu-id="2717d-275">Добавьте к курсору индикатор направления, чтобы помочь найти голограммы.</span><span class="sxs-lookup"><span data-stu-id="2717d-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="2717d-276">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2717d-276">Instructions</span></span>

<span data-ttu-id="2717d-277">Мы будем использовать файл **DirectionIndicator.CS** , который будет выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="2717d-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="2717d-278">Показывать индикатор направления, если пользователь не облаками на голограммах.</span><span class="sxs-lookup"><span data-stu-id="2717d-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="2717d-279">Скрыть индикатор направления, если пользователь облаками на голограммах.</span><span class="sxs-lookup"><span data-stu-id="2717d-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="2717d-280">Обновите индикатор направления, чтобы он указывал на голограммы.</span><span class="sxs-lookup"><span data-stu-id="2717d-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="2717d-281">Начнем.</span><span class="sxs-lookup"><span data-stu-id="2717d-281">Let's get started.</span></span>

1. <span data-ttu-id="2717d-282">Щелкните объект **астроман** на панели **Иерархия** и **щелкните стрелку** , чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="2717d-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="2717d-283">На панели **Иерархия** выберите объект **Директионалиндикатор** в разделе **астроман**.</span><span class="sxs-lookup"><span data-stu-id="2717d-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="2717d-284">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="2717d-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="2717d-285">В меню введите **индикатор направления**поля поиска.</span><span class="sxs-lookup"><span data-stu-id="2717d-285">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="2717d-286">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="2717d-286">Select the search result.</span></span>
5. <span data-ttu-id="2717d-287">На панели **Иерархия** перетащите объект **курсора** на свойство **cursor** в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="2717d-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="2717d-288">На панели **«проект** » в папке « **голограммы** » перетащите ресурс **Директионалиндикатор** в свойство « **указатель направления** » в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="2717d-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="2717d-289">Выполните сборку и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="2717d-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="2717d-290">Посмотрите, как объект «указатель направления» помогает найти-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="2717d-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="2717d-291">Глава 5 — Реклама</span><span class="sxs-lookup"><span data-stu-id="2717d-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="2717d-292">Задачи</span><span class="sxs-lookup"><span data-stu-id="2717d-292">Objectives</span></span>

* <span data-ttu-id="2717d-293">Используйте рекламу, чтобы всегда иметь на себя голограммы.</span><span class="sxs-lookup"><span data-stu-id="2717d-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="2717d-294">Мы будем использовать файл **Billboard.CS** , чтобы поддерживать GameObject, чтобы он всегда был ориентирован на пользователя.</span><span class="sxs-lookup"><span data-stu-id="2717d-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="2717d-295">На панели **Иерархия** выберите объект **астроман** .</span><span class="sxs-lookup"><span data-stu-id="2717d-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="2717d-296">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="2717d-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="2717d-297">В меню введите в поле поиска **объявление**.</span><span class="sxs-lookup"><span data-stu-id="2717d-297">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="2717d-298">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="2717d-298">Select the search result.</span></span>
4. <span data-ttu-id="2717d-299">В **инспекторе** установите для **оси сводной таблицы** значение **Y**.</span><span class="sxs-lookup"><span data-stu-id="2717d-299">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="2717d-300">Попробуйте!</span><span class="sxs-lookup"><span data-stu-id="2717d-300">Try it!</span></span> <span data-ttu-id="2717d-301">Выполните сборку и развертывание приложения, как и прежде.</span><span class="sxs-lookup"><span data-stu-id="2717d-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="2717d-302">Ознакомьтесь с тем, как объект объявления не зависит от того, как вы изменяете точку зрения.</span><span class="sxs-lookup"><span data-stu-id="2717d-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="2717d-303">Удалите скрипт из **астроман** .</span><span class="sxs-lookup"><span data-stu-id="2717d-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="2717d-304">Глава 6-Tag-и</span><span class="sxs-lookup"><span data-stu-id="2717d-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="2717d-305">Задачи</span><span class="sxs-lookup"><span data-stu-id="2717d-305">Objectives</span></span>

* <span data-ttu-id="2717d-306">Используйте тег, чтобы получить наши голограммы, которые следуют нам вокруг комнаты.</span><span class="sxs-lookup"><span data-stu-id="2717d-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="2717d-307">По мере того как мы работаем над этой проблемой, мы будем использовать следующие ограничения проектирования:</span><span class="sxs-lookup"><span data-stu-id="2717d-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="2717d-308">Содержимое всегда должно быть кратким.</span><span class="sxs-lookup"><span data-stu-id="2717d-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="2717d-309">Содержимое не должно быть таким образом.</span><span class="sxs-lookup"><span data-stu-id="2717d-309">Content should not be in the way.</span></span>
* <span data-ttu-id="2717d-310">Содержимое с блокировкой в головном офисе неудобно.</span><span class="sxs-lookup"><span data-stu-id="2717d-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="2717d-311">Решение, используемое здесь, заключается в использовании подхода "Tag-by".</span><span class="sxs-lookup"><span data-stu-id="2717d-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="2717d-312">Объект с тегами не полностью оставляет представление пользователя.</span><span class="sxs-lookup"><span data-stu-id="2717d-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="2717d-313">Можно представить себе тег, а как объект, прикрепленный к заголовку пользователя с помощью резиновых полос.</span><span class="sxs-lookup"><span data-stu-id="2717d-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="2717d-314">По мере того, как пользователь перемещается, содержимое будет оставаться в удобном для вас направлении, не выходя за границы представления.</span><span class="sxs-lookup"><span data-stu-id="2717d-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="2717d-315">Когда пользователь рассматривает объект на основе тега, он становится более полным.</span><span class="sxs-lookup"><span data-stu-id="2717d-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="2717d-316">Мы будем использовать файл **SimpleTagalong.CS** , который будет выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="2717d-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="2717d-317">Определите, находится ли объект с тегом в пределах границ камеры.</span><span class="sxs-lookup"><span data-stu-id="2717d-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="2717d-318">Если это не в представлении фрустум, разместите тег, а частично в представлении фрустум.</span><span class="sxs-lookup"><span data-stu-id="2717d-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="2717d-319">В противном случае разместите тег, а также расстояние по умолчанию от пользователя.</span><span class="sxs-lookup"><span data-stu-id="2717d-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="2717d-320">Для этого сначала необходимо изменить сценарий **Interactible.CS** для вызова **тагалонгактион**.</span><span class="sxs-lookup"><span data-stu-id="2717d-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="2717d-321">Измените **Interactible.CS** , выполнив кодирование упражнения 6. a (Раскомментируйте строки с 84 по 87).</span><span class="sxs-lookup"><span data-stu-id="2717d-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="2717d-322">Сценарий **InteractibleAction.CS** , состоящий из **Interactible.CS** , выполняет пользовательские действия при касании голограмм.</span><span class="sxs-lookup"><span data-stu-id="2717d-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="2717d-323">В этом случае мы будем использовать один из них специально для тега.</span><span class="sxs-lookup"><span data-stu-id="2717d-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="2717d-324">В папке **Scripts** щелкните ресурс **TagalongAction.CS** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2717d-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="2717d-325">Завершите упражнение по написанию кода или измените его на следующее:</span><span class="sxs-lookup"><span data-stu-id="2717d-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="2717d-326">В верхней части **иерархии**в строке поиска введите **ChestButton_Center** и выберите результат.</span><span class="sxs-lookup"><span data-stu-id="2717d-326">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="2717d-327">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="2717d-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="2717d-328">В меню введите в поле поиска **Тагалонг действие**.</span><span class="sxs-lookup"><span data-stu-id="2717d-328">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="2717d-329">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="2717d-329">Select the search result.</span></span>
  * <span data-ttu-id="2717d-330">В папке **голограмм** найдите ресурс **тагалонг** .</span><span class="sxs-lookup"><span data-stu-id="2717d-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="2717d-331">Выберите объект **ChestButton_Center** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="2717d-331">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="2717d-332">Перетащите объект **тагалонг** с панели **проект** на **инспектор** в **объект в свойство тагалонг** .</span><span class="sxs-lookup"><span data-stu-id="2717d-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="2717d-333">Перетащите объект **действия тагалонг** из **инспектора** в поле **действия интерактибле** в скрипте **интерактибле** .</span><span class="sxs-lookup"><span data-stu-id="2717d-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="2717d-334">Дважды щелкните скрипт **тагалонгактион** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2717d-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Настройка интерактибле](images/holograms210-interactible.png)

<span data-ttu-id="2717d-336">Необходимо добавить следующее:</span><span class="sxs-lookup"><span data-stu-id="2717d-336">We need to add the following:</span></span>

* <span data-ttu-id="2717d-337">Добавьте функциональные возможности в функцию Перформактион в скрипте Тагалонгактион (наследуется от Интерактиблеактион).</span><span class="sxs-lookup"><span data-stu-id="2717d-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="2717d-338">Добавьте объявление в объект газед-on и установите для оси сводной диаграммы значение XY.</span><span class="sxs-lookup"><span data-stu-id="2717d-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="2717d-339">Затем добавьте в объект простой тег.</span><span class="sxs-lookup"><span data-stu-id="2717d-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="2717d-340">Вот наше решение, от **TagalongAction.CS**:</span><span class="sxs-lookup"><span data-stu-id="2717d-340">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="2717d-341">Попробуйте!</span><span class="sxs-lookup"><span data-stu-id="2717d-341">Try it!</span></span> <span data-ttu-id="2717d-342">Выполните сборку и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="2717d-342">Build and deploy the app.</span></span>
* <span data-ttu-id="2717d-343">Посмотрите, как содержимое соответствует центру точки взгляда, но не постоянно и не блокирует его.</span><span class="sxs-lookup"><span data-stu-id="2717d-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
