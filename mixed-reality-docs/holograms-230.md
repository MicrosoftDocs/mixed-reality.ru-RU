---
title: Пространственный 230 — пространственное сопоставление
description: Выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы получить сведения о концепциях пространственного сопоставления.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, Academy, руководство, пространственное сопоставление, реконструкция поверхностей, сеть
ms.openlocfilehash: cf4a2dd3e5eb74c0aaf849442e5f5e404d7cb661
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434578"
---
>[!NOTE]
><span data-ttu-id="9215a-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9215a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9215a-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="9215a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9215a-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9215a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9215a-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="9215a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9215a-108">Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="9215a-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="9215a-109">Индекс MR 230: пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="9215a-109">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="9215a-110">[Пространственное сопоставление](spatial-mapping.md) объединяет реальный и виртуальный мир вместе с голограммами о среде.</span><span class="sxs-lookup"><span data-stu-id="9215a-110">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="9215a-111">В MR-пространственном 230 (Project планетариум) мы расскажем:</span><span class="sxs-lookup"><span data-stu-id="9215a-111">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="9215a-112">Проверьте окружение и передайте данные с HoloLens на компьютер разработки.</span><span class="sxs-lookup"><span data-stu-id="9215a-112">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="9215a-113">Изучите шейдеры и Узнайте, как их использовать для визуализации своего пространства.</span><span class="sxs-lookup"><span data-stu-id="9215a-113">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="9215a-114">Разбейте сетку помещений на простые плоскости с помощью обработки сетки.</span><span class="sxs-lookup"><span data-stu-id="9215a-114">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="9215a-115">Выйдите за пределы приемов размещения, которые мы узнали в статье об [основных 101](holograms-101.md), и предоставьте отзыв о том, где можно поместить голограмму в среду.</span><span class="sxs-lookup"><span data-stu-id="9215a-115">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="9215a-116">Изучите эффекты перекрытия, так что когда ваша голограмма находится за реальным объектом, вы по-прежнему можете увидеть ее с помощью концепции x-ray!</span><span class="sxs-lookup"><span data-stu-id="9215a-116">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="9215a-117">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="9215a-117">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9215a-118">Хождение</span><span class="sxs-lookup"><span data-stu-id="9215a-118">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9215a-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9215a-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9215a-120"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="9215a-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9215a-121">Индекс MR 230: пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="9215a-121">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="9215a-122">✔️</span><span class="sxs-lookup"><span data-stu-id="9215a-122">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9215a-123">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="9215a-123">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9215a-124">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="9215a-124">Prerequisites</span></span>

* <span data-ttu-id="9215a-125">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="9215a-125">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="9215a-126">Некоторые базовые C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="9215a-126">Some basic C# programming ability.</span></span>
* <span data-ttu-id="9215a-127">Вы должны были выполнить [Основные сведения о MR 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="9215a-127">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="9215a-128">Устройство HoloLens, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="9215a-128">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="9215a-129">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="9215a-129">Project files</span></span>

* <span data-ttu-id="9215a-130">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="9215a-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="9215a-131"> Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="9215a-131"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="9215a-132">Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="9215a-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="9215a-133">Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="9215a-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="9215a-134">Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="9215a-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="9215a-135">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="9215a-135">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="9215a-136">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="9215a-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="9215a-137">Заметки</span><span class="sxs-lookup"><span data-stu-id="9215a-137">Notes</span></span>

* <span data-ttu-id="9215a-138">Параметр "включить Только мой код" в Visual Studio должен быть отключен (*снят*) в разделе Сервис > Параметры > Отладка для попадания в точки останова в коде.</span><span class="sxs-lookup"><span data-stu-id="9215a-138">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="9215a-139">Установка Unity</span><span class="sxs-lookup"><span data-stu-id="9215a-139">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="9215a-140">Запустите **Unity**.</span><span class="sxs-lookup"><span data-stu-id="9215a-140">Start **Unity**.</span></span>
* <span data-ttu-id="9215a-141">Выберите **создать, чтобы** создать новый проект.</span><span class="sxs-lookup"><span data-stu-id="9215a-141">Select **New** to create a new project.</span></span>
* <span data-ttu-id="9215a-142">Назовите проект **планетариум**.</span><span class="sxs-lookup"><span data-stu-id="9215a-142">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="9215a-143">Убедитесь, что выбран параметр **3D** .</span><span class="sxs-lookup"><span data-stu-id="9215a-143">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="9215a-144">Щелкните **Create Project** (Создать проект).</span><span class="sxs-lookup"><span data-stu-id="9215a-144">Click **Create Project**.</span></span>
* <span data-ttu-id="9215a-145">После запуска Unity перейдите в раздел **правка > параметры проекта > Player**.</span><span class="sxs-lookup"><span data-stu-id="9215a-145">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="9215a-146">На панели **инспектора** найдите и выберите зеленый значок **магазина Windows** .</span><span class="sxs-lookup"><span data-stu-id="9215a-146">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="9215a-147">Разверните **другие параметры**.</span><span class="sxs-lookup"><span data-stu-id="9215a-147">Expand **Other Settings**.</span></span>
* <span data-ttu-id="9215a-148">В разделе " **Подготовка к просмотру** " установите флажок **поддерживаемый виртуальный реальность** .</span><span class="sxs-lookup"><span data-stu-id="9215a-148">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="9215a-149">Убедитесь, что **Windows holographic** отображается в списке **пакетов SDK виртуальной реальности**.</span><span class="sxs-lookup"><span data-stu-id="9215a-149">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="9215a-150">В противном случае нажмите кнопку **+** в нижней части списка и выберите **Windows holographic**.</span><span class="sxs-lookup"><span data-stu-id="9215a-150">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="9215a-151">Разверните узел **Параметры публикации**.</span><span class="sxs-lookup"><span data-stu-id="9215a-151">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="9215a-152">В разделе **возможности** проверьте следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="9215a-152">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="9215a-153">интернетклиентсервер</span><span class="sxs-lookup"><span data-stu-id="9215a-153">InternetClientServer</span></span>
    * <span data-ttu-id="9215a-154">приватенетворкклиентсервер</span><span class="sxs-lookup"><span data-stu-id="9215a-154">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="9215a-155">Microphone</span><span class="sxs-lookup"><span data-stu-id="9215a-155">Microphone</span></span>
    * <span data-ttu-id="9215a-156">спатиалперцептион</span><span class="sxs-lookup"><span data-stu-id="9215a-156">SpatialPerception</span></span>
* <span data-ttu-id="9215a-157">Перейдите к разделу **изменение > параметры проекта > качество**</span><span class="sxs-lookup"><span data-stu-id="9215a-157">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="9215a-158">На панели **инспектора** под значком магазина Windows выберите черную стрелку раскрывающегося списка в строке "по умолчанию" и измените значение по умолчанию на **очень низкое**.</span><span class="sxs-lookup"><span data-stu-id="9215a-158">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="9215a-159">Перейдите в раздел **активы > импортировать пакет > настраиваемый пакет**.</span><span class="sxs-lookup"><span data-stu-id="9215a-159">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="9215a-160">Перейдите в папку **. ..\холографикакадеми-холограмс-230-спатиалмаппинг\стартинг** .</span><span class="sxs-lookup"><span data-stu-id="9215a-160">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="9215a-161">Щелкните **Планетариум. пакет unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="9215a-161">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="9215a-162">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="9215a-162">Click **Open**.</span></span>
* <span data-ttu-id="9215a-163">Появится окно **Импорт пакета Unity** , нажмите кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="9215a-163">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="9215a-164">Дождитесь, пока Unity завершит импорт всех ресурсов, которые понадобятся нам для выполнения этого проекта.</span><span class="sxs-lookup"><span data-stu-id="9215a-164">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="9215a-165">На панели **Иерархия** удалите **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="9215a-165">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="9215a-166">На панели **проект** в папке **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** найдите **основной объект Camera** .</span><span class="sxs-lookup"><span data-stu-id="9215a-166">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="9215a-167">Перетащите **основной prefab камеры** в панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="9215a-167">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9215a-168">На панели **Иерархия** удалите объект **направленного освещения** .</span><span class="sxs-lookup"><span data-stu-id="9215a-168">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="9215a-169">На панели **проект** в папке **голограммы** выберите объект **курсора** .</span><span class="sxs-lookup"><span data-stu-id="9215a-169">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="9215a-170">Перетащите & **курсора** prefab в **иерархию**.</span><span class="sxs-lookup"><span data-stu-id="9215a-170">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="9215a-171">На панели **Иерархия** выберите объект **курсора** .</span><span class="sxs-lookup"><span data-stu-id="9215a-171">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="9215a-172">На панели **инспектора** щелкните раскрывающийся список **слой** и выберите **изменить слои..** ..</span><span class="sxs-lookup"><span data-stu-id="9215a-172">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="9215a-173">Присвойте **пользовательскому уровню 31** значение "**спатиалмаппинг**".</span><span class="sxs-lookup"><span data-stu-id="9215a-173">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="9215a-174">Сохраните новую сцену: **файл > сохранить сцену как...**</span><span class="sxs-lookup"><span data-stu-id="9215a-174">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="9215a-175">Щелкните **создать папку** и присвойте имя папке **сцены**.</span><span class="sxs-lookup"><span data-stu-id="9215a-175">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="9215a-176">Назовите файл «**планетариум**» и сохраните его в папке « **сцены** ».</span><span class="sxs-lookup"><span data-stu-id="9215a-176">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="9215a-177">Глава 1. сканирование</span><span class="sxs-lookup"><span data-stu-id="9215a-177">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="9215a-178">**Служит**</span><span class="sxs-lookup"><span data-stu-id="9215a-178">**Objectives**</span></span>

* <span data-ttu-id="9215a-179">Узнайте о Сурфацеобсервер и о том, как его параметры влияют на работу и производительность.</span><span class="sxs-lookup"><span data-stu-id="9215a-179">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="9215a-180">Создайте процесс сканирования комнаты для сбора сеток комнаты.</span><span class="sxs-lookup"><span data-stu-id="9215a-180">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="9215a-181">**Водим**</span><span class="sxs-lookup"><span data-stu-id="9215a-181">**Instructions**</span></span>

* <span data-ttu-id="9215a-182">В папке **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** на панели **проекта** найдите **спатиалмаппинг** prefab.</span><span class="sxs-lookup"><span data-stu-id="9215a-182">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="9215a-183">Перетащите & **спатиалмаппинг** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="9215a-183">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="9215a-184">**Сборка и развертывание (часть 1)**</span><span class="sxs-lookup"><span data-stu-id="9215a-184">**Build and Deploy (part 1)**</span></span>

* <span data-ttu-id="9215a-185">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="9215a-185">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="9215a-186">Нажмите кнопку **Добавить открытые сцены** , чтобы добавить сцену **планетариум** в сборку.</span><span class="sxs-lookup"><span data-stu-id="9215a-186">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="9215a-187">Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.</span><span class="sxs-lookup"><span data-stu-id="9215a-187">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="9215a-188">Установите для **пакета SDK** значение **универсальной 10** , а для **типа сборки UWP** — **D3D**.</span><span class="sxs-lookup"><span data-stu-id="9215a-188">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="9215a-189">Проверьте **проекты C# Unity**.</span><span class="sxs-lookup"><span data-stu-id="9215a-189">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="9215a-190">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="9215a-190">Click **Build**.</span></span>
* <span data-ttu-id="9215a-191">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="9215a-191">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="9215a-192">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="9215a-192">Single click the **App** folder.</span></span>
* <span data-ttu-id="9215a-193">Нажмите кнопку **Выбор папки** .</span><span class="sxs-lookup"><span data-stu-id="9215a-193">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="9215a-194">После завершения сборки Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="9215a-194">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="9215a-195">Дважды щелкните папку **приложения** , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="9215a-195">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="9215a-196">Дважды щелкните **Планетариум. sln** , чтобы загрузить проект в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9215a-196">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="9215a-197">В Visual Studio используйте верхнюю панель инструментов, чтобы изменить конфигурацию на **выпуск**.</span><span class="sxs-lookup"><span data-stu-id="9215a-197">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="9215a-198">Измените платформу на **x86**.</span><span class="sxs-lookup"><span data-stu-id="9215a-198">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="9215a-199">Щелкните стрелку раскрывающегося списка справа от "локальный компьютер" и выберите **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="9215a-199">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="9215a-200">Введите [IP-адрес устройства](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) в поле адрес и измените режим проверки подлинности на **универсальный (незашифрованный протокол)** .</span><span class="sxs-lookup"><span data-stu-id="9215a-200">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="9215a-201">Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="9215a-201">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="9215a-202">Просмотрите панель **вывода** в Visual Studio для состояния сборки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="9215a-202">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="9215a-203">После развертывания приложения обходится комната.</span><span class="sxs-lookup"><span data-stu-id="9215a-203">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="9215a-204">Вы увидите окружающие области, покрытые черными и белыми проволочными сетками.</span><span class="sxs-lookup"><span data-stu-id="9215a-204">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="9215a-205">Сканирование окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="9215a-205">Scan your surroundings.</span></span> <span data-ttu-id="9215a-206">Обязательно взгляните на стены, цеилингс и пол.</span><span class="sxs-lookup"><span data-stu-id="9215a-206">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="9215a-207">**Сборка и развертывание (часть 2)**</span><span class="sxs-lookup"><span data-stu-id="9215a-207">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="9215a-208">Теперь давайте рассмотрим, как пространственное сопоставление может повлиять на производительность.</span><span class="sxs-lookup"><span data-stu-id="9215a-208">Now let's explore how Spatial Mapping can affect performance.</span></span>

* <span data-ttu-id="9215a-209">В Unity выберите **Window > Profiler**.</span><span class="sxs-lookup"><span data-stu-id="9215a-209">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="9215a-210">Щелкните **Добавить профилировщик > GPU**.</span><span class="sxs-lookup"><span data-stu-id="9215a-210">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="9215a-211">Щелкните **активный профилировщик > <Enter IP>** .</span><span class="sxs-lookup"><span data-stu-id="9215a-211">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="9215a-212">Введите **IP-адрес** HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9215a-212">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="9215a-213">Нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="9215a-213">Click **Connect**.</span></span>
* <span data-ttu-id="9215a-214">Обратите внимание на число миллисекунд, необходимое для отображения кадра графическим процессором.</span><span class="sxs-lookup"><span data-stu-id="9215a-214">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="9215a-215">Останавливает выполнение приложения на устройстве.</span><span class="sxs-lookup"><span data-stu-id="9215a-215">Stop the application from running on the device.</span></span>
* <span data-ttu-id="9215a-216">Вернитесь в Visual Studio и откройте **SpatialMappingObserver.CS**.</span><span class="sxs-lookup"><span data-stu-id="9215a-216">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="9215a-217">Он будет находиться в папке Холотулкит\спатиалмаппинг проекта Assembly-CSharp (универсальные приложения Windows).</span><span class="sxs-lookup"><span data-stu-id="9215a-217">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="9215a-218">Найдите функцию " **спящий ()** " и добавьте следующую строку кода: **трианглесперкубикметер = 1200;**</span><span class="sxs-lookup"><span data-stu-id="9215a-218">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="9215a-219">Повторно разверните проект на устройстве, а затем снова **Подключите профилировщик**.</span><span class="sxs-lookup"><span data-stu-id="9215a-219">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="9215a-220">Обратите внимание на изменение количества миллисекунд для отображения кадра.</span><span class="sxs-lookup"><span data-stu-id="9215a-220">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="9215a-221">Останавливает выполнение приложения на устройстве.</span><span class="sxs-lookup"><span data-stu-id="9215a-221">Stop the application from running on the device.</span></span>

<span data-ttu-id="9215a-222">**Сохранение и загрузка в Unity**</span><span class="sxs-lookup"><span data-stu-id="9215a-222">**Save and load in Unity**</span></span>

<span data-ttu-id="9215a-223">Наконец, давайте экономим сетку комнаты и загружая ее в Unity.</span><span class="sxs-lookup"><span data-stu-id="9215a-223">Finally, let's save our room mesh and load it into Unity.</span></span>

* <span data-ttu-id="9215a-224">Вернитесь в Visual Studio и удалите строку **трианглесперкубикметер** , добавленную в функцию **спящего режима ()** во время предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="9215a-224">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="9215a-225">Повторно разверните проект на устройстве.</span><span class="sxs-lookup"><span data-stu-id="9215a-225">Redeploy the project to your device.</span></span> <span data-ttu-id="9215a-226">Теперь мы должны работать с **500** треугольниками на кубический метр.</span><span class="sxs-lookup"><span data-stu-id="9215a-226">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="9215a-227">Откройте браузер и введите свой IP-адрес HoloLens, чтобы перейти на **портал устройств Windows**.</span><span class="sxs-lookup"><span data-stu-id="9215a-227">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="9215a-228">Выберите параметр **объемное представление** на панели слева.</span><span class="sxs-lookup"><span data-stu-id="9215a-228">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="9215a-229">В разделе **реконструкция поверхности** нажмите кнопку **Обновить** .</span><span class="sxs-lookup"><span data-stu-id="9215a-229">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="9215a-230">Следите за тем, как области, просмотренные на HoloLens, отображаются в окне отображения.</span><span class="sxs-lookup"><span data-stu-id="9215a-230">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="9215a-231">Чтобы сохранить сканирование комнаты, нажмите кнопку **сохранить** .</span><span class="sxs-lookup"><span data-stu-id="9215a-231">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="9215a-232">Откройте папку **downloads** , чтобы найти сохраненную модель комнаты **срмеш. obj**.</span><span class="sxs-lookup"><span data-stu-id="9215a-232">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="9215a-233">Скопируйте **срмеш. obj** в папку **Assets** проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="9215a-233">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="9215a-234">В Unity выберите объект **спатиалмаппинг** на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="9215a-234">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9215a-235">Нахождение компонента **наблюдателя поверхности объектов (script)** .</span><span class="sxs-lookup"><span data-stu-id="9215a-235">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="9215a-236">Щелкните окружность справа от свойства **модель комнаты** .</span><span class="sxs-lookup"><span data-stu-id="9215a-236">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="9215a-237">Найдите и выберите объект **срмеш** , а затем закройте окно.</span><span class="sxs-lookup"><span data-stu-id="9215a-237">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="9215a-238">Убедитесь, что свойство " **модель комнаты** " на панели **инспектора** теперь имеет значение **срмеш**.</span><span class="sxs-lookup"><span data-stu-id="9215a-238">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="9215a-239">Нажмите кнопку **Воспроизведение** , чтобы войти в режим предварительного просмотра Unity.</span><span class="sxs-lookup"><span data-stu-id="9215a-239">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="9215a-240">Компонент Спатиалмаппинг загрузит сетки из сохраненной модели комнаты, чтобы их можно было использовать в Unity.</span><span class="sxs-lookup"><span data-stu-id="9215a-240">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="9215a-241">Переключитесь в представление **сцены** , чтобы увидеть всю модель комнаты, отображаемую с помощью каркасного шейдера.</span><span class="sxs-lookup"><span data-stu-id="9215a-241">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="9215a-242">Нажмите кнопку **воспроизвести** еще раз, чтобы выйти из режима предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="9215a-242">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="9215a-243">**Примечание.** При следующем входе в режим предварительного просмотра в Unity по умолчанию будет загружена сохраненная сетка комнаты.</span><span class="sxs-lookup"><span data-stu-id="9215a-243">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="9215a-244">Глава 2. Визуализация</span><span class="sxs-lookup"><span data-stu-id="9215a-244">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="9215a-245">**Служит**</span><span class="sxs-lookup"><span data-stu-id="9215a-245">**Objectives**</span></span>

* <span data-ttu-id="9215a-246">Изучите основы шейдеров.</span><span class="sxs-lookup"><span data-stu-id="9215a-246">Learn the basics of shaders.</span></span>
* <span data-ttu-id="9215a-247">Визуализация окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="9215a-247">Visualize your surroundings.</span></span>

<span data-ttu-id="9215a-248">**Водим**</span><span class="sxs-lookup"><span data-stu-id="9215a-248">**Instructions**</span></span>

* <span data-ttu-id="9215a-249">На панели **Иерархия** Unity выберите объект **спатиалмаппинг** .</span><span class="sxs-lookup"><span data-stu-id="9215a-249">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="9215a-250">На панели **инспектора** найдите компонент **Диспетчер пространственных сопоставлений (script)** .</span><span class="sxs-lookup"><span data-stu-id="9215a-250">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="9215a-251">Щелкните окружность справа от свойства " **материал поверхности** ".</span><span class="sxs-lookup"><span data-stu-id="9215a-251">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="9215a-252">Найдите и выберите материал **блуелинесонваллс** и закройте окно.</span><span class="sxs-lookup"><span data-stu-id="9215a-252">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="9215a-253">В папке " **шейдеры** " панели **проекта** дважды щелкните **блуелинесонваллс** , чтобы открыть шейдер в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9215a-253">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="9215a-254">Это простой шейдер пикселей (вершина на фрагмент), который выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="9215a-254">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="9215a-255">Преобразует расположение вершины в мировое пространство.</span><span class="sxs-lookup"><span data-stu-id="9215a-255">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="9215a-256">Проверяет нормальную вершину, чтобы определить, является ли пиксель вертикальным.</span><span class="sxs-lookup"><span data-stu-id="9215a-256">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="9215a-257">Задает цвет пикселя для отрисовки.</span><span class="sxs-lookup"><span data-stu-id="9215a-257">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="9215a-258">**Сборка и развертывание**</span><span class="sxs-lookup"><span data-stu-id="9215a-258">**Build and Deploy**</span></span>

* <span data-ttu-id="9215a-259">Вернитесь в Unity и нажмите кнопку **Play** , чтобы перейти в режим предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="9215a-259">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="9215a-260">Синие линии будут отображаться на всех вертикальных поверхностях сетки комнаты (которая автоматически загружается из сохраненных данных сканирования).</span><span class="sxs-lookup"><span data-stu-id="9215a-260">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="9215a-261">Перейдите на вкладку **сцена** , чтобы настроить представление комнаты и увидеть, как вся сетка комнаты отображается в Unity.</span><span class="sxs-lookup"><span data-stu-id="9215a-261">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="9215a-262">На панели **проект** найдите папку **материалы** и выберите материал **блуелинесонваллс** .</span><span class="sxs-lookup"><span data-stu-id="9215a-262">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="9215a-263">Измените некоторые свойства и посмотрите, как изменения отображаются в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="9215a-263">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="9215a-264">На панели **инспектора** измените значение **линескале** , чтобы линии были более толстыми или более тонкими.</span><span class="sxs-lookup"><span data-stu-id="9215a-264">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="9215a-265">На панели **инспектора** настройте значение **линесперметер** , чтобы изменить количество линий, отображаемых на каждой стене.</span><span class="sxs-lookup"><span data-stu-id="9215a-265">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="9215a-266">Снова нажмите кнопку **воспроизвести** , чтобы выйти из режима просмотра.</span><span class="sxs-lookup"><span data-stu-id="9215a-266">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="9215a-267">Выполните сборку и развертывание в HoloLens и обратите внимание на то, как отрисовка шейдера отображается на реальных поверхностях.</span><span class="sxs-lookup"><span data-stu-id="9215a-267">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="9215a-268">Unity — это отличная работа по предварительному просмотру материалов, но рекомендуется всегда отвлекаться от просмотра на устройстве.</span><span class="sxs-lookup"><span data-stu-id="9215a-268">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="9215a-269">Глава 3. обработка</span><span class="sxs-lookup"><span data-stu-id="9215a-269">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="9215a-270">**Служит**</span><span class="sxs-lookup"><span data-stu-id="9215a-270">**Objectives**</span></span>

* <span data-ttu-id="9215a-271">Узнайте о методах обработки данных пространственного сопоставления для использования в приложении.</span><span class="sxs-lookup"><span data-stu-id="9215a-271">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="9215a-272">Анализ данных пространственного сопоставления для поиска плоскостей и удаления треугольников.</span><span class="sxs-lookup"><span data-stu-id="9215a-272">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="9215a-273">Используйте плоскости для размещения голограмм.</span><span class="sxs-lookup"><span data-stu-id="9215a-273">Use planes for hologram placement.</span></span>

<span data-ttu-id="9215a-274">**Водим**</span><span class="sxs-lookup"><span data-stu-id="9215a-274">**Instructions**</span></span>

* <span data-ttu-id="9215a-275">На панели **проекта** Unity в папке **голограмм** найдите объект **спатиалпроцессинг** .</span><span class="sxs-lookup"><span data-stu-id="9215a-275">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="9215a-276">Перетащите & объект **спатиалпроцессинг** на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="9215a-276">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="9215a-277">Спатиалпроцессинг prefab включает компоненты для обработки данных пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="9215a-277">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="9215a-278">**SurfaceMeshesToPlanes.CS** найдет и создаст плоскости на основе данных пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="9215a-278">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="9215a-279">Для представления стен, этажей и цеилингс мы будем использовать плоскости в нашем приложении.</span><span class="sxs-lookup"><span data-stu-id="9215a-279">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="9215a-280">Этот prefab также включает **RemoveSurfaceVertices.CS** , который может удалять вершины из сетки пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="9215a-280">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="9215a-281">Это можно использовать для создания отверстий в сетке или удаления лишних треугольников, которые больше не нужны (так как вместо них можно использовать плоскости).</span><span class="sxs-lookup"><span data-stu-id="9215a-281">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>

* <span data-ttu-id="9215a-282">На панели **проекта** Unity в папке **голограмм** найдите объект **спацеколлектион** .</span><span class="sxs-lookup"><span data-stu-id="9215a-282">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="9215a-283">Перетащите объект **спацеколлектион** на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="9215a-283">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9215a-284">На панели **Иерархия** выберите объект **спатиалпроцессинг** .</span><span class="sxs-lookup"><span data-stu-id="9215a-284">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="9215a-285">На панели **инспектора** найдите компонент **диспетчер пространства воспроизведения (script)** .</span><span class="sxs-lookup"><span data-stu-id="9215a-285">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="9215a-286">Дважды щелкните **PlaySpaceManager.CS** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9215a-286">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="9215a-287">PlaySpaceManager.cs содержит код, зависящий от приложения.</span><span class="sxs-lookup"><span data-stu-id="9215a-287">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="9215a-288">Мы добавим в этот скрипт функциональные возможности, чтобы обеспечить следующее поведение:</span><span class="sxs-lookup"><span data-stu-id="9215a-288">We will add functionality to this script to enable the following behavior:</span></span>

1. <span data-ttu-id="9215a-289">Прерывать сбор данных пространственного сопоставления после превышения предельного времени сканирования (10 секунд).</span><span class="sxs-lookup"><span data-stu-id="9215a-289">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="9215a-290">Обработка данных пространственного сопоставления:</span><span class="sxs-lookup"><span data-stu-id="9215a-290">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="9215a-291">Используйте Сурфацемешестопланес для создания более простого представления мира в виде плоскостей (стен, пол, цеилингс и т. д.).</span><span class="sxs-lookup"><span data-stu-id="9215a-291">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="9215a-292">Используйте Ремовесурфацевертицес, чтобы удалить треугольники Surface, которые попадают в границы плоскости.</span><span class="sxs-lookup"><span data-stu-id="9215a-292">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="9215a-293">Создавайте коллекцию голограмм в мире и размещайте их на стенных и этажных плоскостях рядом с пользователем.</span><span class="sxs-lookup"><span data-stu-id="9215a-293">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="9215a-294">Выполните упражнения по написанию кода, помеченные в PlaySpaceManager.cs, или замените скрипт завершенным решением ниже:</span><span class="sxs-lookup"><span data-stu-id="9215a-294">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="9215a-295">**Сборка и развертывание**</span><span class="sxs-lookup"><span data-stu-id="9215a-295">**Build and Deploy**</span></span>

* <span data-ttu-id="9215a-296">Перед развертыванием в HoloLens нажмите кнопку **воспроизведения** в Unity, чтобы войти в режим воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="9215a-296">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="9215a-297">После загрузки сетки комнаты из файла подождите 10 секунд, прежде чем обработка начнется в сетке пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="9215a-297">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="9215a-298">После завершения обработки отобразятся плоскости, представляющие этаж, стены, потолк и т. д.</span><span class="sxs-lookup"><span data-stu-id="9215a-298">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="9215a-299">После того как все плоскости будут найдены, в таблице пола рядом с камерой появится Солнечная система.</span><span class="sxs-lookup"><span data-stu-id="9215a-299">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="9215a-300">В стены рядом с камерой должны появиться два плаката.</span><span class="sxs-lookup"><span data-stu-id="9215a-300">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="9215a-301">Перейдите на вкладку **сцена** , если вы не видите их в **игровом** режиме.</span><span class="sxs-lookup"><span data-stu-id="9215a-301">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="9215a-302">Нажмите кнопку **воспроизвести** еще раз, чтобы выйти из режима воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="9215a-302">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="9215a-303">Выполните сборку и развертывание в HoloLens, как обычно.</span><span class="sxs-lookup"><span data-stu-id="9215a-303">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="9215a-304">Дождитесь завершения проверки и обработки данных пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="9215a-304">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="9215a-305">Получив плоскости, попытайтесь найти солнечную систему и афиши в мире.</span><span class="sxs-lookup"><span data-stu-id="9215a-305">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="9215a-306">Глава 4. размещение</span><span class="sxs-lookup"><span data-stu-id="9215a-306">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="9215a-307">**Служит**</span><span class="sxs-lookup"><span data-stu-id="9215a-307">**Objectives**</span></span>

* <span data-ttu-id="9215a-308">Определить, умещается ли голограмма на поверхности.</span><span class="sxs-lookup"><span data-stu-id="9215a-308">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="9215a-309">Предоставьте отзыв пользователю, когда голограмма может уместиться на поверхности.</span><span class="sxs-lookup"><span data-stu-id="9215a-309">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="9215a-310">**Водим**</span><span class="sxs-lookup"><span data-stu-id="9215a-310">**Instructions**</span></span>

* <span data-ttu-id="9215a-311">На панели **Иерархия** Unity выберите объект **спатиалпроцессинг** .</span><span class="sxs-lookup"><span data-stu-id="9215a-311">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="9215a-312">На панели **инспектора** найдите элемент " **сетки поверхности" для компонента "плоскости (скрипт)"** .</span><span class="sxs-lookup"><span data-stu-id="9215a-312">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="9215a-313">Измените значение свойства **Draw плоскости** на **Nothing** , чтобы снять выделение.</span><span class="sxs-lookup"><span data-stu-id="9215a-313">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="9215a-314">Измените значение свойства **Draw плоскости** на **настенный**, чтобы отображались только стены.</span><span class="sxs-lookup"><span data-stu-id="9215a-314">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="9215a-315">На панели **проект** в папке **скрипты** дважды щелкните **Placeable.CS** , чтобы открыть ее в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9215a-315">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="9215a-316">**Размещенный** скрипт уже присоединен к полю афиши и проекции, созданному после завершения поиска на плоскости.</span><span class="sxs-lookup"><span data-stu-id="9215a-316">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="9215a-317">Все, что нам нужно сделать, — это раскомментировать некоторый код, и этот сценарий выполнит следующие действия:</span><span class="sxs-lookup"><span data-stu-id="9215a-317">All we need to do is uncomment some code, and this script will achieve the following:</span></span>

1. <span data-ttu-id="9215a-318">Определить, помещается ли голограмма на поверхность, райкастинг от центра и четырех углов ограничивающего Куба.</span><span class="sxs-lookup"><span data-stu-id="9215a-318">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="9215a-319">Проверьте нормальную поверхность, чтобы определить, достаточно ли она для записи на голограмму.</span><span class="sxs-lookup"><span data-stu-id="9215a-319">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="9215a-320">Отрисовка ограничивающего Куба вокруг голограммы для отображения ее фактического размера во время размещения.</span><span class="sxs-lookup"><span data-stu-id="9215a-320">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="9215a-321">Приведите тень в разделе/позади голограммы, чтобы узнать, где она будет размещена на этаже или стене.</span><span class="sxs-lookup"><span data-stu-id="9215a-321">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="9215a-322">Отрисовывает тень как красный, если она не может быть размещена на поверхности или зеленого, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="9215a-322">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="9215a-323">Измените ориентацию голограммы так, чтобы она выработала с типом поверхности (вертикально или горизонтально), с которым он имеет сходство.</span><span class="sxs-lookup"><span data-stu-id="9215a-323">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="9215a-324">Плавно размещайте голограмму на выбранной поверхности, чтобы избежать появления или привязки.</span><span class="sxs-lookup"><span data-stu-id="9215a-324">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="9215a-325">Раскомментируйте весь код в приведенном ниже упражнении кода или используйте это законченное решение в **Placeable.CS**:</span><span class="sxs-lookup"><span data-stu-id="9215a-325">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="9215a-326">**Сборка и развертывание**</span><span class="sxs-lookup"><span data-stu-id="9215a-326">**Build and Deploy**</span></span>

* <span data-ttu-id="9215a-327">Как и ранее, выполните сборку проекта и разверните его в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9215a-327">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="9215a-328">Дождитесь завершения проверки и обработки данных пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="9215a-328">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="9215a-329">Когда появится Солнечная система, Взгляните на поле проекции ниже и выполните жест выбора, чтобы его переместить.</span><span class="sxs-lookup"><span data-stu-id="9215a-329">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="9215a-330">Пока выбрано поле проекции, ограничивающий куб будет виден вокруг поля проекции.</span><span class="sxs-lookup"><span data-stu-id="9215a-330">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="9215a-331">Переместите заголовку, чтобы Взгляните на другое место в комнате.</span><span class="sxs-lookup"><span data-stu-id="9215a-331">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="9215a-332">Поле проекции должно следовать за вашим взглядом.</span><span class="sxs-lookup"><span data-stu-id="9215a-332">The projection box should follow your gaze.</span></span> <span data-ttu-id="9215a-333">Когда тень под полем проекции становится красным, вы не сможете поместить голограмму на этой поверхности.</span><span class="sxs-lookup"><span data-stu-id="9215a-333">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="9215a-334">Когда тень под полем проекции становится зеленой, можно поместить голограмму, выполнив другой жест выбора.</span><span class="sxs-lookup"><span data-stu-id="9215a-334">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="9215a-335">Найдите и выберите один из holographic-афиш на стене, чтобы переместить его в новое место.</span><span class="sxs-lookup"><span data-stu-id="9215a-335">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="9215a-336">Обратите внимание, что вы не можете поместить афишу в этаж или потолк и правильно ориентироваться на каждую стену по мере движения.</span><span class="sxs-lookup"><span data-stu-id="9215a-336">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="9215a-337">Глава 5-перекрытия</span><span class="sxs-lookup"><span data-stu-id="9215a-337">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="9215a-338">**Служит**</span><span class="sxs-lookup"><span data-stu-id="9215a-338">**Objectives**</span></span>

* <span data-ttu-id="9215a-339">Определить, перекрыто ли голограмма в сетке пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="9215a-339">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="9215a-340">Применение различных методов перекрытия для достижения привлекательного воздействия.</span><span class="sxs-lookup"><span data-stu-id="9215a-340">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="9215a-341">**Водим**</span><span class="sxs-lookup"><span data-stu-id="9215a-341">**Instructions**</span></span>

<span data-ttu-id="9215a-342">Во первых, мы собираемся разрешить сетке пространственных сопоставлений окклуде другие голограммы без окклудинг реального мира:</span><span class="sxs-lookup"><span data-stu-id="9215a-342">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>

* <span data-ttu-id="9215a-343">На панели **Иерархия** выберите объект **спатиалпроцессинг** .</span><span class="sxs-lookup"><span data-stu-id="9215a-343">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="9215a-344">На панели **инспектора** найдите компонент **диспетчер пространства воспроизведения (script)** .</span><span class="sxs-lookup"><span data-stu-id="9215a-344">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="9215a-345">Щелкните окружность справа от свойства **дополнительного материала** .</span><span class="sxs-lookup"><span data-stu-id="9215a-345">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="9215a-346">Найдите и выберите материал **перекрытия** и закройте окно.</span><span class="sxs-lookup"><span data-stu-id="9215a-346">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="9215a-347">Далее мы добавим к земле особое поведение, чтобы оно выглядело синим цветом, когда он станет перекрыто другой голограммой (например, солнце) или сеткой пространственного сопоставления:</span><span class="sxs-lookup"><span data-stu-id="9215a-347">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>

* <span data-ttu-id="9215a-348">На панели « **проект** » в папке « **голограммы** » разверните объект **соларсистем** .</span><span class="sxs-lookup"><span data-stu-id="9215a-348">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="9215a-349">Щелкните **Земля**.</span><span class="sxs-lookup"><span data-stu-id="9215a-349">Click on **Earth**.</span></span>
* <span data-ttu-id="9215a-350">На панели **инспектора** найдите материал земли (нижний компонент).</span><span class="sxs-lookup"><span data-stu-id="9215a-350">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="9215a-351">В **раскрывающемся списке шейдер**замените шейдер на **Custom > окклусионрим**.</span><span class="sxs-lookup"><span data-stu-id="9215a-351">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="9215a-352">Это приведет к отображению синего выделения вокруг земли всякий раз, когда он перекрыто другим объектом.</span><span class="sxs-lookup"><span data-stu-id="9215a-352">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="9215a-353">Наконец, мы будем включать результат концепции x-ray для планет в нашей солнечной системе.</span><span class="sxs-lookup"><span data-stu-id="9215a-353">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="9215a-354">Для достижения следующих целей необходимо изменить **PlanetOcclusion.CS** (находится в папке скриптс\соларсистем).</span><span class="sxs-lookup"><span data-stu-id="9215a-354">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>

1. <span data-ttu-id="9215a-355">Определите, перекрыто ли Планета на уровне Спатиалмаппинг (сеток и плоскостей комнаты).</span><span class="sxs-lookup"><span data-stu-id="9215a-355">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="9215a-356">Отображение каркасного представления планеты, когда она перекрыто слоем Спатиалмаппинг.</span><span class="sxs-lookup"><span data-stu-id="9215a-356">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="9215a-357">Скрыть каркасное представление планеты, если оно не заблокировано слоем Спатиалмаппинг.</span><span class="sxs-lookup"><span data-stu-id="9215a-357">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="9215a-358">Выполните упражнения по написанию кода в PlanetOcclusion.cs или используйте следующее решение:</span><span class="sxs-lookup"><span data-stu-id="9215a-358">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="9215a-359">**Сборка и развертывание**</span><span class="sxs-lookup"><span data-stu-id="9215a-359">**Build and Deploy**</span></span>

* <span data-ttu-id="9215a-360">Создайте и разверните приложение в HoloLens, как обычно.</span><span class="sxs-lookup"><span data-stu-id="9215a-360">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="9215a-361">Дождитесь завершения проверки и обработки данных пространственного сопоставления (на стены должны отобразиться синие линии).</span><span class="sxs-lookup"><span data-stu-id="9215a-361">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="9215a-362">Найдите и выберите поле проекция солнечной системы, а затем установите флажок рядом с простенкой или за счетчиком.</span><span class="sxs-lookup"><span data-stu-id="9215a-362">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="9215a-363">Вы можете просмотреть базовые перекрытия, скрывая поверхности к узлу в виде афиши или проекции.</span><span class="sxs-lookup"><span data-stu-id="9215a-363">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="9215a-364">Взгляните на земле. при переходе на другую голограмму или поверхность должен быть выделен синий цвет.</span><span class="sxs-lookup"><span data-stu-id="9215a-364">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="9215a-365">Следите за тем, как планеты перемещаются позади стены или других поверхностей комнаты.</span><span class="sxs-lookup"><span data-stu-id="9215a-365">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="9215a-366">Теперь у вас есть концепция x-ray и видна их каркасы.</span><span class="sxs-lookup"><span data-stu-id="9215a-366">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="9215a-367">Конец</span><span class="sxs-lookup"><span data-stu-id="9215a-367">The End</span></span>

<span data-ttu-id="9215a-368">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="9215a-368">Congratulations!</span></span> <span data-ttu-id="9215a-369">Теперь вы завершили выполнение пространственного **пространственного 230: пространственное сопоставление**.</span><span class="sxs-lookup"><span data-stu-id="9215a-369">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>

* <span data-ttu-id="9215a-370">Вы узнаете, как проверить среду и загрузить данные пространственного сопоставления в Unity.</span><span class="sxs-lookup"><span data-stu-id="9215a-370">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="9215a-371">Вы понимаете основы шейдеров и то, как можно использовать материалы для повторного визуализации мира.</span><span class="sxs-lookup"><span data-stu-id="9215a-371">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="9215a-372">Вы узнали о новых методах обработки для поиска плоскостей и удалении треугольников из сетки.</span><span class="sxs-lookup"><span data-stu-id="9215a-372">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="9215a-373">Вы смогли переместить и разместить голограммы на поверхностях, имеющих смысл.</span><span class="sxs-lookup"><span data-stu-id="9215a-373">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="9215a-374">Вы столкнулись с различными методами перекрытия и использовали преимущества концепции x-ray!</span><span class="sxs-lookup"><span data-stu-id="9215a-374">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
