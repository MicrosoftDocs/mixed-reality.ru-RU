---
title: Совместное использование 240 - несколько устройств HoloLens MR
description: Выполните кодирование Пошаговое руководство по использованию Unity, Visual Studio и HoloLens совместного использования голограммы подробные сведения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, совместное использование, сетей, academy, руководство
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601389"
---
>[!NOTE]
><span data-ttu-id="9eb1c-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9eb1c-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9eb1c-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9eb1c-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9eb1c-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9eb1c-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="9eb1c-110">Совместное использование 240 MR: Несколько устройств HoloLens</span><span class="sxs-lookup"><span data-stu-id="9eb1c-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="9eb1c-111">Голограммы, предоставленному присутствие в наш мир оставшихся в месте по мере продвижения в пространстве.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="9eb1c-112">HoloLens отслеживает голограммы на месте с использованием различных [системы координат](coordinate-systems.md) для отслеживания местоположение и ориентацию объектов.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="9eb1c-113">Когда мы совместно используют эти системы координат, между устройствами, мы можем создать общий интерфейс, который позволяет принять участие в общих holographic мире.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="9eb1c-114">В этом руководстве мы выполним следующее.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="9eb1c-115">Настройка сети для общего качества.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="9eb1c-116">Совместное использование голограммы устройств HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="9eb1c-117">Обнаружение других пользователей, общих holographic мира.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="9eb1c-118">Создайте общий пошаговой процедуры, где можно целевой другие игроки - и запускать летящими их!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="9eb1c-119">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="9eb1c-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9eb1c-120">Курс</span><span class="sxs-lookup"><span data-stu-id="9eb1c-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9eb1c-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9eb1c-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9eb1c-122"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="9eb1c-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9eb1c-123">Совместное использование 240 MR: Несколько устройств HoloLens</span><span class="sxs-lookup"><span data-stu-id="9eb1c-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="9eb1c-124">✔️</span><span class="sxs-lookup"><span data-stu-id="9eb1c-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9eb1c-125">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="9eb1c-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9eb1c-126">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="9eb1c-126">Prerequisites</span></span>

* <span data-ttu-id="9eb1c-127">ПК Windows 10, настроены с правильным [установлены инструменты](install-the-tools.md) с доступом к Интернету.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="9eb1c-128">По крайней мере два устройства HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="9eb1c-129">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="9eb1c-129">Project files</span></span>

* <span data-ttu-id="9eb1c-130">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) требуемые для проекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="9eb1c-131">Требуется компонент Unity 2017.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="9eb1c-132">Если вам по-прежнему требуется поддержка Unity 5.6, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="9eb1c-133">Если вам по-прежнему требуется поддержка Unity 5.5, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="9eb1c-134">Если вам по-прежнему требуется поддержка Unity 5.4, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="9eb1c-135">Удаление архива файлы рабочего стола или других легко положения.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="9eb1c-136">Оставьте имя папки в качестве **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="9eb1c-137">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="9eb1c-138">Глава 1 - Holo World</span><span class="sxs-lookup"><span data-stu-id="9eb1c-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="9eb1c-139">В этой главе мы установки наш первый проект Unity и пошагово выполнять построение и развертывание процесса.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="9eb1c-140">Цели</span><span class="sxs-lookup"><span data-stu-id="9eb1c-140">Objectives</span></span>

* <span data-ttu-id="9eb1c-141">Настройка Unity для разработки приложений holographic.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="9eb1c-142">См. в разделе вашей голограмма!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="9eb1c-143">Инструкция</span><span class="sxs-lookup"><span data-stu-id="9eb1c-143">Instructions</span></span>

* <span data-ttu-id="9eb1c-144">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-144">Start Unity.</span></span>
* <span data-ttu-id="9eb1c-145">Выберите **откройте**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-145">Select **Open**.</span></span>
* <span data-ttu-id="9eb1c-146">Введите расположение как **SharedHolograms** папки, которые вы ранее архиве.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="9eb1c-147">Выберите **имя_проекта** и нажмите кнопку **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="9eb1c-148">В **иерархии**, щелкните правой кнопкой мыши **Main Camera** и выберите **удалить**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="9eb1c-149">В **HoloToolkit-совместное использование-240/Prefabs/камеры** папки, найти **Main Camera** prefab.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="9eb1c-150">Перетаскивание **Main Camera** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="9eb1c-151">В **иерархии**, щелкните **создать** и **создать пустой**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="9eb1c-152">Щелкните правой кнопкой мыши новый **GameObject** и выберите **Переименовать**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="9eb1c-153">Переименовать объект GameObject, чтобы **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="9eb1c-154">Выберите **HologramCollection** объекта в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="9eb1c-155">В **инспектор** задать **преобразование положения** для: **X: 0, Y: -0,25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="9eb1c-156">В **голограммы** папку в **панель проекта**, найти **EnergyHub** активов.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="9eb1c-157">Перетаскивание **EnergyHub** объекта из **панель проекта** для **иерархии** как **потомком HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="9eb1c-158">Выберите **файл > Сохранить сцену как...**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="9eb1c-159">Присвойте сцене имя **SharedHolograms** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="9eb1c-160">Нажмите клавишу **воспроизведение** кнопки в Unity для предварительного просмотра вашего голограммы.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="9eb1c-161">Нажмите клавишу **воспроизведение** второй раз, чтобы выйти из режима предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="9eb1c-162">**Экспортировать проект из Unity в Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="9eb1c-163">В Unity выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="9eb1c-164">Нажмите кнопку **добавьте откройте сцены** Добавление сцены.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="9eb1c-165">Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="9eb1c-166">Задайте **SDK** для **универсальной 10**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="9eb1c-167">Задайте **целевое устройство** для **HoloLens** и **тип сборки UWP** для **D3D**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="9eb1c-168">Проверьте **Unity C# проекты**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="9eb1c-169">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-169">Click **Build**.</span></span>
* <span data-ttu-id="9eb1c-170">В обозревателе файл создать **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="9eb1c-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="9eb1c-171">Одним щелчком мыши **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="9eb1c-172">Нажмите клавишу **выберите папку**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="9eb1c-173">По завершении Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="9eb1c-174">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-174">Open the **App** folder.</span></span>
* <span data-ttu-id="9eb1c-175">Откройте **SharedHolograms.sln** для запуска Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="9eb1c-176">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **X86**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="9eb1c-177">Щелкните стрелку раскрывающегося списка рядом с локального компьютера и выберите **удаленное устройство**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="9eb1c-178">Задайте **адрес** в имя или IP-адрес вашего HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="9eb1c-179">Если вы не знаете IP-адрес устройства, найдите в **параметры > сеть и Интернет > Дополнительно** или попросить Cortana **«Привет, Кортана, что такое Мой IP-адрес?»**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="9eb1c-180">Оставьте **режим проверки подлинности** присвоено **универсальной**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="9eb1c-181">Нажмите кнопку **выберите**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-181">Click **Select**</span></span>
* <span data-ttu-id="9eb1c-182">Нажмите кнопку **Отладка > Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="9eb1c-183">Если это при первом развертывании к устройству, необходимо будет [свяжите его с помощью Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="9eb1c-184">Поместите на вашей HoloLens и найти голограмма EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="9eb1c-185">Глава 2 - взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9eb1c-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="9eb1c-186">В этой главе мы будет взаимодействовать с нашей голограммы.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="9eb1c-187">Во-первых, мы добавим курсора для визуализации наших [помощи](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="9eb1c-188">Затем мы добавим [жесты](gestures.md) и используйте позаниматься для размещения наших голограммы в пространстве.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="9eb1c-189">Цели</span><span class="sxs-lookup"><span data-stu-id="9eb1c-189">Objectives</span></span>

* <span data-ttu-id="9eb1c-190">Используйте взглядом входных данных для управления курсором.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="9eb1c-191">Используйте жест ввода для взаимодействия с голограммы.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="9eb1c-192">Инструкция</span><span class="sxs-lookup"><span data-stu-id="9eb1c-192">Instructions</span></span>

<span data-ttu-id="9eb1c-193">**Взглядом**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-193">**Gaze**</span></span>
* <span data-ttu-id="9eb1c-194">В **панели иерархии** выберите **HologramCollection** объекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="9eb1c-195">В **панели Инспектора** щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="9eb1c-196">В меню, введите в поле поиска **помощи Manager**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="9eb1c-197">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-197">Select the search result.</span></span>
* <span data-ttu-id="9eb1c-198">В **совместное использование 240\Prefabs\Input HoloToolkit** папки, найти **курсор** активов.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="9eb1c-199">Перетаскивание **курсор** активов на **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="9eb1c-200">**Жест**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-200">**Gesture**</span></span>
* <span data-ttu-id="9eb1c-201">В **панели иерархии** выберите **HologramCollection** объекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="9eb1c-202">Нажмите кнопку **добавить компонент** и тип **Manager жест** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="9eb1c-203">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-203">Select the search result.</span></span>
* <span data-ttu-id="9eb1c-204">В **панели иерархии**, разверните **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9eb1c-205">Выберите дочерние **EnergyHub** объекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="9eb1c-206">В **панели Инспектора** щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="9eb1c-207">В меню, введите в поле поиска **голограмма размещения**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="9eb1c-208">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-208">Select the search result.</span></span>
* <span data-ttu-id="9eb1c-209">Сохраните сцену, выбрав **файл > Сохранить сцену**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="9eb1c-210">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="9eb1c-211">Создание и развертывание в вашей HoloLens, следуя инструкциям в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="9eb1c-212">После запуска приложения на вашей HoloLens перемещать голове и обратите внимание на то, как EnergyHub соответствует вашей взглядом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="9eb1c-213">Обратите внимание на то, как выглядит при помощи при голограмма курсора и изменяется на Точечный свет, если не gazing в голограмма.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="9eb1c-214">Выполните жест касания для размещения голограмма.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="9eb1c-215">В настоящее время в нашем проекте можно установить только один раз голограмма (повторное развертывание на попытку).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="9eb1c-216">Глава 3 - Shared координирует</span><span class="sxs-lookup"><span data-stu-id="9eb1c-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="9eb1c-217">Он см. в разделе и взаимодействовать с голограммы вряд ли двигаться дальше.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="9eb1c-218">Мы составим наш первый опытом - голограмма, которые можно будет увидеть друг с другом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="9eb1c-219">Цели</span><span class="sxs-lookup"><span data-stu-id="9eb1c-219">Objectives</span></span>

* <span data-ttu-id="9eb1c-220">Настройка сети для общего качества.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="9eb1c-221">Установите отправную точку.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-221">Establish a common reference point.</span></span>
* <span data-ttu-id="9eb1c-222">Совместное использование системы координат устройства.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="9eb1c-223">Каждый пользователь будет видеть же она!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="9eb1c-224">**InternetClientServer** и **PrivateNetworkClientServer** возможности должны объявляться для приложения для подключения к серверу управления доступом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="9eb1c-225">Для этого вам уже в голограммы 240, но имейте это в виду для ваших собственных проектов.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="9eb1c-226">В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»</span><span class="sxs-lookup"><span data-stu-id="9eb1c-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="9eb1c-227">Перейдите на вкладку «Windows Store»</span><span class="sxs-lookup"><span data-stu-id="9eb1c-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="9eb1c-228">В разделе «Возможности публикации > Параметры» установите флажок **InternetClientServer** возможность и **PrivateNetworkClientServer** возможностей</span><span class="sxs-lookup"><span data-stu-id="9eb1c-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="9eb1c-229">Инструкция</span><span class="sxs-lookup"><span data-stu-id="9eb1c-229">Instructions</span></span>

* <span data-ttu-id="9eb1c-230">В **панель проекта** перейдите к **совместное использование 240\Prefabs\Sharing HoloToolkit** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="9eb1c-231">Перетаскивание **доступ** prefab в **панели иерархии**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="9eb1c-232">Далее нам нужно запустить совместно используемой службе.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="9eb1c-233">Только **одним ПК** в общей работы необходимо выполнить этот шаг.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="9eb1c-234">В Unity — в меню сверху рука об руку - выберите **меню совместное использование 240 HoloToolkit**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="9eb1c-235">Выберите **запуска службы общего доступа к** элемента в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="9eb1c-236">Проверьте **частная сеть** и нажмите кнопку **разрешения доступа к** при появлении брандмауэра.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="9eb1c-237">Запишите IPv4-адрес, отображаемый в окне консоли службы совместного использования.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="9eb1c-238">Это же IP-адрес компьютера, на котором запущен под управлением службы.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="9eb1c-239">Следуйте инструкциям **всех компьютеров под управлением** , присоединяются к опытом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="9eb1c-240">В **иерархии**выберите **доступ** объекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="9eb1c-241">В **инспектор**на **общий доступ к рабочей области** компонента, изменение **адрес сервера** из «localhost» на IPv4-адрес машины, работающей SharingService.exe.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="9eb1c-242">В **иерархии** выберите **HologramCollection** объекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="9eb1c-243">В **инспектор** щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="9eb1c-244">В поле поиска введите **импорта экспорта привязки Manager**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="9eb1c-245">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-245">Select the search result.</span></span>
* <span data-ttu-id="9eb1c-246">В **панель проекта** перейдите к **сценариев** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="9eb1c-247">Дважды щелкните **HologramPlacement** скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="9eb1c-248">Замените содержимое следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-248">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="9eb1c-249">В Unity, выберите **HologramCollection** в **панели иерархии**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="9eb1c-250">В **панели Инспектора** щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="9eb1c-251">В меню, введите в поле поиска **диспетчер состояний приложения**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="9eb1c-252">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-252">Select the search result.</span></span>

<span data-ttu-id="9eb1c-253">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="9eb1c-254">Постройте проект для устройств HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="9eb1c-255">Назначьте один HoloLens для развертывания на первый.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="9eb1c-256">Необходимо будет ждать привязки для отправки в службу до установки EnergyHub (это может занять около 30 – 60 секунд).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="9eb1c-257">До завершения отправки вашего жесты касания будет игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="9eb1c-258">После поместил EnergyHub ее расположение будет отправляться в службу и затем можно развернуть для других устройств HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="9eb1c-259">Когда новый HoloLens сначала присоединится к сеансу, расположение EnergyHub может оказаться неправильной на этом устройстве.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="9eb1c-260">Тем не менее как только привязки и расположений EnergyHub были загружены из службы, EnergyHub должен перейти к новой, общего расположения.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="9eb1c-261">Если этого не происходит в пределах 30 – 60 секунд, пошаговые инструкции для которой был исходный HoloLens, при задании привязки, чтобы собрать дополнительные идеи среды.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="9eb1c-262">Если расположение по-прежнему не блокирует, повторное развертывание на устройстве.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="9eb1c-263">Когда устройства готовы и запуск приложения, найдите EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="9eb1c-264">Можно всем согласовать голограмма расположение и направление, в котором имеются текст?</span><span class="sxs-lookup"><span data-stu-id="9eb1c-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="9eb1c-265">Глава 4 — обнаружения</span><span class="sxs-lookup"><span data-stu-id="9eb1c-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="9eb1c-266">Теперь все можно видеть же голограмма!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="9eb1c-267">Теперь давайте посмотрим, все еще подключены к веб-общего holographic.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="9eb1c-268">В этой главе мы будем захвата головной расположение и поворот все прочие устройства HoloLens в одном сеансе общего доступа.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="9eb1c-269">Цели</span><span class="sxs-lookup"><span data-stu-id="9eb1c-269">Objectives</span></span>

* <span data-ttu-id="9eb1c-270">Обнаруживать друг друга в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="9eb1c-271">Выберите и совместно использовать аватар проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="9eb1c-272">Подключите аватар рядом с головах проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="9eb1c-273">Инструкция</span><span class="sxs-lookup"><span data-stu-id="9eb1c-273">Instructions</span></span>

* <span data-ttu-id="9eb1c-274">В **панель проекта** перейдите к **голограммы** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="9eb1c-275">Перетаскивание **PlayerAvatarStore** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="9eb1c-276">В **панель проекта** перейдите к **сценариев** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="9eb1c-277">Дважды щелкните **AvatarSelector** скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="9eb1c-278">Замените содержимое следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-278">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="9eb1c-279">В **иерархии** выберите **HologramCollection** объекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="9eb1c-280">В **инспектор** щелкните **добавить компонент**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="9eb1c-281">В поле поиска введите **локального диспетчера проигрывателя**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="9eb1c-282">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-282">Select the search result.</span></span>
* <span data-ttu-id="9eb1c-283">В **иерархии** выберите **HologramCollection** объекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="9eb1c-284">В **инспектор** щелкните **добавить компонент**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="9eb1c-285">В поле поиска введите **диспетчера проигрывателя удаленного**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="9eb1c-286">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-286">Select the search result.</span></span>
* <span data-ttu-id="9eb1c-287">Откройте **HologramPlacement** скриптов в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="9eb1c-288">Замените содержимое следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-288">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="9eb1c-289">Откройте **AppStateManager** скриптов в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="9eb1c-290">Замените содержимое следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-290">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="9eb1c-291">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="9eb1c-292">Построение и развертывание проекта на устройства HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="9eb1c-293">Услышав эхо-тестирование звука, найдите меню выбора аватар и выберите аватар с жестом жест касания.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="9eb1c-294">Если вам не нужны в любой голограммы, точки, вокруг курсор света приводит к отключению другой цвет при вашей HoloLens взаимодействует со службой: инициализация (темно-фиолетовый), скачивание привязки (зеленый), Импорт и экспорт данных расположения (желтый), Отправка привязки (синий).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="9eb1c-295">Если точка света вокруг курсора находится цвет по умолчанию (сиреневый), вы будете готовы взаимодействовать с другими пользователями в текущем сеансе!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="9eb1c-296">Просмотрите другие пользователи подключены к вашей место — будет holographic робота над их плечо, сможет узнать и копируя их головной движения!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="9eb1c-297">Глава 5 - размещение</span><span class="sxs-lookup"><span data-stu-id="9eb1c-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="9eb1c-298">В этой главе мы предлагаем удается разместить на поверхностях реальных привязки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="9eb1c-299">Мы будем использовать общий координаты для размещения этой привязки в средняя точка между всех опытом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="9eb1c-300">Цели</span><span class="sxs-lookup"><span data-stu-id="9eb1c-300">Objectives</span></span>

* <span data-ttu-id="9eb1c-301">Поместите голограммы на карте Пространственные, по положению головной игроков.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="9eb1c-302">Инструкция</span><span class="sxs-lookup"><span data-stu-id="9eb1c-302">Instructions</span></span>

* <span data-ttu-id="9eb1c-303">В **панель проекта** перейдите к **голограммы** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="9eb1c-304">Перетаскивание **CustomSpatialMapping** prefab на **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="9eb1c-305">В **панель проекта** перейдите к **сценариев** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="9eb1c-306">Дважды щелкните **AppStateManager** скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="9eb1c-307">Замените содержимое следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-307">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="9eb1c-308">В **панель проекта** перейдите к **сценариев** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="9eb1c-309">Дважды щелкните **HologramPlacement** скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="9eb1c-310">Замените содержимое следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-310">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="9eb1c-311">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="9eb1c-312">Построение и развертывание проекта на устройства HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="9eb1c-313">Когда приложение будет готово, в круге, а также Обратите внимание на то, как EnergyHub отображается в центре всех пользователей.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="9eb1c-314">Коснитесь, чтобы поместить EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="9eb1c-315">Попробуйте голосовых команд «Сбросить Target», чтобы поднять EnergyHub и работают вместе как группа голограмма переместиться в новое расположение.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="9eb1c-316">Глава 6 - реальной физике</span><span class="sxs-lookup"><span data-stu-id="9eb1c-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="9eb1c-317">В этой главе мы добавим голограммы, отражаясь реальных поверхности.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="9eb1c-318">Смотрите модуля заполнения с проектами, запускаемого по вам и вашим друзьям!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="9eb1c-319">Цели</span><span class="sxs-lookup"><span data-stu-id="9eb1c-319">Objectives</span></span>

* <span data-ttu-id="9eb1c-320">Запустите снаряды, отражаясь реальных поверхности.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="9eb1c-321">Используют снаряды, поэтому их можно было видеть других игроков.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="9eb1c-322">Инструкция</span><span class="sxs-lookup"><span data-stu-id="9eb1c-322">Instructions</span></span>

* <span data-ttu-id="9eb1c-323">В **иерархии** выберите **HologramCollection** объекта.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="9eb1c-324">В **инспектор** щелкните **добавить компонент**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="9eb1c-325">В поле поиска введите **Projectile запуска**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="9eb1c-326">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-326">Select the search result.</span></span>

<span data-ttu-id="9eb1c-327">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="9eb1c-328">Создавайте и развертывайте на устройства HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="9eb1c-329">Когда приложение выполняется на всех устройствах, выполните жест касания для запуска projectile в реальном мире поверхности.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="9eb1c-330">См. в разделе, что происходит, когда ваш projectile конфликтует с другим игрока аватар!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="9eb1c-331">Глава 7 - брошены общего итога</span><span class="sxs-lookup"><span data-stu-id="9eb1c-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="9eb1c-332">В этой главе мы будем Открывание это портал, который можно обнаружить только с помощью службы совместной работы.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="9eb1c-333">Цели</span><span class="sxs-lookup"><span data-stu-id="9eb1c-333">Objectives</span></span>

* <span data-ttu-id="9eb1c-334">Совместная работа которых позволяет запустить достаточно летящими у привязки для выявления секретный портала!</span><span class="sxs-lookup"><span data-stu-id="9eb1c-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="9eb1c-335">Инструкция</span><span class="sxs-lookup"><span data-stu-id="9eb1c-335">Instructions</span></span>

* <span data-ttu-id="9eb1c-336">В **панель проекта** перейдите к **голограммы** папки.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="9eb1c-337">Перетаскивание **Underworld** ресурс как **потомком HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="9eb1c-338">С помощью **HologramCollection** , щелкните **добавить компонент** кнопку **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="9eb1c-339">В меню, введите в поле поиска **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="9eb1c-340">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-340">Select the search result.</span></span>
* <span data-ttu-id="9eb1c-341">С помощью **HologramCollection** выбранный из **иерархии** перетащите **EnergyHub** объект **целевой** в **Инспектор**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="9eb1c-342">С помощью **HologramCollection** выбранный из **иерархии** перетащите **Underworld** объект **Underworld** в  **Инспектор**.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="9eb1c-343">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="9eb1c-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="9eb1c-344">Создавайте и развертывайте на устройства HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="9eb1c-345">При запуске приложения работе вместе, чтобы запустить летящими в EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="9eb1c-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="9eb1c-346">В открывшемся underworld запустите летящими в underworld роботов (попадание робота три раза для дополнительных интереса).</span><span class="sxs-lookup"><span data-stu-id="9eb1c-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
