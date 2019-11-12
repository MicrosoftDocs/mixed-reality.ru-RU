---
title: Основные сведения о MR 100-начало работы с Unity
description: Узнайте, как создать первое базовое приложение "Hello World" в смешанной реальности.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, Windows Mixed Reality, HoloLens, иммерсивное, VR, MR, начало работы, голограмма, Academy, учебник
ms.openlocfilehash: 0600383b3cca3f580f014597217afc6ae78836dd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926634"
---
>[!NOTE]
><span data-ttu-id="5265c-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5265c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5265c-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="5265c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5265c-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5265c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5265c-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="5265c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5265c-108">Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="5265c-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="5265c-109">Основные сведения о MR 100: Начало работы с Unity</span><span class="sxs-lookup"><span data-stu-id="5265c-109">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="5265c-110">В этом руководстве описано, как создать базовое приложение смешанной реальности, созданное с помощью Unity.</span><span class="sxs-lookup"><span data-stu-id="5265c-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="5265c-111">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="5265c-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5265c-112">Хождение</span><span class="sxs-lookup"><span data-stu-id="5265c-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5265c-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5265c-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5265c-114"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="5265c-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5265c-115">Основные сведения о MR 100: Начало работы с Unity</span><span class="sxs-lookup"><span data-stu-id="5265c-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="5265c-116">✔️</span><span class="sxs-lookup"><span data-stu-id="5265c-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5265c-117">✔️</span><span class="sxs-lookup"><span data-stu-id="5265c-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="5265c-118">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="5265c-118">Prerequisites</span></span>

* <span data-ttu-id="5265c-119">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5265c-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="5265c-120">Глава 1. Создание нового проекта</span><span class="sxs-lookup"><span data-stu-id="5265c-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="5265c-121">Для создания приложения с Unity необходимо сначала создать проект.</span><span class="sxs-lookup"><span data-stu-id="5265c-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="5265c-122">Этот проект организован в несколько папок, наиболее важным из которых является папка "активы".</span><span class="sxs-lookup"><span data-stu-id="5265c-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="5265c-123">Это папка, содержащая все ресурсы, импортируемые из средств создания цифрового содержимого, такие как Maya, Max кинотеатр 4D или Photoshop, весь код, создаваемый с помощью Visual Studio или избранного редактора кода, и любое количество файлов содержимого, создаваемых Unity в процессе создания сцен. , анимации и другие типы ресурсов Unity в редакторе.</span><span class="sxs-lookup"><span data-stu-id="5265c-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="5265c-124">Чтобы создать и развернуть приложения UWP, Unity может экспортировать проект как решение Visual Studio, которое будет содержать все необходимые файлы ресурсов и файлов кода.</span><span class="sxs-lookup"><span data-stu-id="5265c-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="5265c-125">Запустить Unity</span><span class="sxs-lookup"><span data-stu-id="5265c-125">Start Unity</span></span>
2. <span data-ttu-id="5265c-126">Выберите " **создать** "</span><span class="sxs-lookup"><span data-stu-id="5265c-126">Select **New**</span></span>
3. <span data-ttu-id="5265c-127">Введите имя проекта (например, "Микседреалитинтродуктион").</span><span class="sxs-lookup"><span data-stu-id="5265c-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="5265c-128">Укажите расположение для сохранения проекта</span><span class="sxs-lookup"><span data-stu-id="5265c-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="5265c-129">Убедитесь, что выбран **трехмерный** переключатель.</span><span class="sxs-lookup"><span data-stu-id="5265c-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="5265c-130">Выбор **создания проекта**</span><span class="sxs-lookup"><span data-stu-id="5265c-130">Select **Create project**</span></span>

<span data-ttu-id="5265c-131">Поздравляем, вы все равно можете начать работу с настройками смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5265c-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="5265c-132">Глава 2. Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="5265c-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="5265c-133">Основная камера Unity обрабатывает отслеживание Head и стереоскопик отрисовку.</span><span class="sxs-lookup"><span data-stu-id="5265c-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="5265c-134">Существует несколько изменений, которые необходимо внести в основную камеру для использования в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5265c-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="5265c-135">Выберите Файл > создать сцену</span><span class="sxs-lookup"><span data-stu-id="5265c-135">Select File > New Scene</span></span>

<span data-ttu-id="5265c-136">Во-первых, будет проще размещать приложение, если вы представьтее начальную точку пользователя как (**X**: 0, **Y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="5265c-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="5265c-137">Так как основная камера отслеживает перемещение заголовка пользователя, начальное расположение пользователя можно задать, установив начальную точку основной камеры.</span><span class="sxs-lookup"><span data-stu-id="5265c-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="5265c-138">На панели **Иерархия** выберите **Главная камера** .</span><span class="sxs-lookup"><span data-stu-id="5265c-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="5265c-139">На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** с (**x**: 0, **y**: 1, **z**:-10) на (**x**: 0, **y**: 0, **z**: 0).</span><span class="sxs-lookup"><span data-stu-id="5265c-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="5265c-140">Во вторых, для фона камеры по умолчанию требуется определенная мысль.</span><span class="sxs-lookup"><span data-stu-id="5265c-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="5265c-141">**Для приложений HoloLens**реальный мир должен отображаться позади всей визуализации камеры, а не скибокс текстуры.</span><span class="sxs-lookup"><span data-stu-id="5265c-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="5265c-142">Выбрав **основную камеру** на панели « **Иерархия** », найдите компонент **Камера** на панели **инспектора** и измените раскрывающийся список **снять флаги** с **скибокс** на **сплошной цвет**.</span><span class="sxs-lookup"><span data-stu-id="5265c-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="5265c-143">Выберите средство выбора цвета **фона** и измените значения **RGBA** на (0, 0, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="5265c-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="5265c-144">**Для приложений смешанной реальности, предназначенных для впечатляющих головных телефонов**, мы можем использовать стандартную текстуру скибокс, предоставляемую Unity.</span><span class="sxs-lookup"><span data-stu-id="5265c-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="5265c-145">Выбрав **основную камеру** на панели « **Иерархия** », найдите на панели **инспектора** компонент **Камера** и в раскрывающемся списке **clear Flags (четкие флаги** ) выберите **скибокс**.</span><span class="sxs-lookup"><span data-stu-id="5265c-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="5265c-146">В-третьих, давайте рассмотрим близкую плоскость клипов в Unity и не допускайте, чтобы объекты были слишком близки к глазу пользователей, когда пользователь приближается к объекту или объект приближает пользователя.</span><span class="sxs-lookup"><span data-stu-id="5265c-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="5265c-147">**Для приложений hololens**на ближайшей плоскости Clip можно установить значение hololens, [рекомендуемый](camera-in-unity.md#clip-planes) 0,85 метров.</span><span class="sxs-lookup"><span data-stu-id="5265c-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="5265c-148">Выбрав **основную камеру** на панели " **Иерархия** ", найдите компонент **Камера** на панели **инспектора** и измените поле **ближней плоскости клипа** с **0,3** по умолчанию на HoloLens рекомендованные **0,85.** .</span><span class="sxs-lookup"><span data-stu-id="5265c-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="5265c-149">**Для приложений смешанной реальности, предназначенных для впечатляющих гарнитур**, можно использовать параметр по умолчанию, предоставляемый Unity.</span><span class="sxs-lookup"><span data-stu-id="5265c-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="5265c-150">Выбрав **основную камеру** на панели " **Иерархия** ", найдите компонент **Камера** на панели **инспектора** и заполните поле **ближней плоскости** на значение по умолчанию **0,3**.</span><span class="sxs-lookup"><span data-stu-id="5265c-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="5265c-151">Наконец, позвольте нам сохранить ход выполнения до сих пор.</span><span class="sxs-lookup"><span data-stu-id="5265c-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="5265c-152">Чтобы сохранить изменения сцены, выберите **файл > сохранить сцену как**, назовите сцену **Main**и выберите **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5265c-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="5265c-153">Глава 3. Настройка параметров проекта</span><span class="sxs-lookup"><span data-stu-id="5265c-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="5265c-154">В этой главе мы настроили некоторые параметры проекта Unity, которые помогут нам ориентироваться на пакет SDK для Windows holographic для разработки.</span><span class="sxs-lookup"><span data-stu-id="5265c-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="5265c-155">Также будут заданы некоторые параметры качества для нашего приложения.</span><span class="sxs-lookup"><span data-stu-id="5265c-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="5265c-156">Наконец, мы гарантируем, что наши цели сборки будут установлены в магазин Windows.</span><span class="sxs-lookup"><span data-stu-id="5265c-156">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="5265c-157">Параметры производительности и качества Unity</span><span class="sxs-lookup"><span data-stu-id="5265c-157">Unity performance and quality settings</span></span>

<span data-ttu-id="5265c-158">**Параметры качества Unity для HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5265c-158">**Unity quality settings for HoloLens**</span></span>

![Параметры качества Unity для HoloLens](images/qualitysettings.png)

<span data-ttu-id="5265c-160">Так как поддержание высокой частоты кадров в HoloLens настолько важно, мы хотим, чтобы параметры качества были настроены для обеспечения максимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="5265c-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="5265c-161">Для получения более подробных сведений о производительности, [следуйте рекомендациям по повышению производительности для Unity](performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="5265c-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="5265c-162">Выберите **изменить > параметры проекта > качество**</span><span class="sxs-lookup"><span data-stu-id="5265c-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="5265c-163">Выберите **раскрывающийся список** в эмблеме **магазина Windows** и выберите **очень низкий**.</span><span class="sxs-lookup"><span data-stu-id="5265c-163">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="5265c-164">Вы узнаете, что параметр применяется правильно, если поле в столбце магазина Windows и **очень низкая** строка имеют зеленый цвет.</span><span class="sxs-lookup"><span data-stu-id="5265c-164">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="5265c-165">**Для приложений смешанной реальности, предназначенных для перекрыто**, можно оставить для параметров качества значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5265c-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="5265c-166">Целевой пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="5265c-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="5265c-167">**Целевой пакет SDK для Windows holographic**</span><span class="sxs-lookup"><span data-stu-id="5265c-167">**Target Windows Holographic SDK**</span></span>

![Целевой пакет SDK для Windows holographic](images/xrsettings.png)

<span data-ttu-id="5265c-169">Необходимо разрешить Unity знать, что приложение, которое мы пытаемся экспортировать, должно создать [иммерсивное представление](app-views.md) вместо 2D-представления.</span><span class="sxs-lookup"><span data-stu-id="5265c-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="5265c-170">Для этого необходимо включить поддержку виртуальной реальности в Unity, предназначенном для пакета SDK для Windows 10.</span><span class="sxs-lookup"><span data-stu-id="5265c-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="5265c-171">Выберите **изменить > параметры проекта > Player**.</span><span class="sxs-lookup"><span data-stu-id="5265c-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="5265c-172">На **панели инспектора** для параметров проигрывателя выберите значок **Магазин Windows** .</span><span class="sxs-lookup"><span data-stu-id="5265c-172">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="5265c-173">Разверните группу **Параметры XR** .</span><span class="sxs-lookup"><span data-stu-id="5265c-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="5265c-174">В разделе " **Подготовка** " установите флажок " **Virtual Reality Supported** ", чтобы добавить новый список **пакетов SDK виртуальной реальности** .</span><span class="sxs-lookup"><span data-stu-id="5265c-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="5265c-175">Убедитесь, что в списке присутствует **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="5265c-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="5265c-176">В противном случае нажмите кнопку **+** в нижней части списка и выберите **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="5265c-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="5265c-177">Если значок " **Магазин Windows** " не отображается, убедитесь, что вы выбрали серверную часть скриптов .NET для Магазина Windows перед установкой.</span><span class="sxs-lookup"><span data-stu-id="5265c-177">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="5265c-178">В противном случае может потребоваться переустановить Unity с правильной установкой Windows.</span><span class="sxs-lookup"><span data-stu-id="5265c-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="5265c-179">**Проверка конфигурации .NET**</span><span class="sxs-lookup"><span data-stu-id="5265c-179">**Verify .NET Configuration**</span></span>

![Проверка конфигурации .NET](images/configoptions-375px.png)

1. <span data-ttu-id="5265c-181">Перейдите в раздел **изменить > параметры проекта > проигрывателе** (возможно, это можно будет выполнить на предыдущем шаге).</span><span class="sxs-lookup"><span data-stu-id="5265c-181">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="5265c-182">На **панели инспектора** для параметров проигрывателя выберите значок **Магазин Windows** .</span><span class="sxs-lookup"><span data-stu-id="5265c-182">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="5265c-183">В разделе Настройка **других параметров** убедитесь, что для **серверной части скрипта** задано значение **.NET** .</span><span class="sxs-lookup"><span data-stu-id="5265c-183">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="5265c-184">Задание Awesome для получения всех примененных параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="5265c-184">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="5265c-185">Теперь добавим голограмму!</span><span class="sxs-lookup"><span data-stu-id="5265c-185">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="5265c-186">Глава 4. Создание куба</span><span class="sxs-lookup"><span data-stu-id="5265c-186">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="5265c-187">Создание куба в проекте Unity аналогично созданию любого другого объекта в Unity.</span><span class="sxs-lookup"><span data-stu-id="5265c-187">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="5265c-188">Размещение Куба перед пользователем не представляет трудностей, так как система координат Unity сопоставлена с реальным миром, где один счетчик в Unity является приблизительно одним показателем в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="5265c-188">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="5265c-189">В левом верхнем углу панели **Иерархия** выберите **создать** раскрывающийся список и выберите **трехмерный объект > куб**.</span><span class="sxs-lookup"><span data-stu-id="5265c-189">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="5265c-190">Выберите только что созданный **куб** на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="5265c-190">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="5265c-191">В **инспекторе** найдите компонент **преобразования** и измените его **Расположение** на (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="5265c-191">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="5265c-192">*Это положение Куба 2 метров перед начальной позицией пользователя.*</span><span class="sxs-lookup"><span data-stu-id="5265c-192">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="5265c-193">В компоненте **Преобразование** измените **поворот** на (**x**: 45, **Y**: 45, **Z**: 45) и измените **масштаб** на (**x**: 0,25, **y**: 0,25, **Z**: 0,25).</span><span class="sxs-lookup"><span data-stu-id="5265c-193">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="5265c-194">*При этом куб масштабируется до 0,25 метров.*</span><span class="sxs-lookup"><span data-stu-id="5265c-194">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="5265c-195">Чтобы сохранить изменения сцены, выберите **файл > сохранить сцену**.</span><span class="sxs-lookup"><span data-stu-id="5265c-195">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="5265c-196">Глава 5. Проверка на устройстве из редактора Unity</span><span class="sxs-lookup"><span data-stu-id="5265c-196">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="5265c-197">Теперь, когда мы создали наш куб, пора выполнить быструю проверку устройства.</span><span class="sxs-lookup"><span data-stu-id="5265c-197">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="5265c-198">Это можно сделать непосредственно в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="5265c-198">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="5265c-199">Начальная настройка</span><span class="sxs-lookup"><span data-stu-id="5265c-199">Initial setup</span></span>

1. <span data-ttu-id="5265c-200">На компьютере разработки в Unity откройте окно **файл > параметры сборки** .</span><span class="sxs-lookup"><span data-stu-id="5265c-200">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="5265c-201">Измените **платформу** на **универсальная платформа Windows** и нажмите кнопку **Переключение платформы** .</span><span class="sxs-lookup"><span data-stu-id="5265c-201">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="5265c-202">Для HoloLens используйте удаленное взаимодействие Unity</span><span class="sxs-lookup"><span data-stu-id="5265c-202">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="5265c-203">На HoloLens установите и запустите [проигрыватель holographic Remoting](holographic-remoting-player.md), доступный в магазине Windows.</span><span class="sxs-lookup"><span data-stu-id="5265c-203">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="5265c-204">Запустите приложение на устройстве, и оно перейдет в состояние ожидания и отобразит IP-адрес устройства.</span><span class="sxs-lookup"><span data-stu-id="5265c-204">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="5265c-205">Запишите IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="5265c-205">Note down the IP.</span></span>
2. <span data-ttu-id="5265c-206">Откройте **окно > XR > с эмуляцией holographic**.</span><span class="sxs-lookup"><span data-stu-id="5265c-206">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="5265c-207">Измените **режим эмуляции** с **нет** на **Удаленный с устройством**.</span><span class="sxs-lookup"><span data-stu-id="5265c-207">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="5265c-208">В поле **Удаленный компьютер**введите IP-адрес HoloLens, записанный ранее.</span><span class="sxs-lookup"><span data-stu-id="5265c-208">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="5265c-209">Нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="5265c-209">Click **Connect**.</span></span>
6. <span data-ttu-id="5265c-210">Убедитесь, что **состояние подключения** изменено на зеленый **подключен**.</span><span class="sxs-lookup"><span data-stu-id="5265c-210">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="5265c-211">Теперь можно нажать кнопку **воспроизвести** в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="5265c-211">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="5265c-212">Теперь вы сможете увидеть куб на устройстве и в редакторе.</span><span class="sxs-lookup"><span data-stu-id="5265c-212">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="5265c-213">Вы можете приостанавливать, проверять объекты и выполнять отладку точно так же, как вы запускаете приложение в редакторе, поскольку именно это происходит, но с видео, аудио и входными данными устройства передаются по сети между хост-компьютером и устройством.</span><span class="sxs-lookup"><span data-stu-id="5265c-213">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="5265c-214">Для других головных телефонов с поддержкой смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5265c-214">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="5265c-215">Подключите гарнитуру к компьютеру разработки, используя USB-кабель, HDMI или порт дисплея.</span><span class="sxs-lookup"><span data-stu-id="5265c-215">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="5265c-216">Запустите **портал Mixed Reality** и убедитесь, что вы выполнили первую процедуру запуска.</span><span class="sxs-lookup"><span data-stu-id="5265c-216">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="5265c-217">В Unity теперь можно нажать кнопку Воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="5265c-217">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="5265c-218">Теперь вы сможете увидеть представление куба на гарнитуре смешанной реальности и в редакторе.</span><span class="sxs-lookup"><span data-stu-id="5265c-218">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="5265c-219">Глава 6. сборка и развертывание на устройстве из Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5265c-219">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="5265c-220">Теперь все готово для компиляции нашего проекта в Visual Studio и развертывания на целевом устройстве.</span><span class="sxs-lookup"><span data-stu-id="5265c-220">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="5265c-221">Экспорт в решение Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5265c-221">Export to the Visual Studio solution</span></span>

1.  <span data-ttu-id="5265c-222">Откройте окно **файл > параметры сборки** .</span><span class="sxs-lookup"><span data-stu-id="5265c-222">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="5265c-223">Щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="5265c-223">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="5265c-224">Измените **платформу** на **универсальная платформа Windows** и нажмите кнопку **Сменить платформу**.</span><span class="sxs-lookup"><span data-stu-id="5265c-224">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="5265c-225">В параметрах **магазина Windows** убедитесь, что **пакет SDK** является **универсальным 10**.</span><span class="sxs-lookup"><span data-stu-id="5265c-225">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="5265c-226">Для целевого устройства оставьте на **любом устройстве** для перекрыто отображение или переключитесь на **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="5265c-226">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="5265c-227">**Тип сборки UWP** должен быть **D3D**.</span><span class="sxs-lookup"><span data-stu-id="5265c-227">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="5265c-228">**Пакет SDK для UWP** можно оставить в **последней установленной версии**.</span><span class="sxs-lookup"><span data-stu-id="5265c-228">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="5265c-229">Проверка **проектов C# Unity** при отладке.</span><span class="sxs-lookup"><span data-stu-id="5265c-229">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="5265c-230">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="5265c-230">Click **Build**.</span></span>
10. <span data-ttu-id="5265c-231">В проводнике щелкните **создать папку** и назовите папку **app**.</span><span class="sxs-lookup"><span data-stu-id="5265c-231">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="5265c-232">Выбрав папку **приложения** , нажмите кнопку **выбрать папку** .</span><span class="sxs-lookup"><span data-stu-id="5265c-232">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="5265c-233">После завершения сборки Unity появится окно проводника Windows.</span><span class="sxs-lookup"><span data-stu-id="5265c-233">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="5265c-234">Откройте папку **приложения** в проводнике.</span><span class="sxs-lookup"><span data-stu-id="5265c-234">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="5265c-235">Откройте созданное решение Visual Studio (Микседреалитинтродуктион. sln в этом примере).</span><span class="sxs-lookup"><span data-stu-id="5265c-235">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="5265c-236">Компиляция решения Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5265c-236">Compile the Visual Studio solution</span></span>

<span data-ttu-id="5265c-237">Наконец, мы будем компилировать экспортированное решение Visual Studio, разворачивать его и испытать на устройстве.</span><span class="sxs-lookup"><span data-stu-id="5265c-237">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="5265c-238">С помощью верхней панели инструментов в Visual Studio измените целевой объект с **Отладка** на **выпуск** и с **ARM** на **x86**.</span><span class="sxs-lookup"><span data-stu-id="5265c-238">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="5265c-239">Инструкции отличаются для развертывания на устройстве и в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="5265c-239">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="5265c-240">Выполните инструкции, соответствующие вашей настройке.</span><span class="sxs-lookup"><span data-stu-id="5265c-240">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="5265c-241">Развертывание на устройстве смешанной реальности через Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="5265c-241">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="5265c-242">Щелкните стрелку рядом с кнопкой **локальный компьютер** и измените целевой объект развертывания на **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="5265c-242">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="5265c-243">Введите IP-адрес устройства смешанной реальности и измените **режим проверки подлинности** на универсальный (незашифрованный протокол) для HoloLens и **Windows** для других устройств.</span><span class="sxs-lookup"><span data-stu-id="5265c-243">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="5265c-244">Щелкните **отладка > начать без отладки**.</span><span class="sxs-lookup"><span data-stu-id="5265c-244">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="5265c-245">**Для HoloLens**, если это первое развертывание на устройстве, необходимо связать его [с помощью Visual Studio](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5265c-245">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="5265c-246">Развертывание на устройстве смешанной реальности по USB</span><span class="sxs-lookup"><span data-stu-id="5265c-246">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="5265c-247">Убедитесь, что устройство подключено через USB-кабель.</span><span class="sxs-lookup"><span data-stu-id="5265c-247">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="5265c-248">**Для HoloLens**щелкните стрелку рядом с кнопкой **локальный компьютер** и измените целевой объект развертывания на **Device (устройство**).</span><span class="sxs-lookup"><span data-stu-id="5265c-248">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="5265c-249">**Для устройств перекрыто, подключенных к компьютеру**, сохраните параметр на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="5265c-249">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="5265c-250">Убедитесь, что у вас работает **портал смешанной реальности** .</span><span class="sxs-lookup"><span data-stu-id="5265c-250">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="5265c-251">Щелкните **отладка > начать без отладки**.</span><span class="sxs-lookup"><span data-stu-id="5265c-251">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="5265c-252">Развертывание в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="5265c-252">Deploy to Emulator</span></span>

1. <span data-ttu-id="5265c-253">Щелкните стрелку рядом с кнопкой **устройство** , а затем в раскрывающемся списке выберите **эмулятор HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="5265c-253">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="5265c-254">Щелкните **отладка > начать без отладки**.</span><span class="sxs-lookup"><span data-stu-id="5265c-254">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="5265c-255">Попробуйте приложение</span><span class="sxs-lookup"><span data-stu-id="5265c-255">Try out your app</span></span>

<span data-ttu-id="5265c-256">Теперь, когда ваше приложение развернуто, постарайтесь переместить весь куб и увидеть, что он остается в мире перед вами.</span><span class="sxs-lookup"><span data-stu-id="5265c-256">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="5265c-257">См. также</span><span class="sxs-lookup"><span data-stu-id="5265c-257">See also</span></span>

* [<span data-ttu-id="5265c-258">Обзор разработки в Unity</span><span class="sxs-lookup"><span data-stu-id="5265c-258">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="5265c-259">Рекомендации по работе с Unity и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5265c-259">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="5265c-260">Основные сведения о MR 101</span><span class="sxs-lookup"><span data-stu-id="5265c-260">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="5265c-261">Основные 101Eи MR</span><span class="sxs-lookup"><span data-stu-id="5265c-261">MR Basics 101E</span></span>](holograms-101e.md)
