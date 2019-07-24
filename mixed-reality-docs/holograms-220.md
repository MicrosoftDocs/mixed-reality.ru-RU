---
title: Пространственный 220 — Пространственный звук
description: Выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы узнать о концепциях пространственных звуков.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, Academy, учебник, Пространственный звук
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526910"
---
>[!NOTE]
><span data-ttu-id="cd58c-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="cd58c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="cd58c-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="cd58c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="cd58c-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cd58c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="cd58c-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="cd58c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="cd58c-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cd58c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="cd58c-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="cd58c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="cd58c-110">Индекс MR 220: Пространственное звучание</span><span class="sxs-lookup"><span data-stu-id="cd58c-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="cd58c-111">[Пространственный звук](spatial-sound.md) бреасес в голограммы и дает им присутствие в нашей жизни.</span><span class="sxs-lookup"><span data-stu-id="cd58c-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="cd58c-112">Голограммы состоят из светлого и звукового, и если вы не сможете понять, что вы видите голограммы, Пространственный звук поможет вам найти их.</span><span class="sxs-lookup"><span data-stu-id="cd58c-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="cd58c-113">Пространственный звук не похож на типичный звук, который вы услышите на Радио, это звук, расположенный в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="cd58c-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="cd58c-114">Благодаря пространственному звучанию голограммы могут выглядеть так, как они находятся за вами, рядом с вами или даже на головном компьютере.</span><span class="sxs-lookup"><span data-stu-id="cd58c-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="cd58c-115">В этом курсе будут:</span><span class="sxs-lookup"><span data-stu-id="cd58c-115">In this course, you will:</span></span>

* <span data-ttu-id="cd58c-116">Настройка среды разработки для использования пространственного звука Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="cd58c-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="cd58c-117">Используйте Пространственный звук для улучшения взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="cd58c-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="cd58c-118">Использование пространственного звука в сочетании с пространственным сопоставлением.</span><span class="sxs-lookup"><span data-stu-id="cd58c-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="cd58c-119">Общие сведения о проектировании звука и смешении рекомендаций.</span><span class="sxs-lookup"><span data-stu-id="cd58c-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="cd58c-120">Используйте звук для улучшения специальных эффектов и перенесите пользователя в мир смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="cd58c-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="cd58c-121">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="cd58c-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="cd58c-122">Хождение</span><span class="sxs-lookup"><span data-stu-id="cd58c-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="cd58c-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="cd58c-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="cd58c-124"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="cd58c-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="cd58c-125">Индекс MR 220: Пространственное звучание</span><span class="sxs-lookup"><span data-stu-id="cd58c-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="cd58c-126">✔️</span><span class="sxs-lookup"><span data-stu-id="cd58c-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="cd58c-127">✔️</span><span class="sxs-lookup"><span data-stu-id="cd58c-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="cd58c-128">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="cd58c-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="cd58c-129">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="cd58c-129">Prerequisites</span></span>

* <span data-ttu-id="cd58c-130">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="cd58c-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="cd58c-131">Некоторые базовые C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="cd58c-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="cd58c-132">Вы должны были выполнить [Основные сведения о MR 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="cd58c-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="cd58c-133">Устройство HoloLens, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="cd58c-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="cd58c-134">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="cd58c-134">Project files</span></span>

* <span data-ttu-id="cd58c-135">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="cd58c-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="cd58c-136"> Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="cd58c-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="cd58c-137">Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="cd58c-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="cd58c-138">Этот выпуск может больше не быть обновлен.</span><span class="sxs-lookup"><span data-stu-id="cd58c-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="cd58c-139">Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="cd58c-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="cd58c-140"> Этот выпуск может больше не быть обновлен.</span><span class="sxs-lookup"><span data-stu-id="cd58c-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="cd58c-141">Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="cd58c-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="cd58c-142"> Этот выпуск может больше не быть обновлен.</span><span class="sxs-lookup"><span data-stu-id="cd58c-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="cd58c-143">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="cd58c-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="cd58c-144">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="cd58c-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="cd58c-145">Ошибки и примечания</span><span class="sxs-lookup"><span data-stu-id="cd58c-145">Errata and Notes</span></span>

* <span data-ttu-id="cd58c-146">Параметр "Enable Только мой код" должен быть отключен (*снят*) в Visual Studio в разделе "сервис-> Параметры" — > Отладка для попадания в код точек останова в коде.</span><span class="sxs-lookup"><span data-stu-id="cd58c-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="cd58c-147">Глава 1. Установка Unity</span><span class="sxs-lookup"><span data-stu-id="cd58c-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="cd58c-148">Цели</span><span class="sxs-lookup"><span data-stu-id="cd58c-148">Objectives</span></span>

* <span data-ttu-id="cd58c-149">Измените конфигурацию звука Unity, чтобы использовать пространственный звук Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="cd58c-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="cd58c-150">Добавьте трехмерный звук в объект в Unity.</span><span class="sxs-lookup"><span data-stu-id="cd58c-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="cd58c-151">Инструкция</span><span class="sxs-lookup"><span data-stu-id="cd58c-151">Instructions</span></span>

* <span data-ttu-id="cd58c-152">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="cd58c-152">Start Unity.</span></span>
* <span data-ttu-id="cd58c-153">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-153">Select **Open**.</span></span>
* <span data-ttu-id="cd58c-154">Перейдите к рабочему столу и найдите папку, для которой был отменен Архив.</span><span class="sxs-lookup"><span data-stu-id="cd58c-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="cd58c-155">Щелкните папку **стартинг\деЦибел** , а затем нажмите кнопку **Выбор папки** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="cd58c-156">Дождитесь загрузки проекта в Unity.</span><span class="sxs-lookup"><span data-stu-id="cd58c-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="cd58c-157">На панели **проект** откройте **сценес\деЦибел.Унити**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="cd58c-158">На панели **Иерархия** разверните узел **Холограмколлектион** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="cd58c-159">В инспекторе разверните узел **аудиосаурце** и обратите внимание, что флажок **спатиализе** не установлен.</span><span class="sxs-lookup"><span data-stu-id="cd58c-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="cd58c-160">По умолчанию Unity не загружает подключаемый модуль спатиализер.</span><span class="sxs-lookup"><span data-stu-id="cd58c-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="cd58c-161">Следующие шаги позволят включить Пространственный звук в проекте.</span><span class="sxs-lookup"><span data-stu-id="cd58c-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="cd58c-162">В верхней части меню Unity выберите **правка > параметры проекта > аудио**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="cd58c-163">Найдите раскрывающийся список **подключаемого модуля спатиализер** и выберите **MS хртф спатиализер**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="cd58c-164">На панели **Иерархия** выберите **холограмколлектион > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="cd58c-165">На панели **инспектора** найдите компонент **источник аудио** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="cd58c-166">Установите флажок **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="cd58c-167">Перетащите ползунок **пространственного смешения** на **3D**или введите **1** в поле ввода.</span><span class="sxs-lookup"><span data-stu-id="cd58c-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="cd58c-168">Теперь создадим проект в Unity и настроим решение в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd58c-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="cd58c-169">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="cd58c-170">Щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="cd58c-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="cd58c-171">Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="cd58c-172">Если вы специально разрабатываете для HoloLens, задайте для параметра **целевое устройство** значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="cd58c-173">В противном случае оставьте его на **любом устройстве**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="cd58c-174">Убедитесь, что для **типа сборки** задано значение **D3D** и **пакет SDK** установлен в значение " **Последняя установленная версия** " (это должен быть пакет SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="cd58c-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="cd58c-175">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-175">Click **Build**.</span></span>
7. <span data-ttu-id="cd58c-176">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="cd58c-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="cd58c-177">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="cd58c-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="cd58c-178">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-178">Press **Select Folder**.</span></span>

<span data-ttu-id="cd58c-179">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="cd58c-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="cd58c-180">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="cd58c-181">Откройте **решение шкала Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="cd58c-182">При развертывании в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="cd58c-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="cd58c-183">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="cd58c-184">Щелкните стрелку раскрывающегося списка рядом с кнопкой локальный компьютер и выберите **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="cd58c-185">Введите **IP-адрес устройства HoloLens** и задайте для режима проверки подлинности значение **универсальный (незашифрованный протокол)** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="cd58c-186">Нажмите кнопку **выбрать**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-186">Click **Select**.</span></span> <span data-ttu-id="cd58c-187">Если вы не узнаете IP-адрес устройства, проверьте **параметры > сеть & интернет > дополнительные параметры**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="cd58c-188">В верхней строке меню щелкните Отладка **-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="cd58c-189">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="cd58c-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="cd58c-190">При развертывании на иммерсивное головной телефон:</span><span class="sxs-lookup"><span data-stu-id="cd58c-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="cd58c-191">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="cd58c-192">Убедитесь, что для целевого объекта развертывания задано значение **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="cd58c-193">В верхней строке меню щелкните Отладка **-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="cd58c-194">Глава 2 — Пространственный звук и взаимодействие</span><span class="sxs-lookup"><span data-stu-id="cd58c-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="cd58c-195">Цели</span><span class="sxs-lookup"><span data-stu-id="cd58c-195">Objectives</span></span>

* <span data-ttu-id="cd58c-196">Улучшайте реальную голограмму с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="cd58c-197">Направление взгляда пользователя с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="cd58c-198">Обеспечение обратной связи с жестами с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="cd58c-199">Часть 1. улучшение режима реального времени</span><span class="sxs-lookup"><span data-stu-id="cd58c-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cd58c-200">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="cd58c-200">Key Concepts</span></span>

* <span data-ttu-id="cd58c-201">Спатиализе голограммы.</span><span class="sxs-lookup"><span data-stu-id="cd58c-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="cd58c-202">Звуковые источники должны размещаться в соответствующем месте на голограмме.</span><span class="sxs-lookup"><span data-stu-id="cd58c-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="cd58c-203">Соответствующее расположение звука зависит от голограммы.</span><span class="sxs-lookup"><span data-stu-id="cd58c-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="cd58c-204">Например, если голограмма является человеком, то источник звука должен располагаться рядом с рот, а не с ножками.</span><span class="sxs-lookup"><span data-stu-id="cd58c-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cd58c-205">Инструкция</span><span class="sxs-lookup"><span data-stu-id="cd58c-205">Instructions</span></span>

<span data-ttu-id="cd58c-206">Приведенные ниже инструкции присоединяют Пространственный звук к голограмме.</span><span class="sxs-lookup"><span data-stu-id="cd58c-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="cd58c-207">На панели **Иерархия** разверните узел **Холограмколлектион** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="cd58c-208">На панели **инспектора** в **аудиосаурце**щелкните окружность рядом с элементом **аудиоклип** и выберите пункт с помощью **мыши** в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="cd58c-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="cd58c-209">Щелкните окружность рядом с элементом **выходные данные** и выберите **саундеффектс** во всплывающем окне.</span><span class="sxs-lookup"><span data-stu-id="cd58c-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="cd58c-210">В Project шкала используется компонент **Аудиомиксер** Unity, позволяющий настраивать уровни звука для групп звуков.</span><span class="sxs-lookup"><span data-stu-id="cd58c-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="cd58c-211">Группируя звуки таким образом, можно настроить общий том, сохраняя относительный объем каждого звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="cd58c-212">В **аудиосаурце**разверните **Параметры трехмерного звука**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="cd58c-213">Задайте для **уровня Doppler** значение **0**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="cd58c-214">Если установить для уровня Doppler значение 0, изменения в пошаговом режиме переопределяются движением (какой-либо голограммой или пользователем).</span><span class="sxs-lookup"><span data-stu-id="cd58c-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="cd58c-215">Классический пример Doppler — это быстрый автомобиль.</span><span class="sxs-lookup"><span data-stu-id="cd58c-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="cd58c-216">Когда автомобиль приближается к стационарному прослушивателю, его шаг растет.</span><span class="sxs-lookup"><span data-stu-id="cd58c-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="cd58c-217">Когда прослушиватель проходит, шаг уменьшается на расстояние.</span><span class="sxs-lookup"><span data-stu-id="cd58c-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="cd58c-218">Часть 2. Направление взгляда пользователя</span><span class="sxs-lookup"><span data-stu-id="cd58c-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cd58c-219">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="cd58c-219">Key Concepts</span></span>

* <span data-ttu-id="cd58c-220">Используйте звук для привлечения внимания к важным голограммам.</span><span class="sxs-lookup"><span data-stu-id="cd58c-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="cd58c-221">Ушки помогает непосредственно искать глаза.</span><span class="sxs-lookup"><span data-stu-id="cd58c-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="cd58c-222">Мозг имеет некоторые полученные ожидания.</span><span class="sxs-lookup"><span data-stu-id="cd58c-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="cd58c-223">Одним из примеров полученных ожиданий является то, что птиц обычно находится над головами людей.</span><span class="sxs-lookup"><span data-stu-id="cd58c-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="cd58c-224">Если пользователь слышит звук с высоты птичьего полета, его первоначальная реакция заключается в поиске.</span><span class="sxs-lookup"><span data-stu-id="cd58c-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="cd58c-225">Размещение высоты под пользователем может привести к тому, что они будут направлены на правильное направление звука, но не смогут найти голограмму в зависимости от того, что нужно найти.</span><span class="sxs-lookup"><span data-stu-id="cd58c-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cd58c-226">Инструкция</span><span class="sxs-lookup"><span data-stu-id="cd58c-226">Instructions</span></span>

<span data-ttu-id="cd58c-227">Следующие инструкции позволяют P0LY скрываться за вас, чтобы можно было использовать звук для нахождение голограммы.</span><span class="sxs-lookup"><span data-stu-id="cd58c-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="cd58c-228">На панели **Иерархия** выберите **Диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="cd58c-229">На панели **инспектора** найдите **обработчик речевого ввода**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="cd58c-230">В **обработчике речевого ввода**разверните узел **Скрыть**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="cd58c-231">Не изменяйте **функцию** на **действия с гохиде**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![This Скрыть](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="cd58c-233">Часть 3. Обратная связь по жестам</span><span class="sxs-lookup"><span data-stu-id="cd58c-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cd58c-234">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="cd58c-234">Key Concepts</span></span>

* <span data-ttu-id="cd58c-235">Предоставление пользователю положительного подтверждения жеста с помощью звука</span><span class="sxs-lookup"><span data-stu-id="cd58c-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="cd58c-236">Не перегружать пользователей с помощью звуковых эффектов</span><span class="sxs-lookup"><span data-stu-id="cd58c-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="cd58c-237">Небольшие звуки работают наилучшим образом — не конфликтовали опыт работы</span><span class="sxs-lookup"><span data-stu-id="cd58c-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="cd58c-238">Инструкция</span><span class="sxs-lookup"><span data-stu-id="cd58c-238">Instructions</span></span>

* <span data-ttu-id="cd58c-239">На панели **Иерархия** разверните узел **холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="cd58c-240">Разверните узел **енергихуб** и выберите **базовый**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="cd58c-241">На панели **инспектора** щелкните **Добавить компонент** и добавить **обработчик звука жестов**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="cd58c-242">В **обработчике звука жеста**щелкните окружность рядом с элементом **Навигация начатый** клип и **Навигация обновленный клип** , а затем в раскрывающемся списке выберите **ротатекликк** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="cd58c-243">Дважды щелкните "Жестуресаундхандлер", чтобы загрузить в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd58c-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="cd58c-244">Обработчик звука жестов выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="cd58c-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="cd58c-245">Создание и настройка **аудиосаурце**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="cd58c-246">Поместите **аудиосаурце** в расположение соответствующего **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="cd58c-247">Воспроизводит **аудиоклип** , связанный с жестом.</span><span class="sxs-lookup"><span data-stu-id="cd58c-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="cd58c-248">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="cd58c-248">Build and Deploy</span></span>

1. <span data-ttu-id="cd58c-249">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="cd58c-250">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-250">Click **Build**.</span></span>
3. <span data-ttu-id="cd58c-251">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="cd58c-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="cd58c-252">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-252">Press **Select Folder**.</span></span>

<span data-ttu-id="cd58c-253">Убедитесь, что на панели инструментов указано "выпуск", "x86" или "x64", а также "удаленное устройство".</span><span class="sxs-lookup"><span data-stu-id="cd58c-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="cd58c-254">Если нет, это экземпляр кода Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd58c-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="cd58c-255">Возможно, потребуется повторно открыть решение из папки приложения.</span><span class="sxs-lookup"><span data-stu-id="cd58c-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="cd58c-256">При появлении запроса перезагрузите файлы проекта.</span><span class="sxs-lookup"><span data-stu-id="cd58c-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="cd58c-257">Как и ранее, выполните развертывание из Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd58c-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="cd58c-258">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="cd58c-258">After the application is deployed:</span></span>

* <span data-ttu-id="cd58c-259">Посмотрите, как изменяется звук при перемещении вокруг P0LY.</span><span class="sxs-lookup"><span data-stu-id="cd58c-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="cd58c-260">Скажите *«Скрыть»* , чтобы P0LY переместиться в нужное место.</span><span class="sxs-lookup"><span data-stu-id="cd58c-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="cd58c-261">Найдите его по звуковому сигналу.</span><span class="sxs-lookup"><span data-stu-id="cd58c-261">Find it by the sound.</span></span>
* <span data-ttu-id="cd58c-262">Взгляните на основу концентратора энергии.</span><span class="sxs-lookup"><span data-stu-id="cd58c-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="cd58c-263">Нажмите и перетащите влево или вправо, чтобы повернуть голограмму, и обратите внимание на то, как щелчок звука подтверждает жест.</span><span class="sxs-lookup"><span data-stu-id="cd58c-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="cd58c-264">Примечание. Есть панель текста, которая будет помечаться вместе с вами.</span><span class="sxs-lookup"><span data-stu-id="cd58c-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="cd58c-265">В этом курсе будут содержаться доступные голоса команды, которые можно использовать в рамках этого курса.</span><span class="sxs-lookup"><span data-stu-id="cd58c-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="cd58c-266">Глава 3 — Пространственный звук и пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="cd58c-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="cd58c-267">Цели</span><span class="sxs-lookup"><span data-stu-id="cd58c-267">Objectives</span></span>

* <span data-ttu-id="cd58c-268">Проверьте взаимодействие между голограммами и реальным миром с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="cd58c-269">Окклуде звук с помощью физического мира.</span><span class="sxs-lookup"><span data-stu-id="cd58c-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="cd58c-270">Часть 1. взаимодействие физического мира</span><span class="sxs-lookup"><span data-stu-id="cd58c-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cd58c-271">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="cd58c-271">Key Concepts</span></span>

* <span data-ttu-id="cd58c-272">Физические объекты обычно выявляются звуком при обнаружении поверхности или другого объекта.</span><span class="sxs-lookup"><span data-stu-id="cd58c-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="cd58c-273">Звук должен соответствовать контексту в рамках интерфейса.</span><span class="sxs-lookup"><span data-stu-id="cd58c-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="cd58c-274">Например, при настройке кружка в таблице должен быть скрыт звуковой сигнал, чем удаление Баулдер на куске металла.</span><span class="sxs-lookup"><span data-stu-id="cd58c-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cd58c-275">Инструкция</span><span class="sxs-lookup"><span data-stu-id="cd58c-275">Instructions</span></span>

* <span data-ttu-id="cd58c-276">На панели **Иерархия** разверните узел **холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="cd58c-277">Разверните узел **енергихуб**, выберите **базовый**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="cd58c-278">На панели **инспектора** щелкните **Добавить компонент** и добавить касание, **чтобы поместить звук и действие**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="cd58c-279">**Коснитесь, чтобы поместить звук и действие**:</span><span class="sxs-lookup"><span data-stu-id="cd58c-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="cd58c-280">Установите флажок " **родительский элемент" для TAP**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="cd58c-281">Задание звукового сопровождения **для** **размещения** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="cd58c-282">Установка **звука подбора** для **отправки**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="cd58c-283">Нажмите кнопку + в правом нижнем углу в разделе **действие отправки** и **действие при размещении**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="cd58c-284">Перетащите Енергихуб из сцены в поля **нет (объект)** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="cd58c-285">В разделе **действие при отправке**щелкните **нет функции** -> **енергихуббасе** -> **ресетаниматион**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="cd58c-286">В разделе **действие при размещении**щелкните **нет функции** -> **енергихуббасе** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Коснитесь, чтобы поместить звук и действие](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="cd58c-288">Часть 2. звук перекрытия</span><span class="sxs-lookup"><span data-stu-id="cd58c-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cd58c-289">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="cd58c-289">Key Concepts</span></span>

* <span data-ttu-id="cd58c-290">Звук, как и Light, может быть перекрыто.</span><span class="sxs-lookup"><span data-stu-id="cd58c-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="cd58c-291">Классический пример — это концертный зал.</span><span class="sxs-lookup"><span data-stu-id="cd58c-291">A classic example is a concert hall.</span></span> <span data-ttu-id="cd58c-292">Если прослушиватель находится за пределами зал, а дверца закрыта, музыка звучит муффлед.</span><span class="sxs-lookup"><span data-stu-id="cd58c-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="cd58c-293">Также обычно уменьшается объем тома.</span><span class="sxs-lookup"><span data-stu-id="cd58c-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="cd58c-294">Когда дверца открыта, весь спектр звуковых значений будет слышен на самом томе.</span><span class="sxs-lookup"><span data-stu-id="cd58c-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="cd58c-295">Обычно звуки с высокой частотой обрабатываются более низкой частотой.</span><span class="sxs-lookup"><span data-stu-id="cd58c-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cd58c-296">Инструкция</span><span class="sxs-lookup"><span data-stu-id="cd58c-296">Instructions</span></span>

* <span data-ttu-id="cd58c-297">На панели **Иерархия** разверните узел **Холограмколлектион** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="cd58c-298">На панели **инспектора** щелкните **Добавить компонент** и добавить **аудио передатчик**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="cd58c-299">Класс аудио передатчика предоставляет следующие возможности.</span><span class="sxs-lookup"><span data-stu-id="cd58c-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="cd58c-300">Восстанавливает все изменения в томе **аудиосаурце**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="cd58c-301">Выполняет объект **физик. райкастноналлок** из расположения пользователя в направлении **GameObject** , к которому присоединена **аудиоемиттер** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="cd58c-302">Метод Райкастноналлок используется в качестве оптимизации производительности для ограничения распределения, а также количества возвращаемых результатов.</span><span class="sxs-lookup"><span data-stu-id="cd58c-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="cd58c-303">Для каждого обнаруженного **иаудиоинфлуенцер** вызывает метод **апплеффект** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="cd58c-304">Для всех предыдущих **иаудиоинфлуенцер** , которые больше не встречаются, вызовите метод **ремовиффект** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="cd58c-305">Обратите внимание, что Аудиоемиттер обновляет шкалы времени, а не на основе каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="cd58c-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="cd58c-306">Это делается потому, что люди обычно не перемещаются достаточно быстро, чтобы их обновление выполнялось чаще, чем каждый квартал или половина секунды.</span><span class="sxs-lookup"><span data-stu-id="cd58c-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="cd58c-307">Голограммы, которые можно быстро телепортируйтесь из одного места в другое, могут привести к нарушению иллюзии.</span><span class="sxs-lookup"><span data-stu-id="cd58c-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="cd58c-308">На панели **Иерархия** разверните узел **холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="cd58c-309">Разверните узел **енергихуб** и выберите **блобаутсиде**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="cd58c-310">На панели **инспектора** щелкните **Добавить компонент** и добавить **Audio окклудер**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="cd58c-311">В **Audio окклудер**задайте для параметра **частота отсечки** значение **1500**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="cd58c-312">Этот параметр ограничивает частоту Аудиосаурце до 1500 Гц и ниже.</span><span class="sxs-lookup"><span data-stu-id="cd58c-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="cd58c-313">Задайте для параметра **Volume сквозное** значение **0,9**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="cd58c-314">Этот параметр сокращает объем Аудиосаурце до 90% от текущего уровня.</span><span class="sxs-lookup"><span data-stu-id="cd58c-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="cd58c-315">Audio Окклудер реализует Иаудиоинфлуенцер для:</span><span class="sxs-lookup"><span data-stu-id="cd58c-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="cd58c-316">Примените перекрытияный результат с помощью **аудиоловпассфилтер** , который подключается к **Аудиосаурце** управления купить **аудиоемиттер**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="cd58c-317">Применяет ослабление громкости к Аудиосаурце.</span><span class="sxs-lookup"><span data-stu-id="cd58c-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="cd58c-318">Отключает действие, устанавливая независимую частоту отсечки и отключая фильтр.</span><span class="sxs-lookup"><span data-stu-id="cd58c-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="cd58c-319">Частота, используемая как нейтральная, — 22 кГц (22000 Гц).</span><span class="sxs-lookup"><span data-stu-id="cd58c-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="cd58c-320">Эта частота была выбрана по причине превышения номинальной максимальной частоты, которая может быть продолжена от человеческого звучания, что не повлияет на звук.</span><span class="sxs-lookup"><span data-stu-id="cd58c-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="cd58c-321">На панели **Иерархия** выберите **спатиалмаппинг**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="cd58c-322">На панели **инспектора** щелкните **Добавить компонент** и добавить **Audio окклудер**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="cd58c-323">В **Audio окклудер**задайте для параметра **частота отсечки** значение **750**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="cd58c-324">Если между пользователем и **аудиоемиттер**находится несколько окклудерс, к фильтру применяется самая низкая частота.</span><span class="sxs-lookup"><span data-stu-id="cd58c-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="cd58c-325">Задайте для параметра **Volume сквозное** значение **0,75**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="cd58c-326">Если в пути между пользователем и **аудиоемиттер**находится несколько окклудерс, то этот том применяется аддитивно.</span><span class="sxs-lookup"><span data-stu-id="cd58c-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="cd58c-327">На панели **Иерархия** выберите **Диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="cd58c-328">На панели **инспектора** разверните **обработчик речевого ввода**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="cd58c-329">В **обработчике речевого ввода**раскройте раздел **плата за**начисление.</span><span class="sxs-lookup"><span data-stu-id="cd58c-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="cd58c-330">Не изменяйте **функцию** на **действия с гочарже**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![This Взимать плату](images/gocharge.png)

* <span data-ttu-id="cd58c-332">Разверните **здесь**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="cd58c-333">Не изменяйте **функцию** на **действия с комебакк**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![This Иди сюда](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="cd58c-335">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="cd58c-335">Build and Deploy</span></span>

* <span data-ttu-id="cd58c-336">Как и ранее, создайте проект в Unity и разверните его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd58c-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="cd58c-337">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="cd58c-337">After the application is deployed:</span></span>

* <span data-ttu-id="cd58c-338">Скажите *«выставить плату»* , чтобы у P0LY был вход в центр энергии.</span><span class="sxs-lookup"><span data-stu-id="cd58c-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="cd58c-339">Обратите внимание на изменение звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-339">Note the change in the sound.</span></span> <span data-ttu-id="cd58c-340">Он должен звучит муффлед и немного тихо.</span><span class="sxs-lookup"><span data-stu-id="cd58c-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="cd58c-341">Если вы можете разместить себя на стене или другом объекте между вами и концентратором энергии, вы должны заметить еще один муффлинг звука из-за перекрытия в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="cd58c-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="cd58c-342">Скажем, *"Приходите сюда"* , чтобы P0LY не выходить из концентратора энергии и располагать его в начале работы.</span><span class="sxs-lookup"><span data-stu-id="cd58c-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="cd58c-343">Обратите внимание, что звуковой перекрытия удаляется после того, как P0LY выходит из концентратора энергии.</span><span class="sxs-lookup"><span data-stu-id="cd58c-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="cd58c-344">Если вы по-прежнему слышите перекрытия, P0LY может быть перекрыто в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="cd58c-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="cd58c-345">Попробуйте переместить, чтобы убедиться, что у вас есть четкое представление о P0LY.</span><span class="sxs-lookup"><span data-stu-id="cd58c-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="cd58c-346">Часть 3. модели комнаты</span><span class="sxs-lookup"><span data-stu-id="cd58c-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cd58c-347">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="cd58c-347">Key Concepts</span></span>

* <span data-ttu-id="cd58c-348">Размер пространства предоставляет очереди сублиминал, которые способствуют локализации звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="cd58c-349">Модели комнаты задаются для каждого**аудиосаурце**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="cd58c-350">[Микседреалититулкит для Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) предоставляет код для настройки модели комнаты.</span><span class="sxs-lookup"><span data-stu-id="cd58c-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="cd58c-351">Для возможностей смешанной реальности выберите модель комнаты, которая лучше всего соответствует реальному пространству.</span><span class="sxs-lookup"><span data-stu-id="cd58c-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="cd58c-352">При создании сценария виртуальной реальности выберите модель комнаты, которая лучше подходит для виртуальной среды.</span><span class="sxs-lookup"><span data-stu-id="cd58c-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="cd58c-353">Глава 4. Создание звуковых эффектов</span><span class="sxs-lookup"><span data-stu-id="cd58c-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="cd58c-354">Цели</span><span class="sxs-lookup"><span data-stu-id="cd58c-354">Objectives</span></span>

* <span data-ttu-id="cd58c-355">Общие сведения о эффективной разработке звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="cd58c-356">Узнайте, как смешивать методики и рекомендации.</span><span class="sxs-lookup"><span data-stu-id="cd58c-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="cd58c-357">Часть 1. проектирование звука и опыта</span><span class="sxs-lookup"><span data-stu-id="cd58c-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="cd58c-358">В этом разделе обсуждаются ключевые моменты и рекомендации по проектированию.</span><span class="sxs-lookup"><span data-stu-id="cd58c-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="cd58c-359">Нормализовать все звуки</span><span class="sxs-lookup"><span data-stu-id="cd58c-359">Normalize all sounds</span></span>

<span data-ttu-id="cd58c-360">Это позволяет избежать необходимости в специальном коде, чтобы настроить уровень громкости для звука, что может занимать много времени и ограничивает возможность простого обновления звуковых файлов.</span><span class="sxs-lookup"><span data-stu-id="cd58c-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="cd58c-361">Проектирование для неинтерактивного интерфейса</span><span class="sxs-lookup"><span data-stu-id="cd58c-361">Design for an untethered experience</span></span>

<span data-ttu-id="cd58c-362">HoloLens — это полностью автономный компьютер с неустановленным модемом Holographic.</span><span class="sxs-lookup"><span data-stu-id="cd58c-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="cd58c-363">Ваши пользователи могут и будут использовать ваши возможности во время перемещения.</span><span class="sxs-lookup"><span data-stu-id="cd58c-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="cd58c-364">Не забудьте протестировать звуковой микшер, прополнив обход.</span><span class="sxs-lookup"><span data-stu-id="cd58c-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="cd58c-365">Выдавать звук из логических расположений на голограммах</span><span class="sxs-lookup"><span data-stu-id="cd58c-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="cd58c-366">В реальной жизни собака не лай от своего заключительного фрагмента, а речь не поступает из своих метров.</span><span class="sxs-lookup"><span data-stu-id="cd58c-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="cd58c-367">Старайтесь не создавать звуки на основе непредвиденных частей голограмм.</span><span class="sxs-lookup"><span data-stu-id="cd58c-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="cd58c-368">Для небольших голограмм целесообразно, чтобы звук выдавался из центра геометрии.</span><span class="sxs-lookup"><span data-stu-id="cd58c-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="cd58c-369">Привычные звуки являются наиболее подлежат локализации</span><span class="sxs-lookup"><span data-stu-id="cd58c-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="cd58c-370">Возможность локализации с человеческого голоса и музыки очень проста.</span><span class="sxs-lookup"><span data-stu-id="cd58c-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="cd58c-371">Если кто-то вызывает ваше имя, вы сможете точно определить, откуда поступило направление голоса и с какого края.</span><span class="sxs-lookup"><span data-stu-id="cd58c-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="cd58c-372">Короткие, неизвестные звуки сложнее локализовать.</span><span class="sxs-lookup"><span data-stu-id="cd58c-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="cd58c-373">Компания cognizant ожидания пользователей</span><span class="sxs-lookup"><span data-stu-id="cd58c-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="cd58c-374">Жизненный цикл играет определенную часть в возможности определения местоположения звука.</span><span class="sxs-lookup"><span data-stu-id="cd58c-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="cd58c-375">Это одна из причин, по которой человеческий разговор особенно прост в локализации.</span><span class="sxs-lookup"><span data-stu-id="cd58c-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="cd58c-376">При помещении звуков важно помнить о предполагаемых изменениях пользователя.</span><span class="sxs-lookup"><span data-stu-id="cd58c-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="cd58c-377">Например, когда кто-то слышит песню с заполнением, обычно они ищутся, так как птиц, как правило, находится над линией (перелетаем или в дереве).</span><span class="sxs-lookup"><span data-stu-id="cd58c-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="cd58c-378">Нередко пользователь может включить правильное направление звука, но взгляните на неправильное вертикальное направление и не будет путать или разочаровано, если не удается найти голограмму.</span><span class="sxs-lookup"><span data-stu-id="cd58c-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="cd58c-379">Избегайте скрытых передатчиков</span><span class="sxs-lookup"><span data-stu-id="cd58c-379">Avoid hidden emitters</span></span>

<span data-ttu-id="cd58c-380">В реальной жизни, если мы слышите звук, можно, как правило, найти объект, который порождает звук.</span><span class="sxs-lookup"><span data-stu-id="cd58c-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="cd58c-381">Это также должно иметь значение true в своих впечатлениях.</span><span class="sxs-lookup"><span data-stu-id="cd58c-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="cd58c-382">Это может быть очень неудобно для пользователей услышать звук, знать, откуда поступает звук и не удается увидеть объект.</span><span class="sxs-lookup"><span data-stu-id="cd58c-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="cd58c-383">В этой рекомендации есть некоторые исключения.</span><span class="sxs-lookup"><span data-stu-id="cd58c-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="cd58c-384">Например, окружающие звуки, такие как криккетс в поле, не должны быть видимыми.</span><span class="sxs-lookup"><span data-stu-id="cd58c-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="cd58c-385">Жизненный цикл позволяет нам ознакомиться с источником этих звуков без необходимости его просмотра.</span><span class="sxs-lookup"><span data-stu-id="cd58c-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="cd58c-386">Часть 2. Микширование звука</span><span class="sxs-lookup"><span data-stu-id="cd58c-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="cd58c-387">Нацеливание на микшер для тома 70% на HoloLens</span><span class="sxs-lookup"><span data-stu-id="cd58c-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="cd58c-388">Опыт работы в смешанной реальности позволяет видеть голограммы в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="cd58c-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="cd58c-389">Они также должны позволять слышать реальные звуки.</span><span class="sxs-lookup"><span data-stu-id="cd58c-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="cd58c-390">Целевой объект тома 70% позволяет пользователю слышать мир по всему миру, а также звуковое сопровождение.</span><span class="sxs-lookup"><span data-stu-id="cd58c-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="cd58c-391">На диске HoloLens на 100% Volume должны Drown внешние звуки</span><span class="sxs-lookup"><span data-stu-id="cd58c-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="cd58c-392">Уровень громкости 100% связан с возможностями виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="cd58c-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="cd58c-393">Визуально пользователь переносится в другой мир.</span><span class="sxs-lookup"><span data-stu-id="cd58c-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="cd58c-394">То же самое должно содержаться в значении true воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="cd58c-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="cd58c-395">Настройка категорий звуков с помощью Unity Аудиомиксер</span><span class="sxs-lookup"><span data-stu-id="cd58c-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="cd58c-396">При проектировании Mix часто бывает полезно создавать категории звуковых сигналов и иметь возможность увеличивать или уменьшать объем тома как единое целое.</span><span class="sxs-lookup"><span data-stu-id="cd58c-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="cd58c-397">Это позволяет хранить относительные уровни каждого звука, одновременно позволяя быстро и легко вносить изменения в общий набор.</span><span class="sxs-lookup"><span data-stu-id="cd58c-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="cd58c-398">К общим категориям относятся: звуковые эффекты, окружение, голосовое переработка и фоновая музыка.</span><span class="sxs-lookup"><span data-stu-id="cd58c-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="cd58c-399">Смешивание звуков на основе взгляда пользователя</span><span class="sxs-lookup"><span data-stu-id="cd58c-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="cd58c-400">Часто может оказаться полезным изменить звуковой микшер в зависимости от того, где находится пользователь (или нет).</span><span class="sxs-lookup"><span data-stu-id="cd58c-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="cd58c-401">Одним из распространенных способов использования этой методики является уменьшение уровня громкости для голограмм, находящихся за пределами holographic, чтобы облегчить пользователю сосредоточиться на информации перед ними.</span><span class="sxs-lookup"><span data-stu-id="cd58c-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="cd58c-402">Другой способ — увеличить громкость звука, чтобы привлечь внимание пользователя к важному событию.</span><span class="sxs-lookup"><span data-stu-id="cd58c-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="cd58c-403">Создание набора</span><span class="sxs-lookup"><span data-stu-id="cd58c-403">Building your mix</span></span>

<span data-ttu-id="cd58c-404">При создании сочетания рекомендуется начать с фонового звука и добавить слои на основе важности.</span><span class="sxs-lookup"><span data-stu-id="cd58c-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="cd58c-405">Часто это приводит к громкости каждого слоя, отличного от предыдущего.</span><span class="sxs-lookup"><span data-stu-id="cd58c-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="cd58c-406">При мнимой комбинации в виде инвертированной воронки с наименьшим важным (и обычно тихим звуком) в нижней части рекомендуется структурировать сочетание, похожее на следующую диаграмму.</span><span class="sxs-lookup"><span data-stu-id="cd58c-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Структура звукового микшера](images/soundlevels.png)

<span data-ttu-id="cd58c-408">Наработка голоса является интересным сценарием.</span><span class="sxs-lookup"><span data-stu-id="cd58c-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="cd58c-409">В зависимости от того, что вы создаете, вам может потребоваться стерео (не локализованный) звук или спатиализе голоса.</span><span class="sxs-lookup"><span data-stu-id="cd58c-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="cd58c-410">Два опубликованных в корпорации Майкрософт опыта иллюстрируют отличные примеры каждого сценария.</span><span class="sxs-lookup"><span data-stu-id="cd58c-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="cd58c-411">[Холотаур](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) использует стерео голосовое по.</span><span class="sxs-lookup"><span data-stu-id="cd58c-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="cd58c-412">Когда экранный диктор описывает просматриваемое расположение, звук будет единообразным и не меняется в зависимости от положения пользователя.</span><span class="sxs-lookup"><span data-stu-id="cd58c-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="cd58c-413">Это позволяет экранному диктору описывать сцену, не отвлекаясь от пространственных звуков среды.</span><span class="sxs-lookup"><span data-stu-id="cd58c-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="cd58c-414">[Фрагменты](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) используют пространственный Voice в виде выявляющий.</span><span class="sxs-lookup"><span data-stu-id="cd58c-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="cd58c-415">Голосовое выявляющий используется для того, чтобы привлечь внимание пользователя к важной подсчету, как если бы реальный человек находился в комнате.</span><span class="sxs-lookup"><span data-stu-id="cd58c-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="cd58c-416">Это позволяет даже лучше понять, как погрузиться в возможности решения загадкы.</span><span class="sxs-lookup"><span data-stu-id="cd58c-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="cd58c-417">Часть 3. производительность</span><span class="sxs-lookup"><span data-stu-id="cd58c-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="cd58c-418">Загрузка ЦП</span><span class="sxs-lookup"><span data-stu-id="cd58c-418">CPU usage</span></span>

<span data-ttu-id="cd58c-419">При использовании пространственного звука 10-12 передатчиков будет потреблять примерно 12% ресурсов ЦП.</span><span class="sxs-lookup"><span data-stu-id="cd58c-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="cd58c-420">Потоковая передача длинных звуковых файлов</span><span class="sxs-lookup"><span data-stu-id="cd58c-420">Stream long audio files</span></span>

<span data-ttu-id="cd58c-421">Звуковые данные могут быть большими, особенно в общих частотах выборки (44,1 и 48 кГц).</span><span class="sxs-lookup"><span data-stu-id="cd58c-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="cd58c-422">Общее правило заключается в потоковой передаче звуковых файлов дольше 5-10 секунд, чтобы сократить использование памяти приложения.</span><span class="sxs-lookup"><span data-stu-id="cd58c-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="cd58c-423">В Unity можно пометить звуковой файл для потоковой передачи в параметрах импорта файла.</span><span class="sxs-lookup"><span data-stu-id="cd58c-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Настройки импорта звука](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="cd58c-425">Глава 5-Специальные эффекты</span><span class="sxs-lookup"><span data-stu-id="cd58c-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="cd58c-426">Цели</span><span class="sxs-lookup"><span data-stu-id="cd58c-426">Objectives</span></span>

* <span data-ttu-id="cd58c-427">Добавьте глубину в "волшебные окна".</span><span class="sxs-lookup"><span data-stu-id="cd58c-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="cd58c-428">Перенесите пользователя в виртуальный мир.</span><span class="sxs-lookup"><span data-stu-id="cd58c-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="cd58c-429">Волшебные окна</span><span class="sxs-lookup"><span data-stu-id="cd58c-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cd58c-430">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="cd58c-430">Key Concepts</span></span>

* <span data-ttu-id="cd58c-431">Создание представлений в скрытом мире является визуально привлекательным.</span><span class="sxs-lookup"><span data-stu-id="cd58c-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="cd58c-432">Улучшайте реальные последствия, добавляя звуковые эффекты, когда голограмма или пользователь находится ближе к скрытому миру.</span><span class="sxs-lookup"><span data-stu-id="cd58c-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cd58c-433">Инструкция</span><span class="sxs-lookup"><span data-stu-id="cd58c-433">Instructions</span></span>

* <span data-ttu-id="cd58c-434">На панели **Иерархия** разверните узел **холограмколлектион** и выберите пункт незаполненный **мир**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="cd58c-435">Разверните  узел "подсветка" и выберите **воицесаурце**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="cd58c-436">На панели **инспектора** щелкните **Добавить компонент** и добавить **Пользовательский речевой эффекты**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="cd58c-437">В **воицесаурце**будет добавлен компонент **аудиосаурце** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="cd58c-438">В **аудиосаурце**установите **выходные данные** в **UserVoice (микшер)** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="cd58c-439">Установите флажок **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="cd58c-440">Перетащите ползунок **пространственного смешения** на **3D**или введите **1** в поле ввода.</span><span class="sxs-lookup"><span data-stu-id="cd58c-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="cd58c-441">Разверните **Параметры трехмерного звука**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="cd58c-442">Задайте для **уровня Doppler** значение **0**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="cd58c-443">В поле **Пользовательский видеорезультат**задайте для параметра **родительский объект** значение подсветкой из сцены.</span><span class="sxs-lookup"><span data-stu-id="cd58c-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="cd58c-444">Установите **Максимальное расстояние** равным **1**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="cd58c-445">Установка параметра **Max Distance** сообщает **пользователю** о том, как закрыть пользователя к родительскому объекту до того, как будет включен этот результат.</span><span class="sxs-lookup"><span data-stu-id="cd58c-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="cd58c-446">В окне " **Пользовательский Видеорезультат**" разверните узел **Параметры чорус**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="cd58c-447">Задайте для свойства **Depth** значение **0,1**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="cd58c-448">Установите **касание тома 1**, **Коснитесь 2 тома** и **коснитесь 3 тома** на **0,8**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="cd58c-449">Установите для параметра **исходный звуковой том** значение **0,5**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="cd58c-450">Предыдущие параметры настраивают параметры **Аудиочорусфилтер** Unity, используемые для добавления богатости в речь пользователя.</span><span class="sxs-lookup"><span data-stu-id="cd58c-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="cd58c-451">В окне " **Пользовательский Видеорезультат**" разверните **Параметры Echo**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="cd58c-452">Установить **задержку** в **300**</span><span class="sxs-lookup"><span data-stu-id="cd58c-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="cd58c-453">Установите **соотношение Decay** к **0,2**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="cd58c-454">Установите **0**в качестве **исходного звукового тома** .</span><span class="sxs-lookup"><span data-stu-id="cd58c-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="cd58c-455">Предыдущие параметры настраивают параметры **Аудиоечофилтер** Unity, которые приводят к эхо голоса пользователя.</span><span class="sxs-lookup"><span data-stu-id="cd58c-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="cd58c-456">Сценарий пользовательского голоса отвечает за следующее:</span><span class="sxs-lookup"><span data-stu-id="cd58c-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="cd58c-457">Измерение расстояния между пользователем и **GameObject** , к которому присоединен скрипт.</span><span class="sxs-lookup"><span data-stu-id="cd58c-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="cd58c-458">Определение того, находится ли пользователь в **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="cd58c-459">Для включения этого действия пользователь должен быть направлен на GameObject, независимо от расстояния.</span><span class="sxs-lookup"><span data-stu-id="cd58c-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="cd58c-460">Применение и настройка **аудиочорусфилтер** и **аудиоечофилтер** для **аудиосаурце**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="cd58c-461">Отключение этого действия путем отключения фильтров.</span><span class="sxs-lookup"><span data-stu-id="cd58c-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="cd58c-462">В голосовом режиме для пользователя используется компонент выбора потока MIC из [микседреалититулкит для Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), чтобы выбрать высококачественный голосовой поток и направить его в звуковую систему Unity.</span><span class="sxs-lookup"><span data-stu-id="cd58c-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="cd58c-463">На панели **Иерархия** выберите **Диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="cd58c-464">На панели **инспектора** разверните **обработчик речевого ввода**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="cd58c-465">В **обработчике речевого ввода**разверните узел **Показывать**подсветку.</span><span class="sxs-lookup"><span data-stu-id="cd58c-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="cd58c-466">Не изменяйте **функцию** на **Ундерворлдбасе. OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![This Показывать подсветку](images/showunderworld.png)

* <span data-ttu-id="cd58c-468">Разверните узел **Скрыть**подсветку.</span><span class="sxs-lookup"><span data-stu-id="cd58c-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="cd58c-469">Не изменяйте **функцию** на **Ундерворлдбасе. ondisable**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![This Скрыть подсветку](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="cd58c-471">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="cd58c-471">Build and Deploy</span></span>

* <span data-ttu-id="cd58c-472">Как и ранее, создайте проект в Unity и разверните его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd58c-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="cd58c-473">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="cd58c-473">After the application is deployed:</span></span>

* <span data-ttu-id="cd58c-474">Лицевая поверхность (стена, этаж, таблица) и скажите *«Показывать подсветку»* .</span><span class="sxs-lookup"><span data-stu-id="cd58c-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="cd58c-475">Будет отображена подсветка, а все остальные голограммы будут скрыты.</span><span class="sxs-lookup"><span data-stu-id="cd58c-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="cd58c-476">Если вы не видите подсветку, убедитесь, что вы используете реальную поверхность.</span><span class="sxs-lookup"><span data-stu-id="cd58c-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="cd58c-477">Подход в пределах 1 индикатора немалой голограммы и начните говорить.</span><span class="sxs-lookup"><span data-stu-id="cd58c-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="cd58c-478">Теперь на ваш голос применяются звуковые эффекты!</span><span class="sxs-lookup"><span data-stu-id="cd58c-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="cd58c-479">Отключитесь от подсветки и обратите внимание на то, как это действие больше не применяется.</span><span class="sxs-lookup"><span data-stu-id="cd58c-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="cd58c-480">Скажите *«Скрыть подсветку»* , чтобы скрыть подсветку.</span><span class="sxs-lookup"><span data-stu-id="cd58c-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="cd58c-481">Подсветка будет скрыта, и ранее скрытые голограммы будут отображаться снова.</span><span class="sxs-lookup"><span data-stu-id="cd58c-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="cd58c-482">Конец</span><span class="sxs-lookup"><span data-stu-id="cd58c-482">The End</span></span>

<span data-ttu-id="cd58c-483">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="cd58c-483">Congratulations!</span></span> <span data-ttu-id="cd58c-484">Теперь вы завершили **MR 220: Пространственный звук**.</span><span class="sxs-lookup"><span data-stu-id="cd58c-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="cd58c-485">Прослушайтесь в мире и поработайте со звуком!</span><span class="sxs-lookup"><span data-stu-id="cd58c-485">Listen to the world and bring your experiences to life with sound!</span></span>
