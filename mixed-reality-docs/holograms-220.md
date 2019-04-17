---
title: Пространственный MR 220 - пространственных звука
description: Выполнения данного кода пошагового руководства, с помощью Unity, Visual Studio и HoloLens Дополнительные сведения о пространственных звуковой понятия.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, учебник, пространственных звука
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599016"
---
>[!NOTE]
><span data-ttu-id="2ca01-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="2ca01-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2ca01-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="2ca01-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2ca01-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ca01-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2ca01-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="2ca01-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2ca01-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ca01-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="2ca01-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="2ca01-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="2ca01-110">MR пространственных 220: Пространственное звучание</span><span class="sxs-lookup"><span data-stu-id="2ca01-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="2ca01-111">[Пространственные звук](spatial-sound.md) breathes жизнь в голограммы и обеспечивает их присутствие в наш мир.</span><span class="sxs-lookup"><span data-stu-id="2ca01-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="2ca01-112">Голограммы строятся света и звука, поэтому если вы не виден вашей голограммы, пространственных звук может помочь найти их.</span><span class="sxs-lookup"><span data-stu-id="2ca01-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="2ca01-113">Пространственные звук не похоже типичный звук, который бы услышать-радио, звук, который находится в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="2ca01-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="2ca01-114">Пространственные звуковое сопровождение внесения голограммы звука, как они навсегда, рядом с вами, или даже в голову!</span><span class="sxs-lookup"><span data-stu-id="2ca01-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="2ca01-115">В этом курсе вы научитесь:</span><span class="sxs-lookup"><span data-stu-id="2ca01-115">In this course, you will:</span></span>

* <span data-ttu-id="2ca01-116">Настройте среду разработки, чтобы использовать Microsoft пространственный звуковой сигнал.</span><span class="sxs-lookup"><span data-stu-id="2ca01-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="2ca01-117">Используйте Пространственные звуковой сигнал для улучшения взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2ca01-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="2ca01-118">Используете Пространственные звуковой сигнал в сочетании с пространственными сопоставление.</span><span class="sxs-lookup"><span data-stu-id="2ca01-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="2ca01-119">Сведения о звуковой проектирования и смешение рекомендации.</span><span class="sxs-lookup"><span data-stu-id="2ca01-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="2ca01-120">Использовать звуковой сигнал для улучшения специальные эффекты и переноса пользователя в мире смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2ca01-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="2ca01-121">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="2ca01-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2ca01-122">Курс</span><span class="sxs-lookup"><span data-stu-id="2ca01-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2ca01-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2ca01-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2ca01-124"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="2ca01-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="2ca01-125">MR пространственных 220: Пространственное звучание</span><span class="sxs-lookup"><span data-stu-id="2ca01-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="2ca01-126">✔️</span><span class="sxs-lookup"><span data-stu-id="2ca01-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2ca01-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2ca01-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="2ca01-128">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="2ca01-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2ca01-129">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="2ca01-129">Prerequisites</span></span>

* <span data-ttu-id="2ca01-130">ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="2ca01-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="2ca01-131">Основные C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="2ca01-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="2ca01-132">Необходимо завершить [101 основы MR](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="2ca01-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="2ca01-133">Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="2ca01-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="2ca01-134">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="2ca01-134">Project files</span></span>

* <span data-ttu-id="2ca01-135">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) требуемые для проекта.</span><span class="sxs-lookup"><span data-stu-id="2ca01-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="2ca01-136"> Требуется компонент Unity 2017.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="2ca01-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="2ca01-137">Если вам по-прежнему требуется поддержка Unity 5.6, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="2ca01-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="2ca01-138">Этот выпуск, больше не может быть актуальном состоянии.</span><span class="sxs-lookup"><span data-stu-id="2ca01-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="2ca01-139">Если вам по-прежнему требуется поддержка Unity 5.5, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="2ca01-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="2ca01-140"> Этот выпуск, больше не может быть актуальном состоянии.</span><span class="sxs-lookup"><span data-stu-id="2ca01-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="2ca01-141">Если вам по-прежнему требуется поддержка Unity 5.4, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="2ca01-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="2ca01-142"> Этот выпуск, больше не может быть актуальном состоянии.</span><span class="sxs-lookup"><span data-stu-id="2ca01-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="2ca01-143">Удаление архива файлы рабочего стола или других легко положения.</span><span class="sxs-lookup"><span data-stu-id="2ca01-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="2ca01-144">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="2ca01-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="2ca01-145">Список ошибок и примечания</span><span class="sxs-lookup"><span data-stu-id="2ca01-145">Errata and Notes</span></span>

* <span data-ttu-id="2ca01-146">«Включить только мой код» необходимо отключить (*unchecked*) в Visual Studio в разделе Сервис -> Параметры -> Отладка для точки останова в коде.</span><span class="sxs-lookup"><span data-stu-id="2ca01-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="2ca01-147">Глава 1 - Установка Unity</span><span class="sxs-lookup"><span data-stu-id="2ca01-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="2ca01-148">Цели</span><span class="sxs-lookup"><span data-stu-id="2ca01-148">Objectives</span></span>

* <span data-ttu-id="2ca01-149">Изменение конфигурации звуковой Unity для использования Microsoft пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="2ca01-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="2ca01-150">Добавление трехмерной звук в объект в Unity.</span><span class="sxs-lookup"><span data-stu-id="2ca01-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="2ca01-151">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2ca01-151">Instructions</span></span>

* <span data-ttu-id="2ca01-152">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="2ca01-152">Start Unity.</span></span>
* <span data-ttu-id="2ca01-153">Выберите **откройте**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-153">Select **Open**.</span></span>
* <span data-ttu-id="2ca01-154">Перейдите к рабочего стола и найти папку вы ранее не архивные.</span><span class="sxs-lookup"><span data-stu-id="2ca01-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="2ca01-155">Щелкните **Starting\Decibel** папку и нажмите клавишу **Выбор папки** кнопки.</span><span class="sxs-lookup"><span data-stu-id="2ca01-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="2ca01-156">Дождитесь загрузки в Unity проекта.</span><span class="sxs-lookup"><span data-stu-id="2ca01-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="2ca01-157">В **проекта** панели **Scenes\Decibel.unity**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="2ca01-158">В **иерархии** панели, разверните узел **HologramCollection** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="2ca01-159">В окне инспектора разверните **AudioSource** и обратите внимание, что не **Spatialize** "флажок".</span><span class="sxs-lookup"><span data-stu-id="2ca01-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="2ca01-160">По умолчанию подключаемый модуль spatializer Unity не загружается.</span><span class="sxs-lookup"><span data-stu-id="2ca01-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="2ca01-161">Следующие действия позволит пространственный звук в проекте.</span><span class="sxs-lookup"><span data-stu-id="2ca01-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="2ca01-162">В верхнем меню Unity, перейдите в раздел **изменить > Параметры проекта > аудио**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="2ca01-163">Найти **подключаемый модуль Spatializer** раскрывающийся список и выберите **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="2ca01-164">В **иерархии** панели, выберите **HologramCollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="2ca01-165">В **инспектор** панели, найти **источника аудио** компонента.</span><span class="sxs-lookup"><span data-stu-id="2ca01-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="2ca01-166">Проверьте **Spatialize** флажок.</span><span class="sxs-lookup"><span data-stu-id="2ca01-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="2ca01-167">Перетащите **пространственных Blend** ползунок вплоть до **3D**, или введите **1** в поле ввода.</span><span class="sxs-lookup"><span data-stu-id="2ca01-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="2ca01-168">Теперь мы постройте проект в Unity и настройка решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ca01-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="2ca01-169">В Unity, выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="2ca01-170">Нажмите кнопку **добавьте откройте сцены** Добавление сцены.</span><span class="sxs-lookup"><span data-stu-id="2ca01-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="2ca01-171">Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="2ca01-172">Если вы разрабатываете специально для HoloLens, задайте **целевое устройство** для **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="2ca01-173">В противном случае оставьте его на **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="2ca01-174">Убедитесь, **построение** присваивается **D3D** и **SDK** имеет значение **самую новую установленную** (которое должно быть SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="2ca01-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="2ca01-175">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-175">Click **Build**.</span></span>
7. <span data-ttu-id="2ca01-176">Создание **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="2ca01-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="2ca01-177">Одним щелчком мыши **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="2ca01-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="2ca01-178">Нажмите клавишу **выберите папку**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-178">Press **Select Folder**.</span></span>

<span data-ttu-id="2ca01-179">По завершении Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="2ca01-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="2ca01-180">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="2ca01-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="2ca01-181">Откройте **решение Visual Studio децибел**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="2ca01-182">Если развертывание HoloLens:</span><span class="sxs-lookup"><span data-stu-id="2ca01-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="2ca01-183">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x86**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="2ca01-184">Щелкните стрелку раскрывающегося списка рядом с кнопкой на локальном компьютере и выберите **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="2ca01-185">Введите **IP-адрес устройства HoloLens** и задайте режим проверки подлинности **универсальный (незашифрованный протокол)**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="2ca01-186">Нажмите кнопку **выберите**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-186">Click **Select**.</span></span> <span data-ttu-id="2ca01-187">Если вы не знаете IP-адрес устройства, найдите в **параметры > сеть и Интернет > Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="2ca01-188">В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="2ca01-189">Если это при первом развертывании к устройству, необходимо будет [свяжите его с помощью Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="2ca01-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="2ca01-190">Если развертывание иммерсивных гарнитура:</span><span class="sxs-lookup"><span data-stu-id="2ca01-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="2ca01-191">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x64**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="2ca01-192">Убедитесь, что целевой объект развертывания присваивается **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="2ca01-193">В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="2ca01-194">Глава 2 - пространственных звук и взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2ca01-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="2ca01-195">Цели</span><span class="sxs-lookup"><span data-stu-id="2ca01-195">Objectives</span></span>

* <span data-ttu-id="2ca01-196">Повысьте реализм голограмма, с помощью звук.</span><span class="sxs-lookup"><span data-stu-id="2ca01-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="2ca01-197">Направьте взглядом пользователя, с помощью звук.</span><span class="sxs-lookup"><span data-stu-id="2ca01-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="2ca01-198">Отправка отзывов жест с помощью звук.</span><span class="sxs-lookup"><span data-stu-id="2ca01-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="2ca01-199">Часть 1 - усиления реализм</span><span class="sxs-lookup"><span data-stu-id="2ca01-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="2ca01-200">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="2ca01-200">Key Concepts</span></span>

* <span data-ttu-id="2ca01-201">Spatialize голограмма звуков.</span><span class="sxs-lookup"><span data-stu-id="2ca01-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="2ca01-202">Звуковой источников должны размещаться в соответствующем месте на голограмма.</span><span class="sxs-lookup"><span data-stu-id="2ca01-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="2ca01-203">Соответствующее расположение для звук будет зависеть голограмма.</span><span class="sxs-lookup"><span data-stu-id="2ca01-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="2ca01-204">Например если она имеет человек, звуковой источник должен находиться рядом рот и не метров.</span><span class="sxs-lookup"><span data-stu-id="2ca01-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="2ca01-205">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2ca01-205">Instructions</span></span>

<span data-ttu-id="2ca01-206">Приведенные ниже инструкции будет присоединен голограмма spatialized звука.</span><span class="sxs-lookup"><span data-stu-id="2ca01-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="2ca01-207">В **иерархии** панели, разверните узел **HologramCollection** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="2ca01-208">В **инспектор** на панели **AudioSource**, щелкните круг рядом с полем **AudioClip** и выберите **PolyHover** из всплывающего окна.</span><span class="sxs-lookup"><span data-stu-id="2ca01-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="2ca01-209">Щелкните круг рядом с полем **вывода** и выберите **SoundEffects** из всплывающего окна.</span><span class="sxs-lookup"><span data-stu-id="2ca01-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="2ca01-210">Проект децибел использует Unity **AudioMixer** компонента для включения, настройки звука для групп звуков.</span><span class="sxs-lookup"><span data-stu-id="2ca01-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="2ca01-211">Путем группирования звуки таким образом объем может регулироваться сохраняя относительный объем каждого звука.</span><span class="sxs-lookup"><span data-stu-id="2ca01-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="2ca01-212">В **AudioSource**, разверните **3D Параметры звука**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="2ca01-213">Задайте **уровень Doppler** для **0**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="2ca01-214">Установка уровня Doppler адаптации отключает в шаге шрифта, из-за перемещения (либо голограмма или пользователя).</span><span class="sxs-lookup"><span data-stu-id="2ca01-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="2ca01-215">Классическим примером Doppler является быстроменяющихся автомобиля.</span><span class="sxs-lookup"><span data-stu-id="2ca01-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="2ca01-216">По мере приближения прослушиватель стационарные автомобиль возрастает голос ядра.</span><span class="sxs-lookup"><span data-stu-id="2ca01-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="2ca01-217">При прохождении прослушиватель с расстоянием снижает высоты тона.</span><span class="sxs-lookup"><span data-stu-id="2ca01-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="2ca01-218">Часть 2. направление взглядом пользователя</span><span class="sxs-lookup"><span data-stu-id="2ca01-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="2ca01-219">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="2ca01-219">Key Concepts</span></span>

* <span data-ttu-id="2ca01-220">Использовать звуковой сигнал привлечь внимание к важным голограммы.</span><span class="sxs-lookup"><span data-stu-id="2ca01-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="2ca01-221">Уши помогают направлять, где должен выглядеть глаза.</span><span class="sxs-lookup"><span data-stu-id="2ca01-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="2ca01-222">Мозг имеет несколько известных ожиданиям.</span><span class="sxs-lookup"><span data-stu-id="2ca01-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="2ca01-223">Примером сохраненных ожидаемых является птиц обычно выше головах человека.</span><span class="sxs-lookup"><span data-stu-id="2ca01-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="2ca01-224">Если пользователь слышит bird звука, их сделает — для поиска.</span><span class="sxs-lookup"><span data-stu-id="2ca01-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="2ca01-225">Поместив «Bird» ниже пользователь может привести к их с выходом в правильном направлении звук, но не удается найти голограмма, в зависимости от исходя из предположения необходимы для поиска.</span><span class="sxs-lookup"><span data-stu-id="2ca01-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="2ca01-226">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2ca01-226">Instructions</span></span>

<span data-ttu-id="2ca01-227">Приведенные ниже инструкции включить P0LY скрыть за вас, таким образом, чтобы найти голограмма можно использовать звук.</span><span class="sxs-lookup"><span data-stu-id="2ca01-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="2ca01-228">В **иерархии** панели, выберите **диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="2ca01-229">В **инспектор** панели, найти **обработчика ввода речи**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="2ca01-230">В **обработчика ввода речи**, разверните **Go скрыть**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="2ca01-231">Изменение **ни одна из функций** для **PolyActions.GoHide**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Ключевое слово: Последовательно выберите Скрыть](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="2ca01-233">Часть 3 - жест отзывов</span><span class="sxs-lookup"><span data-stu-id="2ca01-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="2ca01-234">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="2ca01-234">Key Concepts</span></span>

* <span data-ttu-id="2ca01-235">Предоставьте пользователю подтверждения положительное жестов, с помощью звука</span><span class="sxs-lookup"><span data-stu-id="2ca01-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="2ca01-236">Не перегрузить пользователь - get слишком громкий звуки как</span><span class="sxs-lookup"><span data-stu-id="2ca01-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="2ca01-237">Слабая звуки рабочих рекомендации - не отвлечь внимание от опыта</span><span class="sxs-lookup"><span data-stu-id="2ca01-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="2ca01-238">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2ca01-238">Instructions</span></span>

* <span data-ttu-id="2ca01-239">В **иерархии** панели, разверните узел **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="2ca01-240">Разверните **EnergyHub** и выберите **базы**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="2ca01-241">В **инспектор** панели, щелкните **добавить компонент** и добавьте **обработчика жестов звук**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="2ca01-242">В **обработчика жестов звук**, щелкните круг рядом с полем **коллекции к работе навигации** и **клипов обновлены навигации** и выберите **RotateClick**из всплывающего окна для обоих.</span><span class="sxs-lookup"><span data-stu-id="2ca01-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="2ca01-243">Дважды щелкните «GestureSoundHandler» загрузить в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ca01-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="2ca01-244">Обработчик жестов звук выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="2ca01-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="2ca01-245">Создание и настройка **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="2ca01-246">Место **AudioSource** в папке соответствующего **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="2ca01-247">Воспроизводит **AudioClip** связанный с данным жестом.</span><span class="sxs-lookup"><span data-stu-id="2ca01-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="2ca01-248">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="2ca01-248">Build and Deploy</span></span>

1. <span data-ttu-id="2ca01-249">В Unity, выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="2ca01-250">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-250">Click **Build**.</span></span>
3. <span data-ttu-id="2ca01-251">Одним щелчком мыши **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="2ca01-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="2ca01-252">Нажмите клавишу **выберите папку**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-252">Press **Select Folder**.</span></span>

<span data-ttu-id="2ca01-253">Проверьте, что панели инструментов указано «Выпуск», «x 86"или «x64" и «Удаленное устройство».</span><span class="sxs-lookup"><span data-stu-id="2ca01-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="2ca01-254">В противном случае это кодирования экземпляра Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ca01-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="2ca01-255">Может потребоваться повторно открыть решение из папки приложения.</span><span class="sxs-lookup"><span data-stu-id="2ca01-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="2ca01-256">При появлении соответствующего запроса, перезагрузите файлы проекта.</span><span class="sxs-lookup"><span data-stu-id="2ca01-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="2ca01-257">Как и ранее развертывание из Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ca01-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="2ca01-258">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="2ca01-258">After the application is deployed:</span></span>

* <span data-ttu-id="2ca01-259">Обратите внимание, как звук изменяется при перемещении курсора P0LY.</span><span class="sxs-lookup"><span data-stu-id="2ca01-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="2ca01-260">Скажем *«Go скрытие»* вносить P0LY переместить в расположение за вас.</span><span class="sxs-lookup"><span data-stu-id="2ca01-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="2ca01-261">Найдите его с помощью звукового сигнала.</span><span class="sxs-lookup"><span data-stu-id="2ca01-261">Find it by the sound.</span></span>
* <span data-ttu-id="2ca01-262">Помощи в нижней части концентратора энергии.</span><span class="sxs-lookup"><span data-stu-id="2ca01-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="2ca01-263">Коснитесь и перетащите влево или вправо для вращения голограмма и обратите внимание на то, каким образом звук щелчка подтверждает жест.</span><span class="sxs-lookup"><span data-stu-id="2ca01-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="2ca01-264">Примечание. Нет текста панель, в которой будет tag-along с вами.</span><span class="sxs-lookup"><span data-stu-id="2ca01-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="2ca01-265">Оно будет содержать доступные голосовые команды, которые можно использовать на протяжении данного курса.</span><span class="sxs-lookup"><span data-stu-id="2ca01-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="2ca01-266">Глава 3 - пространственное сопоставление звука и пространственных</span><span class="sxs-lookup"><span data-stu-id="2ca01-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="2ca01-267">Цели</span><span class="sxs-lookup"><span data-stu-id="2ca01-267">Objectives</span></span>

* <span data-ttu-id="2ca01-268">Подтвердите взаимодействие между голограммы и реальным миром, используя звук.</span><span class="sxs-lookup"><span data-stu-id="2ca01-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="2ca01-269">Скрывать звук с использованием физического мира.</span><span class="sxs-lookup"><span data-stu-id="2ca01-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="2ca01-270">Часть 1 — взаимодействие физического мира</span><span class="sxs-lookup"><span data-stu-id="2ca01-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="2ca01-271">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="2ca01-271">Key Concepts</span></span>

* <span data-ttu-id="2ca01-272">Физические объекты обычно звуковой сигнал при обнаружении рабочую область или другого объекта.</span><span class="sxs-lookup"><span data-stu-id="2ca01-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="2ca01-273">Звук должен быть контекста, соответствующего в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="2ca01-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="2ca01-274">Например Настройка чашку таблицы следует звуковой сигнал тише чем удаление Боулдер на часть исходного состояния системы.</span><span class="sxs-lookup"><span data-stu-id="2ca01-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="2ca01-275">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2ca01-275">Instructions</span></span>

* <span data-ttu-id="2ca01-276">В **иерархии** панели, разверните узел **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="2ca01-277">Разверните **EnergyHub**выберите **базы**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="2ca01-278">В **инспектор** панели, щелкните **добавить компонент** и добавьте **коснитесь на месте с звук и действие**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="2ca01-279">В **коснитесь, чтобы универсальный инструмент с звук и действие**:</span><span class="sxs-lookup"><span data-stu-id="2ca01-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="2ca01-280">Проверьте **снабдить родительского Tap**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="2ca01-281">Задайте **звук размещения** для **месте**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="2ca01-282">Задайте **звук Pickup** для **Pickup**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="2ca01-283">Нажмите + в нижнем прямо под оба **на действие отправки** и **на действие размещения**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="2ca01-284">Перетащите из сцены в EnergyHub **None (объект)** поля.</span><span class="sxs-lookup"><span data-stu-id="2ca01-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="2ca01-285">В разделе **на действие отправки**, щелкните **функции нет** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="2ca01-286">В разделе **на действие размещения**, щелкните **функции нет** -> **EnergyHubBase** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Коснитесь, чтобы универсальный инструмент с звук и действия](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="2ca01-288">Часть 2 - звуковой перекрытия</span><span class="sxs-lookup"><span data-stu-id="2ca01-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="2ca01-289">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="2ca01-289">Key Concepts</span></span>

* <span data-ttu-id="2ca01-290">Звук, например, свет, может быть перекрыто.</span><span class="sxs-lookup"><span data-stu-id="2ca01-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="2ca01-291">Классический пример — concert hall.</span><span class="sxs-lookup"><span data-stu-id="2ca01-291">A classic example is a concert hall.</span></span> <span data-ttu-id="2ca01-292">Когда прослушиватель основано за пределами компании и дверь закрыта, звуки музыкальных muffled.</span><span class="sxs-lookup"><span data-stu-id="2ca01-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="2ca01-293">Также обычно наблюдается уменьшение объема.</span><span class="sxs-lookup"><span data-stu-id="2ca01-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="2ca01-294">Когда дверь открыта, полный спектр звук воспроизводится фактического объема.</span><span class="sxs-lookup"><span data-stu-id="2ca01-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="2ca01-295">Обычно являются более низких частот поглощает звуков с высокой частотой.</span><span class="sxs-lookup"><span data-stu-id="2ca01-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="2ca01-296">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2ca01-296">Instructions</span></span>

* <span data-ttu-id="2ca01-297">В **иерархии** панели, разверните узел **HologramCollection** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="2ca01-298">В **инспектор** панели, щелкните **добавить компонент** и добавьте **передатчика аудио**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="2ca01-299">Класс передатчика аудио предоставляет следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="2ca01-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="2ca01-300">Восстанавливает все изменения на объем **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="2ca01-301">Выполняет **Physics.RaycastNonAlloc** от положения пользователя в направлении **GameObject** к которому **AudioEmitter** подключен.</span><span class="sxs-lookup"><span data-stu-id="2ca01-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="2ca01-302">Метод RaycastNonAlloc используется в качестве оптимизации производительности для ограничения распределения, а также количество возвращаемых результатов.</span><span class="sxs-lookup"><span data-stu-id="2ca01-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="2ca01-303">Для каждого **IAudioInfluencer** обнаружил вызовы **ApplyEffect** метод.</span><span class="sxs-lookup"><span data-stu-id="2ca01-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="2ca01-304">Для каждого предыдущего **IAudioInfluencer** то есть больше не обнаружены, вызов **RemoveEffect** метод.</span><span class="sxs-lookup"><span data-stu-id="2ca01-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="2ca01-305">Обратите внимание на то, что AudioEmitter обновления в масштабах человека скоростью, в отличие от каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="2ca01-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="2ca01-306">Это делается потому, что люди обычно не перемещать достаточно быстро для эффект, должны обновляться чаще, чем раз в квартал или половины секунды.</span><span class="sxs-lookup"><span data-stu-id="2ca01-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="2ca01-307">Голограммы, teleport быстро из одного расположения в другое может нарушить работу иллюзию.</span><span class="sxs-lookup"><span data-stu-id="2ca01-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="2ca01-308">В **иерархии** панели, разверните узел **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="2ca01-309">Разверните **EnergyHub** и выберите **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="2ca01-310">В **инспектор** панели, щелкните **добавить компонент** и добавьте **Occluder аудио**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="2ca01-311">В **Occluder аудио**, задайте **Частота сканирования** для **1500**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="2ca01-312">Этот параметр ограничивает число частоты AudioSource до 1500 Гц и ниже.</span><span class="sxs-lookup"><span data-stu-id="2ca01-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="2ca01-313">Задайте **тома проход** для **0.9**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="2ca01-314">Этот параметр позволяет уменьшить объем AudioSource 90 процентов от текущего уровня.</span><span class="sxs-lookup"><span data-stu-id="2ca01-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="2ca01-315">Аудио Occluder реализует IAudioInfluencer для:</span><span class="sxs-lookup"><span data-stu-id="2ca01-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="2ca01-316">Применить эффект проверки видимости с помощью **AudioLowPassFilter** который вкладывается в **AudioSource** управляемых купить **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="2ca01-317">Тома затухания применяется к AudioSource.</span><span class="sxs-lookup"><span data-stu-id="2ca01-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="2ca01-318">Отключает эффект, задавая нейтральный частоту среза и отключение фильтра.</span><span class="sxs-lookup"><span data-stu-id="2ca01-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="2ca01-319">Используется в качестве нейтрального частота — 22 кГц (22000 Гц).</span><span class="sxs-lookup"><span data-stu-id="2ca01-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="2ca01-320">Эту частоту был выбран, поскольку они находятся выше Номинальное максимальное частоту, с которой можно прослушивать по Человеческое ухо, делая не заметно влияет звука.</span><span class="sxs-lookup"><span data-stu-id="2ca01-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="2ca01-321">В **иерархии** панели, выберите **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="2ca01-322">В **инспектор** панели, щелкните **добавить компонент** и добавьте **Occluder аудио**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="2ca01-323">В **Occluder аудио**, задайте **Частота сканирования** для **750**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="2ca01-324">Когда несколько occluders находятся в пути между пользователем и **AudioEmitter**, наименьшее частота применяется фильтр.</span><span class="sxs-lookup"><span data-stu-id="2ca01-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="2ca01-325">Задайте **тома проход** для **0,75**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="2ca01-326">Когда несколько occluders находятся в пути между пользователем и **AudioEmitter**, аддитивно применяется сквозной тома.</span><span class="sxs-lookup"><span data-stu-id="2ca01-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="2ca01-327">В **иерархии** панели, выберите **диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="2ca01-328">В **инспектор** панели, разверните узел **обработчика ввода речи**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="2ca01-329">В **обработчика ввода речи**, разверните **Go плата**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="2ca01-330">Изменение **ни одна из функций** для **PolyActions.GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Ключевое слово: Go плата](images/gocharge.png)

* <span data-ttu-id="2ca01-332">Разверните **здесь**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="2ca01-333">Изменение **ни одна из функций** для **PolyActions.ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Ключевое слово: Иди сюда](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="2ca01-335">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="2ca01-335">Build and Deploy</span></span>

* <span data-ttu-id="2ca01-336">Как и раньше постройте проект в Unity и развертывание в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ca01-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="2ca01-337">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="2ca01-337">After the application is deployed:</span></span>

* <span data-ttu-id="2ca01-338">Скажем *«Go плата»* иметь P0LY введите центр энергии.</span><span class="sxs-lookup"><span data-stu-id="2ca01-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="2ca01-339">Обратите внимание на изменения в звук.</span><span class="sxs-lookup"><span data-stu-id="2ca01-339">Note the change in the sound.</span></span> <span data-ttu-id="2ca01-340">Это должно показаться muffled и немного тише.</span><span class="sxs-lookup"><span data-stu-id="2ca01-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="2ca01-341">Если представление себя с стене или другого объекта между вами и центр энергии, можно заметить, дальнейшие muffling звука из-за их перекрытия в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="2ca01-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="2ca01-342">Скажем *«Поступать Here»* иметь P0LY оставьте концентратора энергии и располагаться перед глазами.</span><span class="sxs-lookup"><span data-stu-id="2ca01-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="2ca01-343">Обратите внимание на то, что звуковой перекрытия удаляется после P0LY выходит из центра энергии.</span><span class="sxs-lookup"><span data-stu-id="2ca01-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="2ca01-344">Если вы по-прежнему перекрытия вашим отзывам, P0LY может перекрыто в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="2ca01-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="2ca01-345">Попробуйте переместить, чтобы убедиться, что у вас есть четкое напрямую обращаться к P0LY.</span><span class="sxs-lookup"><span data-stu-id="2ca01-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="2ca01-346">Часть 3 - систем</span><span class="sxs-lookup"><span data-stu-id="2ca01-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="2ca01-347">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="2ca01-347">Key Concepts</span></span>

* <span data-ttu-id="2ca01-348">Размер пространства предоставляет гипнотическая очередей, способствующих звуковой локализации.</span><span class="sxs-lookup"><span data-stu-id="2ca01-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="2ca01-349">Комнаты моделей задаются для каждого-**AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="2ca01-350">[MixedRealityToolkit для Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) предоставляет код для задания места модели.</span><span class="sxs-lookup"><span data-stu-id="2ca01-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="2ca01-351">Для работы в смешанной реальности выберите модель комнаты, которая лучше всего соответствует пространства реального мира.</span><span class="sxs-lookup"><span data-stu-id="2ca01-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="2ca01-352">При создании сценария виртуальной реальности, выберите модель комнаты, которая лучше всего соответствует виртуальной среды.</span><span class="sxs-lookup"><span data-stu-id="2ca01-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="2ca01-353">Глава 4 – систему</span><span class="sxs-lookup"><span data-stu-id="2ca01-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="2ca01-354">Цели</span><span class="sxs-lookup"><span data-stu-id="2ca01-354">Objectives</span></span>

* <span data-ttu-id="2ca01-355">Общие рекомендации по для эффективной звуковой схемы.</span><span class="sxs-lookup"><span data-stu-id="2ca01-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="2ca01-356">Узнайте, смешивая методики и рекомендации.</span><span class="sxs-lookup"><span data-stu-id="2ca01-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="2ca01-357">Часть 1 — звук и проектирование взаимодействия</span><span class="sxs-lookup"><span data-stu-id="2ca01-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="2ca01-358">В этом разделе рассматриваются ключевые звук и рекомендации по проектированию опыт и рекомендации.</span><span class="sxs-lookup"><span data-stu-id="2ca01-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="2ca01-359">Нормализовать все звуки</span><span class="sxs-lookup"><span data-stu-id="2ca01-359">Normalize all sounds</span></span>

<span data-ttu-id="2ca01-360">Это устраняет потребность в специальных вариантов кода уровней громкости в звук колокольчика, который может занять много времени и ограничивает возможность легко обновить звуковые файлы.</span><span class="sxs-lookup"><span data-stu-id="2ca01-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="2ca01-361">Проектирование неограниченными возможностями, которые взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2ca01-361">Design for an untethered experience</span></span>

<span data-ttu-id="2ca01-362">HoloLens — это полностью автономной, неограниченными возможностями, которые holographic компьютер.</span><span class="sxs-lookup"><span data-stu-id="2ca01-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="2ca01-363">Пользователи могут и будут использовать своим опытом, во время перемещения.</span><span class="sxs-lookup"><span data-stu-id="2ca01-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="2ca01-364">Убедитесь, что ваш аудио наборе тестов путем прохода по.</span><span class="sxs-lookup"><span data-stu-id="2ca01-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="2ca01-365">Выдавать звука из логических расположения на вашей голограммы</span><span class="sxs-lookup"><span data-stu-id="2ca01-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="2ca01-366">В реальном мире dog не bark из его заключительного и голос человека он поступил не из его/ее метров.</span><span class="sxs-lookup"><span data-stu-id="2ca01-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="2ca01-367">Не выдавать звуков из Непредвиденная части вашего голограммы.</span><span class="sxs-lookup"><span data-stu-id="2ca01-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="2ca01-368">Для небольших голограммы разумно звук выпуска в центре геометрии.</span><span class="sxs-lookup"><span data-stu-id="2ca01-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="2ca01-369">Знакомые звуки доступны для наиболее локализации</span><span class="sxs-lookup"><span data-stu-id="2ca01-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="2ca01-370">Человеческий голос и музыки очень просты в локализации.</span><span class="sxs-lookup"><span data-stu-id="2ca01-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="2ca01-371">Если кто-то ваше имя, вы сможете очень точно определить, какие направление документации голоса и как далеко.</span><span class="sxs-lookup"><span data-stu-id="2ca01-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="2ca01-372">Короткое, незнакомой звуки довольно сложно локализировать.</span><span class="sxs-lookup"><span data-stu-id="2ca01-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="2ca01-373">Иметь представление о ожиданиям пользователей</span><span class="sxs-lookup"><span data-stu-id="2ca01-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="2ca01-374">Качества жизни играет роль в наши возможности для определения расположения звука.</span><span class="sxs-lookup"><span data-stu-id="2ca01-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="2ca01-375">Это одна из причин, почему человеческий голос особенно легко локализовать.</span><span class="sxs-lookup"><span data-stu-id="2ca01-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="2ca01-376">Это важно учитывать полученные ожиданий пользователей, при помещении звуков.</span><span class="sxs-lookup"><span data-stu-id="2ca01-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="2ca01-377">Например когда кто-то слышит песни bird обычно поиск, как обычно птиц над прямой видимости (находящиеся в полете или в дереве).</span><span class="sxs-lookup"><span data-stu-id="2ca01-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="2ca01-378">Пользователь может включить в правильном направлении звука, но загляните в неправильный вертикальном направлении и стать путать или разочарованы, если им не удается найти голограмма нередко.</span><span class="sxs-lookup"><span data-stu-id="2ca01-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="2ca01-379">Избежать скрытых отправители</span><span class="sxs-lookup"><span data-stu-id="2ca01-379">Avoid hidden emitters</span></span>

<span data-ttu-id="2ca01-380">На практике Если мы слышим звука, мы обычно позволяет определить объект, выдающей звук.</span><span class="sxs-lookup"><span data-stu-id="2ca01-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="2ca01-381">Это также должен содержать значение true в своем опыте работы.</span><span class="sxs-lookup"><span data-stu-id="2ca01-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="2ca01-382">Его можно, манипулируя пользователи могли слышать, знаете, из которого исходят эти звук и он не сможет отобразить объект.</span><span class="sxs-lookup"><span data-stu-id="2ca01-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="2ca01-383">Существуют некоторые исключения этой рекомендации.</span><span class="sxs-lookup"><span data-stu-id="2ca01-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="2ca01-384">Например внешней звуки, такие как crickets в поле, не обязательно видимыми.</span><span class="sxs-lookup"><span data-stu-id="2ca01-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="2ca01-385">Качества жизни дает нам знание источника эти звуки, без необходимости см. в разделе, его.</span><span class="sxs-lookup"><span data-stu-id="2ca01-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="2ca01-386">Часть 2 - микширования</span><span class="sxs-lookup"><span data-stu-id="2ca01-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="2ca01-387">Предназначенных для вашего набора для 70% томе HoloLens</span><span class="sxs-lookup"><span data-stu-id="2ca01-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="2ca01-388">Смешанной реальности возможности позволяют голограммы возникают в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="2ca01-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="2ca01-389">Они также должны предусматривать реальные звуки прослушивания.</span><span class="sxs-lookup"><span data-stu-id="2ca01-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="2ca01-390">Целевой том 70% позволяет пользователю услышать мира их и воспроизведение звука работы.</span><span class="sxs-lookup"><span data-stu-id="2ca01-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="2ca01-391">HoloLens 100% объема следует поток out внешних звуков</span><span class="sxs-lookup"><span data-stu-id="2ca01-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="2ca01-392">Уровень громкости 100% является наименьшей интерфейс виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="2ca01-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="2ca01-393">Визуально он переносится мир.</span><span class="sxs-lookup"><span data-stu-id="2ca01-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="2ca01-394">Также должны выполняться, что необходимо воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="2ca01-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="2ca01-395">Используется для настройки категорий звуков Unity AudioMixer</span><span class="sxs-lookup"><span data-stu-id="2ca01-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="2ca01-396">При разработке на mix, часто бывает полезно для создания звукового категорий и имеют возможность увеличения или уменьшения их том как единое.</span><span class="sxs-lookup"><span data-stu-id="2ca01-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="2ca01-397">Это действие сохранит масштаб каждого звука при включении быстро и легко изменения общего сочетания.</span><span class="sxs-lookup"><span data-stu-id="2ca01-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="2ca01-398">Включать общие категории. звуковые эффекты, окружением, бросков голосовой и фоновую музыку.</span><span class="sxs-lookup"><span data-stu-id="2ca01-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="2ca01-399">Смешивать звуков, в зависимости от пользователя взглядом</span><span class="sxs-lookup"><span data-stu-id="2ca01-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="2ca01-400">Часто бывает полезно изменить звуковые набор взаимодействие о том, где пользователь является (или не) поиск.</span><span class="sxs-lookup"><span data-stu-id="2ca01-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="2ca01-401">Часто применяются в рамках этого способа являются уменьшить уровень volume для голограммы, которые находятся вне Holographic кадра, чтобы упростить пользователям сосредоточиться на информации перед их.</span><span class="sxs-lookup"><span data-stu-id="2ca01-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="2ca01-402">Другой используется для увеличения громкости звука для привлечения внимания пользователя к важное событие.</span><span class="sxs-lookup"><span data-stu-id="2ca01-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="2ca01-403">Построение состав профиля</span><span class="sxs-lookup"><span data-stu-id="2ca01-403">Building your mix</span></span>

<span data-ttu-id="2ca01-404">При создании вашего набора, рекомендуется фоновое воспроизведение аудиофайлов ваш опыт и добавить слои, в зависимости от важности.</span><span class="sxs-lookup"><span data-stu-id="2ca01-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="2ca01-405">Часто в результате каждого слоя, громче по сравнению с предыдущим.</span><span class="sxs-lookup"><span data-stu-id="2ca01-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="2ca01-406">Описывая состав профиля как инвертированный Воронка, с наименее важных (и обычно тихие звуки) внизу, рекомендуется для структурирования вашего mix, аналогичную следующей схеме.</span><span class="sxs-lookup"><span data-stu-id="2ca01-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Структура звуковой mix](images/soundlevels.png)

<span data-ttu-id="2ca01-408">Бросков Voice — это интересный случай.</span><span class="sxs-lookup"><span data-stu-id="2ca01-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="2ca01-409">На основе на работу, вы создаете вы можете стереозвук (не локализованный) или spatialize бросков ваш голос.</span><span class="sxs-lookup"><span data-stu-id="2ca01-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="2ca01-410">Два Корпорация Майкрософт опубликовала опыт проиллюстрировать отличными примерами каждого сценария.</span><span class="sxs-lookup"><span data-stu-id="2ca01-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="2ca01-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) использует стерео голос по.</span><span class="sxs-lookup"><span data-stu-id="2ca01-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="2ca01-412">Когда экранного диктора описывает расположение просматривается, звук согласовано, а не различаются в зависимости от положения пользователя.</span><span class="sxs-lookup"><span data-stu-id="2ca01-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="2ca01-413">Это позволяет экранного диктора для описания сцены без ведения от spatialized звуки среды.</span><span class="sxs-lookup"><span data-stu-id="2ca01-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="2ca01-414">[Фрагменты](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) использует spatialized голос по в виде детективов.</span><span class="sxs-lookup"><span data-stu-id="2ca01-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="2ca01-415">Голосовые детектива используется позволяют вернуть внимание пользователя к важным говорит о том, как если бы был фактический человека в комнате.</span><span class="sxs-lookup"><span data-stu-id="2ca01-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="2ca01-416">Это позволяет еще больше смысла погружения в интерфейс решения тайну.</span><span class="sxs-lookup"><span data-stu-id="2ca01-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="2ca01-417">Часть 3 - производительности</span><span class="sxs-lookup"><span data-stu-id="2ca01-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="2ca01-418">Использование ЦП</span><span class="sxs-lookup"><span data-stu-id="2ca01-418">CPU usage</span></span>

<span data-ttu-id="2ca01-419">При использовании пространственный звук, отправители 10-12 будет составлять примерно 12% ресурсов ЦП.</span><span class="sxs-lookup"><span data-stu-id="2ca01-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="2ca01-420">Stream долго звуковые файлы</span><span class="sxs-lookup"><span data-stu-id="2ca01-420">Stream long audio files</span></span>

<span data-ttu-id="2ca01-421">Аудиоданные могут быть большими, особенно на общих частоты выборки (кГц 44,1 и 48).</span><span class="sxs-lookup"><span data-stu-id="2ca01-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="2ca01-422">Общее правило таково, что звуковые файлы, более 5 – 10 секунд должен передаваться в сократить использование памяти приложения.</span><span class="sxs-lookup"><span data-stu-id="2ca01-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="2ca01-423">В Unity можно пометить звуковой файл для потоковой передачи в параметры импорта файла.</span><span class="sxs-lookup"><span data-stu-id="2ca01-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Параметры импорта звуковых](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="2ca01-425">Глава 5 - специальные эффекты</span><span class="sxs-lookup"><span data-stu-id="2ca01-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="2ca01-426">Цели</span><span class="sxs-lookup"><span data-stu-id="2ca01-426">Objectives</span></span>

* <span data-ttu-id="2ca01-427">Добавьте «Magic Windows» глубина.</span><span class="sxs-lookup"><span data-stu-id="2ca01-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="2ca01-428">Пользователя можно открыть в виртуальный мир.</span><span class="sxs-lookup"><span data-stu-id="2ca01-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="2ca01-429">Magic Windows</span><span class="sxs-lookup"><span data-stu-id="2ca01-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="2ca01-430">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="2ca01-430">Key Concepts</span></span>

* <span data-ttu-id="2ca01-431">Создание представлений в скрытый мир, — визуально привлекательные.</span><span class="sxs-lookup"><span data-stu-id="2ca01-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="2ca01-432">Улучшить реализм, добавив звуковые эффекты, когда голограмма или пользователь приближается к скрытым всему миру.</span><span class="sxs-lookup"><span data-stu-id="2ca01-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="2ca01-433">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2ca01-433">Instructions</span></span>

* <span data-ttu-id="2ca01-434">В **иерархии** панели, разверните узел **HologramCollection** и выберите **Underworld**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="2ca01-435">Разверните **Underworld** и выберите **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="2ca01-436">В **инспектор** панели, щелкните **добавить компонент** и добавьте **эффект голос пользователя**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="2ca01-437">**AudioSource** добавляется компонент **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="2ca01-438">В **AudioSource**, задайте **вывода** для **UserVoice (Mixer)**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="2ca01-439">Проверьте **Spatialize** флажок.</span><span class="sxs-lookup"><span data-stu-id="2ca01-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="2ca01-440">Перетащите **пространственных Blend** ползунок вплоть до **3D**, или введите **1** в поле ввода.</span><span class="sxs-lookup"><span data-stu-id="2ca01-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="2ca01-441">Разверните **3D Параметры звука**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="2ca01-442">Задайте **уровень Doppler** для **0**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="2ca01-443">В **эффект голос пользователя**, задайте **родительский объект** для **Underworld** из сцены.</span><span class="sxs-lookup"><span data-stu-id="2ca01-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="2ca01-444">Задайте **максимальное расстояние** для **1**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="2ca01-445">Установка **максимальное расстояние** сообщает **эффект голос пользователя** как близко пользователь должен быть к родительскому объекту до включения эффекта.</span><span class="sxs-lookup"><span data-stu-id="2ca01-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="2ca01-446">В **эффект голос пользователя**, разверните **параметры горячее**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="2ca01-447">Задайте **глубина** для **0,1**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="2ca01-448">Задайте **коснитесь один том**, **коснитесь 2 тома** и **коснитесь 3 тома** для **0,8**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="2ca01-449">Задайте **исходный Громкость** для **0,5**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="2ca01-450">Предыдущие параметры настройки параметров Unity **AudioChorusFilter** используется для добавления пути расширения возможностей голосовой связи.</span><span class="sxs-lookup"><span data-stu-id="2ca01-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="2ca01-451">В **эффект голос пользователя**, разверните **Echo параметры**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="2ca01-452">Задайте **задержка** для **300**</span><span class="sxs-lookup"><span data-stu-id="2ca01-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="2ca01-453">Задайте **Decay соотношение** для **0,2**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="2ca01-454">Задайте **исходный Громкость** для **0**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="2ca01-455">Предыдущие параметры настройки параметров Unity **AudioEchoFilter** использован голос пользователя для обратной передачи.</span><span class="sxs-lookup"><span data-stu-id="2ca01-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="2ca01-456">Скрипт эффект голос пользователя отвечает за:</span><span class="sxs-lookup"><span data-stu-id="2ca01-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="2ca01-457">Измерение расстояния между пользователем и **GameObject** к которому присоединена скрипт.</span><span class="sxs-lookup"><span data-stu-id="2ca01-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="2ca01-458">Определить, имеются ли пользователь **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="2ca01-459">Пользователь должен с выходом GameObject, независимо от расстояния для эффекта, который требуется включить.</span><span class="sxs-lookup"><span data-stu-id="2ca01-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="2ca01-460">Применение и настройка **AudioChorusFilter** и **AudioEchoFilter** для **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="2ca01-461">Отключение эффекта, отключив фильтры.</span><span class="sxs-lookup"><span data-stu-id="2ca01-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="2ca01-462">Эффект голос пользователя использует компонент селектор Stream Mic из [MixedRealityToolkit для Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), чтобы выбрать поток высокое качество голосовой и направить ее в аудио система Unity.</span><span class="sxs-lookup"><span data-stu-id="2ca01-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="2ca01-463">В **иерархии** панели, выберите **диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="2ca01-464">В **инспектор** панели, разверните узел **обработчика ввода речи**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="2ca01-465">В **обработчика ввода речи**, разверните **Показать Underworld**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="2ca01-466">Изменение **ни одна из функций** для **UnderworldBase.OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Ключевое слово: Показать Underworld](images/showunderworld.png)

* <span data-ttu-id="2ca01-468">Разверните **скрыть Underworld**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="2ca01-469">Изменение **ни одна из функций** для **UnderworldBase.OnDisable**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Ключевое слово: Скрыть Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="2ca01-471">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="2ca01-471">Build and Deploy</span></span>

* <span data-ttu-id="2ca01-472">Как и раньше постройте проект в Unity и развертывание в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ca01-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="2ca01-473">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="2ca01-473">After the application is deployed:</span></span>

* <span data-ttu-id="2ca01-474">Лиц поверхности (по часам, floor, таблицы) и say *«Показать Underworld»*.</span><span class="sxs-lookup"><span data-stu-id="2ca01-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="2ca01-475">Underworld будет отображаться, и все другие голограммы будут скрыты.</span><span class="sxs-lookup"><span data-stu-id="2ca01-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="2ca01-476">Если вы не видите underworld, убедитесь, что, с которыми сталкиваются поверхность реального мира.</span><span class="sxs-lookup"><span data-stu-id="2ca01-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="2ca01-477">Подход в пределах 1 метра от underworld голограмма и начать разговор.</span><span class="sxs-lookup"><span data-stu-id="2ca01-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="2ca01-478">Теперь есть звуковые эффекты применены к свой голос!</span><span class="sxs-lookup"><span data-stu-id="2ca01-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="2ca01-479">Откажутся от underworld и обратите внимание на то, как больше не применяется эффект.</span><span class="sxs-lookup"><span data-stu-id="2ca01-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="2ca01-480">Скажем *«Скрыть Underworld»* скрыть underworld.</span><span class="sxs-lookup"><span data-stu-id="2ca01-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="2ca01-481">Underworld будут скрыты и ранее скрытые голограммы появится на экране.</span><span class="sxs-lookup"><span data-stu-id="2ca01-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="2ca01-482">Конец</span><span class="sxs-lookup"><span data-stu-id="2ca01-482">The End</span></span>

<span data-ttu-id="2ca01-483">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="2ca01-483">Congratulations!</span></span> <span data-ttu-id="2ca01-484">Вы завершили **пространственных 220 MR: Пространственные звук**.</span><span class="sxs-lookup"><span data-stu-id="2ca01-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="2ca01-485">Ожидать передачи всему миру и Оживите своим опытом со звуком!</span><span class="sxs-lookup"><span data-stu-id="2ca01-485">Listen to the world and bring your experiences to life with sound!</span></span>
