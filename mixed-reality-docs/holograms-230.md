---
title: Пространственный MR 230 - пространственное сопоставление
description: Выполните кодирование Пошаговое руководство по использованию Unity, Visual Studio и HoloLens пространственное сопоставление понятий подробные сведения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, учебник, пространственное сопоставление, восстановления на поверхности, сетки
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600926"
---
>[!NOTE]
><span data-ttu-id="8782e-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="8782e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8782e-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="8782e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8782e-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8782e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8782e-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="8782e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8782e-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8782e-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8782e-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="8782e-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="8782e-110">MR пространственных 230: Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="8782e-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="8782e-111">[Пространственное сопоставление](spatial-mapping.md) объединяет реального мира и виртуальный мир путем указания голограммы о среде.</span><span class="sxs-lookup"><span data-stu-id="8782e-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="8782e-112">В пространственных 230 MR (проект планетарий) вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="8782e-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="8782e-113">Проверки среды и передачи данных из HoloLens на свой компьютер разработки.</span><span class="sxs-lookup"><span data-stu-id="8782e-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="8782e-114">Изучите шейдеры и узнайте, как использовать их для визуализации модуля.</span><span class="sxs-lookup"><span data-stu-id="8782e-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="8782e-115">Разделите место сетки в простой плоскости с помощью обработки сетки.</span><span class="sxs-lookup"><span data-stu-id="8782e-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="8782e-116">Выйдите за рамки методики размещения, нам удалось выучить за [101 основы MR](holograms-101.md)и оставить отзыв о которой голограмма могут быть помещены в среде.</span><span class="sxs-lookup"><span data-stu-id="8782e-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="8782e-117">Изучите эффекты перекрытия, поэтому если вашей голограмма находится за реальным объектом, его можно по-прежнему просматривать с рентгеновское зрение!</span><span class="sxs-lookup"><span data-stu-id="8782e-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="8782e-118">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="8782e-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8782e-119">Курс</span><span class="sxs-lookup"><span data-stu-id="8782e-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8782e-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8782e-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8782e-121"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8782e-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="8782e-122">MR пространственных 230: Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="8782e-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="8782e-123">✔️</span><span class="sxs-lookup"><span data-stu-id="8782e-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8782e-124">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="8782e-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8782e-125">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="8782e-125">Prerequisites</span></span>

* <span data-ttu-id="8782e-126">ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="8782e-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="8782e-127">Основные C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="8782e-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="8782e-128">Необходимо завершить [101 основы MR](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="8782e-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="8782e-129">Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="8782e-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="8782e-130">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="8782e-130">Project files</span></span>

* <span data-ttu-id="8782e-131">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) требуемые для проекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="8782e-132"> Требуется компонент Unity 2017.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="8782e-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="8782e-133">Если вам по-прежнему требуется поддержка Unity 5.6, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="8782e-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="8782e-134">Если вам по-прежнему требуется поддержка Unity 5.5, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="8782e-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="8782e-135">Если вам по-прежнему требуется поддержка Unity 5.4, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="8782e-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="8782e-136">Удаление архива файлы рабочего стола или других легко положения.</span><span class="sxs-lookup"><span data-stu-id="8782e-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="8782e-137">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="8782e-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="8782e-138">Примечания</span><span class="sxs-lookup"><span data-stu-id="8782e-138">Notes</span></span>

* <span data-ttu-id="8782e-139">«Включить только мой код» в Visual Studio, необходимо отключить (*unchecked*) в разделе Сервис > Параметры > Отладка для точки останова в коде.</span><span class="sxs-lookup"><span data-stu-id="8782e-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="8782e-140">Программа установки Unity</span><span class="sxs-lookup"><span data-stu-id="8782e-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="8782e-141">Запуск **Unity**.</span><span class="sxs-lookup"><span data-stu-id="8782e-141">Start **Unity**.</span></span>
* <span data-ttu-id="8782e-142">Выберите **New** для создания нового проекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="8782e-143">Назовите проект **планетарий**.</span><span class="sxs-lookup"><span data-stu-id="8782e-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="8782e-144">Убедитесь, что **3D** выбран параметр.</span><span class="sxs-lookup"><span data-stu-id="8782e-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="8782e-145">Нажмите кнопку **Создание проекта**.</span><span class="sxs-lookup"><span data-stu-id="8782e-145">Click **Create Project**.</span></span>
* <span data-ttu-id="8782e-146">После запуска Unity перейдите на **изменить > Параметры проекта > проигрывателя**.</span><span class="sxs-lookup"><span data-stu-id="8782e-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="8782e-147">В **инспектор** панели найдите и выберите зеленый **Windows Store** значок.</span><span class="sxs-lookup"><span data-stu-id="8782e-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="8782e-148">Разверните **другие параметры**.</span><span class="sxs-lookup"><span data-stu-id="8782e-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="8782e-149">В **визуализации** установите флажок **поддерживается виртуальной реальности** параметр.</span><span class="sxs-lookup"><span data-stu-id="8782e-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="8782e-150">Убедитесь, что **Windows Holographic** появится в списке **виртуальной реальности SDK**.</span><span class="sxs-lookup"><span data-stu-id="8782e-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="8782e-151">Если это не так, выберите **+** кнопку в нижней части списка и выберите **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="8782e-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="8782e-152">Разверните **Настройка публикации**.</span><span class="sxs-lookup"><span data-stu-id="8782e-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="8782e-153">В **возможности** раздела, проверьте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="8782e-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="8782e-154">internetClientServer</span><span class="sxs-lookup"><span data-stu-id="8782e-154">InternetClientServer</span></span>
    * <span data-ttu-id="8782e-155">privateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="8782e-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="8782e-156">Микрофон</span><span class="sxs-lookup"><span data-stu-id="8782e-156">Microphone</span></span>
    * <span data-ttu-id="8782e-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="8782e-157">SpatialPerception</span></span>
* <span data-ttu-id="8782e-158">Перейдите к **изменить > Параметры проекта > качества**</span><span class="sxs-lookup"><span data-stu-id="8782e-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="8782e-159">В **инспектор** панели под значком Windows Store, выберите черной стрелкой раскрывающегося списка под строкой «Default» и измените значение параметра по умолчанию на **Fastest**.</span><span class="sxs-lookup"><span data-stu-id="8782e-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Fastest**.</span></span>
* <span data-ttu-id="8782e-160">Перейдите к **ресурсы > Импорт пакета > пользовательского пакета**.</span><span class="sxs-lookup"><span data-stu-id="8782e-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="8782e-161">Перейдите к **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** папки.</span><span class="sxs-lookup"><span data-stu-id="8782e-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="8782e-162">Щелкните **Planetarium.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="8782e-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="8782e-163">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="8782e-163">Click **Open**.</span></span>
* <span data-ttu-id="8782e-164">**Импорт пакета Unity** должно появиться окно, щелкните **импорта** кнопки.</span><span class="sxs-lookup"><span data-stu-id="8782e-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="8782e-165">Дождитесь Unity импортировать все ресурсы, которые требуется для выполнения этого проекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="8782e-166">В **иерархии** панели, удалите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="8782e-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="8782e-167">В **проекта** панели **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** папки, найти **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="8782e-168">Перетаскивание **Main Camera** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="8782e-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="8782e-169">В **иерархии** панели, удалите **направленный свет** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="8782e-170">В **проекта** панели **голограммы** папки, найдите **курсор** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="8782e-171">Перетаскивание **курсор** prefab в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="8782e-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="8782e-172">В **иерархии** панели, выберите **курсор** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="8782e-173">В **инспектор** панели, щелкните **слой** раскрывающегося списка и выберите **слои изменить...** .</span><span class="sxs-lookup"><span data-stu-id="8782e-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="8782e-174">Имя **слой пользовательского 31** как "**SpatialMapping**«.</span><span class="sxs-lookup"><span data-stu-id="8782e-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="8782e-175">Сохраните новую сцену: **Файл > Сохранить сцену как...**</span><span class="sxs-lookup"><span data-stu-id="8782e-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="8782e-176">Нажмите кнопку **новую папку** и назовите папку **сцены**.</span><span class="sxs-lookup"><span data-stu-id="8782e-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="8782e-177">Назовите файл «**планетарий**"и сохраните его в **сцены** папки.</span><span class="sxs-lookup"><span data-stu-id="8782e-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="8782e-178">Глава 1 - сканирование</span><span class="sxs-lookup"><span data-stu-id="8782e-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="8782e-179">**Цели**</span><span class="sxs-lookup"><span data-stu-id="8782e-179">**Objectives**</span></span>
* <span data-ttu-id="8782e-180">Сведения о SurfaceObserver и как она влияет на параметры взаимодействия и производительности.</span><span class="sxs-lookup"><span data-stu-id="8782e-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="8782e-181">Создайте комнату, проверку качества для сбора сетки комнате.</span><span class="sxs-lookup"><span data-stu-id="8782e-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="8782e-182">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="8782e-182">**Instructions**</span></span>
* <span data-ttu-id="8782e-183">В **проекта** панели **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** папки, найти **SpatialMapping** prefab.</span><span class="sxs-lookup"><span data-stu-id="8782e-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="8782e-184">Перетаскивание **SpatialMapping** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="8782e-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="8782e-185">**Построение и развертывание (часть 1)**</span><span class="sxs-lookup"><span data-stu-id="8782e-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="8782e-186">В Unity, выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="8782e-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="8782e-187">Нажмите кнопку **добавьте откройте сцены** добавление **планетарий** сцены в сборке.</span><span class="sxs-lookup"><span data-stu-id="8782e-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="8782e-188">Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="8782e-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="8782e-189">Задайте **SDK** для **универсальной 10** и **тип сборки UWP** для **D3D**.</span><span class="sxs-lookup"><span data-stu-id="8782e-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="8782e-190">Проверьте **Unity C# проекты**.</span><span class="sxs-lookup"><span data-stu-id="8782e-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="8782e-191">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="8782e-191">Click **Build**.</span></span>
* <span data-ttu-id="8782e-192">Создание **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="8782e-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="8782e-193">Одним щелчком мыши **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="8782e-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="8782e-194">Нажмите клавишу **Выбор папки** кнопки.</span><span class="sxs-lookup"><span data-stu-id="8782e-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="8782e-195">После завершения Unity построения, появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="8782e-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="8782e-196">Дважды щелкните **приложения** папку, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="8782e-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="8782e-197">Дважды щелкните **Planetarium.sln** загрузить проект в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8782e-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="8782e-198">В Visual Studio, использовать верхней панели инструментов для изменения конфигурации для **выпуска**.</span><span class="sxs-lookup"><span data-stu-id="8782e-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="8782e-199">Изменение платформы на **x86**.</span><span class="sxs-lookup"><span data-stu-id="8782e-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="8782e-200">Щелкните стрелку раскрывающегося списка справа от «Локальный компьютер» и выберите **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="8782e-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="8782e-201">Введите [IP-адрес вашего устройства](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) в адресе и измените режим проверки подлинности, **универсальный (незашифрованный протокол)**.</span><span class="sxs-lookup"><span data-stu-id="8782e-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="8782e-202">Нажмите кнопку **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8782e-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="8782e-203">Контрольные значения **вывода** панели в Visual Studio для сборки и состояние развертывания.</span><span class="sxs-lookup"><span data-stu-id="8782e-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="8782e-204">Когда приложение развернуто, сильна комнате.</span><span class="sxs-lookup"><span data-stu-id="8782e-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="8782e-205">Вы увидите окружающей поверхности, охваченных черно-белый каркас сеток.</span><span class="sxs-lookup"><span data-stu-id="8782e-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="8782e-206">Сканировать обстановке.</span><span class="sxs-lookup"><span data-stu-id="8782e-206">Scan your surroundings.</span></span> <span data-ttu-id="8782e-207">Убедитесь, что рассмотрим стены, максимальных и пол.</span><span class="sxs-lookup"><span data-stu-id="8782e-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="8782e-208">**Построение и развертывание (часть 2)**</span><span class="sxs-lookup"><span data-stu-id="8782e-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="8782e-209">Теперь давайте рассмотрим, как пространственных сопоставление может повлиять на производительность.</span><span class="sxs-lookup"><span data-stu-id="8782e-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="8782e-210">В Unity, выберите **окна > Profiler**.</span><span class="sxs-lookup"><span data-stu-id="8782e-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="8782e-211">Нажмите кнопку **добавьте Profiler > GPU**.</span><span class="sxs-lookup"><span data-stu-id="8782e-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="8782e-212">Нажмите кнопку **Active Profiler > <Enter IP>** .</span><span class="sxs-lookup"><span data-stu-id="8782e-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="8782e-213">Введите **IP-адрес** из вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8782e-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="8782e-214">Нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="8782e-214">Click **Connect**.</span></span>
* <span data-ttu-id="8782e-215">Наблюдайте за время в миллисекундах, необходимое для графического Процессора для подготовки к просмотру кадр.</span><span class="sxs-lookup"><span data-stu-id="8782e-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="8782e-216">Остановите запуск на устройстве приложений.</span><span class="sxs-lookup"><span data-stu-id="8782e-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="8782e-217">Вернитесь в Visual Studio и откройте **SpatialMappingObserver.cs**.</span><span class="sxs-lookup"><span data-stu-id="8782e-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="8782e-218">Вы найдете его в папке HoloToolkit\SpatialMapping проекта сборки-CSharp (универсальной Windows).</span><span class="sxs-lookup"><span data-stu-id="8782e-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="8782e-219">Найти **Awake()** и добавим следующий код: **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="8782e-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="8782e-220">Повторно разверните проект на устройстве, а затем **повторного подключения профилировщика**.</span><span class="sxs-lookup"><span data-stu-id="8782e-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="8782e-221">Понаблюдайте за изменением количество миллисекунд для подготовки к просмотру кадр.</span><span class="sxs-lookup"><span data-stu-id="8782e-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="8782e-222">Остановите запуск на устройстве приложений.</span><span class="sxs-lookup"><span data-stu-id="8782e-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="8782e-223">**Сохранить и загрузить в Unity**</span><span class="sxs-lookup"><span data-stu-id="8782e-223">**Save and load in Unity**</span></span>

<span data-ttu-id="8782e-224">Наконец сохраните наших место сетки и загрузить их в Unity.</span><span class="sxs-lookup"><span data-stu-id="8782e-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="8782e-225">Вернитесь в Visual Studio и удаление **TrianglesPerCubicMeter** строки, который был добавлен в **Awake()** функции во время предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="8782e-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="8782e-226">Повторно разверните проект на устройство.</span><span class="sxs-lookup"><span data-stu-id="8782e-226">Redeploy the project to your device.</span></span> <span data-ttu-id="8782e-227">Мы теперь выполняется с **500** треугольники за третьего метр.</span><span class="sxs-lookup"><span data-stu-id="8782e-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="8782e-228">Откройте браузер и введите в вашей HoloLens IP-адрес для перехода к **Windows Device Portal**.</span><span class="sxs-lookup"><span data-stu-id="8782e-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="8782e-229">Выберите **объемного вида** параметр на панели слева.</span><span class="sxs-lookup"><span data-stu-id="8782e-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="8782e-230">В разделе **область реконструкции** выберите **обновления** кнопки.</span><span class="sxs-lookup"><span data-stu-id="8782e-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="8782e-231">Посмотрите, как области, которые проверены на вашей HoloLens отображаются в окне просмотра.</span><span class="sxs-lookup"><span data-stu-id="8782e-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="8782e-232">Чтобы сохранить место проверки, нажмите клавишу **Сохранить** кнопки.</span><span class="sxs-lookup"><span data-stu-id="8782e-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="8782e-233">Откройте ваш **Скачивает** папку, чтобы найти сохраненные комнаты модель **SRMesh.obj**.</span><span class="sxs-lookup"><span data-stu-id="8782e-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="8782e-234">Копировать **SRMesh.obj** для **активы** папку проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="8782e-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="8782e-235">В Unity, выберите **SpatialMapping** объекта в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="8782e-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="8782e-236">Найдите **наблюдателя поверхность объекта (скрипт)** компонента.</span><span class="sxs-lookup"><span data-stu-id="8782e-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="8782e-237">Щелкните этот кружок справа от **модели комнаты** свойство.</span><span class="sxs-lookup"><span data-stu-id="8782e-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="8782e-238">Найдите и выберите **SRMesh** объекта, а затем закройте окно.</span><span class="sxs-lookup"><span data-stu-id="8782e-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="8782e-239">Убедитесь, что **модели комнаты** свойство в **инспектор** панели теперь настроен для **SRMesh**.</span><span class="sxs-lookup"><span data-stu-id="8782e-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="8782e-240">Нажмите клавишу **воспроизведение** кнопку, чтобы перейти в режим предварительного просмотра Unity.</span><span class="sxs-lookup"><span data-stu-id="8782e-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="8782e-241">Компонент SpatialMapping загрузит сетки из сохраненного комнаты модели, их можно использовать в Unity.</span><span class="sxs-lookup"><span data-stu-id="8782e-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="8782e-242">Переключиться в режим **сцены** представление, чтобы увидеть все модели комнаты отображаются с шейдером, каркасной модели.</span><span class="sxs-lookup"><span data-stu-id="8782e-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="8782e-243">Нажмите клавишу **воспроизведение** кнопку еще раз, чтобы выйти из режима предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="8782e-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="8782e-244">**ПРИМЕЧАНИЕ.** Следующий раз, что режим предварительного просмотра в Unity, выполняется загрузка сохраненного место сетки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8782e-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="8782e-245">Глава 2 - визуализации</span><span class="sxs-lookup"><span data-stu-id="8782e-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="8782e-246">**Цели**</span><span class="sxs-lookup"><span data-stu-id="8782e-246">**Objectives**</span></span>
* <span data-ttu-id="8782e-247">Ознакомиться с основами шейдеров.</span><span class="sxs-lookup"><span data-stu-id="8782e-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="8782e-248">Визуализация обстановке.</span><span class="sxs-lookup"><span data-stu-id="8782e-248">Visualize your surroundings.</span></span>

<span data-ttu-id="8782e-249">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="8782e-249">**Instructions**</span></span>
* <span data-ttu-id="8782e-250">В Unity **иерархии** панели, выберите **SpatialMapping** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="8782e-251">В **инспектор** панели, найти **пространственных Manager сопоставления (скрипт)** компонента.</span><span class="sxs-lookup"><span data-stu-id="8782e-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="8782e-252">Щелкните этот кружок справа от **материала поверхности** свойство.</span><span class="sxs-lookup"><span data-stu-id="8782e-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="8782e-253">Найдите и выберите **BlueLinesOnWalls** материал и закройте окно.</span><span class="sxs-lookup"><span data-stu-id="8782e-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="8782e-254">В **проекта** панели **шейдеры** папки, дважды щелкните **BlueLinesOnWalls** для открытия шейдеров в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8782e-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="8782e-255">Это простой пиксель (вершины фрагментировать) шейдера, который выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="8782e-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="8782e-256">Преобразует вершины расположение в абсолютном пространстве.</span><span class="sxs-lookup"><span data-stu-id="8782e-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="8782e-257">Проверяет, что вершины могут определить, является ли пикселя по вертикали.</span><span class="sxs-lookup"><span data-stu-id="8782e-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="8782e-258">Задает цвет пикселя для подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="8782e-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="8782e-259">**Создание и развертывание**</span><span class="sxs-lookup"><span data-stu-id="8782e-259">**Build and Deploy**</span></span>
* <span data-ttu-id="8782e-260">Вернуться к Unity и нажмите клавишу **воспроизведение** в режим предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="8782e-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="8782e-261">Синие линии отображаются на всех поверхностях вертикальной сетки комнаты (который автоматически загружается из наших сохраненные данные сканирования).</span><span class="sxs-lookup"><span data-stu-id="8782e-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="8782e-262">Переключиться в режим **сцены** tab, чтобы настроить отображение комнаты и увидите, как отображается сетка всего места в Unity.</span><span class="sxs-lookup"><span data-stu-id="8782e-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="8782e-263">В **проекта** панели, найти **материалы** папку и выберите **BlueLinesOnWalls** материал.</span><span class="sxs-lookup"><span data-stu-id="8782e-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="8782e-264">Изменить некоторые свойства и увидеть, как изменения отображаются в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="8782e-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="8782e-265">В **инспектор** панели, Настройка **LineScale** значение, чтобы сделать толще или более тонкие линии.</span><span class="sxs-lookup"><span data-stu-id="8782e-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="8782e-266">В **инспектор** панели, Настройка **LinesPerMeter** значение изменение количества строк на каждую стену.</span><span class="sxs-lookup"><span data-stu-id="8782e-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="8782e-267">Нажмите кнопку **воспроизведение** еще раз, чтобы выйти из режима предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="8782e-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="8782e-268">Построение и развертывание для HoloLens и наблюдать, как отображается шейдера отрисовки на реальном поверхностях.</span><span class="sxs-lookup"><span data-stu-id="8782e-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="8782e-269">Unity выполняет большую работу Предварительный просмотр материалов, но настоятельно рекомендуется извлечения отрисовка в устройство.</span><span class="sxs-lookup"><span data-stu-id="8782e-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="8782e-270">Глава 3 - обработки</span><span class="sxs-lookup"><span data-stu-id="8782e-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="8782e-271">**Цели**</span><span class="sxs-lookup"><span data-stu-id="8782e-271">**Objectives**</span></span>
* <span data-ttu-id="8782e-272">Ознакомьтесь с приемами для обработки пространственное сопоставление данных для использования в приложении.</span><span class="sxs-lookup"><span data-stu-id="8782e-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="8782e-273">Анализ пространственное сопоставление данных для поиска плоскости и удалить треугольники.</span><span class="sxs-lookup"><span data-stu-id="8782e-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="8782e-274">Используйте плоскостей голограмма размещения.</span><span class="sxs-lookup"><span data-stu-id="8782e-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="8782e-275">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="8782e-275">**Instructions**</span></span>
* <span data-ttu-id="8782e-276">В Unity **проекта** панели **голограммы** папки, найти **SpatialProcessing** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="8782e-277">Перетаскивание **SpatialProcessing** в коллекцию **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="8782e-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="8782e-278">SpatialProcessing prefab включает в себя компоненты для обработки данных пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="8782e-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="8782e-279">**SurfaceMeshesToPlanes.cs** найдет и создать на основе данных пространственное сопоставление плоскости.</span><span class="sxs-lookup"><span data-stu-id="8782e-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="8782e-280">Мы будем использовать плоскостей в нашем приложении для представления стены, пол и перекрытия.</span><span class="sxs-lookup"><span data-stu-id="8782e-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="8782e-281">Также включает этот prefab **RemoveSurfaceVertices.cs** которого можно удалить вершины из пространственное сопоставление сети.</span><span class="sxs-lookup"><span data-stu-id="8782e-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="8782e-282">Это можно использовать для создания бреши в системе в сети или чтобы удалить лишние треугольники, которые больше не требуются (поскольку плоскости можно использовать вместо этого).</span><span class="sxs-lookup"><span data-stu-id="8782e-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="8782e-283">В Unity **проекта** панели **голограммы** папки, найти **SpaceCollection** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="8782e-284">Перетаскивание **SpaceCollection** в коллекцию **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="8782e-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="8782e-285">В **иерархии** панели, выберите **SpatialProcessing** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="8782e-286">В **инспектор** панели, найти **воспроизведения диспетчера пространства (скрипт)** компонента.</span><span class="sxs-lookup"><span data-stu-id="8782e-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="8782e-287">Дважды щелкните **PlaySpaceManager.cs** чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8782e-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="8782e-288">PlaySpaceManager.cs содержит код для конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="8782e-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="8782e-289">Мы добавим функциональность в этот сценарий, чтобы включить следующее поведение:</span><span class="sxs-lookup"><span data-stu-id="8782e-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="8782e-290">Остановите процесс сбора данных пространственное сопоставление, после превышения сканирования ограничение времени (10 секунд).</span><span class="sxs-lookup"><span data-stu-id="8782e-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="8782e-291">Процесс сопоставления пространственных данных:</span><span class="sxs-lookup"><span data-stu-id="8782e-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="8782e-292">Используйте SurfaceMeshesToPlanes для создания простой представление мира в виде плоскости (стены, пол, максимальных и т. д).</span><span class="sxs-lookup"><span data-stu-id="8782e-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="8782e-293">С помощью RemoveSurfaceVertices удалить поверхности треугольники, которые попадают в границы плоскости.</span><span class="sxs-lookup"><span data-stu-id="8782e-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="8782e-294">Создает коллекцию голограммы в мире и помещает их на стене и floor плоскостей рядом с пользователем.</span><span class="sxs-lookup"><span data-stu-id="8782e-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="8782e-295">Завершите упражнений по кодированию помечены в PlaySpaceManager.cs или замените скрипт готового решения из приведенных ниже:</span><span class="sxs-lookup"><span data-stu-id="8782e-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

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

<span data-ttu-id="8782e-296">**Создание и развертывание**</span><span class="sxs-lookup"><span data-stu-id="8782e-296">**Build and Deploy**</span></span>
* <span data-ttu-id="8782e-297">Перед развертыванием в HoloLens, нажмите клавишу **воспроизведение** кнопки в Unity, чтобы перейти в режим воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="8782e-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="8782e-298">После загрузки сетки комнаты из файла, подождите 10 секунд, до начала обработки на сетке пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="8782e-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="8782e-299">По завершении обработки плоскостей будет отображаться для представления floor, стены, ceiling, и т.д.</span><span class="sxs-lookup"><span data-stu-id="8782e-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="8782e-300">В конце концов из плоскостей нет, вы должны увидеть Солнечная система отображаются в таблице floor рядом с камеры.</span><span class="sxs-lookup"><span data-stu-id="8782e-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="8782e-301">Два плакаты слишком появится на стене, рядом с камеры.</span><span class="sxs-lookup"><span data-stu-id="8782e-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="8782e-302">Переключиться в режим **сцены** вкладку, если они не видны в **игру** режим.</span><span class="sxs-lookup"><span data-stu-id="8782e-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="8782e-303">Нажмите клавишу **воспроизведение** кнопку еще раз, чтобы выйти из режима play.</span><span class="sxs-lookup"><span data-stu-id="8782e-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="8782e-304">Создание и развертывание в HoloLens, как обычно.</span><span class="sxs-lookup"><span data-stu-id="8782e-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="8782e-305">Дождитесь завершения сканирования и обработки данных пространственное сопоставление для завершения.</span><span class="sxs-lookup"><span data-stu-id="8782e-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="8782e-306">Как только вы увидите плоскости, попробуйте найти Солнечной системы и плакаты в ваш мир.</span><span class="sxs-lookup"><span data-stu-id="8782e-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="8782e-307">Глава 4 – размещения</span><span class="sxs-lookup"><span data-stu-id="8782e-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="8782e-308">**Цели**</span><span class="sxs-lookup"><span data-stu-id="8782e-308">**Objectives**</span></span>
* <span data-ttu-id="8782e-309">Определите, если голограмма помещается в рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8782e-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="8782e-310">Предоставить отзыв пользователя когда голограмма могут или не помещаются в рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8782e-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="8782e-311">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="8782e-311">**Instructions**</span></span>
* <span data-ttu-id="8782e-312">В Unity **иерархии** панели, выберите **SpatialProcessing** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="8782e-313">В **инспектор** панели, найти **поверхности сетки на плоскости (скрипт)** компонента.</span><span class="sxs-lookup"><span data-stu-id="8782e-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="8782e-314">Изменение **рисования плоскостей** свойства **Nothing** чтобы снять выделение.</span><span class="sxs-lookup"><span data-stu-id="8782e-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="8782e-315">Изменение **рисования плоскостей** свойства **стены**, так что отображается только по часам плоскости.</span><span class="sxs-lookup"><span data-stu-id="8782e-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="8782e-316">В **проекта** панели **сценарии** папки, дважды щелкните **Placeable.cs** чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8782e-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="8782e-317">**Placeable** сценарий уже присоединен к плакаты и поле проекции, созданные после завершения поиск плоскости.</span><span class="sxs-lookup"><span data-stu-id="8782e-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="8782e-318">Нам нужно сделать всего лишь раскомментируйте код, и этот сценарий позволяет достичь следующих:</span><span class="sxs-lookup"><span data-stu-id="8782e-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="8782e-319">Определите, если голограмма может поместиться на рабочую область, точные точки для отслеживания из центра и четырех углов ограничивающего куба.</span><span class="sxs-lookup"><span data-stu-id="8782e-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="8782e-320">Проверьте обычные для определения того, является достаточно smooth для голограмма зафиксированных ставятся в рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8782e-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="8782e-321">Отображать ограничивающий куб вокруг голограмма, чтобы показывать его фактический размер во время помещения.</span><span class="sxs-lookup"><span data-stu-id="8782e-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="8782e-322">Уводят в тень в группе или отставать от голограмма, чтобы показать, где будет располагаться на floor/wall.</span><span class="sxs-lookup"><span data-stu-id="8782e-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="8782e-323">Отрисовки тени красным цветом, если она не могут размещаться на поверхности, и зеленым, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="8782e-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="8782e-324">Получите новую ориентацию голограмма в соответствии с поверхности тип (вертикальные или горизонтальные), что он имеет сходство.</span><span class="sxs-lookup"><span data-stu-id="8782e-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="8782e-325">Плавно снабдить выбранную поверхность, чтобы избежать переход, привязывание голограмма.</span><span class="sxs-lookup"><span data-stu-id="8782e-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="8782e-326">Раскомментируйте весь код в фрагмент кода, или использовать это решение, завершенные в **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="8782e-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

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
    /// The aligntoVerticalSurface parameter is ignored if the object
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

<span data-ttu-id="8782e-327">**Создание и развертывание**</span><span class="sxs-lookup"><span data-stu-id="8782e-327">**Build and Deploy**</span></span>
* <span data-ttu-id="8782e-328">Как и раньше постройте проект и разверните HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8782e-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="8782e-329">Дождитесь завершения сканирования и обработки данных пространственное сопоставление для завершения.</span><span class="sxs-lookup"><span data-stu-id="8782e-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="8782e-330">Обнаружив Солнечной системы помощи на поле проекции ниже и выполните жест, выберите ее перенос.</span><span class="sxs-lookup"><span data-stu-id="8782e-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="8782e-331">Во время проекции поле выбрано, ограничивающий куб будет отображаться вокруг поля проекции.</span><span class="sxs-lookup"><span data-stu-id="8782e-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="8782e-332">Переместите head для помощи в другом месте в комнате.</span><span class="sxs-lookup"><span data-stu-id="8782e-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="8782e-333">Поле проекции должен следовал за вашим взглядом.</span><span class="sxs-lookup"><span data-stu-id="8782e-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="8782e-334">При тени под полем проекции станет красным, она не удается разместить в этой области.</span><span class="sxs-lookup"><span data-stu-id="8782e-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="8782e-335">При тени под полем проекции станет зеленой, можно поместить голограмма путем выполнения другой выберите жест.</span><span class="sxs-lookup"><span data-stu-id="8782e-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="8782e-336">Найдите и выберите один из holographic плакатов на стене, чтобы переместить его в новое расположение.</span><span class="sxs-lookup"><span data-stu-id="8782e-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="8782e-337">Обратите внимание на то, что нельзя размещать плакат на floor и ceiling, и что он остается правильную ориентацию для каждой стенки при перемещении курсора.</span><span class="sxs-lookup"><span data-stu-id="8782e-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="8782e-338">Глава 5 - перекрытия</span><span class="sxs-lookup"><span data-stu-id="8782e-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="8782e-339">**Цели**</span><span class="sxs-lookup"><span data-stu-id="8782e-339">**Objectives**</span></span>
* <span data-ttu-id="8782e-340">Определите, если голограмма является перекрыто по сетке пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="8782e-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="8782e-341">Применить перекрытия различные способы достижения интересную эффект.</span><span class="sxs-lookup"><span data-stu-id="8782e-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="8782e-342">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="8782e-342">**Instructions**</span></span>

<span data-ttu-id="8782e-343">Во-первых мы собираемся разрешить сетке пространственное сопоставление, чтобы скрывать другие голограммы без occluding реального мира:</span><span class="sxs-lookup"><span data-stu-id="8782e-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="8782e-344">В **иерархии** панели, выберите **SpatialProcessing** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="8782e-345">В **инспектор** панели, найти **воспроизведения диспетчера пространства (скрипт)** компонента.</span><span class="sxs-lookup"><span data-stu-id="8782e-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="8782e-346">Щелкните этот кружок справа от **дополнительный материал** свойство.</span><span class="sxs-lookup"><span data-stu-id="8782e-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="8782e-347">Найдите и выберите **перекрытия** материал и закройте окно.</span><span class="sxs-lookup"><span data-stu-id="8782e-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="8782e-348">Затем мы собираемся добавить специальное поведение для поверхности Земли, чтобы он включал синяя рамка, каждый раз, когда он становится перекрыто другой голограмма (например, sun) или пространственное сопоставление сети:</span><span class="sxs-lookup"><span data-stu-id="8782e-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="8782e-349">В **проекта** на панели **голограммы** папку, разверните **SolarSystem** объекта.</span><span class="sxs-lookup"><span data-stu-id="8782e-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="8782e-350">Щелкните **Earth**.</span><span class="sxs-lookup"><span data-stu-id="8782e-350">Click on **Earth**.</span></span>
* <span data-ttu-id="8782e-351">В **инспектор** панели, где находится множество материалов Земли (нижней компонент).</span><span class="sxs-lookup"><span data-stu-id="8782e-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="8782e-352">В **раскрывающегося списка шейдера**, измените шейдер для **Custom > OcclusionRim**.</span><span class="sxs-lookup"><span data-stu-id="8782e-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="8782e-353">Это сделает синяя рамка вокруг Earth всякий раз, когда он является перекрыто другим объектом.</span><span class="sxs-lookup"><span data-stu-id="8782e-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="8782e-354">Наконец мы собираемся включить эффект концепции рентгеновский снимок для планет нашей Солнечной системы.</span><span class="sxs-lookup"><span data-stu-id="8782e-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="8782e-355">Нам потребуется изменить **PlanetOcclusion.cs** (находится в папке Scripts\SolarSystem) для достижения следующих:</span><span class="sxs-lookup"><span data-stu-id="8782e-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="8782e-356">Определите, если планеты перекрыто уровнем SpatialMapping (место сетки и плоскости).</span><span class="sxs-lookup"><span data-stu-id="8782e-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="8782e-357">Показать представление каркас планеты, каждый раз, когда он является перекрыто уровнем SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="8782e-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="8782e-358">Скрыть каркас представлением планеты, когда она не заблокирована на уровне SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="8782e-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="8782e-359">Выполните фрагмент кода в PlanetOcclusion.cs или использовать следующее решение:</span><span class="sxs-lookup"><span data-stu-id="8782e-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

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

<span data-ttu-id="8782e-360">**Создание и развертывание**</span><span class="sxs-lookup"><span data-stu-id="8782e-360">**Build and Deploy**</span></span>
* <span data-ttu-id="8782e-361">Создавайте и развертывайте приложения для HoloLens, как обычно.</span><span class="sxs-lookup"><span data-stu-id="8782e-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="8782e-362">Дождитесь сканирования и обработки данных пространственное сопоставление завершения (вы увидите синие линии отображаются на стене).</span><span class="sxs-lookup"><span data-stu-id="8782e-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="8782e-363">Найдите и выберите поле проекции Солнечной системы и задайте поле рядом с стене или за счетчика.</span><span class="sxs-lookup"><span data-stu-id="8782e-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="8782e-364">Можно просмотреть основные перекрытия, скрытие за поверхности для узла в поле плакат или проекции.</span><span class="sxs-lookup"><span data-stu-id="8782e-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="8782e-365">Найдите поверхности Земли, должно быть эффекта синяя рамка всякий раз, когда оно выходит за пределы другой голограмма или области.</span><span class="sxs-lookup"><span data-stu-id="8782e-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="8782e-366">Следите за планеты переместить за wall или других областей в комнате.</span><span class="sxs-lookup"><span data-stu-id="8782e-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="8782e-367">Теперь имеют рентгеновское зрение и можно увидеть их скелетов каркас!</span><span class="sxs-lookup"><span data-stu-id="8782e-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="8782e-368">Конец</span><span class="sxs-lookup"><span data-stu-id="8782e-368">The End</span></span>

<span data-ttu-id="8782e-369">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="8782e-369">Congratulations!</span></span> <span data-ttu-id="8782e-370">Вы завершили **пространственных 230 MR: Пространственное сопоставление**.</span><span class="sxs-lookup"><span data-stu-id="8782e-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="8782e-371">Вы знаете, как выполнить проверку данных вашей среды и нагрузки пространственное сопоставление для Unity.</span><span class="sxs-lookup"><span data-stu-id="8782e-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="8782e-372">Вы знакомы с основами преобразователей текстур и как материалы можно использовать для повторного визуализации мира.</span><span class="sxs-lookup"><span data-stu-id="8782e-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="8782e-373">Вы узнаете о новые методы обработки для поиска плоскости и снятие сетки треугольников.</span><span class="sxs-lookup"><span data-stu-id="8782e-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="8782e-374">Можно было переместить, и размещать голограммы на поверхности, в которые было уместно.</span><span class="sxs-lookup"><span data-stu-id="8782e-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="8782e-375">Произошел другой перекрытия методов и использовали возможности рентгеновское зрение!</span><span class="sxs-lookup"><span data-stu-id="8782e-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
