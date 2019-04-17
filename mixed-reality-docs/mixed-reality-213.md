---
title: Входные данные MR 213
description: Этот учебник кодирования с помощью Unity, Visual Studio и иммерсивную Дополнительные сведения о контроллерах движения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit-unity, создающий эффект присутствия, движения контроллера, academy, учебник
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604703"
---
>[!NOTE]
><span data-ttu-id="bce47-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="bce47-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="bce47-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="bce47-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="bce47-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bce47-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="bce47-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="bce47-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="bce47-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bce47-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="bce47-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="bce47-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="bce47-110">Входные данные MR 213: Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="bce47-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="bce47-111">Контроллеры движения в мире смешанной реальности добавьте еще один уровень интерактивности.</span><span class="sxs-lookup"><span data-stu-id="bce47-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="bce47-112">С помощью [движения контроллеры](motion-controllers.md), мы может напрямую взаимодействовать с объектами более естественным образом, аналогичную наших физических взаимодействий в реальной жизни, увеличение общения и удовлетворения запросов в интерфейсе приложения.</span><span class="sxs-lookup"><span data-stu-id="bce47-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="bce47-113">В MR входной 213 мы рассмотрим входных событий контроллера движения, создавая возможность простого пространственных рисования.</span><span class="sxs-lookup"><span data-stu-id="bce47-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="bce47-114">С этим приложением пользователям можно рисовать в трехмерном пространстве с различными типами кистей и цвета.</span><span class="sxs-lookup"><span data-stu-id="bce47-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="bce47-115">Разделы, которые описаны в этом руководстве</span><span class="sxs-lookup"><span data-stu-id="bce47-115">Topics covered in this tutorial</span></span>

|![Элемент1 MixedReality213](images/mr213-topic1.png)|![Элемент2 MixedReality213](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="bce47-119">**Контроллер визуализации**</span><span class="sxs-lookup"><span data-stu-id="bce47-119">**Controller visualization**</span></span>|<span data-ttu-id="bce47-120">**События ввода контроллера**</span><span class="sxs-lookup"><span data-stu-id="bce47-120">**Controller input events**</span></span>|<span data-ttu-id="bce47-121">**Настраиваемый контроллер и пользовательского интерфейса**</span><span class="sxs-lookup"><span data-stu-id="bce47-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="bce47-122">Узнайте, как для подготовки к просмотру модели контроллера движения в режима игры Unity и среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="bce47-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="bce47-123">Понять различные виды событий кнопки и их приложения.</span><span class="sxs-lookup"><span data-stu-id="bce47-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="bce47-124">Узнайте, как наложение элементов пользовательского интерфейса на основе контроллера или полностью настроить его.</span><span class="sxs-lookup"><span data-stu-id="bce47-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="bce47-125">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="bce47-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="bce47-126">Курс</span><span class="sxs-lookup"><span data-stu-id="bce47-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="bce47-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="bce47-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="bce47-128"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="bce47-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="bce47-129">Входные данные MR 213: Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="bce47-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="bce47-130">✔️</span><span class="sxs-lookup"><span data-stu-id="bce47-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="bce47-131">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="bce47-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="bce47-132">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="bce47-132">Prerequisites</span></span>

<span data-ttu-id="bce47-133">Контрольный список установки для иммерсивную см. в разделе на [эту страницу](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="bce47-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="bce47-134">В этом руководстве требуется [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="bce47-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="bce47-135">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="bce47-135">Project files</span></span>

* <span data-ttu-id="bce47-136">[Загрузите файлы](https://github.com/Microsoft/MixedReality213/archive/master.zip) требуемые для проекта и извлеките файлы на рабочий стол.</span><span class="sxs-lookup"><span data-stu-id="bce47-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="bce47-137">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="bce47-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="bce47-138">Программа установки Unity</span><span class="sxs-lookup"><span data-stu-id="bce47-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="bce47-139">Цели</span><span class="sxs-lookup"><span data-stu-id="bce47-139">Objectives</span></span>

* <span data-ttu-id="bce47-140">Оптимизация разработки Unity для Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bce47-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="bce47-141">Программа установки смешанной реальности камера</span><span class="sxs-lookup"><span data-stu-id="bce47-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="bce47-142">Настройка среды</span><span class="sxs-lookup"><span data-stu-id="bce47-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="bce47-143">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-143">Instructions</span></span>

* <span data-ttu-id="bce47-144">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="bce47-144">Start Unity.</span></span>
* <span data-ttu-id="bce47-145">Выберите **откройте**.</span><span class="sxs-lookup"><span data-stu-id="bce47-145">Select **Open**.</span></span>
* <span data-ttu-id="bce47-146">Перейдите к рабочего стола и найти **MixedReality213-master** папки, которые вы ранее архиве.</span><span class="sxs-lookup"><span data-stu-id="bce47-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="bce47-147">Щелкните элемент **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="bce47-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="bce47-148">По завершении загрузки файлов проекта Unity можно см. в разделе редактора Unity.</span><span class="sxs-lookup"><span data-stu-id="bce47-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="bce47-149">В Unity, выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="bce47-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="bce47-151">Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу** кнопки.</span><span class="sxs-lookup"><span data-stu-id="bce47-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="bce47-152">Задайте целевое устройство **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="bce47-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="bce47-153">Задайте тип сборки **D3D**</span><span class="sxs-lookup"><span data-stu-id="bce47-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="bce47-154">Установить пакет SDK **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="bce47-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="bce47-155">Проверьте **Unity C# проектов**</span><span class="sxs-lookup"><span data-stu-id="bce47-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="bce47-156">Это позволяет изменять файлы скриптов в проект Visual Studio без повторной сборки проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="bce47-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="bce47-157">Нажмите кнопку **параметры проигрывателя**.</span><span class="sxs-lookup"><span data-stu-id="bce47-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="bce47-158">В **инспектор** прокрутите вниз до нижней панели</span><span class="sxs-lookup"><span data-stu-id="bce47-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="bce47-159">В параметрах XR проверьте **поддерживается виртуальной реальности**</span><span class="sxs-lookup"><span data-stu-id="bce47-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="bce47-160">Установите пакеты SDK для виртуальной реальности **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="bce47-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="bce47-162">Закрыть **параметры построения** окна.</span><span class="sxs-lookup"><span data-stu-id="bce47-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="bce47-163">Структура проекта</span><span class="sxs-lookup"><span data-stu-id="bce47-163">Project structure</span></span>

<span data-ttu-id="bce47-164">В этом руководстве используется  **[смешанной реальности Toolkit — Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span><span class="sxs-lookup"><span data-stu-id="bce47-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="bce47-165">Вы можете найти выпуски на [эту страницу](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="bce47-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="bce47-167">**Завершенные сцен для справки**</span><span class="sxs-lookup"><span data-stu-id="bce47-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="bce47-168">Вы найдете двумя сценами завершенного Unity под **сцены** папки.</span><span class="sxs-lookup"><span data-stu-id="bce47-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="bce47-169">**MixedReality213**: Завершенные сцены с помощью одной кисти</span><span class="sxs-lookup"><span data-stu-id="bce47-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="bce47-170">**MixedReality213Advanced**: Завершено сцены для разработки с помощью нескольких кистей</span><span class="sxs-lookup"><span data-stu-id="bce47-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="bce47-171">**Новые параметры установки сцены для учебника**</span><span class="sxs-lookup"><span data-stu-id="bce47-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="bce47-172">В Unity, нажмите кнопку **файл > создать сцену**</span><span class="sxs-lookup"><span data-stu-id="bce47-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="bce47-173">Удалить **главной камеры** и **направленный свет**</span><span class="sxs-lookup"><span data-stu-id="bce47-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="bce47-174">Из **панель проекта**, найдите и перетащите следующие prefabs в **иерархии** панели:</span><span class="sxs-lookup"><span data-stu-id="bce47-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="bce47-175">Активы/HoloToolkit/входныеданные/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="bce47-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="bce47-176">Активы/AppPrefabs/**среды**</span><span class="sxs-lookup"><span data-stu-id="bce47-176">Assets/AppPrefabs/**Environment**</span></span>

![Камеры и среды](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="bce47-178">Существует две плоскости камеры смешанной реальности Toolkit:</span><span class="sxs-lookup"><span data-stu-id="bce47-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="bce47-179">**MixedRealityCamera.prefab**: Только камеры</span><span class="sxs-lookup"><span data-stu-id="bce47-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="bce47-180">**MixedRealityCameraParent.prefab**: Камера + Teleportation + границ</span><span class="sxs-lookup"><span data-stu-id="bce47-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="bce47-181">В этом руководстве мы будем использовать **MixedRealityCamera** без teleportation функции.</span><span class="sxs-lookup"><span data-stu-id="bce47-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="bce47-182">По этой причине мы добавили простой **среды** готового блока, содержащего основные floor, чтобы назначить пользователя чувствовать основе точных.</span><span class="sxs-lookup"><span data-stu-id="bce47-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="bce47-183">Дополнительные сведения о teleportation с **MixedRealityCameraParent**, см. в разделе [Advanced конструктора - Teleportation и locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="bce47-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="bce47-184">**Программа установки skybox**</span><span class="sxs-lookup"><span data-stu-id="bce47-184">**Skybox setup**</span></span>
* <span data-ttu-id="bce47-185">Нажмите кнопку **окно > освещения > Параметры**</span><span class="sxs-lookup"><span data-stu-id="bce47-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="bce47-186">Щелкните этот кружок в правой части **поле материал Skybox**</span><span class="sxs-lookup"><span data-stu-id="bce47-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="bce47-187">Введите в «gray» и выберите **SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="bce47-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="bce47-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="bce47-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Параметр skybox](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="bce47-190">Проверьте **Skybox** параметр, чтобы иметь возможность см. в разделе назначенный серый градиента skybox</span><span class="sxs-lookup"><span data-stu-id="bce47-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Переключателя skybox](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="bce47-192">Сцены с MixedRealityCamera, окружающей среде и серый skybox будет выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="bce47-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 среды](images/mr213-environment-600px.jpg)
* <span data-ttu-id="bce47-194">Нажмите кнопку **файл > Сохранить сцену как**</span><span class="sxs-lookup"><span data-stu-id="bce47-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="bce47-195">**Сохранить** в сцену в папке сцены с любым именем</span><span class="sxs-lookup"><span data-stu-id="bce47-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="bce47-196">Глава 1 - контроллера визуализации</span><span class="sxs-lookup"><span data-stu-id="bce47-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="bce47-197">Цели</span><span class="sxs-lookup"><span data-stu-id="bce47-197">Objectives</span></span>

* <span data-ttu-id="bce47-198">Узнайте, как для подготовки к просмотру движения контроллера моделей в режиме игр Unity, а также во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="bce47-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="bce47-199">Windows Mixed Reality предоставляет модель анимированных контроллера для контроллера визуализации.</span><span class="sxs-lookup"><span data-stu-id="bce47-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="bce47-200">Существует несколько подходов, которые можно предпринять для визуализации контроллера в приложении:</span><span class="sxs-lookup"><span data-stu-id="bce47-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="bce47-201">По умолчанию — с помощью контроллера по умолчанию без изменений</span><span class="sxs-lookup"><span data-stu-id="bce47-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="bce47-202">Гибридные - с помощью контроллера по умолчанию, но настройка некоторые элементы или наложенной компонентов пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="bce47-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="bce47-203">Замена — с использованием собственных настроенного трехмерной модели для контроллера</span><span class="sxs-lookup"><span data-stu-id="bce47-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="bce47-204">В этой главе будет рассказано о примерах настройки контроллера.</span><span class="sxs-lookup"><span data-stu-id="bce47-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="bce47-205">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-205">Instructions</span></span>

* <span data-ttu-id="bce47-206">В **проекта** панели, введите **MotionControllers** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="bce47-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="bce47-207">Его также можно найти в разделе ресурсов/HoloToolkit/входные данные/Prefabs /.</span><span class="sxs-lookup"><span data-stu-id="bce47-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="bce47-208">Перетащите **MotionControllers** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-209">Щелкните **MotionControllers** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="bce47-210">**MotionControllers prefab**</span><span class="sxs-lookup"><span data-stu-id="bce47-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="bce47-211">**MotionControllers** имеет prefab **MotionControllerVisualizer** сценарий, который предоставляет слотов для моделей альтернативный контроллер.</span><span class="sxs-lookup"><span data-stu-id="bce47-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="bce47-212">Если назначить собственные пользовательские трехмерных моделей, например руки или помехой и проверьте «Всегда использовать альтернативный влево/вправо модель», вы увидите их вместо модели по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bce47-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="bce47-213">Мы будем использовать этот слот в главе 4 для замены модель контроллера с помощью кисти.</span><span class="sxs-lookup"><span data-stu-id="bce47-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="bce47-215">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="bce47-215">**Instructions**</span></span>
* <span data-ttu-id="bce47-216">В **инспектор** панели, дважды щелкните **MotionControllerVisualizer** скрипт, чтобы просмотреть код в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bce47-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="bce47-217">**Сценарий MotionControllerVisualizer**</span><span class="sxs-lookup"><span data-stu-id="bce47-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="bce47-218">**MotionControllerVisualizer** и **MotionControllerInfo** классы предоставляют средства для доступа к & изменения моделей контроллера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bce47-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="bce47-219">**MotionControllerVisualizer** подписывается на Unity **InteractionSourceDetected** событий и автоматически создает экземпляр контроллера моделей, при их обнаружении.</span><span class="sxs-lookup"><span data-stu-id="bce47-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="bce47-220">Модели контроллера доставляются в соответствии с [спецификации glTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="bce47-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="bce47-221">Этот формат будет создана для предоставления общий формат, в то же время улучшает процесс передачи и распаковке трехмерных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="bce47-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="bce47-222">В этом случае нам нужно получить и загружать модели контроллера во время выполнения, как мы хотим сделать максимально эффективным интерфейс пользователя, а не гарантируется контроллеров движения пользователя может используемой версии.</span><span class="sxs-lookup"><span data-stu-id="bce47-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="bce47-223">Этот курс, через набор средств смешанной реальности, использует версию группе Khronos [UnityGLTF проекта](https://github.com/KhronosGroup/UnityGLTF).</span><span class="sxs-lookup"><span data-stu-id="bce47-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="bce47-224">После доставки контроллер, можно использовать скрипты **MotionControllerInfo** найти преобразований для элементов определенного контроллера, чтобы они правильно определения своих положений.</span><span class="sxs-lookup"><span data-stu-id="bce47-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="bce47-225">В следующей главе мы узнаете, как использовать эти сценарии для присоединения к контроллерам элементы пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="bce47-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="bce47-226">*В некоторых сценариях, вы найдете блоки кода с **#if! UNITY_EDITOR** или **UNITY_WSA**. Эти блоки кода выполняются только на UWP среды выполнения, при развертывании Windows. Это обусловлено набор API-интерфейсов, используемых в редакторе Unity и среда выполнения приложений универсальной платформы Windows, отличаются.*</span><span class="sxs-lookup"><span data-stu-id="bce47-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="bce47-227">**Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="bce47-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="bce47-228">Можно видеть сцены с контроллерами движения в вашей гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="bce47-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="bce47-229">Вы увидите подробные анимации для нажатия кнопки, джойстик перемещения и выделение touch сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![По умолчанию MR213_Controller визуализации](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="bce47-231">Глава 2 - присоединение элементы пользовательского интерфейса к контроллеру</span><span class="sxs-lookup"><span data-stu-id="bce47-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="bce47-232">Цели</span><span class="sxs-lookup"><span data-stu-id="bce47-232">Objectives</span></span>

* <span data-ttu-id="bce47-233">Дополнительные сведения об элементах перемещения контроллеров</span><span class="sxs-lookup"><span data-stu-id="bce47-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="bce47-234">Узнайте, как для присоединения объектов к определенной части контроллеров</span><span class="sxs-lookup"><span data-stu-id="bce47-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="bce47-235">В этой главе вы узнаете, как добавить элементы пользовательского интерфейса в контроллер, который пользователь может легко получать доступ и изменить в любое время.</span><span class="sxs-lookup"><span data-stu-id="bce47-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="bce47-236">Также вы узнаете, как добавить простой палитра пользовательского интерфейса с использованием сенсорной панели ввода.</span><span class="sxs-lookup"><span data-stu-id="bce47-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="bce47-237">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-237">Instructions</span></span>

* <span data-ttu-id="bce47-238">В **проекта** панели, поиска **MotionControllerInfo** скрипта.</span><span class="sxs-lookup"><span data-stu-id="bce47-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="bce47-239">В результатах поиска щелкните дважды щелкните **MotionControllerInfo** скрипт, чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bce47-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="bce47-240">**Сценарий MotionControllerInfo**</span><span class="sxs-lookup"><span data-stu-id="bce47-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="bce47-241">Первым делом необходимо решить, какой элемент контроллера вы пользовательского интерфейса для присоединения к.</span><span class="sxs-lookup"><span data-stu-id="bce47-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="bce47-242">Эти элементы определены в **ControllerElementEnum** в **MotionControllerInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="bce47-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="bce47-244">**Домашняя**</span><span class="sxs-lookup"><span data-stu-id="bce47-244">**Home**</span></span>
* <span data-ttu-id="bce47-245">**Меню**</span><span class="sxs-lookup"><span data-stu-id="bce47-245">**Menu**</span></span>
* <span data-ttu-id="bce47-246">**Возьмитесь**</span><span class="sxs-lookup"><span data-stu-id="bce47-246">**Grasp**</span></span>
* <span data-ttu-id="bce47-247">**Джойстик**</span><span class="sxs-lookup"><span data-stu-id="bce47-247">**Thumbstick**</span></span>
* <span data-ttu-id="bce47-248">**Выберите**</span><span class="sxs-lookup"><span data-stu-id="bce47-248">**Select**</span></span>
* <span data-ttu-id="bce47-249">**Сенсорная панель**</span><span class="sxs-lookup"><span data-stu-id="bce47-249">**Touchpad**</span></span>
* <span data-ttu-id="bce47-250">**Указывающего поза** — этот элемент представляет собой кончик контроллера, указывающего направление вперед.</span><span class="sxs-lookup"><span data-stu-id="bce47-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="bce47-251">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="bce47-251">**Instructions**</span></span>
* <span data-ttu-id="bce47-252">В **проекта** панели, поиска **AttachToController** скрипта.</span><span class="sxs-lookup"><span data-stu-id="bce47-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="bce47-253">В результатах поиска щелкните дважды щелкните **AttachToController** скрипт, чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bce47-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="bce47-254">**Сценарий AttachToController**</span><span class="sxs-lookup"><span data-stu-id="bce47-254">**AttachToController script**</span></span>

<span data-ttu-id="bce47-255">**AttachToController** скрипт предоставляет простой способ для присоединения объектов к указанному контроллеру рабочей руки пользователя и элемента.</span><span class="sxs-lookup"><span data-stu-id="bce47-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="bce47-256">В **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="bce47-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="bce47-257">Проверьте рабочей руки пользователя с помощью **MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="bce47-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="bce47-258">Получить конкретный элемент массива контроллере, используя **MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="bce47-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="bce47-259">После получения этого элемента преобразования из родительского объекта, находящегося под его модель контроллера и имеет нулевое значение локального положения и поворота объекта.</span><span class="sxs-lookup"><span data-stu-id="bce47-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="bce47-260">Самый простой способ использования **AttachToController** сценарий должен наследовать его, как мы делали в случае использования **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="bce47-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="bce47-261">Просто заменить **OnAttachToController** и **OnDetatchFromController** функции для выполнения установки / декомпозиции, когда контроллер были обнаружены и отключены.</span><span class="sxs-lookup"><span data-stu-id="bce47-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="bce47-262">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="bce47-262">**Instructions**</span></span>
* <span data-ttu-id="bce47-263">В **проекта** панели, введите в поле поиска **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="bce47-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="bce47-264">Его также можно найти в разделе ресурсов/AppPrefabs /.</span><span class="sxs-lookup"><span data-stu-id="bce47-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="bce47-265">Перетащите **ColorPickerWheel** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-266">Нажмите кнопку **ColorPickerWheel** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-267">В **инспектор** панели, дважды щелкните **ColorPickerWheel** скрипт, чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bce47-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="bce47-269">**Сценарий ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="bce47-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="bce47-270">Так как **ColorPickerWheel** наследует **AttachToController**, он показывает **рабочей руки пользователя** и **элемент** в  **Инспектор** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="bce47-271">Мы будет прикреплен пользовательский Интерфейс к элементу на сенсорной панели на левой контроллере.</span><span class="sxs-lookup"><span data-stu-id="bce47-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Сценарий ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="bce47-273">**ColorPickerWheel** переопределяет **OnAttachToController** и **OnDetatchFromController** подписаться на событие ввода, который будет использоваться в следующей главе для выбранного цвета с сенсорной панели ввода.</span><span class="sxs-lookup"><span data-stu-id="bce47-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* <span data-ttu-id="bce47-274">**Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="bce47-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="bce47-275">**Альтернативный метод для присоединения объектов к контроллерам**</span><span class="sxs-lookup"><span data-stu-id="bce47-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="bce47-276">Мы рекомендуем, чтобы сценарии наследовать от **AttachToController** и переопределить **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="bce47-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="bce47-277">Тем не менее это может не всегда возможно.</span><span class="sxs-lookup"><span data-stu-id="bce47-277">However, this may not always be possible.</span></span> <span data-ttu-id="bce47-278">Альтернативы является использование его в качестве отдельного компонента.</span><span class="sxs-lookup"><span data-stu-id="bce47-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="bce47-279">Это может быть полезно, если вы хотите подключить существующий готового блока к контроллеру без оптимизации кода скриптов.</span><span class="sxs-lookup"><span data-stu-id="bce47-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="bce47-280">Просто иметь класс ожидания IsAttached будет присвоено значение true, если перед выполнением каких-либо настроек.</span><span class="sxs-lookup"><span data-stu-id="bce47-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="bce47-281">Самый простой способ сделать это — с помощью соподпрограмме для «Start».</span><span class="sxs-lookup"><span data-stu-id="bce47-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="bce47-282">Глава 3 - Работа с входными данными для сенсорной панели</span><span class="sxs-lookup"><span data-stu-id="bce47-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="bce47-283">Цели</span><span class="sxs-lookup"><span data-stu-id="bce47-283">Objectives</span></span>

* <span data-ttu-id="bce47-284">Узнайте, как получить события входных данных на сенсорной панели</span><span class="sxs-lookup"><span data-stu-id="bce47-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="bce47-285">Узнайте, как использовать сведения о положении оси сенсорной панели для работы приложения</span><span class="sxs-lookup"><span data-stu-id="bce47-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="bce47-286">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-286">Instructions</span></span>

* <span data-ttu-id="bce47-287">В **иерархии** панели, щелкните **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="bce47-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="bce47-288">В **инспектор** панели **Animatior**, дважды щелкните **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="bce47-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="bce47-289">Можно видеть **Animator** откроется вкладка</span><span class="sxs-lookup"><span data-stu-id="bce47-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="bce47-290">**Отображение/скрытие пользовательского интерфейса с помощью Unity контроллер анимации**</span><span class="sxs-lookup"><span data-stu-id="bce47-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="bce47-291">Для отображения и скрытия **ColorPickerWheel** пользовательского интерфейса с помощью анимации мы используем [системы анимации Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="bce47-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="bce47-292">Установка **ColorPickerWheel** **Visible** значение true или false триггеры **Показать** и **скрыть** триггеров анимации.</span><span class="sxs-lookup"><span data-stu-id="bce47-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="bce47-293">**Показать** и **скрыть** параметры определяются в **ColorPickerWheelController** контроллер анимации.</span><span class="sxs-lookup"><span data-stu-id="bce47-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Контроллер анимации Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="bce47-295">**Инструкции**</span><span class="sxs-lookup"><span data-stu-id="bce47-295">**Instructions**</span></span>
* <span data-ttu-id="bce47-296">В **иерархии** панели, выберите **ColorPickerWheel** prefab</span><span class="sxs-lookup"><span data-stu-id="bce47-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="bce47-297">В **инспектор** панели, дважды щелкните **ColorPickerWheel** скрипт, чтобы просмотреть код в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bce47-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="bce47-298">**Сценарий ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="bce47-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="bce47-299">**ColorPickerWheel** подписывается на Unity **InteractionSourceUpdated** событий для прослушивания событий сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="bce47-300">В **InteractionSourceUpdated()**, сценарий сначала проверяет, убедитесь, что он:</span><span class="sxs-lookup"><span data-stu-id="bce47-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="bce47-301">фактически событие сенсорная панель (obj.state. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="bce47-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="bce47-302">исходит от левой контроллера (obj.state.source. **рабочей руки пользователя**)</span><span class="sxs-lookup"><span data-stu-id="bce47-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="bce47-303">Если выполняются оба условия, поместите сенсорной панели (obj.state. **touchpadPosition**) назначается **selectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="bce47-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="bce47-304">В **Update()**, основываясь на **видимым** свойство, оно активирует отображает или скрывает триггеров анимации в компоненте animator палитра цветов</span><span class="sxs-lookup"><span data-stu-id="bce47-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="bce47-305">В **Update()**, **selectorPosition** используется для приведения в сетке collider цветовой круг, который возвращает позицию UV луча.</span><span class="sxs-lookup"><span data-stu-id="bce47-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="bce47-306">Это положение можно найти пикселя с координатой и значение цветовой круг текстуры цвета.</span><span class="sxs-lookup"><span data-stu-id="bce47-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="bce47-307">Это значение доступно для других сценариев с помощью **SelectedColor** свойство.</span><span class="sxs-lookup"><span data-stu-id="bce47-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Точные точки для отслеживания колесика средство выбора цвета](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="bce47-309">Глава 4 – переопределение модель контроллера</span><span class="sxs-lookup"><span data-stu-id="bce47-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="bce47-310">Цели</span><span class="sxs-lookup"><span data-stu-id="bce47-310">Objectives</span></span>

* <span data-ttu-id="bce47-311">Дополнительные сведения о переопределении модель контроллера с помощью пользовательских трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="bce47-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="bce47-313">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-313">Instructions</span></span>

* <span data-ttu-id="bce47-314">Нажмите кнопку **MotionControllers** в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-315">Щелкните этот кружок в правой части **альтернативный контроллер правой** поля.</span><span class="sxs-lookup"><span data-stu-id="bce47-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="bce47-316">Введите в **"BrushController**" и выберите взята из результата.</span><span class="sxs-lookup"><span data-stu-id="bce47-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="bce47-317">Его можно найти в разделе ресурсов/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="bce47-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="bce47-318">Проверьте **всегда использовать альтернативный оптимальной модели**</span><span class="sxs-lookup"><span data-stu-id="bce47-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="bce47-320">**BrushController** готового блока не обязательно должен быть включены в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="bce47-321">Тем не менее чтобы извлечь его дочерними компонентами:</span><span class="sxs-lookup"><span data-stu-id="bce47-321">However, to check out its child components:</span></span>
* <span data-ttu-id="bce47-322">В **проекта** панели, введите в **BrushController** и перетащите **BrushController** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="bce47-324">Вы найдете **совет** компонент в **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="bce47-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="bce47-325">Мы будем использовать его преобразование, запуска и остановки рисования линии.</span><span class="sxs-lookup"><span data-stu-id="bce47-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="bce47-326">Удалить **BrushController** из **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-327">**Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="bce47-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="bce47-328">Можно увидеть, что модель кисть замены контроллера правой движения.</span><span class="sxs-lookup"><span data-stu-id="bce47-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="bce47-329">Глава 5 - Рисование с помощью Select входных данных</span><span class="sxs-lookup"><span data-stu-id="bce47-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="bce47-330">Цели</span><span class="sxs-lookup"><span data-stu-id="bce47-330">Objectives</span></span>

* <span data-ttu-id="bce47-331">Сведения об использовании событий кнопки "выбрать" для запуска и остановки рисования линии</span><span class="sxs-lookup"><span data-stu-id="bce47-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="bce47-332">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-332">Instructions</span></span>

* <span data-ttu-id="bce47-333">Поиск **BrushController** prefab в **проекта** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="bce47-334">В **инспектор** панели, дважды щелкните **BrushController** скрипт, чтобы просмотреть код в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bce47-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="bce47-335">**Сценарий BrushController**</span><span class="sxs-lookup"><span data-stu-id="bce47-335">**BrushController script**</span></span>

<span data-ttu-id="bce47-336">**BrushController** подписывается на InteractionManager **InteractionSourcePressed** и **InteractionSourceReleased** события.</span><span class="sxs-lookup"><span data-stu-id="bce47-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="bce47-337">Когда **InteractionSourcePressed** событие активируется, кисти **рисования** свойство имеет значение true; в то время, когда **InteractionSourceReleased** событие активируется, кисти **Рисования** свойство имеет значение false.</span><span class="sxs-lookup"><span data-stu-id="bce47-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="bce47-338">Хотя **рисования** имеет значение true, кисть, которая будет создавать точки в созданный экземпляр Unity **LineRenderer**.</span><span class="sxs-lookup"><span data-stu-id="bce47-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="bce47-339">Ссылку на этот готового блока хранится в кисти **Stroke Prefab** поля.</span><span class="sxs-lookup"><span data-stu-id="bce47-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="bce47-340">Чтобы использовать выбранный цвет из палитры цветовой круг пользовательского интерфейса, **BrushController** должен иметь ссылку на **ColorPickerWheel** объекта.</span><span class="sxs-lookup"><span data-stu-id="bce47-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="bce47-341">Так как **BrushController** prefab создается во время выполнения в качестве замены контроллера, необходимо задать во время выполнения все ссылки на объекты на сцене.</span><span class="sxs-lookup"><span data-stu-id="bce47-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="bce47-342">В этом случае мы используем **GameObject.FindObjectOfType** искомого **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="bce47-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* <span data-ttu-id="bce47-343">**Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="bce47-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="bce47-344">Можно для рисования линий и рисования с помощью кнопки "выбрать" на контроллере справа.</span><span class="sxs-lookup"><span data-stu-id="bce47-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="bce47-345">Объект, запускающая с выбранными ввода Глава 6.</span><span class="sxs-lookup"><span data-stu-id="bce47-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="bce47-346">Цели</span><span class="sxs-lookup"><span data-stu-id="bce47-346">Objectives</span></span>

* <span data-ttu-id="bce47-347">Использование Select и понять входных событий для кнопки</span><span class="sxs-lookup"><span data-stu-id="bce47-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="bce47-348">Узнайте, как создавать экземпляры объектов</span><span class="sxs-lookup"><span data-stu-id="bce47-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="bce47-349">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-349">Instructions</span></span>

* <span data-ttu-id="bce47-350">В **проекта** панели, введите **ObjectSpawner** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="bce47-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="bce47-351">Его также можно найти в разделе ресурсов/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="bce47-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="bce47-352">Перетащите **ObjectSpawner** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-353">Нажмите кнопку **ObjectSpawner** в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-354">**ObjectSpawner** есть поле с именем **цвет источника**.</span><span class="sxs-lookup"><span data-stu-id="bce47-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="bce47-355">Из **иерархии** панели, перетащите **ColorPickerWheel** ссылку в это поле.</span><span class="sxs-lookup"><span data-stu-id="bce47-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![Инспектор Spawner объектов](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="bce47-357">Нажмите кнопку **ObjectSpawner** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-358">В **инспектор** панели, дважды щелкните **ObjectSpawner** скрипт, чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bce47-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="bce47-359">**Сценарий ObjectSpawner**</span><span class="sxs-lookup"><span data-stu-id="bce47-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="bce47-360">**ObjectSpawner** создает копии примитив сетки (куб, sphere, цилиндра) в пространстве.</span><span class="sxs-lookup"><span data-stu-id="bce47-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="bce47-361">Когда **InteractionSourcePressed** обнаруживается, он проверяет рабочей руки пользователя и если это **InteractionSourcePressType.Grasp** или **InteractionSourcePressType.Select** событие.</span><span class="sxs-lookup"><span data-stu-id="bce47-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="bce47-362">Для **осознавать** событие, он увеличивает индекс текущего типа сетки (сферу, куб, цилиндр)</span><span class="sxs-lookup"><span data-stu-id="bce47-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="bce47-363">Для **выберите** событий в **SpawnObject()**, новый объект, созданный экземпляр, без родительского элемента и освобожденных в мир.</span><span class="sxs-lookup"><span data-stu-id="bce47-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="bce47-364">**ObjectSpawner** использует **ColorPickerWheel** для задания цвета материала экранного объекта.</span><span class="sxs-lookup"><span data-stu-id="bce47-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="bce47-365">Порожденный объектам предоставляется экземпляр этого материала, поэтому они сохранит их цвет.</span><span class="sxs-lookup"><span data-stu-id="bce47-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="bce47-366">**Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="bce47-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="bce47-367">Можно изменять объекты с помощью кнопки коммерческих тайн и породить объектов с помощью кнопки "выбрать".</span><span class="sxs-lookup"><span data-stu-id="bce47-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="bce47-368">Построение и развертывание приложения в смешанной реальности портала</span><span class="sxs-lookup"><span data-stu-id="bce47-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="bce47-369">В Unity, выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="bce47-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="bce47-370">Нажмите кнопку **добавьте откройте сцены** Добавление текущей сцены **построения кадром**.</span><span class="sxs-lookup"><span data-stu-id="bce47-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="bce47-371">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="bce47-371">Click **Build**.</span></span>
* <span data-ttu-id="bce47-372">Создание **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="bce47-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="bce47-373">Одним щелчком мыши **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="bce47-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="bce47-374">Щелкните элемент **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="bce47-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="bce47-375">По завершении Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="bce47-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="bce47-376">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="bce47-376">Open the **App** folder.</span></span>
* <span data-ttu-id="bce47-377">Дважды щелкните **YourSceneName.sln** файл решения Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bce47-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="bce47-378">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **X64**.</span><span class="sxs-lookup"><span data-stu-id="bce47-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="bce47-379">Щелкните стрелку раскрывающегося списка рядом с кнопкой устройство и выберите **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="bce47-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="bce47-380">Нажмите кнопку **Отладка -> Запуск без отладки** в меню или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="bce47-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="bce47-381">Теперь является построение и установке приложения на портале смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="bce47-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="bce47-382">Его можно запустить снова через меню "Пуск" на портале смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="bce47-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="bce47-383">Дизайн — средства кисть с радиальным макета</span><span class="sxs-lookup"><span data-stu-id="bce47-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="bce47-385">В этой главе вы узнаете, как заменить модель контроллера движения по умолчанию коллекция средство пользовательской кисти.</span><span class="sxs-lookup"><span data-stu-id="bce47-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="bce47-386">Для справки можно найти завершенного сцены **MixedReality213Advanced** под **сцены** папки.</span><span class="sxs-lookup"><span data-stu-id="bce47-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="bce47-387">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-387">Instructions</span></span>

* <span data-ttu-id="bce47-388">В **проекта** панели, введите **BrushSelector** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="bce47-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="bce47-389">Его также можно найти в разделе ресурсов/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="bce47-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="bce47-390">Перетащите **BrushSelector** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-391">Для организации, создайте пустой объект GameObject вызывается **кисти**</span><span class="sxs-lookup"><span data-stu-id="bce47-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="bce47-392">Перетащите следующие prefabs из **проекта** в область переноса **кисти**</span><span class="sxs-lookup"><span data-stu-id="bce47-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="bce47-393">Активы/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="bce47-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="bce47-394">Активы/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="bce47-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="bce47-395">Активы/AppPrefabs/**Ластик**</span><span class="sxs-lookup"><span data-stu-id="bce47-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="bce47-396">Активы/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="bce47-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="bce47-397">Активы/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="bce47-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="bce47-398">Активы/AppPrefabs/**карандаш**</span><span class="sxs-lookup"><span data-stu-id="bce47-398">Assets/AppPrefabs/**Pencil**</span></span>

![Кисти](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="bce47-400">Нажмите кнопку **MotionControllers** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="bce47-401">В **инспектор** панели, снимите флажок **всегда использовать альтернативный справа модель** на **движения контроллера визуализатора**</span><span class="sxs-lookup"><span data-stu-id="bce47-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="bce47-402">В **иерархии** панели, щелкните **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="bce47-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="bce47-403">**BrushSelector** есть поле с именем **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="bce47-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="bce47-404">Из **иерархии** панели, перетащите **ColorPickerWheel** в **ColorPicker** в **инспектор** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![Назначить ColorPickerWheel для кисти выбора варианта](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="bce47-406">В **иерархии** панели **BrushSelector** prefab, выберите **меню** объекта.</span><span class="sxs-lookup"><span data-stu-id="bce47-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="bce47-407">В **инспектор** панели **LineObjectCollection** компонента, откройте **объектов** раскрывающийся список массива.</span><span class="sxs-lookup"><span data-stu-id="bce47-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="bce47-408">Вы увидите 6 пустых слотов.</span><span class="sxs-lookup"><span data-stu-id="bce47-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="bce47-409">Из **иерархии** панели, перетащите prefabs, имеют родителей, в разделе **кисти** GameObject в эти слоты в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="bce47-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="bce47-410">(Убедитесь, что перетаскивания prefabs из сцены, не prefabs в папке проекта.)</span><span class="sxs-lookup"><span data-stu-id="bce47-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Селектор кисти](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="bce47-412">**BrushSelector prefab**</span><span class="sxs-lookup"><span data-stu-id="bce47-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="bce47-413">Так как **BrushSelector** наследует **AttachToController**, он показывает **рабочей руки пользователя** и **элемент** параметры в  **Инспектор** панели.</span><span class="sxs-lookup"><span data-stu-id="bce47-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="bce47-414">Мы выбрали **справа** и **указывает представлять** для присоединения кисть в правом нижнем контроллер в прямом направлении.</span><span class="sxs-lookup"><span data-stu-id="bce47-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="bce47-415">**BrushSelector** использует две служебные программы:</span><span class="sxs-lookup"><span data-stu-id="bce47-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="bce47-416">**Эллипс**: используется для создания точек в пространстве по фигуре эллипса.</span><span class="sxs-lookup"><span data-stu-id="bce47-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="bce47-417">**LineObjectCollection**: распределение объектов с помощью точки, созданные в любой строке класс (например, эллипс).</span><span class="sxs-lookup"><span data-stu-id="bce47-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="bce47-418">Это, что мы будем использовать для размещения наших кисти вдоль фигуры Ellipse.</span><span class="sxs-lookup"><span data-stu-id="bce47-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="bce47-419">Вместе эти служебные программы можно использовать для создания радиального меню.</span><span class="sxs-lookup"><span data-stu-id="bce47-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="bce47-420">**Сценарий LineObjectCollection**</span><span class="sxs-lookup"><span data-stu-id="bce47-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="bce47-421">**LineObjectCollection** есть элементы управления для размера, положения и поворота объектов, распределенных по его линии.</span><span class="sxs-lookup"><span data-stu-id="bce47-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="bce47-422">Это полезно для создания радиального меню как селектор кисти.</span><span class="sxs-lookup"><span data-stu-id="bce47-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="bce47-423">Чтобы создать внешний вид кисти, масштабирования из nothing, так как они подходят положение выбранного центра обработки **ObjectScale** кривой пиковых нагрузок в центре и сходит по краям.</span><span class="sxs-lookup"><span data-stu-id="bce47-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="bce47-424">**Сценарий BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="bce47-424">**BrushSelector script**</span></span>

<span data-ttu-id="bce47-425">В случае использования **BrushSelector**, мы решили использовать процедурного анимации.</span><span class="sxs-lookup"><span data-stu-id="bce47-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="bce47-426">Во-первых, кисть моделей распространяются в эллипс с **LineObjectCollection** скрипта.</span><span class="sxs-lookup"><span data-stu-id="bce47-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="bce47-427">Затем каждый кисть несет ответственность за ведение его позиции в руки пользователя на основе его **DisplayMode** значение, которое изменяется в зависимости от выбора.</span><span class="sxs-lookup"><span data-stu-id="bce47-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="bce47-428">Мы выбрали процедурном подходе из-за высокой вероятности переходов позиции кисти, выполняется прерывание пользователь выбирает кисти.</span><span class="sxs-lookup"><span data-stu-id="bce47-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="bce47-429">Mecanim анимации могут правильно обработать перерывы в работе, но может быть сложнее, чем простой операции Lerp.</span><span class="sxs-lookup"><span data-stu-id="bce47-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="bce47-430">**BrushSelector** используется их сочетание.</span><span class="sxs-lookup"><span data-stu-id="bce47-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="bce47-431">При обнаружении сенсорной панели ввода параметров кисти становятся видимыми и увеличить масштаб вдоль радиального меню.</span><span class="sxs-lookup"><span data-stu-id="bce47-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="bce47-432">По истечении времени ожидания (который указывает, что пользователь сделал выбор) кисть параметров масштабирования вниз, оставляя только выбранной кисти.</span><span class="sxs-lookup"><span data-stu-id="bce47-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="bce47-433">**Визуализация ввода сенсорной панели**</span><span class="sxs-lookup"><span data-stu-id="bce47-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="bce47-434">Даже в случаях, когда модель контроллера был полностью заменен он может быть полезно показать ввода на исходные входные данные модели.</span><span class="sxs-lookup"><span data-stu-id="bce47-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="bce47-435">Это помогает заземление действий пользователя, на самом деле.</span><span class="sxs-lookup"><span data-stu-id="bce47-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="bce47-436">Для **BrushSelector** мы решили отобразить сенсорной панели кратко при получении входных данных.</span><span class="sxs-lookup"><span data-stu-id="bce47-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="bce47-437">Это было сделано, получив элемент сенсорной панели из контроллера, заменив его материал пользовательского материала, а затем применение градиента этот материал цветов в зависимости от последнее время сенсорной ввод получен.</span><span class="sxs-lookup"><span data-stu-id="bce47-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="bce47-438">**Выбор инструментов кисти с входными данными для сенсорной панели**</span><span class="sxs-lookup"><span data-stu-id="bce47-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="bce47-439">Обнаружив селекторе кисть сенсорной панели в нажатом состоянии входных данных, он проверяет позицию ввода, чтобы определить, была ли она влево или вправо.</span><span class="sxs-lookup"><span data-stu-id="bce47-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="bce47-440">**Толщина штриха с selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="bce47-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="bce47-441">Вместо **InteractionSourcePressType.Select** событие в **InteractionSourcePressed()**, можно получить аналогового значение нажатом величину посредством **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="bce47-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="bce47-442">Это значение можно получить в **InteractionSourceUpdated()**.</span><span class="sxs-lookup"><span data-stu-id="bce47-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="bce47-443">**Скрипт Ластик**</span><span class="sxs-lookup"><span data-stu-id="bce47-443">**Eraser script**</span></span>

<span data-ttu-id="bce47-444">**Ластик** — это специальный тип кисть, которая переопределяет базовый **кисть** **DrawOverTime()** функции.</span><span class="sxs-lookup"><span data-stu-id="bce47-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="bce47-445">Во время рисования имеет значение true, резинки проверяет, пересекается ли его tip с любой существующей мазков кисти.</span><span class="sxs-lookup"><span data-stu-id="bce47-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="bce47-446">В этом случае они добавляются в очередь для работы и удалены.</span><span class="sxs-lookup"><span data-stu-id="bce47-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="bce47-447">Дополнительные возможности макета - Teleportation и locomotion</span><span class="sxs-lookup"><span data-stu-id="bce47-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="bce47-448">Если вы хотите разрешить пользователю перемещать сцены с помощью джойстик teleportation, используйте **MixedRealityCameraParent** вместо **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="bce47-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="bce47-449">Необходимо также добавить **InputManager** и **DefaultCusor**.</span><span class="sxs-lookup"><span data-stu-id="bce47-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="bce47-450">Так как **MixedRealityCameraParent** уже включает в себя **MotionControllers** и **границ** как дочерние компоненты, необходимо удалить существующий  **MotionControllers** и **среды** prefab.</span><span class="sxs-lookup"><span data-stu-id="bce47-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="bce47-451">Инструкция</span><span class="sxs-lookup"><span data-stu-id="bce47-451">Instructions</span></span>

* <span data-ttu-id="bce47-452">В **иерархии** панели, удалите **MixedRealityCamera**, **среды** и **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="bce47-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="bce47-453">Из **панель проекта**, найдите и перетащите следующие prefabs в **иерархии** панели:</span><span class="sxs-lookup"><span data-stu-id="bce47-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="bce47-454">Активы/AppPrefabs/входныеданные/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="bce47-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="bce47-455">Активы/AppPrefabs/входныеданные/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="bce47-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="bce47-456">Активы/AppPrefabs/входныеданные/Prefabs/курсор/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="bce47-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Родительский смешанной реальности камера](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="bce47-458">В **иерархии** панели, щелкните **диспетчер ввода**</span><span class="sxs-lookup"><span data-stu-id="bce47-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="bce47-459">В **инспектор** панели, прокрутите вниз до раздела **простой единичный выбор указатель** раздел</span><span class="sxs-lookup"><span data-stu-id="bce47-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="bce47-460">Из **иерархии** панели, перетащите **DefaultCursor** в **курсор** поля</span><span class="sxs-lookup"><span data-stu-id="bce47-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![Назначение DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="bce47-462">**Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="bce47-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="bce47-463">Можно использовать джойстик для поворота влево/вправо или teleport.</span><span class="sxs-lookup"><span data-stu-id="bce47-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="bce47-464">Конец</span><span class="sxs-lookup"><span data-stu-id="bce47-464">The end</span></span>

<span data-ttu-id="bce47-465">И это, чтобы в конце этого руководства!</span><span class="sxs-lookup"><span data-stu-id="bce47-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="bce47-466">Вы узнали:</span><span class="sxs-lookup"><span data-stu-id="bce47-466">You learned:</span></span>
* <span data-ttu-id="bce47-467">Как работать с моделями движения контроллер в режим игры и среды выполнения Unity.</span><span class="sxs-lookup"><span data-stu-id="bce47-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="bce47-468">Сведения об использовании различных типов событий кнопки и их приложения.</span><span class="sxs-lookup"><span data-stu-id="bce47-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="bce47-469">Как наложение элементов пользовательского интерфейса на основе контроллера или полностью настроить.</span><span class="sxs-lookup"><span data-stu-id="bce47-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="bce47-470">Теперь вы готовы приступить к созданию собственного присутствия с контроллерами движения!</span><span class="sxs-lookup"><span data-stu-id="bce47-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="bce47-471">Завершенные сцены</span><span class="sxs-lookup"><span data-stu-id="bce47-471">Completed scenes</span></span>

* <span data-ttu-id="bce47-472">В Unity **проекта** щелкните панель **сцены** папки.</span><span class="sxs-lookup"><span data-stu-id="bce47-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="bce47-473">Вы найдете два Unity sceens **MixedReality213** и **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="bce47-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="bce47-474">**MixedReality213**: Завершенные сцены с помощью одной кисти</span><span class="sxs-lookup"><span data-stu-id="bce47-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="bce47-475">**MixedReality213Advanced**: Завершенные сцены с помощью нескольких кисти с примером сумма нажмите кнопки select</span><span class="sxs-lookup"><span data-stu-id="bce47-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="bce47-476">См. также</span><span class="sxs-lookup"><span data-stu-id="bce47-476">See also</span></span>

* [<span data-ttu-id="bce47-477">Файлы проекта 213 MR входных данных</span><span class="sxs-lookup"><span data-stu-id="bce47-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="bce47-478">Смешанной реальности Toolkit — сцены движения контроллера тестирования</span><span class="sxs-lookup"><span data-stu-id="bce47-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="bce47-479">Набор средств для смешанной реальности - механизм захвата</span><span class="sxs-lookup"><span data-stu-id="bce47-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="bce47-480">Рекомендации по разработке контроллера движения</span><span class="sxs-lookup"><span data-stu-id="bce47-480">Motion controller development guidelines</span></span>](motion-controllers.md)
