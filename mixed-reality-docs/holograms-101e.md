---
title: Основные сведения о 101E — завершение проекта с помощью эмулятора
description: Выполните это пошаговое руководство по программированию с помощью Unity, Visual Studio и эмулятора HoloLens, чтобы изучить основные принципы работы с приложением Holographic.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, Windows Mixed Reality, HoloLens, голограмма, Academy, учебник, эмулятор
ms.openlocfilehash: b1d8e1f3f272051bdd6f69ab88c3aef4f86f13ef
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434703"
---
>[!NOTE]
><span data-ttu-id="0e465-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="0e465-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0e465-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="0e465-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0e465-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0e465-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0e465-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="0e465-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0e465-108">Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="0e465-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="0e465-109">Основные сведения о 101E: завершение проекта с помощью эмулятора</span><span class="sxs-lookup"><span data-stu-id="0e465-109">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="0e465-110">В этом руководстве описывается полный проект, встроенный в Unity, демонстрирующий основные функции Windows Mixed Reality в HoloLens, включая [взгляд](gaze-and-commit.md), [жесты](gaze-and-commit.md#composite-gestures), [речевой ввод](voice-input.md), [Пространственный звук](spatial-sound.md) и [пространственное сопоставление](spatial-mapping.md) . .</span><span class="sxs-lookup"><span data-stu-id="0e465-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="0e465-111">Выполнение руководства займет примерно 1 час.</span><span class="sxs-lookup"><span data-stu-id="0e465-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="0e465-112">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="0e465-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0e465-113">Хождение</span><span class="sxs-lookup"><span data-stu-id="0e465-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0e465-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0e465-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0e465-115"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="0e465-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0e465-116">Основные сведения о 101E: завершение проекта с помощью эмулятора</span><span class="sxs-lookup"><span data-stu-id="0e465-116">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="0e465-117">✔️</span><span class="sxs-lookup"><span data-stu-id="0e465-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0e465-118">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="0e465-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0e465-119">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="0e465-119">Prerequisites</span></span>

* <span data-ttu-id="0e465-120">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0e465-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="0e465-121">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="0e465-121">Project files</span></span>

* <span data-ttu-id="0e465-122">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="0e465-122">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="0e465-123"> Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="0e465-123"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0e465-124">Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0e465-124">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="0e465-125">Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0e465-125">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="0e465-126">Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0e465-126">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="0e465-127">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="0e465-127">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0e465-128">В качестве имени папки используйте **Origami**.</span><span class="sxs-lookup"><span data-stu-id="0e465-128">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="0e465-129">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="0e465-129">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0e465-130">Глава 1-"Холо"</span><span class="sxs-lookup"><span data-stu-id="0e465-130">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="0e465-131">В этой главе мы создадим наш первый проект Unity и пошаговым процессом сборки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="0e465-131">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0e465-132">Задачи</span><span class="sxs-lookup"><span data-stu-id="0e465-132">Objectives</span></span>

* <span data-ttu-id="0e465-133">Настройка Unity для разработки с Holographic.</span><span class="sxs-lookup"><span data-stu-id="0e465-133">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="0e465-134">Создайте голограмму.</span><span class="sxs-lookup"><span data-stu-id="0e465-134">Make a hologram.</span></span>
* <span data-ttu-id="0e465-135">Ознакомьтесь с созданной голограммой.</span><span class="sxs-lookup"><span data-stu-id="0e465-135">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="0e465-136">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0e465-136">Instructions</span></span>

* <span data-ttu-id="0e465-137">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="0e465-137">Start Unity.</span></span>
* <span data-ttu-id="0e465-138">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="0e465-138">Select **Open**.</span></span>
* <span data-ttu-id="0e465-139">Введите Location в качестве папки **Origami** , которая была отменена для архивации.</span><span class="sxs-lookup"><span data-stu-id="0e465-139">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="0e465-140">Выберите **Origami** и щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="0e465-140">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="0e465-141">Сохраните новую сцену: **файл** / **сохранить сцену как**.</span><span class="sxs-lookup"><span data-stu-id="0e465-141">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="0e465-142">Присвойте сцене имя **Origami** и нажмите кнопку **Save (сохранить** ).</span><span class="sxs-lookup"><span data-stu-id="0e465-142">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="0e465-143">Настройка основной камеры</span><span class="sxs-lookup"><span data-stu-id="0e465-143">Setup the main camera</span></span>

* <span data-ttu-id="0e465-144">На **панели Иерархия**выберите **Главная камера**.</span><span class="sxs-lookup"><span data-stu-id="0e465-144">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="0e465-145">В **инспекторе** задайте для его параметра «transform **» значение 0, 0,** 0.</span><span class="sxs-lookup"><span data-stu-id="0e465-145">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="0e465-146">Найдите свойство **clear flags** и измените раскрывающийся список с **скибокс** на **сплошной цвет**.</span><span class="sxs-lookup"><span data-stu-id="0e465-146">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="0e465-147">Щелкните поле **Background (фон** ), чтобы открыть палитру цветов.</span><span class="sxs-lookup"><span data-stu-id="0e465-147">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="0e465-148">Задайте значения **R, G, B и A** равными **0**.</span><span class="sxs-lookup"><span data-stu-id="0e465-148">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="0e465-149">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="0e465-149">Setup the scene</span></span>

* <span data-ttu-id="0e465-150">На **панели Иерархия**щелкните **создать** и **создать пустой**.</span><span class="sxs-lookup"><span data-stu-id="0e465-150">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="0e465-151">Щелкните правой кнопкой мыши новый **GameObject** и выберите команду Переименовать.</span><span class="sxs-lookup"><span data-stu-id="0e465-151">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="0e465-152">Переименуйте GameObject в **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0e465-152">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="0e465-153">Из папки **голограмм** на **панели проекта**:</span><span class="sxs-lookup"><span data-stu-id="0e465-153">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="0e465-154">Перетащите **этап** в иерархию, чтобы он был дочерним элементом **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0e465-154">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0e465-155">Перетащите **Sphere1** в иерархию, чтобы она была дочерней для **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0e465-155">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0e465-156">Перетащите **Sphere2** в иерархию, чтобы она была дочерней для **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0e465-156">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0e465-157">Щелкните правой кнопкой мыши **направленный объект Light** на **панели Иерархия** и выберите команду **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="0e465-157">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="0e465-158">Перетащите **индикаторы** из папки **голограммы** в корневую папку **панели Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="0e465-158">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="0e465-159">В **иерархии**выберите **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0e465-159">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0e465-160">В **инспекторе**задайте для параметра Расположение преобразования значение **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="0e465-160">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="0e465-161">Нажмите кнопку **воспроизвести** в Unity, чтобы просмотреть голограммы.</span><span class="sxs-lookup"><span data-stu-id="0e465-161">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0e465-162">В окне предварительного просмотра должны отобразиться объекты Origami.</span><span class="sxs-lookup"><span data-stu-id="0e465-162">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="0e465-163">Чтобы выйти из режима предварительного просмотра, нажмите кнопку **воспроизвести** еще раз.</span><span class="sxs-lookup"><span data-stu-id="0e465-163">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="0e465-164">Экспорт проекта из Unity в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e465-164">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="0e465-165">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="0e465-165">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="0e465-166">Выберите **Магазин Windows** в списке **платформа** и щелкните **Переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="0e465-166">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="0e465-167">Задайте для **пакета SDK** значение **универсальное 10** , а для **типа сборки** — **D3D**.</span><span class="sxs-lookup"><span data-stu-id="0e465-167">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="0e465-168">Проверьте **проекты C# Unity**.</span><span class="sxs-lookup"><span data-stu-id="0e465-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="0e465-169">Щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="0e465-169">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0e465-170">Щелкните **Параметры проигрывателя...** .</span><span class="sxs-lookup"><span data-stu-id="0e465-170">Click **Player Settings...**.</span></span>
* <span data-ttu-id="0e465-171">На панели инспектора выберите **логотип магазина Windows**.</span><span class="sxs-lookup"><span data-stu-id="0e465-171">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="0e465-172">Затем выберите **Параметры публикации**.</span><span class="sxs-lookup"><span data-stu-id="0e465-172">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="0e465-173">В разделе **возможности** выберите возможности **микрофона** и **спатиалперцептион** .</span><span class="sxs-lookup"><span data-stu-id="0e465-173">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="0e465-174">Вернувшись в окно параметры сборки, щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="0e465-174">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="0e465-175">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="0e465-175">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0e465-176">Щелкните **папку приложения**одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="0e465-176">Single click the **App Folder**.</span></span>
* <span data-ttu-id="0e465-177">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="0e465-177">Press **Select Folder**.</span></span>
* <span data-ttu-id="0e465-178">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="0e465-178">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0e465-179">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="0e465-179">Open the **App** folder.</span></span>
* <span data-ttu-id="0e465-180">Откройте **решение Origami Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0e465-180">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="0e465-181">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="0e465-181">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="0e465-182">Щелкните стрелку рядом с кнопкой устройство и выберите **эмулятор HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0e465-182">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="0e465-183">Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="0e465-183">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="0e465-184">Через некоторое время эмулятор начнет работу с проектом Origami.</span><span class="sxs-lookup"><span data-stu-id="0e465-184">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="0e465-185">При первом запуске [эмулятора](using-the-hololens-emulator.md)для запуска эмулятора может потребоваться до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="0e465-185">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="0e465-186">После запуска не закрывайте его.</span><span class="sxs-lookup"><span data-stu-id="0e465-186">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="0e465-187">Глава 2. взгляд</span><span class="sxs-lookup"><span data-stu-id="0e465-187">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="0e465-188">В этой главе мы будем познакомиться с первым из трех способов взаимодействия с голограммами — [Взгляните](gaze-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="0e465-188">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="0e465-189">Задачи</span><span class="sxs-lookup"><span data-stu-id="0e465-189">Objectives</span></span>

* <span data-ttu-id="0e465-190">Визуализируйте взгляд с помощью курсора, заблокированного по всему миру.</span><span class="sxs-lookup"><span data-stu-id="0e465-190">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="0e465-191">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0e465-191">Instructions</span></span>

* <span data-ttu-id="0e465-192">Вернитесь к проекту Unity и закройте окно параметры сборки, если оно все еще открыто.</span><span class="sxs-lookup"><span data-stu-id="0e465-192">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="0e465-193">Выберите папку **голограммы** на **панели проект**.</span><span class="sxs-lookup"><span data-stu-id="0e465-193">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="0e465-194">Перетащите объект **курсора** на **панель Иерархия** на корневом уровне.</span><span class="sxs-lookup"><span data-stu-id="0e465-194">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="0e465-195">Дважды щелкните объект **курсора** , чтобы просмотреть его Подробнее.</span><span class="sxs-lookup"><span data-stu-id="0e465-195">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="0e465-196">Щелкните правой кнопкой мыши папку **сценарии** на панели проект.</span><span class="sxs-lookup"><span data-stu-id="0e465-196">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="0e465-197">Щелкните подменю **создать** .</span><span class="sxs-lookup"><span data-stu-id="0e465-197">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="0e465-198">Выберите  **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="0e465-198">Select **C# Script**.</span></span>
* <span data-ttu-id="0e465-199">Назовите сценарий **ворлдкурсор**.</span><span class="sxs-lookup"><span data-stu-id="0e465-199">Name the script **WorldCursor**.</span></span> <span data-ttu-id="0e465-200">Примечание. в имени учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="0e465-200">Note: The name is case-sensitive.</span></span> <span data-ttu-id="0e465-201">Добавлять расширение CS не требуется.</span><span class="sxs-lookup"><span data-stu-id="0e465-201">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="0e465-202">Выберите объект **курсора** на **панели Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="0e465-202">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="0e465-203">Перетащите сценарий **ворлдкурсор** на **Панель инспектора**.</span><span class="sxs-lookup"><span data-stu-id="0e465-203">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="0e465-204">Дважды щелкните скрипт **ворлдкурсор** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e465-204">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0e465-205">Скопируйте и вставьте этот код в **WorldCursor.CS** и **Сохраните все**.</span><span class="sxs-lookup"><span data-stu-id="0e465-205">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="0e465-206">Перестройте приложение из **файла > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="0e465-206">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="0e465-207">Вернитесь к решению Visual Studio, которое ранее использовалось для развертывания в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="0e465-207">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="0e465-208">При появлении запроса выберите "перезагрузить все".</span><span class="sxs-lookup"><span data-stu-id="0e465-208">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="0e465-209">Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="0e465-209">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0e465-210">Используйте контроллер Xbox для просмотра сцены.</span><span class="sxs-lookup"><span data-stu-id="0e465-210">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="0e465-211">Обратите внимание, что курсор взаимодействует с формой объектов.</span><span class="sxs-lookup"><span data-stu-id="0e465-211">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="0e465-212">Глава 3 — жесты</span><span class="sxs-lookup"><span data-stu-id="0e465-212">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="0e465-213">В этой главе мы добавим поддержку [жестов](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="0e465-213">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="0e465-214">Когда пользователь выбирает бумажную сферу, мы сделаем сферу, включив для нее функцию "сила притяжения" с помощью системы обработки физических модулей Unity.</span><span class="sxs-lookup"><span data-stu-id="0e465-214">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="0e465-215">Задачи</span><span class="sxs-lookup"><span data-stu-id="0e465-215">Objectives</span></span>

* <span data-ttu-id="0e465-216">Контролируйте голограммы с помощью жеста выбора.</span><span class="sxs-lookup"><span data-stu-id="0e465-216">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="0e465-217">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0e465-217">Instructions</span></span>

<span data-ttu-id="0e465-218">Начнем с создания сценария, чем может обнаружить жест выбора.</span><span class="sxs-lookup"><span data-stu-id="0e465-218">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="0e465-219">В папке **Scripts** создайте скрипт с именем **газежестуреманажер**.</span><span class="sxs-lookup"><span data-stu-id="0e465-219">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="0e465-220">Перетащите скрипт **газежестуреманажер** на объект **оригамиколлектион** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="0e465-220">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="0e465-221">Откройте скрипт **газежестуреманажер** в Visual Studio и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="0e465-221">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="0e465-222">Создайте другой скрипт в папке Scripts с именем **сферекоммандс**.</span><span class="sxs-lookup"><span data-stu-id="0e465-222">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="0e465-223">Разверните объект **оригамиколлектион** в представлении иерархии.</span><span class="sxs-lookup"><span data-stu-id="0e465-223">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="0e465-224">Перетащите скрипт **сферекоммандс** на объект **Sphere1** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="0e465-224">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0e465-225">Перетащите скрипт **сферекоммандс** на объект **Sphere2** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="0e465-225">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0e465-226">Откройте скрипт в Visual Studio для редактирования и замените код по умолчанию следующим:</span><span class="sxs-lookup"><span data-stu-id="0e465-226">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="0e465-227">Экспортируйте, создайте и разверните приложение в эмуляторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0e465-227">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0e465-228">Взгляните на сцену и помещайтесь по центру на одном из шарик.</span><span class="sxs-lookup"><span data-stu-id="0e465-228">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="0e465-229">Нажмите кнопку **на** контроллере Xbox или нажмите клавишу пробел, чтобы имитировать жест выбора.</span><span class="sxs-lookup"><span data-stu-id="0e465-229">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="0e465-230">Глава 4-Voice</span><span class="sxs-lookup"><span data-stu-id="0e465-230">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="0e465-231">В этой главе мы добавим поддержку двух [голосовых команд](voice-input.md): "сбросить мир", чтобы вернуть удаленные шарик к их исходному расположению и "удалить шар", чтобы сделать сферу.</span><span class="sxs-lookup"><span data-stu-id="0e465-231">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="0e465-232">Задачи</span><span class="sxs-lookup"><span data-stu-id="0e465-232">Objectives</span></span>

* <span data-ttu-id="0e465-233">Добавление речевых команд, которые всегда прослушиваются в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="0e465-233">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="0e465-234">Создайте голограмму, которая реагирует на голосовую команду.</span><span class="sxs-lookup"><span data-stu-id="0e465-234">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="0e465-235">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0e465-235">Instructions</span></span>

* <span data-ttu-id="0e465-236">В папке **Scripts** создайте скрипт с именем **спичманажер**.</span><span class="sxs-lookup"><span data-stu-id="0e465-236">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="0e465-237">Перетащите скрипт **спичманажер** на объект **оригамиколлектион** в иерархии</span><span class="sxs-lookup"><span data-stu-id="0e465-237">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="0e465-238">Откройте скрипт **спичманажер** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e465-238">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0e465-239">Скопируйте и вставьте этот код в **SpeechManager.CS** и **Сохраните все**:</span><span class="sxs-lookup"><span data-stu-id="0e465-239">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="0e465-240">Откройте скрипт **сферекоммандс** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e465-240">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="0e465-241">Обновите скрипт для чтения следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0e465-241">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="0e465-242">Экспортируйте, создайте и разверните приложение в эмуляторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0e465-242">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0e465-243">Эмулятор будет поддерживать микрофон компьютера и отвечать на ваш голос: настройте представление таким образом, чтобы курсор наследовался на одном из шарик и сказал «Drop Sphere».</span><span class="sxs-lookup"><span data-stu-id="0e465-243">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="0e465-244">Скажите «**сбросить мир**», чтобы вернуть их в исходное положение.</span><span class="sxs-lookup"><span data-stu-id="0e465-244">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="0e465-245">Глава 5 — Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="0e465-245">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="0e465-246">В этой главе мы добавим музыку в приложение, а затем активируем звуковые эффекты для определенных действий.</span><span class="sxs-lookup"><span data-stu-id="0e465-246">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="0e465-247">Мы будем использовать [Пространственный звук](spatial-sound.md) , чтобы дать звуковое сопровождение определенному месту в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="0e465-247">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0e465-248">Задачи</span><span class="sxs-lookup"><span data-stu-id="0e465-248">Objectives</span></span>

* <span data-ttu-id="0e465-249">Прослушайте голограммы в своем мире.</span><span class="sxs-lookup"><span data-stu-id="0e465-249">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="0e465-250">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0e465-250">Instructions</span></span>

* <span data-ttu-id="0e465-251">В элементе Unity выберите в верхнем меню **правка > параметры проекта > звук**</span><span class="sxs-lookup"><span data-stu-id="0e465-251">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="0e465-252">Найдите параметр **подключаемого модуля спатиализер** и выберите **MS хртф спатиализер**.</span><span class="sxs-lookup"><span data-stu-id="0e465-252">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="0e465-253">В папке **голограмм** перетащите объект **окружения** на объект **оригамиколлектион** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="0e465-253">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="0e465-254">Выберите **оригамиколлектион** и найдите компонент " **источник аудио** ".</span><span class="sxs-lookup"><span data-stu-id="0e465-254">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="0e465-255">Измените следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="0e465-255">Change these properties:</span></span>
  * <span data-ttu-id="0e465-256">Проверьте свойство **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="0e465-256">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="0e465-257">Проверьте **Воспроизведение в спящем**режиме.</span><span class="sxs-lookup"><span data-stu-id="0e465-257">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="0e465-258">Измените **пространственный переход** на **3D** , перетащив ползунок вправо.</span><span class="sxs-lookup"><span data-stu-id="0e465-258">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="0e465-259">Проверьте свойство **Loop** .</span><span class="sxs-lookup"><span data-stu-id="0e465-259">Check the **Loop** property.</span></span>
  * <span data-ttu-id="0e465-260">Разверните **Параметры 3D Sound**и введите **0,1** для **уровня Doppler**.</span><span class="sxs-lookup"><span data-stu-id="0e465-260">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="0e465-261">Задайте для параметра **Volume роллофф** значение **логарифмической роллофф**.</span><span class="sxs-lookup"><span data-stu-id="0e465-261">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="0e465-262">Установите **Максимальное расстояние** равным **20**.</span><span class="sxs-lookup"><span data-stu-id="0e465-262">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="0e465-263">В папке **Scripts** создайте скрипт с именем **сфересаундс**.</span><span class="sxs-lookup"><span data-stu-id="0e465-263">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="0e465-264">Перетащите **сфересаундс** в объекты **Sphere1** и **Sphere2** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="0e465-264">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="0e465-265">Откройте **сфересаундс** в Visual Studio, обновите следующий код и **Сохраните все**.</span><span class="sxs-lookup"><span data-stu-id="0e465-265">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="0e465-266">Сохраните скрипт и вернитесь в Unity.</span><span class="sxs-lookup"><span data-stu-id="0e465-266">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="0e465-267">Экспортируйте, создайте и разверните приложение в эмуляторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0e465-267">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0e465-268">Выизнос наушников, чтобы получить полный результат, и продвинуться ближе и дальше от этапа, чтобы услышать смену звуков.</span><span class="sxs-lookup"><span data-stu-id="0e465-268">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="0e465-269">Глава 6-пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="0e465-269">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="0e465-270">Теперь мы будем использовать [пространственное сопоставление](spatial-mapping.md) , чтобы поместить игровую доску на реальный объект в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="0e465-270">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="0e465-271">Задачи</span><span class="sxs-lookup"><span data-stu-id="0e465-271">Objectives</span></span>

* <span data-ttu-id="0e465-272">Приведите реальный мир к виртуальному миру.</span><span class="sxs-lookup"><span data-stu-id="0e465-272">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="0e465-273">Размещайте голограммы, где это важно.</span><span class="sxs-lookup"><span data-stu-id="0e465-273">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="0e465-274">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0e465-274">Instructions</span></span>

* <span data-ttu-id="0e465-275">Щелкните папку **голограмм** на панели проект.</span><span class="sxs-lookup"><span data-stu-id="0e465-275">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="0e465-276">Перетащите ресурс **пространственного сопоставления** в корень **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="0e465-276">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="0e465-277">Щелкните объект **пространственного сопоставления** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="0e465-277">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="0e465-278">На **панели инспектора**измените следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="0e465-278">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="0e465-279">Установите флажок **рисовать визуальные сетки** .</span><span class="sxs-lookup"><span data-stu-id="0e465-279">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="0e465-280">Перейдите на вкладку **Рисование материалов** и щелкните окружность справа.</span><span class="sxs-lookup"><span data-stu-id="0e465-280">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="0e465-281">Введите "**каркасная**схема" в поле поиска вверху.</span><span class="sxs-lookup"><span data-stu-id="0e465-281">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="0e465-282">Щелкните результат, а затем закройте окно.</span><span class="sxs-lookup"><span data-stu-id="0e465-282">Click on the result and then close the window.</span></span>
* <span data-ttu-id="0e465-283">Экспортируйте, создайте и разверните приложение в эмуляторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0e465-283">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0e465-284">При запуске приложения сеть ранее проверенной в реальном времени области будет отображаться в каркасе.</span><span class="sxs-lookup"><span data-stu-id="0e465-284">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="0e465-285">Следите за тем, как изкрутка будет выпадать за пределы этапа, и на этаж!</span><span class="sxs-lookup"><span data-stu-id="0e465-285">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="0e465-286">Теперь мы покажем, как переместить Оригамиколлектион в новое расположение:</span><span class="sxs-lookup"><span data-stu-id="0e465-286">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="0e465-287">В папке **Scripts** создайте скрипт с именем **таптоплацепарент**.</span><span class="sxs-lookup"><span data-stu-id="0e465-287">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="0e465-288">В **иерархии**разверните **оригамиколлектион** и выберите объект **Stage** .</span><span class="sxs-lookup"><span data-stu-id="0e465-288">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="0e465-289">Перетащите скрипт **таптоплацепарент** на объект Stage.</span><span class="sxs-lookup"><span data-stu-id="0e465-289">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="0e465-290">Откройте скрипт **таптоплацепарент** в Visual Studio и обновите его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0e465-290">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="0e465-291">Экспорт, сборка и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="0e465-291">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0e465-292">Теперь вы можете разместить игру в определенном месте, облаками ее с помощью жеста выбора (**a** или пробела), а затем переместить в новое место и снова с помощью жеста выбора.</span><span class="sxs-lookup"><span data-stu-id="0e465-292">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="0e465-293">Конец</span><span class="sxs-lookup"><span data-stu-id="0e465-293">The end</span></span>

<span data-ttu-id="0e465-294">И это окончание этого руководства.</span><span class="sxs-lookup"><span data-stu-id="0e465-294">And that's the end of this tutorial!</span></span>

<span data-ttu-id="0e465-295">Вы узнали:</span><span class="sxs-lookup"><span data-stu-id="0e465-295">You learned:</span></span>

* <span data-ttu-id="0e465-296">Создание приложения holographic в Unity.</span><span class="sxs-lookup"><span data-stu-id="0e465-296">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="0e465-297">Использование взгляда, жеста, голоса, звуков и пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="0e465-297">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="0e465-298">Как создать и развернуть приложение с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e465-298">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="0e465-299">Теперь вы готовы приступить к созданию собственных приложений holographic!</span><span class="sxs-lookup"><span data-stu-id="0e465-299">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="0e465-300">См. также</span><span class="sxs-lookup"><span data-stu-id="0e465-300">See also</span></span>

* [<span data-ttu-id="0e465-301">Основные сведения о MR 101: завершение проекта с помощью устройства</span><span class="sxs-lookup"><span data-stu-id="0e465-301">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="0e465-302">Взгляд</span><span class="sxs-lookup"><span data-stu-id="0e465-302">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0e465-303">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="0e465-303">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0e465-304">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="0e465-304">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="0e465-305">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="0e465-305">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="0e465-306">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="0e465-306">Spatial mapping</span></span>](spatial-mapping.md)
