---
title: Основы MR 101 - полный проект с устройством
description: Выполнения данного кода пошагового руководства, с помощью Unity, Visual Studio и HoloLens, чтобы ознакомиться с основами Windows смешанной реальности.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: смешанной реальности, смешанной реальности Windows, HoloLens, голограмма, academy, учебник
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599359"
---
>[!NOTE]
><span data-ttu-id="36892-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="36892-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="36892-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="36892-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="36892-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="36892-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="36892-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="36892-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="36892-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="36892-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="36892-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="36892-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="36892-110">MR Basics 101: Полный проект с устройством</span><span class="sxs-lookup"><span data-stu-id="36892-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="36892-111">Этот учебник поможет в проекте, встроенные в Unity, который демонстрирует основные возможности Windows Mixed Reality, в том числе HoloLens [помощи](gaze.md), [жесты](gestures.md), [голоса](voice-input.md), [пространственных звук](spatial-sound.md) и [пространственное сопоставление](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="36892-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="36892-112">Руководства займет примерно 1 час.</span><span class="sxs-lookup"><span data-stu-id="36892-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="36892-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="36892-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="36892-114">Курс</span><span class="sxs-lookup"><span data-stu-id="36892-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="36892-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36892-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36892-116"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="36892-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="36892-117">MR Basics 101: Полный проект с устройством</span><span class="sxs-lookup"><span data-stu-id="36892-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="36892-118">✔️</span><span class="sxs-lookup"><span data-stu-id="36892-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="36892-119">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="36892-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="36892-120">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="36892-120">Prerequisites</span></span>

* <span data-ttu-id="36892-121">ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="36892-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="36892-122">Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="36892-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="36892-123">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="36892-123">Project files</span></span>

* <span data-ttu-id="36892-124">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) требуемые для проекта.</span><span class="sxs-lookup"><span data-stu-id="36892-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="36892-125"> Требуется компонент Unity 2017.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="36892-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="36892-126">Если вам по-прежнему требуется поддержка Unity 5.6, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="36892-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="36892-127">Если вам по-прежнему требуется поддержка Unity 5.5, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="36892-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="36892-128">Если вам по-прежнему требуется поддержка Unity 5.4, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="36892-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="36892-129">Удаление архива файлы рабочего стола или других легко положения.</span><span class="sxs-lookup"><span data-stu-id="36892-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="36892-130">Оставьте имя папки в качестве **Origami**.</span><span class="sxs-lookup"><span data-stu-id="36892-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="36892-131">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="36892-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="36892-132">Глава 1 - world «Holo»</span><span class="sxs-lookup"><span data-stu-id="36892-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="36892-133">В этой главе мы установки наш первый проект Unity и пошагово выполнять построение и развертывание процесса.</span><span class="sxs-lookup"><span data-stu-id="36892-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="36892-134">Цели</span><span class="sxs-lookup"><span data-stu-id="36892-134">Objectives</span></span>

* <span data-ttu-id="36892-135">Настройка Unity для holographic разработки.</span><span class="sxs-lookup"><span data-stu-id="36892-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="36892-136">Сделайте голограмма.</span><span class="sxs-lookup"><span data-stu-id="36892-136">Make a hologram.</span></span>
* <span data-ttu-id="36892-137">См. в разделе голограмма, созданную.</span><span class="sxs-lookup"><span data-stu-id="36892-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="36892-138">Инструкция</span><span class="sxs-lookup"><span data-stu-id="36892-138">Instructions</span></span>

* <span data-ttu-id="36892-139">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="36892-139">Start Unity.</span></span>
* <span data-ttu-id="36892-140">Выберите **откройте**.</span><span class="sxs-lookup"><span data-stu-id="36892-140">Select **Open**.</span></span>
* <span data-ttu-id="36892-141">Введите расположение как **Origami** папку вы ранее не архивные.</span><span class="sxs-lookup"><span data-stu-id="36892-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="36892-142">Выберите **Origami** и нажмите кнопку **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="36892-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="36892-143">Так как **Origami** проект не содержит сцены, сохраните сцену пустым по умолчанию в новый файл с помощью: **Файл** / **сохранить сцену как**.</span><span class="sxs-lookup"><span data-stu-id="36892-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="36892-144">Назовите новую сцену **Origami** и нажмите клавишу **Сохранить** кнопки.</span><span class="sxs-lookup"><span data-stu-id="36892-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="36892-145">Настройка главной виртуальной камеры</span><span class="sxs-lookup"><span data-stu-id="36892-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="36892-146">В **панели иерархии**выберите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="36892-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="36892-147">В **инспектор** задайте его положение преобразования **0,0,0**.</span><span class="sxs-lookup"><span data-stu-id="36892-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="36892-148">Найти **очистить флаги** свойство и измените раскрывающийся список из **Skybox** для **Одноцветная**.</span><span class="sxs-lookup"><span data-stu-id="36892-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="36892-149">Щелкните **фона** поля, чтобы открыть палитру цветов.</span><span class="sxs-lookup"><span data-stu-id="36892-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="36892-150">Задайте **R, G, B и A** для **0**.</span><span class="sxs-lookup"><span data-stu-id="36892-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="36892-151">Программа установки сцены</span><span class="sxs-lookup"><span data-stu-id="36892-151">Setup the scene</span></span>

* <span data-ttu-id="36892-152">В **панели иерархии**, щелкните **создать** и **создать пустой**.</span><span class="sxs-lookup"><span data-stu-id="36892-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="36892-153">Щелкните правой кнопкой мыши новый **GameObject** и выберите Переименовать.</span><span class="sxs-lookup"><span data-stu-id="36892-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="36892-154">Переименовать объект GameObject, чтобы **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="36892-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="36892-155">Из **голограммы** папку «проект» (развернуть ресурсы и выберите голограммы или дважды щелкните папку голограммы «проект»):</span><span class="sxs-lookup"><span data-stu-id="36892-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="36892-156">Перетащите **этап** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="36892-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="36892-157">Перетащите **Sphere1** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="36892-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="36892-158">Перетащите **Sphere2** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="36892-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="36892-159">Щелкните правой кнопкой мыши **направленный свет** объекта в **панели иерархии** и выберите **удалить**.</span><span class="sxs-lookup"><span data-stu-id="36892-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="36892-160">Из **голограммы** папки, перетащите **индикаторы** в корне **панели иерархии**.</span><span class="sxs-lookup"><span data-stu-id="36892-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="36892-161">В **иерархии**выберите **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="36892-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="36892-162">В **инспектор**, задайте положение преобразования **0, -0,5, 2.0**.</span><span class="sxs-lookup"><span data-stu-id="36892-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="36892-163">Нажмите клавишу **воспроизведение** кнопки в Unity для предварительного просмотра вашего голограммы.</span><span class="sxs-lookup"><span data-stu-id="36892-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="36892-164">Вы увидите Origami объекты в окне предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="36892-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="36892-165">Нажмите клавишу **воспроизведение** второй раз, чтобы выйти из режима предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="36892-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="36892-166">Экспортировать проект из Unity в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36892-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="36892-167">В Unity выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="36892-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="36892-168">Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="36892-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="36892-169">Задайте **SDK** для **универсальной 10** и **тип сборки** для **D3D**.</span><span class="sxs-lookup"><span data-stu-id="36892-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="36892-170">Проверьте **Unity C# проекты**.</span><span class="sxs-lookup"><span data-stu-id="36892-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="36892-171">Нажмите кнопку **добавьте откройте сцены** Добавление сцены.</span><span class="sxs-lookup"><span data-stu-id="36892-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="36892-172">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="36892-172">Click **Build**.</span></span>
* <span data-ttu-id="36892-173">В обозревателе файл создать **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="36892-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="36892-174">Одним щелчком мыши **папки приложения**.</span><span class="sxs-lookup"><span data-stu-id="36892-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="36892-175">Нажмите клавишу **выберите папку**.</span><span class="sxs-lookup"><span data-stu-id="36892-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="36892-176">По завершении Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="36892-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="36892-177">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="36892-177">Open the **App** folder.</span></span>
* <span data-ttu-id="36892-178">Открыть (двойной щелчок) **Origami.sln**.</span><span class="sxs-lookup"><span data-stu-id="36892-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="36892-179">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **X86**.</span><span class="sxs-lookup"><span data-stu-id="36892-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="36892-180">Щелкните стрелку рядом с кнопкой на устройстве и выберите **удаленный компьютер** для развертывания по Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="36892-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="36892-181">Задайте **адрес** в имя или IP-адрес вашего HoloLens.</span><span class="sxs-lookup"><span data-stu-id="36892-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="36892-182">Если вы не знаете IP-адрес устройства, найдите в **параметры > сеть и Интернет > Дополнительно** или попросить Cortana **«Привет, Кортана, что такое Мой IP-адрес?»**</span><span class="sxs-lookup"><span data-stu-id="36892-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="36892-183">HoloLens, подключенного через USB, можно вместо этого выбрать **устройства** для развертывания по USB.</span><span class="sxs-lookup"><span data-stu-id="36892-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="36892-184">Оставьте **режим проверки подлинности** присвоено **универсальной**.</span><span class="sxs-lookup"><span data-stu-id="36892-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="36892-185">Нажмите кнопку **выберите**</span><span class="sxs-lookup"><span data-stu-id="36892-185">Click **Select**</span></span>

* <span data-ttu-id="36892-186">Нажмите кнопку **Отладка > Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="36892-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="36892-187">Если это при первом развертывании к устройству, необходимо будет [свяжите его с помощью Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span><span class="sxs-lookup"><span data-stu-id="36892-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="36892-188">Проект Origami будет теперь сборки, развертывания вашей HoloLens и запустите.</span><span class="sxs-lookup"><span data-stu-id="36892-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="36892-189">Поместите на вашей HoloLens и оглядитесь для вашего нового голограммы см. в разделе.</span><span class="sxs-lookup"><span data-stu-id="36892-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="36892-190">Глава 2 - взглядом</span><span class="sxs-lookup"><span data-stu-id="36892-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="36892-191">В этой главе мы собираемся установки первого из трех способов взаимодействия с вашей голограммы-- [помощи](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="36892-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="36892-192">Цели</span><span class="sxs-lookup"><span data-stu-id="36892-192">Objectives</span></span>

* <span data-ttu-id="36892-193">Визуализация вашей взглядом, с помощью курсора заблокирован в мире.</span><span class="sxs-lookup"><span data-stu-id="36892-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="36892-194">Инструкция</span><span class="sxs-lookup"><span data-stu-id="36892-194">Instructions</span></span>

* <span data-ttu-id="36892-195">Вернитесь к проекту Unity и закрыть окно Параметры построения, если он по-прежнему открыт.</span><span class="sxs-lookup"><span data-stu-id="36892-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="36892-196">Выберите **голограммы** папку в **панель проекта**.</span><span class="sxs-lookup"><span data-stu-id="36892-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="36892-197">Перетащите **курсор** в коллекцию **панели иерархии** на корневом уровне.</span><span class="sxs-lookup"><span data-stu-id="36892-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="36892-198">Дважды щелкните **курсор** объекта более подробно рассмотрим вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="36892-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="36892-199">Щелкните правой кнопкой мыши **сценариев** папку «проект».</span><span class="sxs-lookup"><span data-stu-id="36892-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="36892-200">Нажмите кнопку **создать** подменю.</span><span class="sxs-lookup"><span data-stu-id="36892-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="36892-201">Выберите  **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="36892-201">Select **C# Script**.</span></span>
* <span data-ttu-id="36892-202">Назовите сценарий **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="36892-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="36892-203">Примечание. Имя обрабатывается с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="36892-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="36892-204">Необходимо добавить расширение CS.</span><span class="sxs-lookup"><span data-stu-id="36892-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="36892-205">Выберите **курсор** объекта в **панели иерархии**.</span><span class="sxs-lookup"><span data-stu-id="36892-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="36892-206">Перетаскивание **WorldCursor** внесена в **панели Инспектора**.</span><span class="sxs-lookup"><span data-stu-id="36892-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="36892-207">Дважды щелкните **WorldCursor** скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36892-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="36892-208">Скопируйте и вставьте этот код в **WorldCursor.cs** и **сохранить все**.</span><span class="sxs-lookup"><span data-stu-id="36892-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="36892-209">Перестройте приложение из **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="36892-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="36892-210">Вернитесь к ранее используется для развертывания вашего HoloLens решения Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36892-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="36892-211">Выберите «Обновить все» при появлении запроса.</span><span class="sxs-lookup"><span data-stu-id="36892-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="36892-212">Нажмите кнопку **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="36892-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="36892-213">Теперь оглядитесь сцены и обратите внимание на то, как курсор взаимодействует с форму объектов.</span><span class="sxs-lookup"><span data-stu-id="36892-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="36892-214">Глава 3 - жесты</span><span class="sxs-lookup"><span data-stu-id="36892-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="36892-215">В этой главе мы добавим поддержку [жесты](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="36892-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="36892-216">Когда пользователь выбирает сферы бумаги, сделаем сферы делятся, включив гравитации, с помощью обработчика физики Unity.</span><span class="sxs-lookup"><span data-stu-id="36892-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="36892-217">Цели</span><span class="sxs-lookup"><span data-stu-id="36892-217">Objectives</span></span>

* <span data-ttu-id="36892-218">Управлять вашей голограммы с выберите жестом.</span><span class="sxs-lookup"><span data-stu-id="36892-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="36892-219">Инструкция</span><span class="sxs-lookup"><span data-stu-id="36892-219">Instructions</span></span>

<span data-ttu-id="36892-220">Мы начнем с создания сценария, то может обнаружить выберите жест.</span><span class="sxs-lookup"><span data-stu-id="36892-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="36892-221">В **сценарии** папки, создайте сценарий с именем **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="36892-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="36892-222">Перетащите **GazeGestureManager** скрипт на **OrigamiCollection** объект в иерархии.</span><span class="sxs-lookup"><span data-stu-id="36892-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="36892-223">Откройте **GazeGestureManager** сценариев в Visual Studio и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="36892-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="36892-224">Создание другого сценария в папке Scripts, это время с именем **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="36892-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="36892-225">Разверните **OrigamiCollection** объекта в иерархическом представлении.</span><span class="sxs-lookup"><span data-stu-id="36892-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="36892-226">Перетащите **SphereCommands** скрипт на **Sphere1** объект на панели «иерархии».</span><span class="sxs-lookup"><span data-stu-id="36892-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="36892-227">Перетащите **SphereCommands** скрипт на **Sphere2** объект на панели «иерархии».</span><span class="sxs-lookup"><span data-stu-id="36892-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="36892-228">Откройте скрипт в Visual Studio для редактирования и замените код по умолчанию это:</span><span class="sxs-lookup"><span data-stu-id="36892-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="36892-229">Экспорт, построение и развертывание приложения в вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="36892-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="36892-230">Рассмотрим один из сферы.</span><span class="sxs-lookup"><span data-stu-id="36892-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="36892-231">Сделайте жест select и просмотр сферы фигуру на область, расположенную ниже.</span><span class="sxs-lookup"><span data-stu-id="36892-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="36892-232">Глава 4 – голоса</span><span class="sxs-lookup"><span data-stu-id="36892-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="36892-233">В этой главе мы добавим поддержку для двух [голосовые команды](voice-input.md): «Сброс world» вернуть удаленные как шары, расположенные в их исходное расположение, перетаскивания «сферы» чтобы делятся сферы.</span><span class="sxs-lookup"><span data-stu-id="36892-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="36892-234">Цели</span><span class="sxs-lookup"><span data-stu-id="36892-234">Objectives</span></span>

* <span data-ttu-id="36892-235">Добавьте голосовые команды, которые всегда ожидать передачи данных в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="36892-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="36892-236">Создайте голограмма, на которое реагирует на команды голосом.</span><span class="sxs-lookup"><span data-stu-id="36892-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="36892-237">Инструкция</span><span class="sxs-lookup"><span data-stu-id="36892-237">Instructions</span></span>

* <span data-ttu-id="36892-238">В **сценарии** папки, создайте сценарий с именем **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="36892-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="36892-239">Перетащите **SpeechManager** скрипт на **OrigamiCollection** объект в иерархии</span><span class="sxs-lookup"><span data-stu-id="36892-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="36892-240">Откройте **SpeechManager** скриптов в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36892-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="36892-241">Скопируйте и вставьте этот код в **SpeechManager.cs** и **сохранить все**:</span><span class="sxs-lookup"><span data-stu-id="36892-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="36892-242">Откройте **SphereCommands** скриптов в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36892-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="36892-243">Обновите сценарий следующим образом:</span><span class="sxs-lookup"><span data-stu-id="36892-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="36892-244">Экспорт, построение и развертывание приложения в вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="36892-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="36892-245">Посмотреть на один из сферы и сказать «**Drop Sphere**«.</span><span class="sxs-lookup"><span data-stu-id="36892-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="36892-246">Сказать «**Сброс World**"Чтобы вернуть их обратно в их начальной позиции.</span><span class="sxs-lookup"><span data-stu-id="36892-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="36892-247">Глава 5 - Пространственные звука</span><span class="sxs-lookup"><span data-stu-id="36892-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="36892-248">В этой главе мы добавить музыку в приложение и затем активировать звуковые эффекты на определенные действия.</span><span class="sxs-lookup"><span data-stu-id="36892-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="36892-249">Мы будем использовать [пространственных звук](spatial-sound.md) для предоставления звуков на определенное расположение в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="36892-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="36892-250">Цели</span><span class="sxs-lookup"><span data-stu-id="36892-250">Objectives</span></span>

* <span data-ttu-id="36892-251">Услышать голограммы в ваш мир.</span><span class="sxs-lookup"><span data-stu-id="36892-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="36892-252">Инструкция</span><span class="sxs-lookup"><span data-stu-id="36892-252">Instructions</span></span>

* <span data-ttu-id="36892-253">В Unity выберите в верхнем меню **изменить > Параметры проекта > аудио**</span><span class="sxs-lookup"><span data-stu-id="36892-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="36892-254">В правой части панели Инспектора найти **подключаемый модуль Spatializer** задание и выберите **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="36892-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="36892-255">Из **голограммы** папку «проект», перетащите **окружением** объекта на **OrigamiCollection** объект на панели «иерархии».</span><span class="sxs-lookup"><span data-stu-id="36892-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="36892-256">Выберите **OrigamiCollection** и найти **источника аудио** компонент на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="36892-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="36892-257">Измените следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="36892-257">Change these properties:</span></span>
  * <span data-ttu-id="36892-258">Проверьте **Spatialize** свойство.</span><span class="sxs-lookup"><span data-stu-id="36892-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="36892-259">Проверьте **играть на переходит в спящий режим**.</span><span class="sxs-lookup"><span data-stu-id="36892-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="36892-260">Изменение **пространственных Blend** для **3D** путем перетаскивания бегунка вплоть до справа.</span><span class="sxs-lookup"><span data-stu-id="36892-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="36892-261">Значение должно изменяться от 0 до 1, при перемещении ползунка.</span><span class="sxs-lookup"><span data-stu-id="36892-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="36892-262">Проверьте **цикл** свойство.</span><span class="sxs-lookup"><span data-stu-id="36892-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="36892-263">Разверните **3D Параметры звука**и введите **0,1** для **Doppler уровень**.</span><span class="sxs-lookup"><span data-stu-id="36892-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="36892-264">Задайте **Rolloff тома** для **логарифмической Rolloff**.</span><span class="sxs-lookup"><span data-stu-id="36892-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="36892-265">Задайте **максимальное расстояние** для **20**.</span><span class="sxs-lookup"><span data-stu-id="36892-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="36892-266">В **сценарии** папки, создайте сценарий с именем **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="36892-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="36892-267">Перетаскивание **SphereSounds** для **Sphere1** и **Sphere2** объектов в иерархии.</span><span class="sxs-lookup"><span data-stu-id="36892-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="36892-268">Откройте **SphereSounds** в Visual Studio, измените следующий код и **сохранить все**.</span><span class="sxs-lookup"><span data-stu-id="36892-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="36892-269">Сохраните сценарий и вернуться к Unity.</span><span class="sxs-lookup"><span data-stu-id="36892-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="36892-270">Экспорт, построение и развертывание приложения в вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="36892-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="36892-271">Переместите ближе и максимально далеко от рабочей области и включить для параллельных звуковое изменить.</span><span class="sxs-lookup"><span data-stu-id="36892-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="36892-272">Глава 6 - пространственных сопоставление</span><span class="sxs-lookup"><span data-stu-id="36892-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="36892-273">Теперь мы собираемся использовать [пространственное сопоставление](spatial-mapping.md) снабдить реальный объект в реальном мире игровое поле.</span><span class="sxs-lookup"><span data-stu-id="36892-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="36892-274">Цели</span><span class="sxs-lookup"><span data-stu-id="36892-274">Objectives</span></span>

* <span data-ttu-id="36892-275">Можно открыть в реальном мире в виртуальный мир.</span><span class="sxs-lookup"><span data-stu-id="36892-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="36892-276">Поместите вашей голограммы, где они наиболее важны для вас.</span><span class="sxs-lookup"><span data-stu-id="36892-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="36892-277">Инструкция</span><span class="sxs-lookup"><span data-stu-id="36892-277">Instructions</span></span>

* <span data-ttu-id="36892-278">В Unity, щелкните **голограммы** папку «проект».</span><span class="sxs-lookup"><span data-stu-id="36892-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="36892-279">Перетащите **пространственных сопоставление** активов в корне **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="36892-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="36892-280">Щелкните **пространственных сопоставление** объект в иерархии.</span><span class="sxs-lookup"><span data-stu-id="36892-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="36892-281">В **панели Инспектора**, измените следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="36892-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="36892-282">Проверьте **рисования сетки Visual** поле.</span><span class="sxs-lookup"><span data-stu-id="36892-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="36892-283">Найдите **рисования материал** и щелкните этот кружок в правой части.</span><span class="sxs-lookup"><span data-stu-id="36892-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="36892-284">Тип "**каркас**" в поле поиска вверху.</span><span class="sxs-lookup"><span data-stu-id="36892-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="36892-285">Щелкните результат, а затем закройте окно.</span><span class="sxs-lookup"><span data-stu-id="36892-285">Click on the result and then close the window.</span></span> <span data-ttu-id="36892-286">При этом для рисования материал должен получить значение каркасной модели.</span><span class="sxs-lookup"><span data-stu-id="36892-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="36892-287">Экспорт, построение и развертывание приложения в вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="36892-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="36892-288">При запуске приложения, каркаса сетки отправляет сообщение в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="36892-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="36892-289">Смотрите, как последовательное сферы попадает off рабочей области, а также на пол!</span><span class="sxs-lookup"><span data-stu-id="36892-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="36892-290">Теперь мы покажем, как переместить OrigamiCollection в новое расположение:</span><span class="sxs-lookup"><span data-stu-id="36892-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="36892-291">В **сценарии** папки, создайте сценарий с именем **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="36892-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="36892-292">В **иерархии**, разверните **OrigamiCollection** и выберите **этап** объекта.</span><span class="sxs-lookup"><span data-stu-id="36892-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="36892-293">Перетащите **TapToPlaceParent** скрипт на объект, к рабочей области.</span><span class="sxs-lookup"><span data-stu-id="36892-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="36892-294">Откройте **TapToPlaceParent** сценариев в Visual Studio и обновить его следующим:</span><span class="sxs-lookup"><span data-stu-id="36892-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="36892-295">Экспорт, построения и развертывания приложения.</span><span class="sxs-lookup"><span data-stu-id="36892-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="36892-296">Теперь теперь можно поместить игры в определенном расположении путем gazing на него, с помощью Select жест перемещения в новое расположение и еще раз с помощью Select жест.</span><span class="sxs-lookup"><span data-stu-id="36892-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="36892-297">Глава 7 - Holographic fun</span><span class="sxs-lookup"><span data-stu-id="36892-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="36892-298">Цели</span><span class="sxs-lookup"><span data-stu-id="36892-298">Objectives</span></span>

* <span data-ttu-id="36892-299">Показать входом holographic underworld.</span><span class="sxs-lookup"><span data-stu-id="36892-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="36892-300">Инструкция</span><span class="sxs-lookup"><span data-stu-id="36892-300">Instructions</span></span>

<span data-ttu-id="36892-301">Теперь мы покажем, как выявлять holographic underworld:</span><span class="sxs-lookup"><span data-stu-id="36892-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="36892-302">Из **голограммы** папку «проект»:</span><span class="sxs-lookup"><span data-stu-id="36892-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="36892-303">Перетащите **Underworld** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="36892-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="36892-304">В **сценарии** папки, создайте сценарий с именем **HitTarget**.</span><span class="sxs-lookup"><span data-stu-id="36892-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="36892-305">В **иерархии**, разверните **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="36892-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="36892-306">Разверните **этап** объекта и выберите **целевой** объекта (синий вентилятора).</span><span class="sxs-lookup"><span data-stu-id="36892-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="36892-307">Перетащите **HitTarget** скрипт на **целевой** объекта.</span><span class="sxs-lookup"><span data-stu-id="36892-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="36892-308">Откройте **HitTarget** сценариев в Visual Studio и обновить его следующим:</span><span class="sxs-lookup"><span data-stu-id="36892-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="36892-309">В Unity, выберите **целевой** объекта.</span><span class="sxs-lookup"><span data-stu-id="36892-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="36892-310">Два открытых свойства теперь отображаются на **попаданий целевой** компонента и необходимости ссылаться на объекты в сцене наших:</span><span class="sxs-lookup"><span data-stu-id="36892-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="36892-311">Перетащите **Underworld** из **иерархии** панели **Underworld** свойство **попаданий целевой** компонента.</span><span class="sxs-lookup"><span data-stu-id="36892-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="36892-312">Перетащите **этап** из **иерархии** панели **объекта, чтобы скрыть** свойство **попаданий целевой** компонента.</span><span class="sxs-lookup"><span data-stu-id="36892-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="36892-313">Экспорт, построения и развертывания приложения.</span><span class="sxs-lookup"><span data-stu-id="36892-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="36892-314">Размещение коллекции Origami на ближайшее снизу целое и затем использовать жест Select для принятия сферы drop.</span><span class="sxs-lookup"><span data-stu-id="36892-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="36892-315">Когда сферы достигает целевого (синий вентилятора), будет выполняться развертывание.</span><span class="sxs-lookup"><span data-stu-id="36892-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="36892-316">Коллекции будут скрыты, и появится отверстия для underworld.</span><span class="sxs-lookup"><span data-stu-id="36892-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="36892-317">Конец</span><span class="sxs-lookup"><span data-stu-id="36892-317">The end</span></span>

<span data-ttu-id="36892-318">И это, чтобы в конце этого руководства!</span><span class="sxs-lookup"><span data-stu-id="36892-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="36892-319">Вы узнали:</span><span class="sxs-lookup"><span data-stu-id="36892-319">You learned:</span></span>

* <span data-ttu-id="36892-320">Как создать приложение holographic в Unity.</span><span class="sxs-lookup"><span data-stu-id="36892-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="36892-321">Как сделать использование взглядом, жест, голоса, звук и пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="36892-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="36892-322">Как создавать и развертывать приложения с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36892-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="36892-323">Теперь вы готовы приступить к созданию собственных голографический интерфейс!</span><span class="sxs-lookup"><span data-stu-id="36892-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="36892-324">См. также</span><span class="sxs-lookup"><span data-stu-id="36892-324">See also</span></span>

* [<span data-ttu-id="36892-325">Общие сведения об MR 101E: Полный проект с помощью эмулятора</span><span class="sxs-lookup"><span data-stu-id="36892-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="36892-326">Взглядом</span><span class="sxs-lookup"><span data-stu-id="36892-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="36892-327">Жесты</span><span class="sxs-lookup"><span data-stu-id="36892-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="36892-328">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="36892-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="36892-329">Пространственные звука</span><span class="sxs-lookup"><span data-stu-id="36892-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="36892-330">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="36892-330">Spatial mapping</span></span>](spatial-mapping.md)
