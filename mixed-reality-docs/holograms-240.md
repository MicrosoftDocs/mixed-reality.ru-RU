---
title: MR-общий доступ 240 — несколько устройств HoloLens
description: Следуйте этому пошаговому руководству по созданию кода с помощью Unity, Visual Studio и HoloLens, чтобы получить сведения о голограммах общего доступа.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, общий доступ, сети, Academy, учебник
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522332"
---
>[!NOTE]
><span data-ttu-id="0a4bd-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0a4bd-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0a4bd-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0a4bd-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0a4bd-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0a4bd-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="0a4bd-110">MR совместное использование 240: Несколько устройств HoloLens</span><span class="sxs-lookup"><span data-stu-id="0a4bd-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="0a4bd-111">Голограммы задаются в нашем мире по мере перемещения о месте в пространстве.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="0a4bd-112">HoloLens сохраняет голограммы на месте, используя различные [системы координат](coordinate-systems.md) для наблюдения за расположением и ориентацией объектов.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="0a4bd-113">При совместном использовании этих систем координат между устройствами мы можем создать общий интерфейс, который позволит нам принять участие в совместном мире Holographic.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="0a4bd-114">В этом учебнике мы будем делать следующее:</span><span class="sxs-lookup"><span data-stu-id="0a4bd-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="0a4bd-115">Настройте сеть для совместной работы.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="0a4bd-116">Делитесь голограммами на устройствах HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="0a4bd-117">Знакомство с другими людьми в нашей общей жизни.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="0a4bd-118">Создайте общедоступную интерактивную среду, где вы можете ориентироваться на другие игроки и запустить снаряды.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="0a4bd-119">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="0a4bd-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0a4bd-120">Хождение</span><span class="sxs-lookup"><span data-stu-id="0a4bd-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0a4bd-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0a4bd-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0a4bd-122"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="0a4bd-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0a4bd-123">MR совместное использование 240: Несколько устройств HoloLens</span><span class="sxs-lookup"><span data-stu-id="0a4bd-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="0a4bd-124">✔️</span><span class="sxs-lookup"><span data-stu-id="0a4bd-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0a4bd-125">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="0a4bd-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0a4bd-126">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="0a4bd-126">Prerequisites</span></span>

* <span data-ttu-id="0a4bd-127">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md) с доступом к Интернету.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="0a4bd-128">По крайней мере два устройства HoloLens [настроены для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="0a4bd-129">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="0a4bd-129">Project files</span></span>

* <span data-ttu-id="0a4bd-130">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="0a4bd-131">Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0a4bd-132">Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="0a4bd-133">Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="0a4bd-134">Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="0a4bd-135">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0a4bd-136">В качестве имени папки используйте **шаредхолограмс**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="0a4bd-137">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0a4bd-138">Глава 1 — Холо World</span><span class="sxs-lookup"><span data-stu-id="0a4bd-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="0a4bd-139">В этой главе мы создадим наш первый проект Unity и пошаговым процессом сборки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0a4bd-140">Цели</span><span class="sxs-lookup"><span data-stu-id="0a4bd-140">Objectives</span></span>

* <span data-ttu-id="0a4bd-141">Настройте Unity для разработки holographic приложений.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="0a4bd-142">Ознакомьтесь с голограммой!</span><span class="sxs-lookup"><span data-stu-id="0a4bd-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="0a4bd-143">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0a4bd-143">Instructions</span></span>

* <span data-ttu-id="0a4bd-144">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-144">Start Unity.</span></span>
* <span data-ttu-id="0a4bd-145">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-145">Select **Open**.</span></span>
* <span data-ttu-id="0a4bd-146">Введите Location в качестве ранее неархивированной папки **шаредхолограмс** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="0a4bd-147">Выберите **имя проекта** и щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="0a4bd-148">В **иерархии**щелкните правой кнопкой мыши **основную камеру** и выберите **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="0a4bd-149">В папке **холотулкит-Shared-240/Prefabs/Camera** найдите **главную камеру** prefab.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="0a4bd-150">Перетащите **основную камеру** в **иерархию**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="0a4bd-151">В **иерархии**щелкните **создать** и **создать пустой**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="0a4bd-152">Щелкните правой кнопкой мыши новый **GameObject** и выберите команду **Переименовать**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="0a4bd-153">Переименуйте GameObject в **холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="0a4bd-154">Выберите объект **холограмколлектион** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="0a4bd-155">В **инспекторе** задайте для параметра **Расположение преобразования** значение: **X 0, Y:-0,25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="0a4bd-156">В папке **голограмм** на **панели проект**найдите ресурс **енергихуб** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="0a4bd-157">Перетащите объект **енергихуб** с **панели проект** в **иерархию** в качестве дочернего **элемента холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="0a4bd-158">Выберите **файл > сохранить сцену как...**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="0a4bd-159">Присвойте сцене имя **шаредхолограмс** и нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="0a4bd-160">Нажмите кнопку **воспроизвести** в Unity, чтобы просмотреть голограммы.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0a4bd-161">Чтобы выйти из режима предварительного просмотра, нажмите кнопку **воспроизвести** еще раз.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="0a4bd-162">**Экспорт проекта из Unity в Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="0a4bd-163">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="0a4bd-164">Щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0a4bd-165">Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="0a4bd-166">Задайте для **пакета SDK** значение **универсальное 10**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="0a4bd-167">Присвойте **целевому устройству** значение **HoloLens** , а для **типа сборки UWP** — **D3D**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="0a4bd-168">Проверьте **проекты C# Unity**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="0a4bd-169">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-169">Click **Build**.</span></span>
* <span data-ttu-id="0a4bd-170">В открывшемся окне проводника создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0a4bd-171">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="0a4bd-172">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="0a4bd-173">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0a4bd-174">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-174">Open the **App** folder.</span></span>
* <span data-ttu-id="0a4bd-175">Откройте **шаредхолограмс. sln** , чтобы запустить Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="0a4bd-176">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="0a4bd-177">Щелкните стрелку раскрывающегося списка рядом с пунктом локальный компьютер и выберите **удаленное устройство**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="0a4bd-178">Присвойте **адресу** имя или IP-адрес HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="0a4bd-179">Если вы не знакомы с IP-адресом устройства, проверьте **параметры > сеть & интернет > дополнительные параметры** или спросите Кортану **"Привет, Кортана," мой IP-адрес ".**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="0a4bd-180">Оставьте для параметра **режим проверки** подлинности значение **универсальное**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="0a4bd-181">Нажмите кнопку **выбрать** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-181">Click **Select**</span></span>
* <span data-ttu-id="0a4bd-182">Щелкните **отладка > начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="0a4bd-183">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="0a4bd-184">Поставьте на HoloLens и найдите голограмму Енергихуб.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="0a4bd-185">Глава 2 — взаимодействие</span><span class="sxs-lookup"><span data-stu-id="0a4bd-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="0a4bd-186">В этой главе мы будем взаимодействовать с нашими голограммами.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="0a4bd-187">Сначала мы добавим курсор для визуализации нашего [взгляда](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="0a4bd-188">Затем мы добавим [жесты](gestures.md) и будем использовать нашу руку, чтобы разместить наши голограммы в пространстве.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0a4bd-189">Цели</span><span class="sxs-lookup"><span data-stu-id="0a4bd-189">Objectives</span></span>

* <span data-ttu-id="0a4bd-190">Для управления курсором используйте ввод с помощью указателя.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="0a4bd-191">Используйте ввод жестов для взаимодействия с голограммами.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="0a4bd-192">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0a4bd-192">Instructions</span></span>

<span data-ttu-id="0a4bd-193">**Взгляд**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-193">**Gaze**</span></span>
* <span data-ttu-id="0a4bd-194">На **панели Иерархия** выберите объект **холограмколлектион** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="0a4bd-195">На **панели инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="0a4bd-196">В меню введите в поле поиска пункт **Менеджер**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="0a4bd-197">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-197">Select the search result.</span></span>
* <span data-ttu-id="0a4bd-198">В папке **HoloToolkit-Sharing-240\Prefabs\Input** найдите ресурс **cursor** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="0a4bd-199">Перетащите в **иерархию**ресурс с **курсором** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="0a4bd-200">**Рисуйте**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-200">**Gesture**</span></span>
* <span data-ttu-id="0a4bd-201">На **панели Иерархия** выберите объект **холограмколлектион** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="0a4bd-202">Щелкните **Добавить компонент** и введите **Диспетчер жестов** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="0a4bd-203">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-203">Select the search result.</span></span>
* <span data-ttu-id="0a4bd-204">На **панели Иерархия**разверните узел **холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="0a4bd-205">Выберите дочерний объект **енергихуб** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="0a4bd-206">На **панели инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="0a4bd-207">В меню введите текст в поле поиска с **голограммой**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="0a4bd-208">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-208">Select the search result.</span></span>
* <span data-ttu-id="0a4bd-209">Сохраните сцену, выбрав **файл > сохранить сцену**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="0a4bd-210">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="0a4bd-211">Выполните сборку и развертывание в HoloLens, следуя инструкциям из предыдущей главы.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="0a4bd-212">Когда приложение запустится на HoloLens, переместите заголовок и обратите внимание на то, как Енергихуб соответствует вашему взгляду.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="0a4bd-213">Обратите внимание на то, что курсор отображается при взгляде на голограмму, и меняется на светло-точечный, когда не облаками на голограмме.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="0a4bd-214">Выполните касание, чтобы разместить голограмму.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="0a4bd-215">В настоящее время в нашем проекте можно разместить голограмму только один раз (повторное развертывание, чтобы повторить попытку).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="0a4bd-216">Глава 3. Общие координаты</span><span class="sxs-lookup"><span data-stu-id="0a4bd-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="0a4bd-217">Приятно видеть голограммы и взаимодействовать с ними, но давайте дальше.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="0a4bd-218">Мы настроили наш первый общий интерфейс, который все может видеть одновременно.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="0a4bd-219">Цели</span><span class="sxs-lookup"><span data-stu-id="0a4bd-219">Objectives</span></span>

* <span data-ttu-id="0a4bd-220">Настройте сеть для совместной работы.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="0a4bd-221">Создание общей контрольной точки.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-221">Establish a common reference point.</span></span>
* <span data-ttu-id="0a4bd-222">Совместное использование систем координат на разных устройствах.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="0a4bd-223">Все видят одну голограмму!</span><span class="sxs-lookup"><span data-stu-id="0a4bd-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="0a4bd-224">Для подключения приложения к серверу общего доступа необходимо объявить возможности **интернетклиентсервер** и **приватенетворкклиентсервер** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="0a4bd-225">Это делается для тех, кто уже находится в голограммах 240, но не забывайте об этом с учетом собственных проектов.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="0a4bd-226">В редакторе Unity перейдите к параметрам проигрывателя, перейдя к разделу "изменение параметров проекта > > Player".</span><span class="sxs-lookup"><span data-stu-id="0a4bd-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="0a4bd-227">Перейдите на вкладку "Магазин Windows".</span><span class="sxs-lookup"><span data-stu-id="0a4bd-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="0a4bd-228">В разделе "Параметры публикации > возможности" проверьте возможность **интернетклиентсервер** и возможности **приватенетворкклиентсервер** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="0a4bd-229">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0a4bd-229">Instructions</span></span>

* <span data-ttu-id="0a4bd-230">На **панели "проект** " перейдите в папку **HoloToolkit-Sharing-240\Prefabs\Sharing** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="0a4bd-231">Перетащите prefab **доступа** на **панель Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="0a4bd-232">Далее необходимо запустить службу общего доступа.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="0a4bd-233">Только **один компьютер** в общем интерфейсе должен выполнить этот шаг.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="0a4bd-234">В Unity — в меню верхнего уровня — выберите **меню холотулкит-Sharing-240**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="0a4bd-235">В раскрывающемся списке выберите пункт **запустить службу общего доступа** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="0a4bd-236">Проверьте параметр **частная сеть** и нажмите кнопку **Разрешить доступ** при появлении окна брандмауэра.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="0a4bd-237">Запишите IPv4-адрес, отображаемый в окне консоли службы общего доступа.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="0a4bd-238">Это тот же IP-адрес, что и у компьютера, на котором выполняется служба.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="0a4bd-239">Следуйте остальным инструкциям на **всех ПК** , которые будут присоединяться к общему интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="0a4bd-240">В **иерархии**выберите объект **общего доступа** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="0a4bd-241">В **инспекторе**в компоненте " **этап предоставления общего доступа** " измените **адрес сервера** с "localhost" на IPv4-адрес компьютера, на котором выполняется шарингсервице. exe.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="0a4bd-242">В **иерархии** выберите объект **холограмколлектион** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="0a4bd-243">В **инспекторе** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="0a4bd-244">В поле поиска введите **Импорт экспорт привязки диспетчер**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="0a4bd-245">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-245">Select the search result.</span></span>
* <span data-ttu-id="0a4bd-246">На **панели проект** перейдите к папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="0a4bd-247">Дважды щелкните скрипт **холограмплацемент** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0a4bd-248">Замените содержимое на приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="0a4bd-249">Вернитесь в Unity, выберите **холограмколлектион** на **панели Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="0a4bd-250">На **панели инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="0a4bd-251">В меню введите в поле поиска **диспетчер состояний приложения**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="0a4bd-252">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-252">Select the search result.</span></span>

<span data-ttu-id="0a4bd-253">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="0a4bd-254">Создайте проект для устройств HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="0a4bd-255">Назначьте один HoloLens для развертывания первым.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="0a4bd-256">Необходимо подождать, пока привязка будет отправлена в службу, прежде чем можно будет поместить Енергихуб (это может занять около 30-60 секунд).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="0a4bd-257">Пока передача не будет выполнена, жесты касания будут игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="0a4bd-258">После размещения Енергихуб его расположение загружается в службу, а затем можно выполнить развертывание на всех других устройствах HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="0a4bd-259">Когда новый HoloLens впервые присоединяется к сеансу, расположение Енергихуб может быть неправильным на этом устройстве.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="0a4bd-260">Однако, как только расположения привязки и Енергихуб загружаются из службы, Енергихуб должен перейти к новому общему расположению.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="0a4bd-261">Если это не происходит в течение ~ 30-60 секунд, перед настройкой привязки для получения дополнительных сведений о среде следует проанализировать расположение исходного HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="0a4bd-262">Если расположение по-прежнему не блокируется, выполните повторное развертывание на устройстве.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="0a4bd-263">Когда устройства готовы и запускают приложение, найдите Енергихуб.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="0a4bd-264">Можно ли принять все согласие на расположение голограммы и направление текста?</span><span class="sxs-lookup"><span data-stu-id="0a4bd-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="0a4bd-265">Глава 4. Обнаружение</span><span class="sxs-lookup"><span data-stu-id="0a4bd-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="0a4bd-266">Теперь все могут видеть одну голограмму!</span><span class="sxs-lookup"><span data-stu-id="0a4bd-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="0a4bd-267">Теперь давайте посмотрим все, кто еще подключен к нашему миру.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="0a4bd-268">В этой главе мы будем перехватить расположение и поворот всех других устройств HoloLens в одном сеансе совместного доступа.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="0a4bd-269">Цели</span><span class="sxs-lookup"><span data-stu-id="0a4bd-269">Objectives</span></span>

* <span data-ttu-id="0a4bd-270">Найдите друг друга в нашем общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="0a4bd-271">Выберите и поделитесь с вами аватаром игрока.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="0a4bd-272">Вложите аватар игрока рядом с головами всех.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="0a4bd-273">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0a4bd-273">Instructions</span></span>

* <span data-ttu-id="0a4bd-274">На **панели проект** перейдите к папке **голограмм** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="0a4bd-275">Перетащите **плайераватарсторе** в **иерархию**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="0a4bd-276">На **панели проект** перейдите к папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="0a4bd-277">Дважды щелкните скрипт **аватарселектор** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0a4bd-278">Замените содержимое на приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="0a4bd-279">В **иерархии** выберите объект **холограмколлектион** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="0a4bd-280">В **инспекторе** щелкните **Добавить компонент**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="0a4bd-281">В поле поиска введите " **диспетчер локальных игроков**".</span><span class="sxs-lookup"><span data-stu-id="0a4bd-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="0a4bd-282">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-282">Select the search result.</span></span>
* <span data-ttu-id="0a4bd-283">В **иерархии** выберите объект **холограмколлектион** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="0a4bd-284">В **инспекторе** щелкните **Добавить компонент**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="0a4bd-285">В поле поиска введите **Remote Player Manager**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="0a4bd-286">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-286">Select the search result.</span></span>
* <span data-ttu-id="0a4bd-287">Откройте скрипт **холограмплацемент** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="0a4bd-288">Замените содержимое на приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="0a4bd-289">Откройте скрипт **аппстатеманажер** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0a4bd-290">Замените содержимое на приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="0a4bd-291">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="0a4bd-292">Выполните сборку и развертывание проекта на устройствах HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="0a4bd-293">Когда вы слышите звуковой сигнал, найдите меню выбора аватара и выберите аватар с помощью жеста касания.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="0a4bd-294">Если вы не видите ни одной голограммы, то, когда HoloLens взаимодействует со службой, световая точка вокруг курсора будет иметь другой цвет: инициализация (темно-фиолетовый), Загрузка привязки (зеленый цвет), импорт/экспорт данных о расположении (желтый цвет) Отправка привязки (синий цвет).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="0a4bd-295">Если точкой вокруг курсора является цвет по умолчанию (светло-сиреневый), вы готовы к взаимодействию с другими игроками в вашем сеансе!</span><span class="sxs-lookup"><span data-stu-id="0a4bd-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="0a4bd-296">Взгляните на других пользователей, подключенных к своему модулю. в этом случае у вас будет один и тот же робот, а затем копируя свои головные движения!</span><span class="sxs-lookup"><span data-stu-id="0a4bd-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="0a4bd-297">Глава 5. размещение</span><span class="sxs-lookup"><span data-stu-id="0a4bd-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="0a4bd-298">В этой главе привязку можно разместить на реальных поверхностях.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="0a4bd-299">Мы будем использовать общие координаты для размещения этой привязки в средней точке между всеми, подключенными к общему интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="0a4bd-300">Цели</span><span class="sxs-lookup"><span data-stu-id="0a4bd-300">Objectives</span></span>

* <span data-ttu-id="0a4bd-301">Поместите голограммы на пространственной карте на основе головного расположения игроков.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="0a4bd-302">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0a4bd-302">Instructions</span></span>

* <span data-ttu-id="0a4bd-303">На **панели проект** перейдите к папке **голограмм** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="0a4bd-304">Перетащите **кустомспатиалмаппинг** prefab на **иерархию**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="0a4bd-305">На **панели проект** перейдите к папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="0a4bd-306">Дважды щелкните скрипт **аппстатеманажер** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0a4bd-307">Замените содержимое на приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="0a4bd-308">На **панели проект** перейдите к папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="0a4bd-309">Дважды щелкните скрипт **холограмплацемент** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0a4bd-310">Замените содержимое на приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="0a4bd-311">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="0a4bd-312">Выполните сборку и развертывание проекта на устройствах HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="0a4bd-313">Когда приложение будет готово, наведите на окружность и обратите внимание на то, как Енергихуб отображается в центре всех.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="0a4bd-314">Коснитесь, чтобы поместить Енергихуб.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="0a4bd-315">Попробуйте выполнить команду "Сброс целевого объекта", чтобы выбрать Енергихуб резервное копирование и совместная работа в качестве группы для перемещения голограммы в новое место.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="0a4bd-316">Глава 6-вещественная физика</span><span class="sxs-lookup"><span data-stu-id="0a4bd-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="0a4bd-317">В этой главе мы добавим голограммы, которые возводят на реальные поверхности.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="0a4bd-318">Просматривайте свое пространство с помощью проектов, запущенных вами и вашими друзьями!</span><span class="sxs-lookup"><span data-stu-id="0a4bd-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="0a4bd-319">Цели</span><span class="sxs-lookup"><span data-stu-id="0a4bd-319">Objectives</span></span>

* <span data-ttu-id="0a4bd-320">Запустите снаряды, который перевернут на реальные поверхности.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="0a4bd-321">Предоставьте общий доступ к снаряды, чтобы другие игроки могли видеть их.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="0a4bd-322">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0a4bd-322">Instructions</span></span>

* <span data-ttu-id="0a4bd-323">В **иерархии** выберите объект **холограмколлектион** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="0a4bd-324">В **инспекторе** щелкните **Добавить компонент**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="0a4bd-325">В поле поиска введите **Прожектиле Launcher**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="0a4bd-326">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-326">Select the search result.</span></span>

<span data-ttu-id="0a4bd-327">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="0a4bd-328">Выполните сборку и развертывание на устройствах HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="0a4bd-329">Когда приложение выполняется на всех устройствах, выполните воздушное касание, чтобы запустить прожектиле на реальных поверхностях.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="0a4bd-330">Узнайте, что происходит, когда прожектиле конфликтует с аватаром другого игрока!</span><span class="sxs-lookup"><span data-stu-id="0a4bd-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="0a4bd-331">Глава 7-Общий итог</span><span class="sxs-lookup"><span data-stu-id="0a4bd-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="0a4bd-332">В этой главе мы расскажем о портале, который может быть обнаружен только при совместной работе.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="0a4bd-333">Цели</span><span class="sxs-lookup"><span data-stu-id="0a4bd-333">Objectives</span></span>

* <span data-ttu-id="0a4bd-334">Совместное использование позволяет запустить достаточно снаряды на привязке, чтобы обнаружить секретный портал.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="0a4bd-335">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0a4bd-335">Instructions</span></span>

* <span data-ttu-id="0a4bd-336">На **панели проект** перейдите к папке **голограмм** .</span><span class="sxs-lookup"><span data-stu-id="0a4bd-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="0a4bd-337">Перетащите **этот ресурс** в качестве дочернего **для холограмколлектион**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="0a4bd-338">Выбрав **холограмколлектион** , нажмите кнопку **Добавить компонент** в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="0a4bd-339">В меню введите **експлодетаржет**в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="0a4bd-340">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-340">Select the search result.</span></span>
* <span data-ttu-id="0a4bd-341">Выбрав **холограмколлектион** , из **иерархии** перетащите объект **енергихуб** в целевое поле в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="0a4bd-342">Выбрав **холограмколлектион** , из **иерархии** перетащите объект «незаполненный **мир** » в поле «незаполненный **мир** » в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="0a4bd-343">**Развертывание и наслаждайтесь**</span><span class="sxs-lookup"><span data-stu-id="0a4bd-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="0a4bd-344">Выполните сборку и развертывание на устройствах HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="0a4bd-345">После запуска приложения совместная работа для запуска снаряды на Енергихуб.</span><span class="sxs-lookup"><span data-stu-id="0a4bd-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="0a4bd-346">Когда появится подсветка, запустите снаряды в подсвете роботов (нажмите робота три раза, чтобы получить дополнительные развлечения).</span><span class="sxs-lookup"><span data-stu-id="0a4bd-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
