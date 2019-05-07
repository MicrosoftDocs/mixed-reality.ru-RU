---
title: Основы MR 100 - Приступая к работе с Unity
description: Узнайте, как создать свое первое приложение «hello world» основные смешанной реальности.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: смешанной реальности, смешанной реальности Windows, HoloLens, создающий эффект присутствия, виртуальной реальности, mr, приступить к работе, голограмма, academy, учебник
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993623"
---
>[!NOTE]
><span data-ttu-id="d6026-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="d6026-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d6026-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="d6026-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d6026-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d6026-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d6026-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="d6026-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d6026-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d6026-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d6026-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="d6026-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="d6026-110">MR Basics 100: Приступая к работе с Unity</span><span class="sxs-lookup"><span data-stu-id="d6026-110">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="d6026-111">Этот учебник поможет выполнить создание основных смешанной реальности приложений, созданных с помощью Unity.</span><span class="sxs-lookup"><span data-stu-id="d6026-111">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="d6026-112">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="d6026-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d6026-113">Курс</span><span class="sxs-lookup"><span data-stu-id="d6026-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d6026-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d6026-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d6026-115"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d6026-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d6026-116">MR Basics 100: Приступая к работе с Unity</span><span class="sxs-lookup"><span data-stu-id="d6026-116">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="d6026-117">✔️</span><span class="sxs-lookup"><span data-stu-id="d6026-117">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d6026-118">✔️</span><span class="sxs-lookup"><span data-stu-id="d6026-118">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="d6026-119">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="d6026-119">Prerequisites</span></span>

* <span data-ttu-id="d6026-120">ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d6026-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="d6026-121">Глава 1 - Создание нового проекта</span><span class="sxs-lookup"><span data-stu-id="d6026-121">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="d6026-122">Чтобы создать приложение с помощью Unity, необходимо сначала создать проект.</span><span class="sxs-lookup"><span data-stu-id="d6026-122">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="d6026-123">Этот проект организована в несколько папок, наиболее важным из которых является папку ресурсы.</span><span class="sxs-lookup"><span data-stu-id="d6026-123">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="d6026-124">Это папка, содержащая все ресурсы, импортированные из средства Создание цифрового содержимого, такие как Maya, кинотеатрах максимум 4D или Photoshop, весь код, созданных с помощью Visual Studio или свой основной редактор кода, и любое количество файлов содержимого, что Unity создается такое же вы объедините сцены , анимации и другие типы активов Unity в редакторе.</span><span class="sxs-lookup"><span data-stu-id="d6026-124">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="d6026-125">Для создания и развертывания приложений универсальной платформы Windows, Unity можно экспортировать как решение Visual Studio, который будет содержать все необходимые средства и файлы кода проекта.</span><span class="sxs-lookup"><span data-stu-id="d6026-125">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="d6026-126">Запустите Unity</span><span class="sxs-lookup"><span data-stu-id="d6026-126">Start Unity</span></span>
2. <span data-ttu-id="d6026-127">Выберите **New**</span><span class="sxs-lookup"><span data-stu-id="d6026-127">Select **New**</span></span>
3. <span data-ttu-id="d6026-128">Введите имя проекта (например) «MixedRealityIntroduction»)</span><span class="sxs-lookup"><span data-stu-id="d6026-128">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="d6026-129">Введите расположение для сохранения проекта</span><span class="sxs-lookup"><span data-stu-id="d6026-129">Enter a location to save your project</span></span>
5. <span data-ttu-id="d6026-130">Убедитесь, **3D** выбран переключатель</span><span class="sxs-lookup"><span data-stu-id="d6026-130">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="d6026-131">Выберите **создать проект**</span><span class="sxs-lookup"><span data-stu-id="d6026-131">Select **Create project**</span></span>

<span data-ttu-id="d6026-132">Поздравляем Вы являетесь информации о настройке быстро начать работу с настройки смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d6026-132">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="d6026-133">Глава 2 - Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="d6026-133">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="d6026-134">Unity Main Camera обрабатывает отслеживания head "и" stereoscopic Подготовка к просмотру.</span><span class="sxs-lookup"><span data-stu-id="d6026-134">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="d6026-135">Существуют некоторые изменения, чтобы вносить Main Camera, чтобы использовать его с помощью смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d6026-135">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>
1. <span data-ttu-id="d6026-136">Выберите Файл > создать сцену</span><span class="sxs-lookup"><span data-stu-id="d6026-136">Select File > New Scene</span></span>

<span data-ttu-id="d6026-137">Во-первых, он будет проще макета приложения, если представить пользователя в качестве начальной позиции (**X**: 0, **Y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="d6026-137">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="d6026-138">Поскольку Main Camera отслеживает перемещение головы пользователя, задавая начальное положение Main Camera можно задать начальную позицию пользователь.</span><span class="sxs-lookup"><span data-stu-id="d6026-138">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>
1. <span data-ttu-id="d6026-139">Выберите **Main Camera** в **иерархии** панели</span><span class="sxs-lookup"><span data-stu-id="d6026-139">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="d6026-140">В **инспектор** панели, найти **преобразования** компонента и изменение **позиции** из (**X**: 0, **Y**: 1, **Z**: -10) для (**X**: 0, **Y**: 0, **Z**: 0)</span><span class="sxs-lookup"><span data-stu-id="d6026-140">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="d6026-141">Во-вторых фон камеры по умолчанию необходимо продумать.</span><span class="sxs-lookup"><span data-stu-id="d6026-141">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="d6026-142">**Для приложений HoloLens**, реальный мир должен отображаться за все камеры подготовке к просмотру не Skybox текстуры.</span><span class="sxs-lookup"><span data-stu-id="d6026-142">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>
1. <span data-ttu-id="d6026-143">С помощью **Main Camera** снимая выделение в **иерархии** панели, найти **камеры** компонент в **инспектор** панели и изменить **Очистить флаги** раскрывающийся список **Skybox** для **Одноцветная**.</span><span class="sxs-lookup"><span data-stu-id="d6026-143">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="d6026-144">Выберите **фона** палитра цветов и изменение **RGBA** значения (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="d6026-144">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="d6026-145">**Для смешанной реальности приложения, назначенные для иммерсивную**, мы можем использовать текстуру Skybox по умолчанию, среда Unity предоставляет.</span><span class="sxs-lookup"><span data-stu-id="d6026-145">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>
1. <span data-ttu-id="d6026-146">С помощью **Main Camera** снимая выделение в **иерархии** панели, найти **камеры** компонент в **инспектор** панели и сохранить **Очистить флаги** раскрывающийся список, чтобы **Skybox**.</span><span class="sxs-lookup"><span data-stu-id="d6026-146">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="d6026-147">В-третьих давайте рассмотрим ближней отсекающей плоскости в Unity и предотвращают объектов представляется слишком близко к пользователям глаза как пользователь достигает объект или объект приближается к пользователю.</span><span class="sxs-lookup"><span data-stu-id="d6026-147">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="d6026-148">**Для приложений HoloLens**, может быть присвоено ближней отсекающей плоскости [HoloLens рекомендуется](camera-in-unity.md#clip-planes) 0,85 метров.</span><span class="sxs-lookup"><span data-stu-id="d6026-148">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>
1. <span data-ttu-id="d6026-149">С помощью **Main Camera** снимая выделение в **иерархии** панели, найти **камеры** компонент в **инспектор** панели и изменить **Практически отсекающей плоскости** поле по умолчанию **0,3** для HoloLens рекомендуется **0,85**.</span><span class="sxs-lookup"><span data-stu-id="d6026-149">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="d6026-150">**Для смешанной реальности приложения, назначенные для иммерсивную**, можно использовать параметр по умолчанию, который предоставляет Unity.</span><span class="sxs-lookup"><span data-stu-id="d6026-150">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>
1. <span data-ttu-id="d6026-151">С помощью **Main Camera** снимая выделение в **иерархии** панели, найти **камеры** компонент в **инспектор** панели и сохранить **Практически отсекающей плоскости** поле по умолчанию **0,3**.</span><span class="sxs-lookup"><span data-stu-id="d6026-151">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="d6026-152">Наконец сообщите нам сохраните наши достижения промежуточные.</span><span class="sxs-lookup"><span data-stu-id="d6026-152">Finally, let us save our progress so far.</span></span> <span data-ttu-id="d6026-153">Чтобы сохранить изменения сцены, выберите **файл > Сохранить сцену как**, присвойте сцене имя **Main**и выберите **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="d6026-153">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="d6026-154">Глава 3 - Настройка параметров проекта</span><span class="sxs-lookup"><span data-stu-id="d6026-154">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="d6026-155">В этой главе мы определим некоторые параметры проекта Unity, которые помогают нам целевого пакета SDK Windows Holographic для разработки приложений.</span><span class="sxs-lookup"><span data-stu-id="d6026-155">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="d6026-156">Мы также будет задать некоторые параметры качества для нашего приложения.</span><span class="sxs-lookup"><span data-stu-id="d6026-156">We will also set some quality settings for our application.</span></span> <span data-ttu-id="d6026-157">Наконец мы гарантируем, что наших целевых объектов сборки установлены в Windows Store.</span><span class="sxs-lookup"><span data-stu-id="d6026-157">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="d6026-158">Параметры производительности и качества Unity</span><span class="sxs-lookup"><span data-stu-id="d6026-158">Unity performance and quality settings</span></span>

<span data-ttu-id="d6026-159">**Параметры качества Unity для HoloLens**</span><span class="sxs-lookup"><span data-stu-id="d6026-159">**Unity quality settings for HoloLens**</span></span>

![Параметры качества Unity для HoloLens](images/qualitysettings.png) 

<span data-ttu-id="d6026-161">Так как обслуживание высокой частоты кадров на HoloLens так важен, мы хотим параметры качества, такая конфигурация специально наибольшую производительность.</span><span class="sxs-lookup"><span data-stu-id="d6026-161">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="d6026-162">Более подробные сведения о производительности, [рекомендации по производительности для Unity](performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="d6026-162">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>
1. <span data-ttu-id="d6026-163">Выберите **изменить > Параметры проекта > качества**</span><span class="sxs-lookup"><span data-stu-id="d6026-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="d6026-164">Выберите **раскрывающийся список** под **Windows Store** логотип и выберите **очень низкий**.</span><span class="sxs-lookup"><span data-stu-id="d6026-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="d6026-165">Вы будете знать, применяется параметр правильно при поле в столбце Windows Store и **очень низкий** строки отображается зеленым цветом.</span><span class="sxs-lookup"><span data-stu-id="d6026-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="d6026-166">**Для смешанной реальности приложения, назначенные для перекрыто отображает**, параметры качества можно оставить значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d6026-166">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="d6026-167">Целевая платформа — Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="d6026-167">Target Windows 10 SDK</span></span>

<span data-ttu-id="d6026-168">**Целевой объект Windows Holographic SDK**</span><span class="sxs-lookup"><span data-stu-id="d6026-168">**Target Windows Holographic SDK**</span></span>

![Целевой объект Windows Holographic SDK](images/xrsettings.png) 

<span data-ttu-id="d6026-170">Нужно сообщить Unity известно, что следует создать приложение, мы пытаемся Экспорт [иммерсивных представление](app-views.md) вместо двухмерном виде.</span><span class="sxs-lookup"><span data-stu-id="d6026-170">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="d6026-171">Это делается путем включения поддержки виртуальной реальности в Unity для различных версий пакета SDK для Windows 10.</span><span class="sxs-lookup"><span data-stu-id="d6026-171">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>
1. <span data-ttu-id="d6026-172">Перейдите к **изменить > Параметры проекта > проигрывателя**.</span><span class="sxs-lookup"><span data-stu-id="d6026-172">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="d6026-173">В **панели Инспектора** параметры проигрывателя, выбор **Windows Store** значок.</span><span class="sxs-lookup"><span data-stu-id="d6026-173">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="d6026-174">Разверните **XR параметры** группы.</span><span class="sxs-lookup"><span data-stu-id="d6026-174">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="d6026-175">В **визуализации** установите флажок **поддерживается виртуальной реальности** флажок, чтобы добавить новый **виртуальной реальности SDK** списка.</span><span class="sxs-lookup"><span data-stu-id="d6026-175">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="d6026-176">Убедитесь, что **Windows Mixed Reality** появится в списке.</span><span class="sxs-lookup"><span data-stu-id="d6026-176">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="d6026-177">Если это не так, выберите **+** кнопку в нижней части списка и выберите **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="d6026-177">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="d6026-178">Если вы не видите **Windows Store** значок, проверьте соответствие всем требованиям, чтобы убедиться, что вы выбрали Windows Store сценариев серверной части .NET перед установкой.</span><span class="sxs-lookup"><span data-stu-id="d6026-178">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="d6026-179">В противном случае может потребоваться переустановить Unity с правильной установки Windows.</span><span class="sxs-lookup"><span data-stu-id="d6026-179">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="d6026-180">**Проверка конфигурации .NET**</span><span class="sxs-lookup"><span data-stu-id="d6026-180">**Verify .NET Configuration**</span></span>

![Проверка конфигурации .NET](images/configoptions-375px.png)

1. <span data-ttu-id="d6026-182">Перейдите к **изменить > Параметры проекта > проигрывателя** (по-прежнему возможно, это на предыдущем шаге).</span><span class="sxs-lookup"><span data-stu-id="d6026-182">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="d6026-183">В **панели Инспектора** параметры проигрывателя, выбор **Windows Store** значок.</span><span class="sxs-lookup"><span data-stu-id="d6026-183">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="d6026-184">В **другие параметры** конфигурации раздела, убедитесь, что **сценариев серверной части** присваивается **.NET**</span><span class="sxs-lookup"><span data-stu-id="d6026-184">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="d6026-185">Awesome задания в начало всех проекта параметры, применяемые.</span><span class="sxs-lookup"><span data-stu-id="d6026-185">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="d6026-186">Затем добавьте голограмма сообщите нам!</span><span class="sxs-lookup"><span data-stu-id="d6026-186">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="d6026-187">Глава 4 — Создание куба</span><span class="sxs-lookup"><span data-stu-id="d6026-187">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="d6026-188">Создание куба в проекте Unity — аналогично созданию любого другого объекта в Unity.</span><span class="sxs-lookup"><span data-stu-id="d6026-188">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="d6026-189">Размещение куба глазах у пользователя несложно, так как система координат Unity сопоставляется реальном мире - где метра в Unity — приблизительно метра в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="d6026-189">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>
1. <span data-ttu-id="d6026-190">В верхнем левом углу **иерархии** панели, выберите **создать** раскрывающийся список и выберите **трехмерный объект > куба**.</span><span class="sxs-lookup"><span data-stu-id="d6026-190">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="d6026-191">Выберите только что созданный **куба** в **иерархии** панели</span><span class="sxs-lookup"><span data-stu-id="d6026-191">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="d6026-192">В **инспектор** найти **преобразования** компонента и изменение **позиции** для (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="d6026-192">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="d6026-193">*Это размещает куба 2 м перед его начальной позиции.*</span><span class="sxs-lookup"><span data-stu-id="d6026-193">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="d6026-194">В **преобразования** компонента, изменение **поворота** для (**X**: 45, **Y**: 45, **Z**: 45) и измените **масштабирования** для (**X**: 0,25, **Y**: 0,25, **Z**: 0.25).</span><span class="sxs-lookup"><span data-stu-id="d6026-194">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="d6026-195">*При этом размер куба 0,25 метров.*</span><span class="sxs-lookup"><span data-stu-id="d6026-195">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="d6026-196">Чтобы сохранить изменения сцены, выберите **файл > Сохранить сцену**.</span><span class="sxs-lookup"><span data-stu-id="d6026-196">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="d6026-197">Глава 5 - убедитесь в том, на устройстве из редактора Unity</span><span class="sxs-lookup"><span data-stu-id="d6026-197">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="d6026-198">Теперь, после создания куба, настала пора выполнить быструю проверку на устройстве.</span><span class="sxs-lookup"><span data-stu-id="d6026-198">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="d6026-199">Это можно сделать непосредственно из в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="d6026-199">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="d6026-200">Начальная настройка</span><span class="sxs-lookup"><span data-stu-id="d6026-200">Initial setup</span></span>
1. <span data-ttu-id="d6026-201">На Компьютере, разработки в Unity, откройте **файл > Параметры сборки** окна.</span><span class="sxs-lookup"><span data-stu-id="d6026-201">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="d6026-202">Изменение **платформы** для **универсальной платформы Windows** и нажмите кнопку **платформам коммутатора**</span><span class="sxs-lookup"><span data-stu-id="d6026-202">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="d6026-203">Для HoloLens использования удаленного взаимодействия для Unity</span><span class="sxs-lookup"><span data-stu-id="d6026-203">For HoloLens use Unity Remoting</span></span>
1. <span data-ttu-id="d6026-204">На ваш HoloLens, установить и запустить [Holographic проигрывателя удаленного взаимодействия](holographic-remoting-player.md), доступном Windows Store.</span><span class="sxs-lookup"><span data-stu-id="d6026-204">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="d6026-205">Запустите приложение на устройстве, и он будет переходить в состояние ожидания и отобразить IP-адрес устройства.</span><span class="sxs-lookup"><span data-stu-id="d6026-205">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="d6026-206">Запишите IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d6026-206">Note down the IP.</span></span>
2. <span data-ttu-id="d6026-207">Откройте **окна > XR > Holographic эмуляции**.</span><span class="sxs-lookup"><span data-stu-id="d6026-207">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="d6026-208">Изменение **режима эмуляции** из **None** для **удаленного устройство**.</span><span class="sxs-lookup"><span data-stu-id="d6026-208">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="d6026-209">В **удаленный компьютер**, введите IP-адрес вашего HoloLens, записанные ранее.</span><span class="sxs-lookup"><span data-stu-id="d6026-209">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="d6026-210">Нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="d6026-210">Click **Connect**.</span></span>
6. <span data-ttu-id="d6026-211">Убедитесь, **состояние подключения** становится зеленым **подключено**.</span><span class="sxs-lookup"><span data-stu-id="d6026-211">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="d6026-212">Теперь необходимо щелкнуть **воспроизведение** в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="d6026-212">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="d6026-213">Теперь можно видеть куба на устройстве и в редакторе.</span><span class="sxs-lookup"><span data-stu-id="d6026-213">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="d6026-214">Можно приостановить, проверять объекты и отладки так же, как вы запускаете приложение в редакторе, потому что по сути это том, что происходит, но с видео, аудио и устройствами ввода, и обратно при передаче по сети между хост-компьютере и устройством.</span><span class="sxs-lookup"><span data-stu-id="d6026-214">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="d6026-215">Для других смешанной реальности поддерживается гарнитуры</span><span class="sxs-lookup"><span data-stu-id="d6026-215">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="d6026-216">Подключитесь к Компьютеру с помощью USB-кабеля и HDMI разработки гарнитуры или отображения кабель порт.</span><span class="sxs-lookup"><span data-stu-id="d6026-216">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="d6026-217">Запустите **смешанной реальности портала** и убедитесь, что вы выполнили первого запуска.</span><span class="sxs-lookup"><span data-stu-id="d6026-217">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="d6026-218">Из Unity теперь можно нажать кнопку воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="d6026-218">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="d6026-219">Теперь можно увидеть отрисовку куба, в вашей гарнитуры смешанной реальности и в редакторе.</span><span class="sxs-lookup"><span data-stu-id="d6026-219">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="d6026-220">Глава 6 - создание и развертывание на устройстве из Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d6026-220">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="d6026-221">Теперь мы готовы для компиляции наш проект в Visual Studio и развертывания наших целевое устройство.</span><span class="sxs-lookup"><span data-stu-id="d6026-221">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="d6026-222">Экспорт в решение Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d6026-222">Export to the Visual Studio solution</span></span>
1.  <span data-ttu-id="d6026-223">Откройте **файл > Параметры сборки** окна.</span><span class="sxs-lookup"><span data-stu-id="d6026-223">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="d6026-224">Нажмите кнопку **добавьте откройте сцены** Добавление сцены.</span><span class="sxs-lookup"><span data-stu-id="d6026-224">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="d6026-225">Изменение **платформы** для **универсальной платформы Windows** и нажмите кнопку **переключить платформу**.</span><span class="sxs-lookup"><span data-stu-id="d6026-225">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="d6026-226">В **Windows Store** параметры обеспечения **SDK** — **универсальной 10**.</span><span class="sxs-lookup"><span data-stu-id="d6026-226">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="d6026-227">Для целевого устройства, оставьте **любого устройства** перекрыто отображает или переключиться в режим **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="d6026-227">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="d6026-228">**Тип сборки UWP** должно быть **D3D**.</span><span class="sxs-lookup"><span data-stu-id="d6026-228">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="d6026-229">**Пакет SDK для UWP** может остаться в **самую новую установленную**.</span><span class="sxs-lookup"><span data-stu-id="d6026-229">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="d6026-230">Проверьте **Unity C# проекты** в режиме отладки.</span><span class="sxs-lookup"><span data-stu-id="d6026-230">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="d6026-231">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="d6026-231">Click **Build**.</span></span>
10. <span data-ttu-id="d6026-232">В проводнике щелкните **новую папку** и назовите папку **«Приложение»**.</span><span class="sxs-lookup"><span data-stu-id="d6026-232">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="d6026-233">С помощью **приложения** щелкните папку, **Выбор папки** кнопки.</span><span class="sxs-lookup"><span data-stu-id="d6026-233">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="d6026-234">После завершения Unity построения, появится окно проводника Windows.</span><span class="sxs-lookup"><span data-stu-id="d6026-234">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="d6026-235">Откройте **приложения** папку в проводнике.</span><span class="sxs-lookup"><span data-stu-id="d6026-235">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="d6026-236">Откройте созданный решение Visual Studio (MixedRealityIntroduction.sln в этом примере)</span><span class="sxs-lookup"><span data-stu-id="d6026-236">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="d6026-237">Скомпилируйте решение Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d6026-237">Compile the Visual Studio solution</span></span>

<span data-ttu-id="d6026-238">Наконец мы компиляции экспортированного решения Visual Studio, развернуть его и опробовать его на устройстве.</span><span class="sxs-lookup"><span data-stu-id="d6026-238">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>
1. <span data-ttu-id="d6026-239">С помощью верхней панели инструментов в Visual Studio, изменить целевую платформу в списке **Отладка** для **выпуска** и из **ARM** для **X86**.</span><span class="sxs-lookup"><span data-stu-id="d6026-239">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="d6026-240">Инструкции зависят от развертывание на устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="d6026-240">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="d6026-241">Следуйте инструкциям, которые соответствуют вашей установки.</span><span class="sxs-lookup"><span data-stu-id="d6026-241">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="d6026-242">Развертывание по Wi-Fi на устройстве смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="d6026-242">Deploy to mixed reality device over Wi-Fi</span></span>
1. <span data-ttu-id="d6026-243">Щелкните стрелку рядом с полем **локального компьютера** кнопку и цели развертывания, чтобы изменить **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="d6026-243">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="d6026-244">Введите IP-адрес устройства смешанной реальности и измените **режим проверки подлинности** универсальный (незашифрованный протокол) для HoloLens и **Windows** для других устройств.</span><span class="sxs-lookup"><span data-stu-id="d6026-244">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="d6026-245">Нажмите кнопку **Отладка > Запуск без отладки**.</span><span class="sxs-lookup"><span data-stu-id="d6026-245">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="d6026-246">**Для HoloLens**, если это при первом развертывании на устройстве, вам потребуется пара [с помощью Visual Studio](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d6026-246">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="d6026-247">Развертывание по USB на устройстве смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="d6026-247">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="d6026-248">Убедитесь, что ваше устройство подключено через USB-кабеля.</span><span class="sxs-lookup"><span data-stu-id="d6026-248">Ensure you device is plugged in via the USB cable.</span></span>
1. <span data-ttu-id="d6026-249">**Для HoloLens**, щелкните стрелку рядом с полем **локального компьютера** кнопку и цели развертывания, чтобы изменить **устройства**.</span><span class="sxs-lookup"><span data-stu-id="d6026-249">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="d6026-250">**Для нацеливания перекрыто устройств, подключенных к ПК**, оставить значение на локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="d6026-250">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="d6026-251">Убедитесь в наличии **смешанной реальности портала** под управлением.</span><span class="sxs-lookup"><span data-stu-id="d6026-251">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="d6026-252">Нажмите кнопку **Отладка > Запуск без отладки**.</span><span class="sxs-lookup"><span data-stu-id="d6026-252">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="d6026-253">Развертывание в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="d6026-253">Deploy to Emulator</span></span>
1. <span data-ttu-id="d6026-254">Щелкните стрелку рядом с полем **устройства** кнопку и в раскрывающемся списке выберите **HoloLens эмулятор**.</span><span class="sxs-lookup"><span data-stu-id="d6026-254">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="d6026-255">Нажмите кнопку **Отладка > Запуск без отладки**.</span><span class="sxs-lookup"><span data-stu-id="d6026-255">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="d6026-256">Проверьте работу приложения</span><span class="sxs-lookup"><span data-stu-id="d6026-256">Try out your app</span></span>

<span data-ttu-id="d6026-257">Теперь, когда ваше приложение развертывается, попробуйте переместить по всему куба и обратите внимание, что он остается в мире перед глазами.</span><span class="sxs-lookup"><span data-stu-id="d6026-257">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6026-258">См. также</span><span class="sxs-lookup"><span data-stu-id="d6026-258">See also</span></span>
* [<span data-ttu-id="d6026-259">Обзор разработки в Unity</span><span class="sxs-lookup"><span data-stu-id="d6026-259">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="d6026-260">Рекомендации по работе с Unity и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d6026-260">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="d6026-261">Основы MR 101</span><span class="sxs-lookup"><span data-stu-id="d6026-261">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="d6026-262">Основы MR 101E</span><span class="sxs-lookup"><span data-stu-id="d6026-262">MR Basics 101E</span></span>](holograms-101e.md)
