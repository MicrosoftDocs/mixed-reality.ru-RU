---
title: Основные сведения о MR 101 — завершение проекта с помощью устройства
description: Для ознакомления с основами Windows Mixed Reality следуйте этому пошаговому руководству по созданию кода с помощью Unity, Visual Studio и HoloLens.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Смешанная реальность, Windows Mixed Reality, HoloLens, голограмма, Academy, учебник
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524025"
---
>[!NOTE]
><span data-ttu-id="ca51c-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="ca51c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ca51c-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="ca51c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ca51c-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ca51c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ca51c-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="ca51c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ca51c-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ca51c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ca51c-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="ca51c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="ca51c-110">Основные сведения о MR 101: Завершение проекта с помощью устройства</span><span class="sxs-lookup"><span data-stu-id="ca51c-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="ca51c-111">В этом руководстве описывается полный проект, встроенный в Unity, демонстрирующий основные функции Windows Mixed Reality в HoloLens, включая [взгляд](gaze.md), [жесты](gestures.md), [речевой ввод](voice-input.md), [пространственный звук](spatial-sound.md) и [пространственное сопоставление](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="ca51c-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="ca51c-112">Выполнение руководства займет примерно 1 час.</span><span class="sxs-lookup"><span data-stu-id="ca51c-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="ca51c-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="ca51c-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ca51c-114">Хождение</span><span class="sxs-lookup"><span data-stu-id="ca51c-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ca51c-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ca51c-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ca51c-116"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="ca51c-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="ca51c-117">Основные сведения о MR 101: Завершение проекта с помощью устройства</span><span class="sxs-lookup"><span data-stu-id="ca51c-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="ca51c-118">✔️</span><span class="sxs-lookup"><span data-stu-id="ca51c-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="ca51c-119">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="ca51c-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ca51c-120">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="ca51c-120">Prerequisites</span></span>

* <span data-ttu-id="ca51c-121">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="ca51c-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="ca51c-122">Устройство HoloLens, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="ca51c-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="ca51c-123">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="ca51c-123">Project files</span></span>

* <span data-ttu-id="ca51c-124">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="ca51c-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="ca51c-125"> Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ca51c-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="ca51c-126">Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="ca51c-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="ca51c-127">Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="ca51c-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="ca51c-128">Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="ca51c-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="ca51c-129">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="ca51c-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="ca51c-130">В качестве имени папки используйте **Origami**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="ca51c-131">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="ca51c-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="ca51c-132">Глава 1-"Холо"</span><span class="sxs-lookup"><span data-stu-id="ca51c-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="ca51c-133">В этой главе мы создадим наш первый проект Unity и пошаговым процессом сборки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="ca51c-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="ca51c-134">Цели</span><span class="sxs-lookup"><span data-stu-id="ca51c-134">Objectives</span></span>

* <span data-ttu-id="ca51c-135">Настройка Unity для разработки с Holographic.</span><span class="sxs-lookup"><span data-stu-id="ca51c-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="ca51c-136">Создайте голограмму.</span><span class="sxs-lookup"><span data-stu-id="ca51c-136">Make a hologram.</span></span>
* <span data-ttu-id="ca51c-137">Ознакомьтесь с созданной голограммой.</span><span class="sxs-lookup"><span data-stu-id="ca51c-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="ca51c-138">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ca51c-138">Instructions</span></span>

* <span data-ttu-id="ca51c-139">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="ca51c-139">Start Unity.</span></span>
* <span data-ttu-id="ca51c-140">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-140">Select **Open**.</span></span>
* <span data-ttu-id="ca51c-141">Введите Location в качестве папки **Origami** , которая была отменена для архивации.</span><span class="sxs-lookup"><span data-stu-id="ca51c-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="ca51c-142">Выберите **Origami** и щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="ca51c-143">Так как проект **Origami** не содержит сцены, сохраните пустую сцену по умолчанию в новом файле, используя:Файл / **сохранить сцену как**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="ca51c-144">Назовите новую сцену **Origami** и нажмите кнопку **Save (сохранить** ).</span><span class="sxs-lookup"><span data-stu-id="ca51c-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="ca51c-145">Настройка основной виртуальной камеры</span><span class="sxs-lookup"><span data-stu-id="ca51c-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="ca51c-146">На **панели Иерархия**выберите **Главная камера**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="ca51c-147">В инспекторе задайте для его параметра «transform **» значение 0, 0,** 0.</span><span class="sxs-lookup"><span data-stu-id="ca51c-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="ca51c-148">Найдите свойство **clear flags** и измените раскрывающийся список с **скибокс** на **сплошной цвет**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="ca51c-149">Щелкните поле **Background (фон** ), чтобы открыть палитру цветов.</span><span class="sxs-lookup"><span data-stu-id="ca51c-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="ca51c-150">Задайте значения **R, G, B и A** равными **0**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="ca51c-151">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="ca51c-151">Setup the scene</span></span>

* <span data-ttu-id="ca51c-152">На **панели Иерархия**щелкните **создать** и **создать пустой**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="ca51c-153">Щелкните правой кнопкой мыши новый **GameObject** и выберите команду Переименовать.</span><span class="sxs-lookup"><span data-stu-id="ca51c-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="ca51c-154">Переименуйте GameObject в **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="ca51c-155">В папке **голограмм** на панели проекта (разверните ресурсы и выберите голограммы или дважды щелкните папку голограммы на панели проекта):</span><span class="sxs-lookup"><span data-stu-id="ca51c-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="ca51c-156">Перетащите **этап** в иерархию, чтобы он был дочерним элементом **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="ca51c-157">Перетащите **Sphere1** в иерархию, чтобы она была дочерней для **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="ca51c-158">Перетащите **Sphere2** в иерархию, чтобы она была дочерней для **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="ca51c-159">Щелкните правой кнопкой мыши **направленный объект Light** на **панели Иерархия** и выберите команду **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="ca51c-160">Перетащите **индикаторы** из папки **голограммы** в корневую папку **панели Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="ca51c-161">В **иерархии**выберите **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="ca51c-162">В **инспекторе**задайте для параметра Расположение преобразования значение **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="ca51c-163">Нажмите кнопку **воспроизвести** в Unity, чтобы просмотреть голограммы.</span><span class="sxs-lookup"><span data-stu-id="ca51c-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="ca51c-164">В окне предварительного просмотра должны отобразиться объекты Origami.</span><span class="sxs-lookup"><span data-stu-id="ca51c-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="ca51c-165">Чтобы выйти из режима предварительного просмотра, нажмите кнопку **воспроизвести** еще раз.</span><span class="sxs-lookup"><span data-stu-id="ca51c-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="ca51c-166">Экспорт проекта из Unity в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca51c-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="ca51c-167">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="ca51c-168">Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="ca51c-169">Задайте для **пакета SDK** значение **универсальное 10** , а для **типа сборки** — **D3D**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="ca51c-170">Проверьте **проекты C# Unity**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="ca51c-171">Щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="ca51c-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="ca51c-172">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-172">Click **Build**.</span></span>
* <span data-ttu-id="ca51c-173">В открывшемся окне проводника создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="ca51c-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="ca51c-174">Щелкните **папку приложения**одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="ca51c-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="ca51c-175">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="ca51c-176">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="ca51c-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="ca51c-177">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="ca51c-177">Open the **App** folder.</span></span>
* <span data-ttu-id="ca51c-178">Откройте (дважды щелкните) **Origami. sln**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="ca51c-179">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="ca51c-180">Щелкните стрелку рядом с кнопкой устройство и выберите **Удаленный компьютер** для развертывания через Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="ca51c-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="ca51c-181">Присвойте **адресу** имя или IP-адрес HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca51c-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="ca51c-182">Если вы не знакомы с IP-адресом устройства, проверьте **параметры > сеть & интернет > дополнительные параметры** или спросите Кортану **"Привет, Кортана," мой IP-адрес ".**</span><span class="sxs-lookup"><span data-stu-id="ca51c-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="ca51c-183">Если HoloLens подключен через USB, вы можете выбрать **устройство** для развертывания через USB.</span><span class="sxs-lookup"><span data-stu-id="ca51c-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="ca51c-184">Оставьте для параметра **режим проверки** подлинности значение **универсальное**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="ca51c-185">Нажмите кнопку **выбрать** .</span><span class="sxs-lookup"><span data-stu-id="ca51c-185">Click **Select**</span></span>

* <span data-ttu-id="ca51c-186">Щелкните **отладка > начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="ca51c-187">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span><span class="sxs-lookup"><span data-stu-id="ca51c-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="ca51c-188">Теперь проект Origami будет строиться, развертываться в HoloLens, а затем выполнен.</span><span class="sxs-lookup"><span data-stu-id="ca51c-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="ca51c-189">Помещайтесь на HoloLens и проведите поиск, чтобы увидеть новые голограммы.</span><span class="sxs-lookup"><span data-stu-id="ca51c-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="ca51c-190">Глава 2. взгляд</span><span class="sxs-lookup"><span data-stu-id="ca51c-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="ca51c-191">В этой главе мы будем познакомиться с первым из трех способов взаимодействия с голограммами — [Взгляните](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="ca51c-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="ca51c-192">Цели</span><span class="sxs-lookup"><span data-stu-id="ca51c-192">Objectives</span></span>

* <span data-ttu-id="ca51c-193">Визуализируйте взгляд с помощью курсора, заблокированного по всему миру.</span><span class="sxs-lookup"><span data-stu-id="ca51c-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="ca51c-194">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ca51c-194">Instructions</span></span>

* <span data-ttu-id="ca51c-195">Вернитесь к проекту Unity и закройте окно параметры сборки, если оно все еще открыто.</span><span class="sxs-lookup"><span data-stu-id="ca51c-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="ca51c-196">Выберите папку **голограммы** на **панели проект**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="ca51c-197">Перетащите объект **курсора** на **панель Иерархия** на корневом уровне.</span><span class="sxs-lookup"><span data-stu-id="ca51c-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="ca51c-198">Дважды щелкните объект курсора , чтобы просмотреть его Подробнее.</span><span class="sxs-lookup"><span data-stu-id="ca51c-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="ca51c-199">Щелкните правой кнопкой мыши папку **сценарии** на панели проект.</span><span class="sxs-lookup"><span data-stu-id="ca51c-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="ca51c-200">Щелкните подменю **создать** .</span><span class="sxs-lookup"><span data-stu-id="ca51c-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="ca51c-201">Выберите  **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-201">Select **C# Script**.</span></span>
* <span data-ttu-id="ca51c-202">Назовите сценарий **ворлдкурсор**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="ca51c-203">Примечание. Имя обрабатывается с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="ca51c-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="ca51c-204">Добавлять расширение CS не требуется.</span><span class="sxs-lookup"><span data-stu-id="ca51c-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="ca51c-205">Выберите объект **курсора** на **панели Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="ca51c-206">Перетащите сценарий **ворлдкурсор** на **Панель инспектора**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="ca51c-207">Дважды щелкните скрипт **ворлдкурсор** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca51c-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="ca51c-208">Скопируйте и вставьте этот код в **WorldCursor.CS** и **Сохраните все**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="ca51c-209">Перестройте приложение из **файла > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="ca51c-210">Вернитесь к решению Visual Studio, которое ранее использовалось для развертывания в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca51c-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="ca51c-211">При появлении запроса выберите "перезагрузить все".</span><span class="sxs-lookup"><span data-stu-id="ca51c-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="ca51c-212">Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="ca51c-213">Теперь взгляните на сцену и обратите внимание на то, как курсор взаимодействует с формой объектов.</span><span class="sxs-lookup"><span data-stu-id="ca51c-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="ca51c-214">Глава 3 — жесты</span><span class="sxs-lookup"><span data-stu-id="ca51c-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="ca51c-215">В этой главе мы добавим поддержку [жестов](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="ca51c-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="ca51c-216">Когда пользователь выбирает бумажную сферу, мы сделаем сферу, включив для нее функцию "сила притяжения" с помощью системы обработки физических модулей Unity.</span><span class="sxs-lookup"><span data-stu-id="ca51c-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="ca51c-217">Цели</span><span class="sxs-lookup"><span data-stu-id="ca51c-217">Objectives</span></span>

* <span data-ttu-id="ca51c-218">Контролируйте голограммы с помощью жеста выбора.</span><span class="sxs-lookup"><span data-stu-id="ca51c-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="ca51c-219">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ca51c-219">Instructions</span></span>

<span data-ttu-id="ca51c-220">Начнем с создания скрипта, который затем может обнаружить жест выбора.</span><span class="sxs-lookup"><span data-stu-id="ca51c-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="ca51c-221">В папке **Scripts** создайте скрипт с именем **газежестуреманажер**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="ca51c-222">Перетащите скрипт **газежестуреманажер** на объект **оригамиколлектион** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="ca51c-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="ca51c-223">Откройте скрипт **газежестуреманажер** в Visual Studio и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="ca51c-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="ca51c-224">Создайте другой скрипт в папке Scripts с именем **сферекоммандс**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="ca51c-225">Разверните объект **оригамиколлектион** в представлении иерархии.</span><span class="sxs-lookup"><span data-stu-id="ca51c-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="ca51c-226">Перетащите скрипт **сферекоммандс** на объект **Sphere1** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="ca51c-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="ca51c-227">Перетащите скрипт **сферекоммандс** на объект **Sphere2** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="ca51c-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="ca51c-228">Откройте скрипт в Visual Studio для редактирования и замените код по умолчанию следующим:</span><span class="sxs-lookup"><span data-stu-id="ca51c-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="ca51c-229">Экспортируйте, создайте и разверните приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca51c-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="ca51c-230">Взгляните на одну из шарик.</span><span class="sxs-lookup"><span data-stu-id="ca51c-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="ca51c-231">Выполните жест SELECT и посмотрите на поверхность, расположенную ниже.</span><span class="sxs-lookup"><span data-stu-id="ca51c-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="ca51c-232">Глава 4-Voice</span><span class="sxs-lookup"><span data-stu-id="ca51c-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="ca51c-233">В этой главе мы добавим поддержку двух [команд Voice](voice-input.md): "Сбросить мир", чтобы вернуть удаленные шарик к их исходному расположению и "удалить шар", чтобы сделать сферу.</span><span class="sxs-lookup"><span data-stu-id="ca51c-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="ca51c-234">Цели</span><span class="sxs-lookup"><span data-stu-id="ca51c-234">Objectives</span></span>

* <span data-ttu-id="ca51c-235">Добавление речевых команд, которые всегда прослушиваются в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="ca51c-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="ca51c-236">Создайте голограмму, которая реагирует на голосовую команду.</span><span class="sxs-lookup"><span data-stu-id="ca51c-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="ca51c-237">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ca51c-237">Instructions</span></span>

* <span data-ttu-id="ca51c-238">В папке **Scripts** создайте скрипт с именем **спичманажер**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="ca51c-239">Перетащите скрипт **спичманажер** на объект **оригамиколлектион** в иерархии</span><span class="sxs-lookup"><span data-stu-id="ca51c-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="ca51c-240">Откройте скрипт **спичманажер** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca51c-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="ca51c-241">Скопируйте и вставьте этот код в **SpeechManager.CS** и **Сохраните все**:</span><span class="sxs-lookup"><span data-stu-id="ca51c-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="ca51c-242">Откройте скрипт **сферекоммандс** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca51c-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="ca51c-243">Обновите скрипт для чтения следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ca51c-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="ca51c-244">Экспортируйте, создайте и разверните приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca51c-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="ca51c-245">Взгляните на одну из шарик и скажите «**Drop Sphere**».</span><span class="sxs-lookup"><span data-stu-id="ca51c-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="ca51c-246">Скажите «**сбросить мир**», чтобы вернуть их в исходное положение.</span><span class="sxs-lookup"><span data-stu-id="ca51c-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="ca51c-247">Глава 5 — Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="ca51c-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="ca51c-248">В этой главе мы добавим музыку в приложение, а затем активируем звуковые эффекты для определенных действий.</span><span class="sxs-lookup"><span data-stu-id="ca51c-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="ca51c-249">Мы будем использовать [Пространственный звук](spatial-sound.md) , чтобы дать звуковое сопровождение определенному месту в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="ca51c-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="ca51c-250">Цели</span><span class="sxs-lookup"><span data-stu-id="ca51c-250">Objectives</span></span>

* <span data-ttu-id="ca51c-251">Прослушайте голограммы в своем мире.</span><span class="sxs-lookup"><span data-stu-id="ca51c-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="ca51c-252">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ca51c-252">Instructions</span></span>

* <span data-ttu-id="ca51c-253">В Unity выберите в верхнем меню **правка > параметры проекта > звук**</span><span class="sxs-lookup"><span data-stu-id="ca51c-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="ca51c-254">На панели инспектора с правой стороны найдите параметр подключаемый **модуль спатиализер** и выберите **MS хртф спатиализер**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="ca51c-255">Из папки **голограмм** на панели проекта перетащите объект окружения на объект **оригамиколлектион** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="ca51c-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="ca51c-256">Выберите **оригамиколлектион** и найдите компонент « **источник звука** » на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="ca51c-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="ca51c-257">Измените следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="ca51c-257">Change these properties:</span></span>
  * <span data-ttu-id="ca51c-258">Проверьте свойство **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="ca51c-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="ca51c-259">Проверьте **Воспроизведение в спящем**режиме.</span><span class="sxs-lookup"><span data-stu-id="ca51c-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="ca51c-260">Измените **пространственный переход** на **3D** , перетащив ползунок вправо.</span><span class="sxs-lookup"><span data-stu-id="ca51c-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="ca51c-261">При перемещении ползунка значение должно меняться с 0 на 1.</span><span class="sxs-lookup"><span data-stu-id="ca51c-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="ca51c-262">Проверьте свойство **Loop** .</span><span class="sxs-lookup"><span data-stu-id="ca51c-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="ca51c-263">Разверните **Параметры 3D Sound**и введите **0,1** для **уровня Doppler**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="ca51c-264">Задайте для параметра **Volume роллофф** значение **логарифмической роллофф**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="ca51c-265">Установите **Максимальное расстояние** равным **20**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="ca51c-266">В папке **Scripts** создайте скрипт с именем **сфересаундс**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="ca51c-267">Перетащите **сфересаундс** в объекты **Sphere1** и **Sphere2** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="ca51c-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="ca51c-268">Откройте **сфересаундс** в Visual Studio, обновите следующий код и **Сохраните все**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="ca51c-269">Сохраните скрипт и вернитесь в Unity.</span><span class="sxs-lookup"><span data-stu-id="ca51c-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="ca51c-270">Экспортируйте, создайте и разверните приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca51c-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="ca51c-271">Передвиньтесь ближе и дальше с этапа и перенесите его на сторону, чтобы услышать смену звуков.</span><span class="sxs-lookup"><span data-stu-id="ca51c-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="ca51c-272">Глава 6-пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="ca51c-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="ca51c-273">Теперь мы будем использовать пространственное [сопоставление](spatial-mapping.md) , чтобы поместить игровую доску на реальный объект в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="ca51c-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="ca51c-274">Цели</span><span class="sxs-lookup"><span data-stu-id="ca51c-274">Objectives</span></span>

* <span data-ttu-id="ca51c-275">Приведите реальный мир к виртуальному миру.</span><span class="sxs-lookup"><span data-stu-id="ca51c-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="ca51c-276">Размещайте голограммы, где это важно.</span><span class="sxs-lookup"><span data-stu-id="ca51c-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="ca51c-277">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ca51c-277">Instructions</span></span>

* <span data-ttu-id="ca51c-278">В Unity щелкните папку **голограмм** на панели проект.</span><span class="sxs-lookup"><span data-stu-id="ca51c-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="ca51c-279">Перетащите ресурс **пространственного сопоставления** в корень **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="ca51c-280">Щелкните объект **пространственного сопоставления** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="ca51c-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="ca51c-281">На **панели инспектора**измените следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="ca51c-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="ca51c-282">Установите флажок **рисовать визуальные сетки** .</span><span class="sxs-lookup"><span data-stu-id="ca51c-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="ca51c-283">Перейдите на вкладку **Рисование материалов** и щелкните окружность справа.</span><span class="sxs-lookup"><span data-stu-id="ca51c-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="ca51c-284">Введите "**каркасная**схема" в поле поиска вверху.</span><span class="sxs-lookup"><span data-stu-id="ca51c-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="ca51c-285">Щелкните результат, а затем закройте окно.</span><span class="sxs-lookup"><span data-stu-id="ca51c-285">Click on the result and then close the window.</span></span> <span data-ttu-id="ca51c-286">При этом значение для рисования материала должно быть установлено в каркас.</span><span class="sxs-lookup"><span data-stu-id="ca51c-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="ca51c-287">Экспортируйте, создайте и разверните приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca51c-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="ca51c-288">При запуске приложения в реальной среде будет накладываться каркасная сетка.</span><span class="sxs-lookup"><span data-stu-id="ca51c-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="ca51c-289">Следите за тем, как изкрутка будет выпадать за пределы этапа, и на этаж!</span><span class="sxs-lookup"><span data-stu-id="ca51c-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="ca51c-290">Теперь мы покажем, как переместить Оригамиколлектион в новое расположение:</span><span class="sxs-lookup"><span data-stu-id="ca51c-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="ca51c-291">В папке **Scripts** создайте скрипт с именем **таптоплацепарент**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="ca51c-292">В **иерархии**разверните **оригамиколлектион** и выберите объект **Stage** .</span><span class="sxs-lookup"><span data-stu-id="ca51c-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="ca51c-293">Перетащите скрипт **таптоплацепарент** на объект Stage.</span><span class="sxs-lookup"><span data-stu-id="ca51c-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="ca51c-294">Откройте скрипт **таптоплацепарент** в Visual Studio и обновите его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ca51c-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="ca51c-295">Экспорт, сборка и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="ca51c-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="ca51c-296">Теперь вы можете разместить игру в определенном месте, облаками ее с помощью жеста SELECT, а затем переместить в новое место и снова с помощью жеста выбора.</span><span class="sxs-lookup"><span data-stu-id="ca51c-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="ca51c-297">Глава 7-holographic</span><span class="sxs-lookup"><span data-stu-id="ca51c-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="ca51c-298">Цели</span><span class="sxs-lookup"><span data-stu-id="ca51c-298">Objectives</span></span>

* <span data-ttu-id="ca51c-299">Показать вход в неограниченный мир.</span><span class="sxs-lookup"><span data-stu-id="ca51c-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="ca51c-300">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ca51c-300">Instructions</span></span>

<span data-ttu-id="ca51c-301">Теперь мы покажем, как открыть немалое время:</span><span class="sxs-lookup"><span data-stu-id="ca51c-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="ca51c-302">Из папки **голограмм** на панели проекта:</span><span class="sxs-lookup"><span data-stu-id="ca51c-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="ca51c-303">Перетащите элемент "подсветка **мира** " в иерархию, чтобы он был дочерним элементом **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="ca51c-304">В папке **Scripts** создайте скрипт с именем **хиттаржет**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="ca51c-305">В **иерархии**разверните узел **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="ca51c-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="ca51c-306">Разверните объект **Stage** и выберите **целевой** объект (синий вентилятор).</span><span class="sxs-lookup"><span data-stu-id="ca51c-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="ca51c-307">Перетащите скрипт **хиттаржет** на **целевой** объект.</span><span class="sxs-lookup"><span data-stu-id="ca51c-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="ca51c-308">Откройте скрипт **хиттаржет** в Visual Studio и обновите его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ca51c-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="ca51c-309">В Unity выберите **целевой** объект.</span><span class="sxs-lookup"><span data-stu-id="ca51c-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="ca51c-310">Два открытых свойства теперь видны на целевом компоненте для **попадания** и должны ссылаться на объекты в нашей сцене:</span><span class="sxs-lookup"><span data-stu-id="ca51c-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="ca51c-311">Перетащите элемент «подсветка **мира** » с панели « **Иерархия** » в свойство «подсветка» для **целевого** компонента.</span><span class="sxs-lookup"><span data-stu-id="ca51c-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="ca51c-312">Перетащите **этап** из панели **Иерархия** в **объект, чтобы скрыть** свойство в целевом компоненте для **попадания** .</span><span class="sxs-lookup"><span data-stu-id="ca51c-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="ca51c-313">Экспорт, сборка и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="ca51c-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="ca51c-314">Поместите коллекцию Origami в этаж, а затем с помощью жеста выбора выполните перетаскивание сферы.</span><span class="sxs-lookup"><span data-stu-id="ca51c-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="ca51c-315">Когда сфера достигнет цели (синий вентилятор), произойдет развертывание.</span><span class="sxs-lookup"><span data-stu-id="ca51c-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="ca51c-316">Коллекция будет скрыта, и появится отверстие для подсветки.</span><span class="sxs-lookup"><span data-stu-id="ca51c-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="ca51c-317">Конец</span><span class="sxs-lookup"><span data-stu-id="ca51c-317">The end</span></span>

<span data-ttu-id="ca51c-318">И это окончание этого руководства.</span><span class="sxs-lookup"><span data-stu-id="ca51c-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="ca51c-319">Вы узнали:</span><span class="sxs-lookup"><span data-stu-id="ca51c-319">You learned:</span></span>

* <span data-ttu-id="ca51c-320">Создание приложения holographic в Unity.</span><span class="sxs-lookup"><span data-stu-id="ca51c-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="ca51c-321">Как использовать взгляд, жест, голосовое, звуковое и пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="ca51c-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="ca51c-322">Как создать и развернуть приложение с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca51c-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="ca51c-323">Теперь вы готовы приступить к созданию собственного опыта.</span><span class="sxs-lookup"><span data-stu-id="ca51c-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="ca51c-324">См. также</span><span class="sxs-lookup"><span data-stu-id="ca51c-324">See also</span></span>

* [<span data-ttu-id="ca51c-325">101E. Основы смешанной реальности: полный проект с использованием эмулятора</span><span class="sxs-lookup"><span data-stu-id="ca51c-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="ca51c-326">Взгляд</span><span class="sxs-lookup"><span data-stu-id="ca51c-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="ca51c-327">Жесты</span><span class="sxs-lookup"><span data-stu-id="ca51c-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="ca51c-328">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="ca51c-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="ca51c-329">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="ca51c-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="ca51c-330">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="ca51c-330">Spatial mapping</span></span>](spatial-mapping.md)
