---
title: Пространственный 220 — Пространственный звук
description: Выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы узнать о концепциях пространственных звуков.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, Academy, учебник, Пространственный звук
ms.openlocfilehash: a3fc054927d73cf9ac21f831caa4ec23875977bd
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434727"
---
>[!NOTE]
><span data-ttu-id="1e9de-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1e9de-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1e9de-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="1e9de-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1e9de-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1e9de-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1e9de-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="1e9de-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1e9de-108">Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="1e9de-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="1e9de-109">MR 220: Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="1e9de-109">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="1e9de-110">[Пространственный звук](spatial-sound.md) бреасес в голограммы и дает им присутствие в нашей жизни.</span><span class="sxs-lookup"><span data-stu-id="1e9de-110">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="1e9de-111">Голограммы состоят из светлого и звукового, и если вы не сможете понять, что вы видите голограммы, Пространственный звук поможет вам найти их.</span><span class="sxs-lookup"><span data-stu-id="1e9de-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="1e9de-112">Пространственный звук не похож на типичный звук, который вы услышите на Радио, это звук, расположенный в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="1e9de-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="1e9de-113">Благодаря пространственному звучанию голограммы могут выглядеть так, как они находятся за вами, рядом с вами или даже на головном компьютере.</span><span class="sxs-lookup"><span data-stu-id="1e9de-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="1e9de-114">В этом курсе будут:</span><span class="sxs-lookup"><span data-stu-id="1e9de-114">In this course, you will:</span></span>

* <span data-ttu-id="1e9de-115">Настройка среды разработки для использования пространственного звука Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1e9de-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="1e9de-116">Используйте Пространственный звук для улучшения взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1e9de-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="1e9de-117">Использование пространственного звука в сочетании с [пространственным сопоставлением](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="1e9de-117">Use Spatial Sound in conjunction with [Spatial Mapping](spatial-mapping.md).</span></span>
* <span data-ttu-id="1e9de-118">Общие сведения о проектировании звука и смешении рекомендаций.</span><span class="sxs-lookup"><span data-stu-id="1e9de-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="1e9de-119">Используйте звук для улучшения специальных эффектов и перенесите пользователя в мир смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1e9de-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="1e9de-120">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="1e9de-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1e9de-121">Хождение</span><span class="sxs-lookup"><span data-stu-id="1e9de-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1e9de-122"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1e9de-122"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1e9de-123"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="1e9de-123"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1e9de-124">MR 220: Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="1e9de-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="1e9de-125">✔️</span><span class="sxs-lookup"><span data-stu-id="1e9de-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1e9de-126">✔️</span><span class="sxs-lookup"><span data-stu-id="1e9de-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1e9de-127">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="1e9de-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1e9de-128">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="1e9de-128">Prerequisites</span></span>

* <span data-ttu-id="1e9de-129">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1e9de-129">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="1e9de-130">Некоторые базовые C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="1e9de-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="1e9de-131">Вы должны были выполнить [Основные сведения о MR 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="1e9de-131">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="1e9de-132">Устройство HoloLens, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="1e9de-132">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="1e9de-133">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="1e9de-133">Project files</span></span>

* <span data-ttu-id="1e9de-134">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="1e9de-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="1e9de-135"> Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="1e9de-135"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="1e9de-136">Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="1e9de-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="1e9de-137">Этот выпуск может больше не быть обновлен.</span><span class="sxs-lookup"><span data-stu-id="1e9de-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="1e9de-138">Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="1e9de-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="1e9de-139"> Этот выпуск может больше не быть обновлен.</span><span class="sxs-lookup"><span data-stu-id="1e9de-139"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="1e9de-140">Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="1e9de-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="1e9de-141"> Этот выпуск может больше не быть обновлен.</span><span class="sxs-lookup"><span data-stu-id="1e9de-141"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="1e9de-142">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="1e9de-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="1e9de-143">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="1e9de-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="1e9de-144">Ошибки и примечания</span><span class="sxs-lookup"><span data-stu-id="1e9de-144">Errata and Notes</span></span>

* <span data-ttu-id="1e9de-145">Параметр "Enable Только мой код" должен быть отключен (*снят*) в Visual Studio в разделе "сервис-> Параметры" — > Отладка для попадания в код точек останова в коде.</span><span class="sxs-lookup"><span data-stu-id="1e9de-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="1e9de-146">Глава 1. Установка Unity</span><span class="sxs-lookup"><span data-stu-id="1e9de-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="1e9de-147">Задачи</span><span class="sxs-lookup"><span data-stu-id="1e9de-147">Objectives</span></span>

* <span data-ttu-id="1e9de-148">Измените конфигурацию звука Unity, чтобы использовать пространственный звук Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1e9de-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="1e9de-149">Добавьте трехмерный звук в объект в Unity.</span><span class="sxs-lookup"><span data-stu-id="1e9de-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="1e9de-150">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1e9de-150">Instructions</span></span>

* <span data-ttu-id="1e9de-151">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="1e9de-151">Start Unity.</span></span>
* <span data-ttu-id="1e9de-152">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-152">Select **Open**.</span></span>
* <span data-ttu-id="1e9de-153">Перейдите к рабочему столу и найдите папку, для которой был отменен Архив.</span><span class="sxs-lookup"><span data-stu-id="1e9de-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="1e9de-154">Щелкните папку **стартинг\деЦибел** , а затем нажмите кнопку **Выбор папки** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="1e9de-155">Дождитесь загрузки проекта в Unity.</span><span class="sxs-lookup"><span data-stu-id="1e9de-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="1e9de-156">На панели **проект** откройте **сценес\деЦибел.Унити**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="1e9de-157">На панели **Иерархия** разверните узел **Холограмколлектион** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="1e9de-158">В инспекторе разверните узел **аудиосаурце** и обратите внимание, что флажок **спатиализе** не установлен.</span><span class="sxs-lookup"><span data-stu-id="1e9de-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="1e9de-159">По умолчанию Unity не загружает подключаемый модуль спатиализер.</span><span class="sxs-lookup"><span data-stu-id="1e9de-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="1e9de-160">Следующие шаги позволят включить Пространственный звук в проекте.</span><span class="sxs-lookup"><span data-stu-id="1e9de-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="1e9de-161">В верхней части меню Unity выберите **правка > параметры проекта > аудио**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="1e9de-162">Найдите раскрывающийся список **подключаемого модуля спатиализер** и выберите **MS хртф спатиализер**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="1e9de-163">На панели **Иерархия** выберите **холограмколлектион > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="1e9de-164">На панели **инспектора** найдите компонент **источник аудио** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="1e9de-165">Установите флажок **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="1e9de-166">Перетащите ползунок **пространственного смешения** на **3D**или введите **1** в поле ввода.</span><span class="sxs-lookup"><span data-stu-id="1e9de-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="1e9de-167">Теперь создадим проект в Unity и настроим решение в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e9de-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="1e9de-168">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="1e9de-169">Щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="1e9de-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="1e9de-170">Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="1e9de-171">Если вы специально разрабатываете для HoloLens, задайте для параметра **целевое устройство** значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="1e9de-172">В противном случае оставьте его на **любом устройстве**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="1e9de-173">Убедитесь, что для **типа сборки** задано значение **D3D** и **пакет SDK** установлен в значение " **Последняя установленная версия** " (это должен быть пакет SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="1e9de-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="1e9de-174">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-174">Click **Build**.</span></span>
7. <span data-ttu-id="1e9de-175">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="1e9de-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="1e9de-176">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="1e9de-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="1e9de-177">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-177">Press **Select Folder**.</span></span>

<span data-ttu-id="1e9de-178">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="1e9de-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="1e9de-179">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="1e9de-180">Откройте **решение шкала Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="1e9de-181">При развертывании в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="1e9de-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="1e9de-182">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="1e9de-183">Щелкните стрелку раскрывающегося списка рядом с кнопкой локальный компьютер и выберите **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="1e9de-184">Введите **IP-адрес устройства HoloLens** и задайте для режима проверки подлинности значение **универсальный (незашифрованный протокол)** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="1e9de-185">Нажмите кнопку **выбрать**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-185">Click **Select**.</span></span> <span data-ttu-id="1e9de-186">Если вы не узнаете IP-адрес устройства, проверьте **параметры > сеть & интернет > дополнительные параметры**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="1e9de-187">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="1e9de-188">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="1e9de-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="1e9de-189">При развертывании на иммерсивное головной телефон:</span><span class="sxs-lookup"><span data-stu-id="1e9de-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="1e9de-190">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="1e9de-191">Убедитесь, что для целевого объекта развертывания задано значение **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="1e9de-192">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="1e9de-193">Глава 2 — Пространственный звук и взаимодействие</span><span class="sxs-lookup"><span data-stu-id="1e9de-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="1e9de-194">Задачи</span><span class="sxs-lookup"><span data-stu-id="1e9de-194">Objectives</span></span>

* <span data-ttu-id="1e9de-195">Улучшайте реальную голограмму с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="1e9de-196">Направление взгляда пользователя с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="1e9de-197">Обеспечение обратной связи с жестами с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="1e9de-198">Часть 1. улучшение режима реального времени</span><span class="sxs-lookup"><span data-stu-id="1e9de-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1e9de-199">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="1e9de-199">Key Concepts</span></span>

* <span data-ttu-id="1e9de-200">Спатиализе голограммы.</span><span class="sxs-lookup"><span data-stu-id="1e9de-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="1e9de-201">Звуковые источники должны размещаться в соответствующем месте на голограмме.</span><span class="sxs-lookup"><span data-stu-id="1e9de-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="1e9de-202">Соответствующее расположение звука зависит от голограммы.</span><span class="sxs-lookup"><span data-stu-id="1e9de-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="1e9de-203">Например, если голограмма является человеком, то источник звука должен располагаться рядом с рот, а не с ножками.</span><span class="sxs-lookup"><span data-stu-id="1e9de-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1e9de-204">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1e9de-204">Instructions</span></span>

<span data-ttu-id="1e9de-205">Приведенные ниже инструкции присоединяют Пространственный звук к голограмме.</span><span class="sxs-lookup"><span data-stu-id="1e9de-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="1e9de-206">На панели **Иерархия** разверните узел **Холограмколлектион** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="1e9de-207">На панели **инспектора** в **аудиосаурце**щелкните окружность рядом с элементом **аудиоклип** и выберите пункт с помощью **мыши** в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="1e9de-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="1e9de-208">Щелкните окружность рядом с элементом **выходные данные** и выберите **саундеффектс** во всплывающем окне.</span><span class="sxs-lookup"><span data-stu-id="1e9de-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="1e9de-209">В Project шкала используется компонент **Аудиомиксер** Unity, позволяющий настраивать уровни звука для групп звуков.</span><span class="sxs-lookup"><span data-stu-id="1e9de-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="1e9de-210">Группируя звуки таким образом, можно настроить общий том, сохраняя относительный объем каждого звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="1e9de-211">В **аудиосаурце**разверните **Параметры трехмерного звука**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="1e9de-212">Задайте для **уровня Doppler** значение **0**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="1e9de-213">Если установить для уровня Doppler значение 0, изменения в пошаговом режиме переопределяются движением (какой-либо голограммой или пользователем).</span><span class="sxs-lookup"><span data-stu-id="1e9de-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="1e9de-214">Классический пример Doppler — это быстрый автомобиль.</span><span class="sxs-lookup"><span data-stu-id="1e9de-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="1e9de-215">Когда автомобиль приближается к стационарному прослушивателю, его шаг растет.</span><span class="sxs-lookup"><span data-stu-id="1e9de-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="1e9de-216">Когда прослушиватель проходит, шаг уменьшается на расстояние.</span><span class="sxs-lookup"><span data-stu-id="1e9de-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="1e9de-217">Часть 2. Направление взгляда пользователя</span><span class="sxs-lookup"><span data-stu-id="1e9de-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1e9de-218">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="1e9de-218">Key Concepts</span></span>

* <span data-ttu-id="1e9de-219">Используйте звук для привлечения внимания к важным голограммам.</span><span class="sxs-lookup"><span data-stu-id="1e9de-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="1e9de-220">Ушки помогает непосредственно искать глаза.</span><span class="sxs-lookup"><span data-stu-id="1e9de-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="1e9de-221">Мозг имеет некоторые полученные ожидания.</span><span class="sxs-lookup"><span data-stu-id="1e9de-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="1e9de-222">Одним из примеров полученных ожиданий является то, что птиц обычно находится над головами людей.</span><span class="sxs-lookup"><span data-stu-id="1e9de-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="1e9de-223">Если пользователь слышит звук с высоты птичьего полета, его первоначальная реакция заключается в поиске.</span><span class="sxs-lookup"><span data-stu-id="1e9de-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="1e9de-224">Размещение высоты под пользователем может привести к тому, что они будут направлены на правильное направление звука, но не смогут найти голограмму в зависимости от того, что нужно найти.</span><span class="sxs-lookup"><span data-stu-id="1e9de-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1e9de-225">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1e9de-225">Instructions</span></span>

<span data-ttu-id="1e9de-226">Следующие инструкции позволяют P0LY скрываться за вас, чтобы можно было использовать звук для нахождение голограммы.</span><span class="sxs-lookup"><span data-stu-id="1e9de-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="1e9de-227">На панели **Иерархия** выберите **Диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="1e9de-228">На панели **инспектора** найдите **обработчик речевого ввода**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="1e9de-229">В **обработчике речевого ввода**разверните узел **Скрыть**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="1e9de-230">Не изменяйте **функцию** на **действия с гохиде**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Ключевое слово: Hide](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="1e9de-232">Часть 3. Обратная связь по жестам</span><span class="sxs-lookup"><span data-stu-id="1e9de-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1e9de-233">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="1e9de-233">Key Concepts</span></span>

* <span data-ttu-id="1e9de-234">Предоставление пользователю положительного подтверждения жеста с помощью звука</span><span class="sxs-lookup"><span data-stu-id="1e9de-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="1e9de-235">Не перегружать пользователей с помощью звуковых эффектов</span><span class="sxs-lookup"><span data-stu-id="1e9de-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="1e9de-236">Небольшие звуки работают наилучшим образом — не конфликтовали опыт работы</span><span class="sxs-lookup"><span data-stu-id="1e9de-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="1e9de-237">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1e9de-237">Instructions</span></span>

* <span data-ttu-id="1e9de-238">На панели **Иерархия** разверните узел **холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="1e9de-239">Разверните узел **енергихуб** и выберите **базовый**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="1e9de-240">На панели **инспектора** щелкните **Добавить компонент** и добавить **обработчик звука жестов**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="1e9de-241">В **обработчике звука жеста**щелкните окружность рядом с элементом **Навигация начатый** клип и **Навигация обновленный клип** , а затем в раскрывающемся списке выберите **ротатекликк** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="1e9de-242">Дважды щелкните "Жестуресаундхандлер", чтобы загрузить в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e9de-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="1e9de-243">Обработчик звука жестов выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="1e9de-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="1e9de-244">Создание и настройка **аудиосаурце**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="1e9de-245">Поместите **аудиосаурце** в расположение соответствующего **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="1e9de-246">Воспроизводит **аудиоклип** , связанный с жестом.</span><span class="sxs-lookup"><span data-stu-id="1e9de-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="1e9de-247">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="1e9de-247">Build and Deploy</span></span>

1. <span data-ttu-id="1e9de-248">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="1e9de-249">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-249">Click **Build**.</span></span>
3. <span data-ttu-id="1e9de-250">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="1e9de-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="1e9de-251">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-251">Press **Select Folder**.</span></span>

<span data-ttu-id="1e9de-252">Убедитесь, что на панели инструментов указано "выпуск", "x86" или "x64", а также "удаленное устройство".</span><span class="sxs-lookup"><span data-stu-id="1e9de-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="1e9de-253">Если нет, это экземпляр кода Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e9de-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="1e9de-254">Возможно, потребуется повторно открыть решение из папки приложения.</span><span class="sxs-lookup"><span data-stu-id="1e9de-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="1e9de-255">При появлении запроса перезагрузите файлы проекта.</span><span class="sxs-lookup"><span data-stu-id="1e9de-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="1e9de-256">Как и ранее, выполните развертывание из Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e9de-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="1e9de-257">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="1e9de-257">After the application is deployed:</span></span>

* <span data-ttu-id="1e9de-258">Посмотрите, как изменяется звук при перемещении вокруг P0LY.</span><span class="sxs-lookup"><span data-stu-id="1e9de-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="1e9de-259">Скажите *«Скрыть»* , чтобы P0LY переместиться в нужное место.</span><span class="sxs-lookup"><span data-stu-id="1e9de-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="1e9de-260">Найдите его по звуковому сигналу.</span><span class="sxs-lookup"><span data-stu-id="1e9de-260">Find it by the sound.</span></span>
* <span data-ttu-id="1e9de-261">Взгляните на основу концентратора энергии.</span><span class="sxs-lookup"><span data-stu-id="1e9de-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="1e9de-262">Нажмите и перетащите влево или вправо, чтобы повернуть голограмму, и обратите внимание на то, как щелчок звука подтверждает жест.</span><span class="sxs-lookup"><span data-stu-id="1e9de-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="1e9de-263">Примечание. есть панель текста, которая будет помечаться вместе с вами.</span><span class="sxs-lookup"><span data-stu-id="1e9de-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="1e9de-264">В этом курсе будут содержаться доступные голоса команды, которые можно использовать в рамках этого курса.</span><span class="sxs-lookup"><span data-stu-id="1e9de-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="1e9de-265">Глава 3 — Пространственный звук и пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="1e9de-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="1e9de-266">Задачи</span><span class="sxs-lookup"><span data-stu-id="1e9de-266">Objectives</span></span>

* <span data-ttu-id="1e9de-267">Проверьте взаимодействие между голограммами и реальным миром с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="1e9de-268">Окклуде звук с помощью физического мира.</span><span class="sxs-lookup"><span data-stu-id="1e9de-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="1e9de-269">Часть 1. взаимодействие физического мира</span><span class="sxs-lookup"><span data-stu-id="1e9de-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1e9de-270">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="1e9de-270">Key Concepts</span></span>

* <span data-ttu-id="1e9de-271">Физические объекты обычно выявляются звуком при обнаружении поверхности или другого объекта.</span><span class="sxs-lookup"><span data-stu-id="1e9de-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="1e9de-272">Звук должен соответствовать контексту в рамках интерфейса.</span><span class="sxs-lookup"><span data-stu-id="1e9de-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="1e9de-273">Например, при настройке кружка в таблице должен быть скрыт звуковой сигнал, чем удаление Баулдер на куске металла.</span><span class="sxs-lookup"><span data-stu-id="1e9de-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1e9de-274">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1e9de-274">Instructions</span></span>

* <span data-ttu-id="1e9de-275">На панели **Иерархия** разверните узел **холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="1e9de-276">Разверните узел **енергихуб**, выберите **базовый**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="1e9de-277">На панели **инспектора** щелкните **Добавить компонент** и добавить **касание, чтобы поместить звук и действие**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="1e9de-278">**Коснитесь, чтобы поместить звук и действие**:</span><span class="sxs-lookup"><span data-stu-id="1e9de-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="1e9de-279">Установите флажок " **родительский элемент" для TAP**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="1e9de-280">Задание **звукового сопровождения** **для**размещения.</span><span class="sxs-lookup"><span data-stu-id="1e9de-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="1e9de-281">Установка **звука подбора** для **отправки**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="1e9de-282">Нажмите кнопку + в правом нижнем углу в разделе **действие отправки** и **действие при размещении**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="1e9de-283">Перетащите Енергихуб из сцены в поля **нет (объект)** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="1e9de-284">В разделе **действие при отправке**щелкните **без функции** -> **енергихуббасе** -> **ресетаниматион**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="1e9de-285">В разделе **действие при размещении**щелкните **нет функции** -> **енергихуббасе** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Коснитесь, чтобы поместить звук и действие](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="1e9de-287">Часть 2. звук перекрытия</span><span class="sxs-lookup"><span data-stu-id="1e9de-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1e9de-288">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="1e9de-288">Key Concepts</span></span>

* <span data-ttu-id="1e9de-289">Звук, как и Light, может быть перекрыто.</span><span class="sxs-lookup"><span data-stu-id="1e9de-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="1e9de-290">Классический пример — это концертный зал.</span><span class="sxs-lookup"><span data-stu-id="1e9de-290">A classic example is a concert hall.</span></span> <span data-ttu-id="1e9de-291">Если прослушиватель находится за пределами зал, а дверца закрыта, музыка звучит муффлед.</span><span class="sxs-lookup"><span data-stu-id="1e9de-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="1e9de-292">Также обычно уменьшается объем тома.</span><span class="sxs-lookup"><span data-stu-id="1e9de-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="1e9de-293">Когда дверца открыта, весь спектр звуковых значений будет слышен на самом томе.</span><span class="sxs-lookup"><span data-stu-id="1e9de-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="1e9de-294">Обычно звуки с высокой частотой обрабатываются более низкой частотой.</span><span class="sxs-lookup"><span data-stu-id="1e9de-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1e9de-295">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1e9de-295">Instructions</span></span>

* <span data-ttu-id="1e9de-296">На панели **Иерархия** разверните узел **Холограмколлектион** и выберите **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="1e9de-297">На панели **инспектора** щелкните **Добавить компонент** и добавить **аудио передатчик**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="1e9de-298">Класс аудио передатчика предоставляет следующие возможности.</span><span class="sxs-lookup"><span data-stu-id="1e9de-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="1e9de-299">Восстанавливает все изменения в томе **аудиосаурце**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="1e9de-300">Выполняет объект **физик. райкастноналлок** из расположения пользователя в направлении **GameObject** , к которому присоединена **аудиоемиттер** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="1e9de-301">Метод Райкастноналлок используется в качестве оптимизации производительности для ограничения распределения, а также количества возвращаемых результатов.</span><span class="sxs-lookup"><span data-stu-id="1e9de-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="1e9de-302">Для каждого обнаруженного **иаудиоинфлуенцер** вызывает метод **апплеффект** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="1e9de-303">Для всех предыдущих **иаудиоинфлуенцер** , которые больше не встречаются, вызовите метод **ремовиффект** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="1e9de-304">Обратите внимание, что Аудиоемиттер обновляет шкалы времени, а не на основе каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="1e9de-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="1e9de-305">Это делается потому, что люди обычно не перемещаются достаточно быстро, чтобы их обновление выполнялось чаще, чем каждый квартал или половина секунды.</span><span class="sxs-lookup"><span data-stu-id="1e9de-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="1e9de-306">Голограммы, которые можно быстро телепортируйтесь из одного места в другое, могут привести к нарушению иллюзии.</span><span class="sxs-lookup"><span data-stu-id="1e9de-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="1e9de-307">На панели **Иерархия** разверните узел **холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="1e9de-308">Разверните узел **енергихуб** и выберите **блобаутсиде**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="1e9de-309">На панели **инспектора** щелкните **Добавить компонент** и добавить **Audio окклудер**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="1e9de-310">В **Audio окклудер**задайте для параметра **частота отсечки** значение **1500**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="1e9de-311">Этот параметр ограничивает частоту Аудиосаурце до 1500 Гц и ниже.</span><span class="sxs-lookup"><span data-stu-id="1e9de-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="1e9de-312">Задайте для параметра **Volume сквозное** значение **0,9**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="1e9de-313">Этот параметр сокращает объем Аудиосаурце до 90% от текущего уровня.</span><span class="sxs-lookup"><span data-stu-id="1e9de-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="1e9de-314">Audio Окклудер реализует Иаудиоинфлуенцер для:</span><span class="sxs-lookup"><span data-stu-id="1e9de-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="1e9de-315">Примените перекрытияный результат с помощью **аудиоловпассфилтер** , который подключается к **Аудиосаурце** управления купить **аудиоемиттер**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="1e9de-316">Применяет ослабление громкости к Аудиосаурце.</span><span class="sxs-lookup"><span data-stu-id="1e9de-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="1e9de-317">Отключает действие, устанавливая независимую частоту отсечки и отключая фильтр.</span><span class="sxs-lookup"><span data-stu-id="1e9de-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="1e9de-318">Частота, используемая как нейтральная, — 22 кГц (22000 Гц).</span><span class="sxs-lookup"><span data-stu-id="1e9de-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="1e9de-319">Эта частота была выбрана по причине превышения номинальной максимальной частоты, которая может быть продолжена от человеческого звучания, что не повлияет на звук.</span><span class="sxs-lookup"><span data-stu-id="1e9de-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="1e9de-320">На панели **Иерархия** выберите **спатиалмаппинг**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="1e9de-321">На панели **инспектора** щелкните **Добавить компонент** и добавить **Audio окклудер**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="1e9de-322">В **Audio окклудер**задайте для параметра **частота отсечки** значение **750**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="1e9de-323">Если между пользователем и **аудиоемиттер**находится несколько окклудерс, к фильтру применяется самая низкая частота.</span><span class="sxs-lookup"><span data-stu-id="1e9de-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="1e9de-324">Задайте для параметра **Volume сквозное** значение **0,75**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="1e9de-325">Если в пути между пользователем и **аудиоемиттер**находится несколько окклудерс, то этот том применяется аддитивно.</span><span class="sxs-lookup"><span data-stu-id="1e9de-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="1e9de-326">На панели **Иерархия** выберите **Диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="1e9de-327">На панели **инспектора** разверните **обработчик речевого ввода**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="1e9de-328">В **обработчике речевого ввода**раскройте раздел **плата за начисление**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="1e9de-329">Не изменяйте **функцию** на **действия с гочарже**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Ключевое слово: плата за подставку](images/gocharge.png)

* <span data-ttu-id="1e9de-331">Разверните **здесь**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="1e9de-332">Не изменяйте **функцию** на **действия с комебакк**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Ключевое слово:](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="1e9de-334">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="1e9de-334">Build and Deploy</span></span>

* <span data-ttu-id="1e9de-335">Как и ранее, создайте проект в Unity и разверните его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e9de-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="1e9de-336">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="1e9de-336">After the application is deployed:</span></span>

* <span data-ttu-id="1e9de-337">Скажите *«выставить плату»* , чтобы у P0LY был вход в центр энергии.</span><span class="sxs-lookup"><span data-stu-id="1e9de-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="1e9de-338">Обратите внимание на изменение звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-338">Note the change in the sound.</span></span> <span data-ttu-id="1e9de-339">Он должен звучит муффлед и немного тихо.</span><span class="sxs-lookup"><span data-stu-id="1e9de-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="1e9de-340">Если вы можете разместить себя на стене или другом объекте между вами и концентратором энергии, вы должны заметить еще один муффлинг звука из-за перекрытия в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="1e9de-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="1e9de-341">Скажем, *"Приходите сюда"* , чтобы P0LY не выходить из концентратора энергии и располагать его в начале работы.</span><span class="sxs-lookup"><span data-stu-id="1e9de-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="1e9de-342">Обратите внимание, что звуковой перекрытия удаляется после того, как P0LY выходит из концентратора энергии.</span><span class="sxs-lookup"><span data-stu-id="1e9de-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="1e9de-343">Если вы по-прежнему слышите перекрытия, P0LY может быть перекрыто в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="1e9de-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="1e9de-344">Попробуйте переместить, чтобы убедиться, что у вас есть четкое представление о P0LY.</span><span class="sxs-lookup"><span data-stu-id="1e9de-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="1e9de-345">Часть 3. модели комнаты</span><span class="sxs-lookup"><span data-stu-id="1e9de-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1e9de-346">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="1e9de-346">Key Concepts</span></span>

* <span data-ttu-id="1e9de-347">Размер пространства предоставляет очереди сублиминал, которые способствуют локализации звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="1e9de-348">Модели комнаты задаются для каждого**аудиосаурце**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="1e9de-349">[Микседреалититулкит для Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) предоставляет код для настройки модели комнаты.</span><span class="sxs-lookup"><span data-stu-id="1e9de-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="1e9de-350">Для возможностей смешанной реальности выберите модель комнаты, которая лучше всего соответствует реальному пространству.</span><span class="sxs-lookup"><span data-stu-id="1e9de-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="1e9de-351">При создании сценария виртуальной реальности выберите модель комнаты, которая лучше подходит для виртуальной среды.</span><span class="sxs-lookup"><span data-stu-id="1e9de-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="1e9de-352">Глава 4. Создание звуковых эффектов</span><span class="sxs-lookup"><span data-stu-id="1e9de-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="1e9de-353">Задачи</span><span class="sxs-lookup"><span data-stu-id="1e9de-353">Objectives</span></span>

* <span data-ttu-id="1e9de-354">Общие сведения о эффективной разработке звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="1e9de-355">Узнайте, как смешивать методики и рекомендации.</span><span class="sxs-lookup"><span data-stu-id="1e9de-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="1e9de-356">Часть 1. проектирование звука и опыта</span><span class="sxs-lookup"><span data-stu-id="1e9de-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="1e9de-357">В этом разделе обсуждаются ключевые моменты и рекомендации по проектированию.</span><span class="sxs-lookup"><span data-stu-id="1e9de-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="1e9de-358">Нормализовать все звуки</span><span class="sxs-lookup"><span data-stu-id="1e9de-358">Normalize all sounds</span></span>

<span data-ttu-id="1e9de-359">Это позволяет избежать необходимости в специальном коде, чтобы настроить уровень громкости для звука, что может занимать много времени и ограничивает возможность простого обновления звуковых файлов.</span><span class="sxs-lookup"><span data-stu-id="1e9de-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="1e9de-360">Проектирование для неинтерактивного интерфейса</span><span class="sxs-lookup"><span data-stu-id="1e9de-360">Design for an untethered experience</span></span>

<span data-ttu-id="1e9de-361">HoloLens — это полностью автономный компьютер с неустановленным модемом Holographic.</span><span class="sxs-lookup"><span data-stu-id="1e9de-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="1e9de-362">Ваши пользователи могут и будут использовать ваши возможности во время перемещения.</span><span class="sxs-lookup"><span data-stu-id="1e9de-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="1e9de-363">Не забудьте протестировать звуковой микшер, прополнив обход.</span><span class="sxs-lookup"><span data-stu-id="1e9de-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="1e9de-364">Выдавать звук из логических расположений на голограммах</span><span class="sxs-lookup"><span data-stu-id="1e9de-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="1e9de-365">В реальной жизни собака не лай от своего заключительного фрагмента, а речь не поступает из своих метров.</span><span class="sxs-lookup"><span data-stu-id="1e9de-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="1e9de-366">Старайтесь не создавать звуки на основе непредвиденных частей голограмм.</span><span class="sxs-lookup"><span data-stu-id="1e9de-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="1e9de-367">Для небольших голограмм целесообразно, чтобы звук выдавался из центра геометрии.</span><span class="sxs-lookup"><span data-stu-id="1e9de-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="1e9de-368">Привычные звуки являются наиболее подлежат локализации</span><span class="sxs-lookup"><span data-stu-id="1e9de-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="1e9de-369">Возможность локализации с человеческого голоса и музыки очень проста.</span><span class="sxs-lookup"><span data-stu-id="1e9de-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="1e9de-370">Если кто-то вызывает ваше имя, вы сможете точно определить, откуда поступило направление голоса и с какого края.</span><span class="sxs-lookup"><span data-stu-id="1e9de-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="1e9de-371">Короткие, неизвестные звуки сложнее локализовать.</span><span class="sxs-lookup"><span data-stu-id="1e9de-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="1e9de-372">Компания cognizant ожидания пользователей</span><span class="sxs-lookup"><span data-stu-id="1e9de-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="1e9de-373">Жизненный цикл играет определенную часть в возможности определения местоположения звука.</span><span class="sxs-lookup"><span data-stu-id="1e9de-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="1e9de-374">Это одна из причин, по которой человеческий разговор особенно прост в локализации.</span><span class="sxs-lookup"><span data-stu-id="1e9de-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="1e9de-375">При помещении звуков важно помнить о предполагаемых изменениях пользователя.</span><span class="sxs-lookup"><span data-stu-id="1e9de-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="1e9de-376">Например, когда кто-то слышит песню с заполнением, обычно они ищутся, так как птиц, как правило, находится над линией (перелетаем или в дереве).</span><span class="sxs-lookup"><span data-stu-id="1e9de-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="1e9de-377">Нередко пользователь может включить правильное направление звука, но взгляните на неправильное вертикальное направление и не будет путать или разочаровано, если не удается найти голограмму.</span><span class="sxs-lookup"><span data-stu-id="1e9de-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="1e9de-378">Избегайте скрытых передатчиков</span><span class="sxs-lookup"><span data-stu-id="1e9de-378">Avoid hidden emitters</span></span>

<span data-ttu-id="1e9de-379">В реальной жизни, если мы слышите звук, можно, как правило, найти объект, который порождает звук.</span><span class="sxs-lookup"><span data-stu-id="1e9de-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="1e9de-380">Это также должно иметь значение true в своих впечатлениях.</span><span class="sxs-lookup"><span data-stu-id="1e9de-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="1e9de-381">Это может быть очень неудобно для пользователей услышать звук, знать, откуда поступает звук и не удается увидеть объект.</span><span class="sxs-lookup"><span data-stu-id="1e9de-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="1e9de-382">В этой рекомендации есть некоторые исключения.</span><span class="sxs-lookup"><span data-stu-id="1e9de-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="1e9de-383">Например, окружающие звуки, такие как криккетс в поле, не должны быть видимыми.</span><span class="sxs-lookup"><span data-stu-id="1e9de-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="1e9de-384">Жизненный цикл позволяет нам ознакомиться с источником этих звуков без необходимости его просмотра.</span><span class="sxs-lookup"><span data-stu-id="1e9de-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="1e9de-385">Часть 2. Микширование звука</span><span class="sxs-lookup"><span data-stu-id="1e9de-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="1e9de-386">Нацеливание на микшер для тома 70% на HoloLens</span><span class="sxs-lookup"><span data-stu-id="1e9de-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="1e9de-387">Опыт работы в смешанной реальности позволяет видеть голограммы в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="1e9de-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="1e9de-388">Они также должны позволять слышать реальные звуки.</span><span class="sxs-lookup"><span data-stu-id="1e9de-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="1e9de-389">Целевой объект тома 70% позволяет пользователю слышать мир по всему миру, а также звуковое сопровождение.</span><span class="sxs-lookup"><span data-stu-id="1e9de-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="1e9de-390">На диске HoloLens на 100% Volume должны Drown внешние звуки</span><span class="sxs-lookup"><span data-stu-id="1e9de-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="1e9de-391">Уровень громкости 100% связан с возможностями виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="1e9de-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="1e9de-392">Визуально пользователь переносится в другой мир.</span><span class="sxs-lookup"><span data-stu-id="1e9de-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="1e9de-393">То же самое должно содержаться в значении true воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="1e9de-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="1e9de-394">Настройка категорий звуков с помощью Unity Аудиомиксер</span><span class="sxs-lookup"><span data-stu-id="1e9de-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="1e9de-395">При проектировании Mix часто бывает полезно создавать категории звуковых сигналов и иметь возможность увеличивать или уменьшать объем тома как единое целое.</span><span class="sxs-lookup"><span data-stu-id="1e9de-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="1e9de-396">Это позволяет хранить относительные уровни каждого звука, одновременно позволяя быстро и легко вносить изменения в общий набор.</span><span class="sxs-lookup"><span data-stu-id="1e9de-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="1e9de-397">К общим категориям относятся: звуковые эффекты, окружение, голосовое переработка и фоновая музыка.</span><span class="sxs-lookup"><span data-stu-id="1e9de-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="1e9de-398">Смешивание звуков на основе взгляда пользователя</span><span class="sxs-lookup"><span data-stu-id="1e9de-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="1e9de-399">Часто может оказаться полезным изменить звуковой микшер в зависимости от того, где находится пользователь (или нет).</span><span class="sxs-lookup"><span data-stu-id="1e9de-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="1e9de-400">Одним из распространенных способов использования этой методики является уменьшение уровня громкости для голограмм, находящихся за пределами holographic, чтобы облегчить пользователю сосредоточиться на информации перед ними.</span><span class="sxs-lookup"><span data-stu-id="1e9de-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="1e9de-401">Другой способ — увеличить громкость звука, чтобы привлечь внимание пользователя к важному событию.</span><span class="sxs-lookup"><span data-stu-id="1e9de-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="1e9de-402">Создание набора</span><span class="sxs-lookup"><span data-stu-id="1e9de-402">Building your mix</span></span>

<span data-ttu-id="1e9de-403">При создании сочетания рекомендуется начать с фонового звука и добавить слои на основе важности.</span><span class="sxs-lookup"><span data-stu-id="1e9de-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="1e9de-404">Часто это приводит к громкости каждого слоя, отличного от предыдущего.</span><span class="sxs-lookup"><span data-stu-id="1e9de-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="1e9de-405">При мнимой комбинации в виде инвертированной воронки с наименьшим важным (и обычно тихим звуком) в нижней части рекомендуется структурировать сочетание, похожее на следующую диаграмму.</span><span class="sxs-lookup"><span data-stu-id="1e9de-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Структура звукового микшера](images/soundlevels.png)

<span data-ttu-id="1e9de-407">Наработка голоса является интересным сценарием.</span><span class="sxs-lookup"><span data-stu-id="1e9de-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="1e9de-408">В зависимости от того, что вы создаете, вам может потребоваться стерео (не локализованный) звук или спатиализе голоса.</span><span class="sxs-lookup"><span data-stu-id="1e9de-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="1e9de-409">Два опубликованных в корпорации Майкрософт опыта иллюстрируют отличные примеры каждого сценария.</span><span class="sxs-lookup"><span data-stu-id="1e9de-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="1e9de-410">[Холотаур](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) использует стерео голосовое по.</span><span class="sxs-lookup"><span data-stu-id="1e9de-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="1e9de-411">Когда экранный диктор описывает просматриваемое расположение, звук будет единообразным и не меняется в зависимости от положения пользователя.</span><span class="sxs-lookup"><span data-stu-id="1e9de-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="1e9de-412">Это позволяет экранному диктору описывать сцену, не отвлекаясь от пространственных звуков среды.</span><span class="sxs-lookup"><span data-stu-id="1e9de-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="1e9de-413">[Фрагменты](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) используют пространственный Voice в виде выявляющий.</span><span class="sxs-lookup"><span data-stu-id="1e9de-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="1e9de-414">Голосовое выявляющий используется для того, чтобы привлечь внимание пользователя к важной подсчету, как если бы реальный человек находился в комнате.</span><span class="sxs-lookup"><span data-stu-id="1e9de-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="1e9de-415">Это позволяет даже лучше понять, как погрузиться в возможности решения загадкы.</span><span class="sxs-lookup"><span data-stu-id="1e9de-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="1e9de-416">Часть 3. производительность</span><span class="sxs-lookup"><span data-stu-id="1e9de-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="1e9de-417">Загрузка ЦП</span><span class="sxs-lookup"><span data-stu-id="1e9de-417">CPU usage</span></span>

<span data-ttu-id="1e9de-418">При использовании пространственного звука 10-12 передатчиков будет потреблять примерно 12% ресурсов ЦП.</span><span class="sxs-lookup"><span data-stu-id="1e9de-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="1e9de-419">Потоковая передача длинных звуковых файлов</span><span class="sxs-lookup"><span data-stu-id="1e9de-419">Stream long audio files</span></span>

<span data-ttu-id="1e9de-420">Звуковые данные могут быть большими, особенно в общих частотах выборки (44,1 и 48 кГц).</span><span class="sxs-lookup"><span data-stu-id="1e9de-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="1e9de-421">Общее правило заключается в потоковой передаче звуковых файлов дольше 5-10 секунд, чтобы сократить использование памяти приложения.</span><span class="sxs-lookup"><span data-stu-id="1e9de-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="1e9de-422">В Unity можно пометить звуковой файл для потоковой передачи в параметрах импорта файла.</span><span class="sxs-lookup"><span data-stu-id="1e9de-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Настройки импорта звука](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="1e9de-424">Глава 5-Специальные эффекты</span><span class="sxs-lookup"><span data-stu-id="1e9de-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="1e9de-425">Задачи</span><span class="sxs-lookup"><span data-stu-id="1e9de-425">Objectives</span></span>

* <span data-ttu-id="1e9de-426">Добавьте глубину в "волшебные окна".</span><span class="sxs-lookup"><span data-stu-id="1e9de-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="1e9de-427">Перенесите пользователя в виртуальный мир.</span><span class="sxs-lookup"><span data-stu-id="1e9de-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="1e9de-428">Волшебные окна</span><span class="sxs-lookup"><span data-stu-id="1e9de-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1e9de-429">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="1e9de-429">Key Concepts</span></span>

* <span data-ttu-id="1e9de-430">Создание представлений в скрытом мире является визуально привлекательным.</span><span class="sxs-lookup"><span data-stu-id="1e9de-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="1e9de-431">Улучшайте реальные последствия, добавляя звуковые эффекты, когда голограмма или пользователь находится ближе к скрытому миру.</span><span class="sxs-lookup"><span data-stu-id="1e9de-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1e9de-432">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1e9de-432">Instructions</span></span>

* <span data-ttu-id="1e9de-433">На панели **Иерархия** разверните узел **холограмколлектион** и выберите пункт незаполненный **мир**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="1e9de-434">Разверните узел " **подсветка** " и выберите **воицесаурце**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="1e9de-435">На панели **инспектора** щелкните **Добавить компонент** и добавить **Пользовательский речевой эффекты**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="1e9de-436">В **воицесаурце**будет добавлен компонент **аудиосаурце** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="1e9de-437">В **аудиосаурце**установите **выходные данные** в **UserVoice (микшер)** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="1e9de-438">Установите флажок **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="1e9de-439">Перетащите ползунок **пространственного смешения** на **3D**или введите **1** в поле ввода.</span><span class="sxs-lookup"><span data-stu-id="1e9de-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="1e9de-440">Разверните **Параметры трехмерного звука**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="1e9de-441">Задайте для **уровня Doppler** значение **0**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="1e9de-442">В поле **Пользовательский видеорезультат**задайте для параметра **родительский объект** значение подсветкой из сцены.</span><span class="sxs-lookup"><span data-stu-id="1e9de-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="1e9de-443">Установите **Максимальное расстояние** равным **1**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="1e9de-444">Установка параметра **Max Distance** сообщает **пользователю** о том, как закрыть пользователя к родительскому объекту до того, как будет включен этот результат.</span><span class="sxs-lookup"><span data-stu-id="1e9de-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="1e9de-445">В окне " **Пользовательский Видеорезультат**" разверните узел **Параметры чорус**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="1e9de-446">Задайте для свойства **Depth** значение **0,1**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="1e9de-447">Установите **касание тома 1**, **Коснитесь 2 тома** и **коснитесь 3 тома** на **0,8**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="1e9de-448">Установите для параметра **исходный звуковой том** значение **0,5**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="1e9de-449">Предыдущие параметры настраивают параметры **Аудиочорусфилтер** Unity, используемые для добавления богатости в речь пользователя.</span><span class="sxs-lookup"><span data-stu-id="1e9de-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="1e9de-450">В окне " **Пользовательский Видеорезультат**" разверните **Параметры Echo**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="1e9de-451">Установить **задержку** в **300**</span><span class="sxs-lookup"><span data-stu-id="1e9de-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="1e9de-452">Установите **соотношение Decay** к **0,2**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="1e9de-453">Установите **0**в качестве **исходного звукового тома** .</span><span class="sxs-lookup"><span data-stu-id="1e9de-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="1e9de-454">Предыдущие параметры настраивают параметры **Аудиоечофилтер** Unity, которые приводят к эхо голоса пользователя.</span><span class="sxs-lookup"><span data-stu-id="1e9de-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="1e9de-455">Сценарий пользовательского голоса отвечает за следующее:</span><span class="sxs-lookup"><span data-stu-id="1e9de-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="1e9de-456">Измерение расстояния между пользователем и **GameObject** , к которому присоединен скрипт.</span><span class="sxs-lookup"><span data-stu-id="1e9de-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="1e9de-457">Определение того, находится ли пользователь в **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="1e9de-458">Для включения этого действия пользователь должен быть направлен на GameObject, независимо от расстояния.</span><span class="sxs-lookup"><span data-stu-id="1e9de-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="1e9de-459">Применение и настройка **аудиочорусфилтер** и **аудиоечофилтер** для **аудиосаурце**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="1e9de-460">Отключение этого действия путем отключения фильтров.</span><span class="sxs-lookup"><span data-stu-id="1e9de-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="1e9de-461">В голосовом режиме для пользователя используется компонент выбора потока MIC из [микседреалититулкит для Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), чтобы выбрать высококачественный голосовой поток и направить его в звуковую систему Unity.</span><span class="sxs-lookup"><span data-stu-id="1e9de-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="1e9de-462">На панели **Иерархия** выберите **Диспетчеры**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="1e9de-463">На панели **инспектора** разверните **обработчик речевого ввода**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="1e9de-464">В **обработчике речевого ввода**разверните узел **Показывать подсветку**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="1e9de-465">Не изменяйте **функцию** на **Ундерворлдбасе. OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Ключевое слово: показывать подсветку](images/showunderworld.png)

* <span data-ttu-id="1e9de-467">Разверните узел **Скрыть подсветку**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="1e9de-468">Не изменяйте **функцию** на **Ундерворлдбасе. ondisable**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Ключевое слово: Скрыть подсветку](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="1e9de-470">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="1e9de-470">Build and Deploy</span></span>

* <span data-ttu-id="1e9de-471">Как и ранее, создайте проект в Unity и разверните его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e9de-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="1e9de-472">После развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="1e9de-472">After the application is deployed:</span></span>

* <span data-ttu-id="1e9de-473">Лицевая поверхность (стена, этаж, таблица) и скажите *«Показывать подсветку»* .</span><span class="sxs-lookup"><span data-stu-id="1e9de-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="1e9de-474">Будет отображена подсветка, а все остальные голограммы будут скрыты.</span><span class="sxs-lookup"><span data-stu-id="1e9de-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="1e9de-475">Если вы не видите подсветку, убедитесь, что вы используете реальную поверхность.</span><span class="sxs-lookup"><span data-stu-id="1e9de-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="1e9de-476">Подход в пределах 1 индикатора немалой голограммы и начните говорить.</span><span class="sxs-lookup"><span data-stu-id="1e9de-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="1e9de-477">Теперь на ваш голос применяются звуковые эффекты!</span><span class="sxs-lookup"><span data-stu-id="1e9de-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="1e9de-478">Отключитесь от подсветки и обратите внимание на то, как это действие больше не применяется.</span><span class="sxs-lookup"><span data-stu-id="1e9de-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="1e9de-479">Скажите *«Скрыть подсветку»* , чтобы скрыть подсветку.</span><span class="sxs-lookup"><span data-stu-id="1e9de-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="1e9de-480">Подсветка будет скрыта, и ранее скрытые голограммы будут отображаться снова.</span><span class="sxs-lookup"><span data-stu-id="1e9de-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="1e9de-481">Конец</span><span class="sxs-lookup"><span data-stu-id="1e9de-481">The End</span></span>

<span data-ttu-id="1e9de-482">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1e9de-482">Congratulations!</span></span> <span data-ttu-id="1e9de-483">Теперь вы завершили выполнение пространственного **пространственного 220: Пространственный звук**.</span><span class="sxs-lookup"><span data-stu-id="1e9de-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="1e9de-484">Прослушайтесь в мире и поработайте со звуком!</span><span class="sxs-lookup"><span data-stu-id="1e9de-484">Listen to the world and bring your experiences to life with sound!</span></span>
