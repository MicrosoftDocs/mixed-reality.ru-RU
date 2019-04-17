---
title: Основы MR 101E - полный проект с помощью эмулятора
description: Выполните кодирование Пошаговое руководство по использованию Unity, Visual Studio и эмулятора HoloLens, чтобы ознакомиться с основами holographic приложения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Смешанная реальность, смешанная реальность Windows, HoloLens, голограмма academy, руководства, эмулятор
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599406"
---
>[!NOTE]
><span data-ttu-id="88af2-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="88af2-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="88af2-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="88af2-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="88af2-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="88af2-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="88af2-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="88af2-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="88af2-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="88af2-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="88af2-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="88af2-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="88af2-110">Общие сведения об MR 101E: Полный проект с помощью эмулятора</span><span class="sxs-lookup"><span data-stu-id="88af2-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="88af2-111">Этот учебник поможет в проекте, встроенные в Unity, который демонстрирует основные возможности Windows Mixed Reality, в том числе HoloLens [помощи](gaze.md), [жесты](gestures.md), [голоса](voice-input.md), [пространственных звук](spatial-sound.md) и [пространственное сопоставление](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="88af2-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="88af2-112">Руководства займет примерно 1 час.</span><span class="sxs-lookup"><span data-stu-id="88af2-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="88af2-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="88af2-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="88af2-114">Курс</span><span class="sxs-lookup"><span data-stu-id="88af2-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="88af2-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="88af2-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="88af2-116"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="88af2-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="88af2-117">Общие сведения об MR 101E: Полный проект с помощью эмулятора</span><span class="sxs-lookup"><span data-stu-id="88af2-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="88af2-118">✔️</span><span class="sxs-lookup"><span data-stu-id="88af2-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="88af2-119">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="88af2-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="88af2-120">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="88af2-120">Prerequisites</span></span>

* <span data-ttu-id="88af2-121">ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="88af2-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="88af2-122">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="88af2-122">Project files</span></span>

* <span data-ttu-id="88af2-123">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) требуемые для проекта.</span><span class="sxs-lookup"><span data-stu-id="88af2-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="88af2-124"> Требуется компонент Unity 2017.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="88af2-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="88af2-125">Если вам по-прежнему требуется поддержка Unity 5.6, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="88af2-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="88af2-126">Если вам по-прежнему требуется поддержка Unity 5.5, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="88af2-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="88af2-127">Если вам по-прежнему требуется поддержка Unity 5.4, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="88af2-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="88af2-128">Удаление архива файлы рабочего стола или других легко положения.</span><span class="sxs-lookup"><span data-stu-id="88af2-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="88af2-129">Оставьте имя папки в качестве **Origami**.</span><span class="sxs-lookup"><span data-stu-id="88af2-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="88af2-130">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="88af2-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="88af2-131">Глава 1 - world «Holo»</span><span class="sxs-lookup"><span data-stu-id="88af2-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="88af2-132">В этой главе мы установки наш первый проект Unity и пошагово выполнять построение и развертывание процесса.</span><span class="sxs-lookup"><span data-stu-id="88af2-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="88af2-133">Цели</span><span class="sxs-lookup"><span data-stu-id="88af2-133">Objectives</span></span>

* <span data-ttu-id="88af2-134">Настройка Unity для holographic разработки.</span><span class="sxs-lookup"><span data-stu-id="88af2-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="88af2-135">Сделайте голограмма.</span><span class="sxs-lookup"><span data-stu-id="88af2-135">Make a hologram.</span></span>
* <span data-ttu-id="88af2-136">См. в разделе голограмма, созданную.</span><span class="sxs-lookup"><span data-stu-id="88af2-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="88af2-137">Инструкция</span><span class="sxs-lookup"><span data-stu-id="88af2-137">Instructions</span></span>

* <span data-ttu-id="88af2-138">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="88af2-138">Start Unity.</span></span>
* <span data-ttu-id="88af2-139">Выберите **откройте**.</span><span class="sxs-lookup"><span data-stu-id="88af2-139">Select **Open**.</span></span>
* <span data-ttu-id="88af2-140">Введите расположение как **Origami** папку вы ранее не архивные.</span><span class="sxs-lookup"><span data-stu-id="88af2-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="88af2-141">Выберите **Origami** и нажмите кнопку **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="88af2-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="88af2-142">Сохраните новую сцену: **Файл** / **сохранить сцену как**.</span><span class="sxs-lookup"><span data-stu-id="88af2-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="88af2-143">Присвойте сцене имя **Origami** и нажмите клавишу **Сохранить** кнопки.</span><span class="sxs-lookup"><span data-stu-id="88af2-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="88af2-144">Настройка главной камеры</span><span class="sxs-lookup"><span data-stu-id="88af2-144">Setup the main camera</span></span>

* <span data-ttu-id="88af2-145">В **панели иерархии**выберите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="88af2-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="88af2-146">В **инспектор** задайте его положение преобразования **0,0,0**.</span><span class="sxs-lookup"><span data-stu-id="88af2-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="88af2-147">Найти **очистить флаги** свойство и измените раскрывающийся список из **Skybox** для **Одноцветная**.</span><span class="sxs-lookup"><span data-stu-id="88af2-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="88af2-148">Щелкните **фона** поля, чтобы открыть палитру цветов.</span><span class="sxs-lookup"><span data-stu-id="88af2-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="88af2-149">Задайте **R, G, B и A** для **0**.</span><span class="sxs-lookup"><span data-stu-id="88af2-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="88af2-150">Программа установки сцены</span><span class="sxs-lookup"><span data-stu-id="88af2-150">Setup the scene</span></span>

* <span data-ttu-id="88af2-151">В **панели иерархии**, щелкните **создать** и **создать пустой**.</span><span class="sxs-lookup"><span data-stu-id="88af2-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="88af2-152">Щелкните правой кнопкой мыши новый **GameObject** и выберите Переименовать.</span><span class="sxs-lookup"><span data-stu-id="88af2-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="88af2-153">Переименовать объект GameObject, чтобы **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="88af2-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="88af2-154">Из **голограммы** папку в **панель проекта**:</span><span class="sxs-lookup"><span data-stu-id="88af2-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="88af2-155">Перетащите **этап** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="88af2-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="88af2-156">Перетащите **Sphere1** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="88af2-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="88af2-157">Перетащите **Sphere2** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="88af2-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="88af2-158">Щелкните правой кнопкой мыши **направленный свет** объекта в **панели иерархии** и выберите **удалить**.</span><span class="sxs-lookup"><span data-stu-id="88af2-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="88af2-159">Из **голограммы** папки, перетащите **индикаторы** в корне **панели иерархии**.</span><span class="sxs-lookup"><span data-stu-id="88af2-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="88af2-160">В **иерархии**выберите **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="88af2-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="88af2-161">В **инспектор**, задайте положение преобразования **0, -0,5, 2.0**.</span><span class="sxs-lookup"><span data-stu-id="88af2-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="88af2-162">Нажмите клавишу **воспроизведение** кнопки в Unity для предварительного просмотра вашего голограммы.</span><span class="sxs-lookup"><span data-stu-id="88af2-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="88af2-163">Вы увидите Origami объекты в окне предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="88af2-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="88af2-164">Нажмите клавишу **воспроизведение** второй раз, чтобы выйти из режима предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="88af2-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="88af2-165">Экспортировать проект из Unity в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88af2-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="88af2-166">В Unity выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="88af2-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="88af2-167">Выберите **Windows Store** в **платформы** списке и нажмите кнопку **переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="88af2-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="88af2-168">Задайте **SDK** для **универсальной 10** и **тип сборки** для **D3D**.</span><span class="sxs-lookup"><span data-stu-id="88af2-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="88af2-169">Проверьте **Unity C# проекты**.</span><span class="sxs-lookup"><span data-stu-id="88af2-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="88af2-170">Нажмите кнопку **добавьте откройте сцены** Добавление сцены.</span><span class="sxs-lookup"><span data-stu-id="88af2-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="88af2-171">Нажмите кнопку **параметры проигрывателя...** .</span><span class="sxs-lookup"><span data-stu-id="88af2-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="88af2-172">В панели Инспектора выберите **логотип Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="88af2-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="88af2-173">Затем выберите **параметров публикации**.</span><span class="sxs-lookup"><span data-stu-id="88af2-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="88af2-174">В **возможности** выберите **"микрофон"** и **SpatialPerception** возможности.</span><span class="sxs-lookup"><span data-stu-id="88af2-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="88af2-175">В окне «Параметры построения» щелкните **построения**.</span><span class="sxs-lookup"><span data-stu-id="88af2-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="88af2-176">Создание **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="88af2-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="88af2-177">Одним щелчком мыши **папки приложения**.</span><span class="sxs-lookup"><span data-stu-id="88af2-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="88af2-178">Нажмите клавишу **выберите папку**.</span><span class="sxs-lookup"><span data-stu-id="88af2-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="88af2-179">По завершении Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="88af2-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="88af2-180">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="88af2-180">Open the **App** folder.</span></span>
* <span data-ttu-id="88af2-181">Откройте **решение Visual Studio Origami**.</span><span class="sxs-lookup"><span data-stu-id="88af2-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="88af2-182">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **X86**.</span><span class="sxs-lookup"><span data-stu-id="88af2-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="88af2-183">Щелкните стрелку рядом с кнопкой на устройстве и выберите **HoloLens эмулятор**.</span><span class="sxs-lookup"><span data-stu-id="88af2-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="88af2-184">Нажмите кнопку **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="88af2-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="88af2-185">Через некоторое время эмулятор, загрузится с помощью проекта Origami.</span><span class="sxs-lookup"><span data-stu-id="88af2-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="88af2-186">При первом запуске [эмулятор](using-the-hololens-emulator.md), может занять до 15 минут для запуска эмулятора.</span><span class="sxs-lookup"><span data-stu-id="88af2-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="88af2-187">Сразу после запуска, но закрывайте его.</span><span class="sxs-lookup"><span data-stu-id="88af2-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="88af2-188">Глава 2 - взглядом</span><span class="sxs-lookup"><span data-stu-id="88af2-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="88af2-189">В этой главе мы собираемся установки первого из трех способов взаимодействия с вашей голограммы-- [помощи](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="88af2-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="88af2-190">Цели</span><span class="sxs-lookup"><span data-stu-id="88af2-190">Objectives</span></span>

* <span data-ttu-id="88af2-191">Визуализация вашей взглядом, с помощью курсора заблокирован в мире.</span><span class="sxs-lookup"><span data-stu-id="88af2-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="88af2-192">Инструкция</span><span class="sxs-lookup"><span data-stu-id="88af2-192">Instructions</span></span>

* <span data-ttu-id="88af2-193">Вернитесь к проекту Unity и закрыть окно Параметры построения, если он по-прежнему открыт.</span><span class="sxs-lookup"><span data-stu-id="88af2-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="88af2-194">Выберите **голограммы** папку в **панель проекта**.</span><span class="sxs-lookup"><span data-stu-id="88af2-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="88af2-195">Перетащите **курсор** в коллекцию **панели иерархии** на корневом уровне.</span><span class="sxs-lookup"><span data-stu-id="88af2-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="88af2-196">Дважды щелкните **курсор** объекта более подробно рассмотрим вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="88af2-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="88af2-197">Щелкните правой кнопкой мыши **сценариев** папку «проект».</span><span class="sxs-lookup"><span data-stu-id="88af2-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="88af2-198">Нажмите кнопку **создать** подменю.</span><span class="sxs-lookup"><span data-stu-id="88af2-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="88af2-199">Выберите  **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="88af2-199">Select **C# Script**.</span></span>
* <span data-ttu-id="88af2-200">Назовите сценарий **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="88af2-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="88af2-201">Примечание. Имя обрабатывается с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="88af2-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="88af2-202">Необходимо добавить расширение CS.</span><span class="sxs-lookup"><span data-stu-id="88af2-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="88af2-203">Выберите **курсор** объекта в **панели иерархии**.</span><span class="sxs-lookup"><span data-stu-id="88af2-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="88af2-204">Перетаскивание **WorldCursor** внесена в **панели Инспектора**.</span><span class="sxs-lookup"><span data-stu-id="88af2-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="88af2-205">Дважды щелкните **WorldCursor** скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88af2-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="88af2-206">Скопируйте и вставьте этот код в **WorldCursor.cs** и **сохранить все**.</span><span class="sxs-lookup"><span data-stu-id="88af2-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="88af2-207">Перестройте приложение из **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="88af2-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="88af2-208">Вернитесь к ранее используется для развертывания в эмуляторе решение Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88af2-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="88af2-209">Выберите «Обновить все» при появлении запроса.</span><span class="sxs-lookup"><span data-stu-id="88af2-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="88af2-210">Нажмите кнопку **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="88af2-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="88af2-211">Для поиска вокруг сцены, используется контроллер Xbox.</span><span class="sxs-lookup"><span data-stu-id="88af2-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="88af2-212">Обратите внимание на то, как курсор взаимодействует с форму объектов.</span><span class="sxs-lookup"><span data-stu-id="88af2-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="88af2-213">Глава 3 - жесты</span><span class="sxs-lookup"><span data-stu-id="88af2-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="88af2-214">В этой главе мы добавим поддержку [жесты](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="88af2-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="88af2-215">Когда пользователь выбирает сферы бумаги, сделаем сферы делятся, включив гравитации, с помощью обработчика физики Unity.</span><span class="sxs-lookup"><span data-stu-id="88af2-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="88af2-216">Цели</span><span class="sxs-lookup"><span data-stu-id="88af2-216">Objectives</span></span>

* <span data-ttu-id="88af2-217">Управлять вашей голограммы с выберите жестом.</span><span class="sxs-lookup"><span data-stu-id="88af2-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="88af2-218">Инструкция</span><span class="sxs-lookup"><span data-stu-id="88af2-218">Instructions</span></span>

<span data-ttu-id="88af2-219">Мы начнем путем создания скрипта, не может обнаружить выберите жест.</span><span class="sxs-lookup"><span data-stu-id="88af2-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="88af2-220">В **сценарии** папки, создайте сценарий с именем **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="88af2-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="88af2-221">Перетащите **GazeGestureManager** скрипт на **OrigamiCollection** объект в иерархии.</span><span class="sxs-lookup"><span data-stu-id="88af2-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="88af2-222">Откройте **GazeGestureManager** сценариев в Visual Studio и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="88af2-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="88af2-223">Создание другого сценария в папке Scripts, это время с именем **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="88af2-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="88af2-224">Разверните **OrigamiCollection** объекта в иерархическом представлении.</span><span class="sxs-lookup"><span data-stu-id="88af2-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="88af2-225">Перетащите **SphereCommands** скрипт на **Sphere1** объект на панели «иерархии».</span><span class="sxs-lookup"><span data-stu-id="88af2-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="88af2-226">Перетащите **SphereCommands** скрипт на **Sphere2** объект на панели «иерархии».</span><span class="sxs-lookup"><span data-stu-id="88af2-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="88af2-227">Откройте скрипт в Visual Studio для редактирования и замените код по умолчанию это:</span><span class="sxs-lookup"><span data-stu-id="88af2-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="88af2-228">Экспорт, создавайте и развертывайте приложения в эмуляторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88af2-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="88af2-229">Оглядитесь сцены; центр на одном из сферы.</span><span class="sxs-lookup"><span data-stu-id="88af2-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="88af2-230">Нажмите клавишу **A** кнопку на Xbox контроллере или клавишу ПРОБЕЛ, чтобы имитировать выберите жест.</span><span class="sxs-lookup"><span data-stu-id="88af2-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="88af2-231">Глава 4 – голоса</span><span class="sxs-lookup"><span data-stu-id="88af2-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="88af2-232">В этой главе мы добавим поддержку для двух [голосовые команды](voice-input.md): Возвращает «Сброс world», чтобы удаленные как шары, расположенные в их исходное расположение и «Drop sphere» чтобы делятся сферы.</span><span class="sxs-lookup"><span data-stu-id="88af2-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="88af2-233">Цели</span><span class="sxs-lookup"><span data-stu-id="88af2-233">Objectives</span></span>

* <span data-ttu-id="88af2-234">Добавьте голосовые команды, которые всегда ожидать передачи данных в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="88af2-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="88af2-235">Создайте голограмма, на которое реагирует на команды голосом.</span><span class="sxs-lookup"><span data-stu-id="88af2-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="88af2-236">Инструкция</span><span class="sxs-lookup"><span data-stu-id="88af2-236">Instructions</span></span>

* <span data-ttu-id="88af2-237">В **сценарии** папки, создайте сценарий с именем **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="88af2-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="88af2-238">Перетащите **SpeechManager** скрипт на **OrigamiCollection** объект в иерархии</span><span class="sxs-lookup"><span data-stu-id="88af2-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="88af2-239">Откройте **SpeechManager** скриптов в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88af2-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="88af2-240">Скопируйте и вставьте этот код в **SpeechManager.cs** и **сохранить все**:</span><span class="sxs-lookup"><span data-stu-id="88af2-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="88af2-241">Откройте **SphereCommands** скриптов в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88af2-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="88af2-242">Обновите сценарий следующим образом:</span><span class="sxs-lookup"><span data-stu-id="88af2-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="88af2-243">Экспорт, создавайте и развертывайте приложения в эмуляторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88af2-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="88af2-244">Эмулятор будет поддерживать "микрофон" компьютер и отвечать на ваш голос: настроить представление, чтобы курсор находится на одном из сферы, и сказать «Drop Sphere».</span><span class="sxs-lookup"><span data-stu-id="88af2-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="88af2-245">Сказать «**Сброс World**"Чтобы вернуть их обратно в их начальной позиции.</span><span class="sxs-lookup"><span data-stu-id="88af2-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="88af2-246">Глава 5 - Пространственные звука</span><span class="sxs-lookup"><span data-stu-id="88af2-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="88af2-247">В этой главе мы добавить музыку в приложение и затем активировать звуковые эффекты на определенные действия.</span><span class="sxs-lookup"><span data-stu-id="88af2-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="88af2-248">Мы будем использовать [пространственных звук](spatial-sound.md) для предоставления звуков на определенное расположение в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="88af2-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="88af2-249">Цели</span><span class="sxs-lookup"><span data-stu-id="88af2-249">Objectives</span></span>

* <span data-ttu-id="88af2-250">Услышать голограммы в ваш мир.</span><span class="sxs-lookup"><span data-stu-id="88af2-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="88af2-251">Инструкция</span><span class="sxs-lookup"><span data-stu-id="88af2-251">Instructions</span></span>

* <span data-ttu-id="88af2-252">В верхнем меню выберите Unity **изменить > Параметры проекта > аудио**</span><span class="sxs-lookup"><span data-stu-id="88af2-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="88af2-253">Найти **подключаемый модуль Spatializer** задание и выберите **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="88af2-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="88af2-254">Из **голограммы** папки, перетащите **окружением** объекта на **OrigamiCollection** объект на панели «иерархии».</span><span class="sxs-lookup"><span data-stu-id="88af2-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="88af2-255">Выберите **OrigamiCollection** и найти **источника аудио** компонента.</span><span class="sxs-lookup"><span data-stu-id="88af2-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="88af2-256">Измените следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="88af2-256">Change these properties:</span></span>
  * <span data-ttu-id="88af2-257">Проверьте **Spatialize** свойство.</span><span class="sxs-lookup"><span data-stu-id="88af2-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="88af2-258">Проверьте **играть на переходит в спящий режим**.</span><span class="sxs-lookup"><span data-stu-id="88af2-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="88af2-259">Изменение **пространственных Blend** для **3D** путем перетаскивания бегунка вплоть до справа.</span><span class="sxs-lookup"><span data-stu-id="88af2-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="88af2-260">Проверьте **цикл** свойство.</span><span class="sxs-lookup"><span data-stu-id="88af2-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="88af2-261">Разверните **3D Параметры звука**и введите **0,1** для **Doppler уровень**.</span><span class="sxs-lookup"><span data-stu-id="88af2-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="88af2-262">Задайте **Rolloff тома** для **логарифмической Rolloff**.</span><span class="sxs-lookup"><span data-stu-id="88af2-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="88af2-263">Задайте **максимальное расстояние** для **20**.</span><span class="sxs-lookup"><span data-stu-id="88af2-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="88af2-264">В **сценарии** папки, создайте сценарий с именем **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="88af2-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="88af2-265">Перетащите **SphereSounds** для **Sphere1** и **Sphere2** объектов в иерархии.</span><span class="sxs-lookup"><span data-stu-id="88af2-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="88af2-266">Откройте **SphereSounds** в Visual Studio, измените следующий код и **сохранить все**.</span><span class="sxs-lookup"><span data-stu-id="88af2-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="88af2-267">Сохраните сценарий и вернуться к Unity.</span><span class="sxs-lookup"><span data-stu-id="88af2-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="88af2-268">Экспорт, создавайте и развертывайте приложения в эмуляторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88af2-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="88af2-269">Надеть наушники получить полные результаты и переместить ближе и максимально далеко от рабочей области звуковое изменить.</span><span class="sxs-lookup"><span data-stu-id="88af2-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="88af2-270">Глава 6 - пространственных сопоставление</span><span class="sxs-lookup"><span data-stu-id="88af2-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="88af2-271">Теперь мы собираемся использовать [пространственное сопоставление](spatial-mapping.md) снабдить реальный объект в реальном мире игровое поле.</span><span class="sxs-lookup"><span data-stu-id="88af2-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="88af2-272">Цели</span><span class="sxs-lookup"><span data-stu-id="88af2-272">Objectives</span></span>

* <span data-ttu-id="88af2-273">Можно открыть в реальном мире в виртуальный мир.</span><span class="sxs-lookup"><span data-stu-id="88af2-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="88af2-274">Поместите вашей голограммы, где они наиболее важны для вас.</span><span class="sxs-lookup"><span data-stu-id="88af2-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="88af2-275">Инструкция</span><span class="sxs-lookup"><span data-stu-id="88af2-275">Instructions</span></span>

* <span data-ttu-id="88af2-276">Щелкните **голограммы** папку «проект».</span><span class="sxs-lookup"><span data-stu-id="88af2-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="88af2-277">Перетащите **пространственных сопоставление** активов в корне **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="88af2-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="88af2-278">Щелкните **пространственных сопоставление** объект в иерархии.</span><span class="sxs-lookup"><span data-stu-id="88af2-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="88af2-279">В **панели Инспектора**, измените следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="88af2-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="88af2-280">Проверьте **рисования сетки Visual** поле.</span><span class="sxs-lookup"><span data-stu-id="88af2-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="88af2-281">Найдите **рисования материал** и щелкните этот кружок в правой части.</span><span class="sxs-lookup"><span data-stu-id="88af2-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="88af2-282">Тип "**каркас**" в поле поиска вверху.</span><span class="sxs-lookup"><span data-stu-id="88af2-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="88af2-283">Щелкните результат, а затем закройте окно.</span><span class="sxs-lookup"><span data-stu-id="88af2-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="88af2-284">Экспорт, создавайте и развертывайте приложения в эмуляторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88af2-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="88af2-285">При запуске приложения, сетка ранее отсканированных реальных гостиной отображается в области каркаса.</span><span class="sxs-lookup"><span data-stu-id="88af2-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="88af2-286">Смотрите, как последовательное сферы попадает off рабочей области, а также на пол!</span><span class="sxs-lookup"><span data-stu-id="88af2-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="88af2-287">Теперь мы покажем, как переместить OrigamiCollection в новое расположение:</span><span class="sxs-lookup"><span data-stu-id="88af2-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="88af2-288">В **сценарии** папки, создайте сценарий с именем **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="88af2-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="88af2-289">В **иерархии**, разверните **OrigamiCollection** и выберите **этап** объекта.</span><span class="sxs-lookup"><span data-stu-id="88af2-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="88af2-290">Перетащите **TapToPlaceParent** скрипт на объект, к рабочей области.</span><span class="sxs-lookup"><span data-stu-id="88af2-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="88af2-291">Откройте **TapToPlaceParent** сценариев в Visual Studio и обновить его следующим:</span><span class="sxs-lookup"><span data-stu-id="88af2-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="88af2-292">Экспорт, построения и развертывания приложения.</span><span class="sxs-lookup"><span data-stu-id="88af2-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="88af2-293">Теперь теперь можно поместить игры в определенном расположении путем gazing на него, используя Select жестов (**объект** или пробел) и перемещения в новое расположение и еще раз с помощью Select жест.</span><span class="sxs-lookup"><span data-stu-id="88af2-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="88af2-294">Конец</span><span class="sxs-lookup"><span data-stu-id="88af2-294">The end</span></span>

<span data-ttu-id="88af2-295">И это, чтобы в конце этого руководства!</span><span class="sxs-lookup"><span data-stu-id="88af2-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="88af2-296">Вы узнали:</span><span class="sxs-lookup"><span data-stu-id="88af2-296">You learned:</span></span>

* <span data-ttu-id="88af2-297">Как создать приложение holographic в Unity.</span><span class="sxs-lookup"><span data-stu-id="88af2-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="88af2-298">Как сделать использование взглядом, жест, голоса, звуки и пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="88af2-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="88af2-299">Как создавать и развертывать приложения с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88af2-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="88af2-300">Теперь вы готовы приступить к созданию собственных holographic приложений!</span><span class="sxs-lookup"><span data-stu-id="88af2-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="88af2-301">См. также</span><span class="sxs-lookup"><span data-stu-id="88af2-301">See also</span></span>

* [<span data-ttu-id="88af2-302">Общие сведения об MR 101: Полный проект с устройством</span><span class="sxs-lookup"><span data-stu-id="88af2-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="88af2-303">Взглядом</span><span class="sxs-lookup"><span data-stu-id="88af2-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="88af2-304">Жесты</span><span class="sxs-lookup"><span data-stu-id="88af2-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="88af2-305">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="88af2-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="88af2-306">Пространственные звука</span><span class="sxs-lookup"><span data-stu-id="88af2-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="88af2-307">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="88af2-307">Spatial mapping</span></span>](spatial-mapping.md)
