---
title: Ввод MR 213
description: Следуйте этому руководству по программированию с помощью Unity, Visual Studio и впечатляющих головных телефонов для получения сведений об контроллерах движения.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, иммерсивное, контроллер движения, Academy, руководство
ms.openlocfilehash: 273d1bf384d588ab24bfe29e30f299b7a41fe541
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926821"
---
>[!NOTE]
><span data-ttu-id="44e2a-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="44e2a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="44e2a-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="44e2a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="44e2a-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="44e2a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="44e2a-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="44e2a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="44e2a-108">Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="44e2a-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="44e2a-109">Ввод с MR 213: контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="44e2a-109">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="44e2a-110">Контроллеры движения в мире смешанной реальности добавляют еще один уровень интерактивности.</span><span class="sxs-lookup"><span data-stu-id="44e2a-110">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="44e2a-111">Используя [контроллеры движения](motion-controllers.md), мы можем напрямую взаимодействовать с объектами более естественным образом, аналогично нашим физическим взаимодействиям в реальном времени, повышая иммерсивное и удовлетворения запросов в работе приложения.</span><span class="sxs-lookup"><span data-stu-id="44e2a-111">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="44e2a-112">В MR input 213 мы рассмотрим события ввода контроллера движения, создав простой интерфейс для пространственного рисования.</span><span class="sxs-lookup"><span data-stu-id="44e2a-112">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="44e2a-113">С помощью этого приложения пользователи могут закрашивать трехмерное пространство с помощью различных типов кистей и цветов.</span><span class="sxs-lookup"><span data-stu-id="44e2a-113">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="44e2a-114">Темы, описанные в этом руководстве</span><span class="sxs-lookup"><span data-stu-id="44e2a-114">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="44e2a-118">**Визуализация контроллера**</span><span class="sxs-lookup"><span data-stu-id="44e2a-118">**Controller visualization**</span></span>|<span data-ttu-id="44e2a-119">**События ввода контроллера**</span><span class="sxs-lookup"><span data-stu-id="44e2a-119">**Controller input events**</span></span>|<span data-ttu-id="44e2a-120">**Пользовательский контроллер и пользовательский интерфейс**</span><span class="sxs-lookup"><span data-stu-id="44e2a-120">**Custom controller and UI**</span></span>|
|<span data-ttu-id="44e2a-121">Узнайте, как визуализировать модели контроллеров движения в игровом режиме и среде выполнения Unity.</span><span class="sxs-lookup"><span data-stu-id="44e2a-121">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="44e2a-122">Изучите различные типы событий кнопок и их приложений.</span><span class="sxs-lookup"><span data-stu-id="44e2a-122">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="44e2a-123">Узнайте, как наложение элементов пользовательского интерфейса поверх контроллера или его полная настройка.</span><span class="sxs-lookup"><span data-stu-id="44e2a-123">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="44e2a-124">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="44e2a-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="44e2a-125">Хождение</span><span class="sxs-lookup"><span data-stu-id="44e2a-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="44e2a-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="44e2a-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="44e2a-127"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="44e2a-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="44e2a-128">Ввод с MR 213: контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="44e2a-128">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="44e2a-129">✔️</span><span class="sxs-lookup"><span data-stu-id="44e2a-129">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="44e2a-130">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="44e2a-130">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="44e2a-131">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="44e2a-131">Prerequisites</span></span>

<span data-ttu-id="44e2a-132">См. Контрольный список установки для впечатляющих головных телефонов на [этой странице](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="44e2a-132">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="44e2a-133">Для работы с этим руководством требуется [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="44e2a-133">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="44e2a-134">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="44e2a-134">Project files</span></span>

* <span data-ttu-id="44e2a-135">[Скачайте файлы](https://github.com/Microsoft/MixedReality213/archive/master.zip) , необходимые для проекта, и извлеките файлы на Рабочий стол.</span><span class="sxs-lookup"><span data-stu-id="44e2a-135">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="44e2a-136">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="44e2a-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="44e2a-137">Установка Unity</span><span class="sxs-lookup"><span data-stu-id="44e2a-137">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="44e2a-138">Задачи</span><span class="sxs-lookup"><span data-stu-id="44e2a-138">Objectives</span></span>

* <span data-ttu-id="44e2a-139">Оптимизация Unity для разработки Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="44e2a-139">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="44e2a-140">Настройка камеры смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="44e2a-140">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="44e2a-141">Среда установки</span><span class="sxs-lookup"><span data-stu-id="44e2a-141">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="44e2a-142">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-142">Instructions</span></span>

* <span data-ttu-id="44e2a-143">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="44e2a-143">Start Unity.</span></span>
* <span data-ttu-id="44e2a-144">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-144">Select **Open**.</span></span>
* <span data-ttu-id="44e2a-145">Перейдите к рабочему столу и найдите папку **MixedReality213-Master** , которая ранее была неархивирована.</span><span class="sxs-lookup"><span data-stu-id="44e2a-145">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="44e2a-146">Щелкните элемент **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-146">Click **Select Folder**.</span></span>
* <span data-ttu-id="44e2a-147">После того как Unity закончит загрузку файлов проекта, вы сможете увидеть редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="44e2a-147">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="44e2a-148">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-148">In Unity, select **File > Build Settings**.</span></span>

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* <span data-ttu-id="44e2a-150">Выберите **универсальная платформа Windows** в списке **платформа** и нажмите кнопку **переключателя платформы** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-150">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="44e2a-151">Задать целевое устройство для **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="44e2a-151">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="44e2a-152">Задать для типа сборки **D3D**</span><span class="sxs-lookup"><span data-stu-id="44e2a-152">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="44e2a-153">Установить **последний установленный** пакет SDK</span><span class="sxs-lookup"><span data-stu-id="44e2a-153">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="44e2a-154">Проверка **проектов C# Unity**</span><span class="sxs-lookup"><span data-stu-id="44e2a-154">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="44e2a-155">Это позволяет изменять файлы скриптов в проекте Visual Studio без перестроения проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="44e2a-155">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="44e2a-156">Щелкните **Параметры проигрывателя**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-156">Click **Player Settings**.</span></span>
* <span data-ttu-id="44e2a-157">Прокрутите панель **инспектора** вниз до конца</span><span class="sxs-lookup"><span data-stu-id="44e2a-157">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="44e2a-158">В параметрах XR проверьте, **поддерживается ли виртуальная реальность**</span><span class="sxs-lookup"><span data-stu-id="44e2a-158">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="44e2a-159">В разделе пакеты SDK для Virtual Reality выберите **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-159">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* <span data-ttu-id="44e2a-161">Закройте окно **параметров сборки** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-161">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="44e2a-162">Структура проекта</span><span class="sxs-lookup"><span data-stu-id="44e2a-162">Project structure</span></span>

<span data-ttu-id="44e2a-163">В этом руководстве используется **[набор средств для смешанной реальности — Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-163">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="44e2a-164">Выпуски можно найти на [этой странице](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="44e2a-164">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![прожектструктуре](images/mr213-projectstructure-650px.png)

<span data-ttu-id="44e2a-166">**Завершенные монтажные кадры для справки**</span><span class="sxs-lookup"><span data-stu-id="44e2a-166">**Completed scenes for your reference**</span></span>

* <span data-ttu-id="44e2a-167">В папке **сцены** вы найдете два завершенных сцен Unity.</span><span class="sxs-lookup"><span data-stu-id="44e2a-167">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="44e2a-168">**MixedReality213**: завершено сцену с одной кистью</span><span class="sxs-lookup"><span data-stu-id="44e2a-168">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="44e2a-169">**MixedReality213Advanced**: Готовая сцена для расширенного проектирования с несколькими кистями</span><span class="sxs-lookup"><span data-stu-id="44e2a-169">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="44e2a-170">**Настройка новой сцены для учебника**</span><span class="sxs-lookup"><span data-stu-id="44e2a-170">**New Scene setup for the tutorial**</span></span>

* <span data-ttu-id="44e2a-171">В Unity щелкните **файл > создать сцену** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-171">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="44e2a-172">Удаление **основной камеры** и **направленного освещения**</span><span class="sxs-lookup"><span data-stu-id="44e2a-172">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="44e2a-173">На **панели проект**найдите и перетащите следующий Prefabs на панель **Иерархия** :</span><span class="sxs-lookup"><span data-stu-id="44e2a-173">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="44e2a-174">Assets/Холотулкит/input/Prefabs/**микседреалитикамера**</span><span class="sxs-lookup"><span data-stu-id="44e2a-174">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="44e2a-175">Активы/Апппрефабс/**Среда**</span><span class="sxs-lookup"><span data-stu-id="44e2a-175">Assets/AppPrefabs/**Environment**</span></span>

    ![Камера и среда](images/mr213-cameraenvironment-300px.jpg)

* <span data-ttu-id="44e2a-177">В наборе средств Mixed Reality есть два Prefabs камеры:</span><span class="sxs-lookup"><span data-stu-id="44e2a-177">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="44e2a-178">**Микседреалитикамера. prefab**: только Камера</span><span class="sxs-lookup"><span data-stu-id="44e2a-178">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="44e2a-179">**Микседреалитикамерапарент. prefab**: Камера + телеперенос + граница</span><span class="sxs-lookup"><span data-stu-id="44e2a-179">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="44e2a-180">В этом учебнике мы будем использовать **микседреалитикамера** без функции телепереноса.</span><span class="sxs-lookup"><span data-stu-id="44e2a-180">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="44e2a-181">По этой причине мы добавили простой prefab **среды** , который содержит базовое основание для того, чтобы пользователь был заземлен.</span><span class="sxs-lookup"><span data-stu-id="44e2a-181">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="44e2a-182">Дополнительные сведения о сопоставлении с **микседреалитикамерапарент**см. в статье [Расширенный Дизайн — телесхема и локомотион](#advanced-design---teleportation-and-locomotion) .</span><span class="sxs-lookup"><span data-stu-id="44e2a-182">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="44e2a-183">**Установка скибокс**</span><span class="sxs-lookup"><span data-stu-id="44e2a-183">**Skybox setup**</span></span>

* <span data-ttu-id="44e2a-184">Щелкните **окно > освещение > параметры**</span><span class="sxs-lookup"><span data-stu-id="44e2a-184">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="44e2a-185">Щелкните окружность справа от **поля Скибокс Material (материальный материал** ).</span><span class="sxs-lookup"><span data-stu-id="44e2a-185">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="44e2a-186">Введите "серый" и выберите **скибоксграй** (Assets/Апппрефабс/support/Materials/скибоксграй. Asset).</span><span class="sxs-lookup"><span data-stu-id="44e2a-186">Type in ‘gray’ and select **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

    ![Настройка скибокс](images/mr123-skyboxsetting-400px.jpg)

* <span data-ttu-id="44e2a-188">Проверьте параметр **скибокс** , чтобы увидеть назначенный серый градиент скибокс</span><span class="sxs-lookup"><span data-stu-id="44e2a-188">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

    ![Переключить параметр скибокс](images/mr213-skyboxcheck-400px.jpg)

* <span data-ttu-id="44e2a-190">Сцена с Микседреалитикамера, средой и серым скибокс будет выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="44e2a-190">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

    ![Среда MixedReality213](images/mr213-environment-600px.jpg)

* <span data-ttu-id="44e2a-192">Щелкните **файл > сохранить сцену как** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-192">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="44e2a-193">**Сохраните** сцену в папке сцены с любым именем.</span><span class="sxs-lookup"><span data-stu-id="44e2a-193">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="44e2a-194">Глава 1. Визуализация контроллера</span><span class="sxs-lookup"><span data-stu-id="44e2a-194">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="44e2a-195">Задачи</span><span class="sxs-lookup"><span data-stu-id="44e2a-195">Objectives</span></span>

* <span data-ttu-id="44e2a-196">Узнайте, как визуализировать модели контроллеров движения в игровом режиме Unity и во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="44e2a-196">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="44e2a-197">Windows Mixed Reality предоставляет анимированную модель контроллера для визуализации контроллера.</span><span class="sxs-lookup"><span data-stu-id="44e2a-197">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="44e2a-198">Существует несколько подходов, которые можно предпринять для визуализации контроллера в приложении:</span><span class="sxs-lookup"><span data-stu-id="44e2a-198">There are several approaches you can take for controller visualization in your app:</span></span>

* <span data-ttu-id="44e2a-199">По умолчанию — использование контроллера по умолчанию без изменения</span><span class="sxs-lookup"><span data-stu-id="44e2a-199">Default - Using default controller without modification</span></span>
* <span data-ttu-id="44e2a-200">Гибридный — использование контроллера по умолчанию, но настройка некоторых его элементов или переверстка компонентов пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="44e2a-200">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="44e2a-201">Замена. с помощью собственной настраиваемой трехмерной модели контроллера</span><span class="sxs-lookup"><span data-stu-id="44e2a-201">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="44e2a-202">В этой главе мы рассмотрим примеры этих настроек контроллера.</span><span class="sxs-lookup"><span data-stu-id="44e2a-202">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="44e2a-203">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-203">Instructions</span></span>

* <span data-ttu-id="44e2a-204">На панели **проект** введите **мотионконтроллерс** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="44e2a-204">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="44e2a-205">Его также можно найти в разделе Assets/Холотулкит/input/Prefabs/.</span><span class="sxs-lookup"><span data-stu-id="44e2a-205">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="44e2a-206">Перетащите **мотионконтроллерс** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-206">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-207">Щелкните **мотионконтроллерс** prefab на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-207">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="44e2a-208">**Мотионконтроллерс prefab**</span><span class="sxs-lookup"><span data-stu-id="44e2a-208">**MotionControllers prefab**</span></span>

<span data-ttu-id="44e2a-209">**Мотионконтроллерс** prefab содержит скрипт **мотионконтроллервисуализер** , который предоставляет слоты для альтернативных моделей контроллера.</span><span class="sxs-lookup"><span data-stu-id="44e2a-209">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="44e2a-210">Если вы назначили собственные настраиваемые трехмерные модели, такие как рука или технологий, и установите флажок "всегда использовать альтернативную левую или правую модель", вы увидите их вместо модели по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="44e2a-210">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="44e2a-211">Мы будем использовать этот слот в главе 4 для замены модели контроллера на кисть.</span><span class="sxs-lookup"><span data-stu-id="44e2a-211">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="44e2a-213">**Водим**</span><span class="sxs-lookup"><span data-stu-id="44e2a-213">**Instructions**</span></span>

* <span data-ttu-id="44e2a-214">На панели **инспектора** дважды щелкните сценарий **мотионконтроллервисуализер** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44e2a-214">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="44e2a-215">**Сценарий Мотионконтроллервисуализер**</span><span class="sxs-lookup"><span data-stu-id="44e2a-215">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="44e2a-216">Классы **мотионконтроллервисуализер** и **мотионконтроллеринфо** предоставляют средства для доступа к & изменения моделей контроллеров по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="44e2a-216">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="44e2a-217">**Мотионконтроллервисуализер** подписывается на событие **интерактионсаурцедетектед** Unity и автоматически создает экземпляры моделей контроллеров при их обнаружении.</span><span class="sxs-lookup"><span data-stu-id="44e2a-217">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="44e2a-218">Модели контроллера доставляются в соответствии со [спецификацией глтф](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="44e2a-218">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="44e2a-219">Этот формат был создан для предоставления общего формата, в то же время улучшая процесс передачи и распаковки трехмерных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="44e2a-219">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="44e2a-220">В этом случае нам нужно извлечь и загрузить модели контроллера во время выполнения, так как мы хотим сделать работу пользователя максимально эффективной, а также не гарантируется, какая версия контроллеров движения может использоваться пользователем.</span><span class="sxs-lookup"><span data-stu-id="44e2a-220">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="44e2a-221">В этом курсе с помощью набора средств Mixed Reality используется версия [проекта Унитиглтф](https://github.com/KhronosGroup/UnityGLTF)группы кхронос.</span><span class="sxs-lookup"><span data-stu-id="44e2a-221">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="44e2a-222">После доставки контроллера скрипты могут использовать **мотионконтроллеринфо** для поиска преобразований для конкретных элементов контроллера, чтобы они могли правильно позиционироваться.</span><span class="sxs-lookup"><span data-stu-id="44e2a-222">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="44e2a-223">В следующей главе будет показано, как использовать эти скрипты для присоединения элементов пользовательского интерфейса к контроллерам.</span><span class="sxs-lookup"><span data-stu-id="44e2a-223">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="44e2a-224">*В некоторых сценариях вы найдете блоки кода с **#if! UNITY_EDITOR** или **UNITY_WSA**. Эти блоки кода выполняются только в среде выполнения UWP при развертывании в Windows. Это обусловлено тем, что набор интерфейсов API, используемых редактором Unity и средой выполнения приложений UWP, отличается.*</span><span class="sxs-lookup"><span data-stu-id="44e2a-224">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>

* <span data-ttu-id="44e2a-225">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-225">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="44e2a-226">Вы увидите сцену с контроллерами движения на гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="44e2a-226">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="44e2a-227">Можно просмотреть подробные анимации для нажатий кнопок, движения аналогового стика и выделения сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="44e2a-227">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller визуализации по умолчанию](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="44e2a-229">Глава 2. присоединение элементов пользовательского интерфейса к контроллеру</span><span class="sxs-lookup"><span data-stu-id="44e2a-229">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="44e2a-230">Задачи</span><span class="sxs-lookup"><span data-stu-id="44e2a-230">Objectives</span></span>

* <span data-ttu-id="44e2a-231">Сведения об элементах контроллеров Motion</span><span class="sxs-lookup"><span data-stu-id="44e2a-231">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="44e2a-232">Сведения о присоединении объектов к конкретным частям контроллеров</span><span class="sxs-lookup"><span data-stu-id="44e2a-232">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="44e2a-233">В этой главе вы узнаете, как добавлять элементы пользовательского интерфейса к контроллеру, к которому пользователь может легко получать доступ и работать в любое время.</span><span class="sxs-lookup"><span data-stu-id="44e2a-233">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="44e2a-234">Вы также узнаете, как добавить простой пользовательский интерфейс выбора цвета с помощью сенсорной панели ввода.</span><span class="sxs-lookup"><span data-stu-id="44e2a-234">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="44e2a-235">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-235">Instructions</span></span>

* <span data-ttu-id="44e2a-236">На панели **проект** найдите скрипт **мотионконтроллеринфо** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-236">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="44e2a-237">В результатах поиска дважды щелкните **мотионконтроллеринфо** script, чтобы увидеть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44e2a-237">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="44e2a-238">**Сценарий Мотионконтроллеринфо**</span><span class="sxs-lookup"><span data-stu-id="44e2a-238">**MotionControllerInfo script**</span></span>

<span data-ttu-id="44e2a-239">Первым шагом является выбор элемента контроллера, к которому должен быть присоединен пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="44e2a-239">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="44e2a-240">Эти элементы определяются в **контроллерелементенум** в **MotionControllerInfo.CS**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-240">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 Мотионконтроллерелементс](images/mr213-motioncontrollerelements-1000px.jpg)

* <span data-ttu-id="44e2a-242">**Домом**</span><span class="sxs-lookup"><span data-stu-id="44e2a-242">**Home**</span></span>
* <span data-ttu-id="44e2a-243">**Меню**</span><span class="sxs-lookup"><span data-stu-id="44e2a-243">**Menu**</span></span>
* <span data-ttu-id="44e2a-244">**Осознавать**</span><span class="sxs-lookup"><span data-stu-id="44e2a-244">**Grasp**</span></span>
* <span data-ttu-id="44e2a-245">**Джойстик**</span><span class="sxs-lookup"><span data-stu-id="44e2a-245">**Thumbstick**</span></span>
* <span data-ttu-id="44e2a-246">**Метьте**</span><span class="sxs-lookup"><span data-stu-id="44e2a-246">**Select**</span></span>
* <span data-ttu-id="44e2a-247">**Сенсорная панель**</span><span class="sxs-lookup"><span data-stu-id="44e2a-247">**Touchpad**</span></span>
* <span data-ttu-id="44e2a-248">**Указание** элемента "элемент" — Этот пункт представляет собой Совет контроллера, указывающего направление вперед.</span><span class="sxs-lookup"><span data-stu-id="44e2a-248">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="44e2a-249">**Водим**</span><span class="sxs-lookup"><span data-stu-id="44e2a-249">**Instructions**</span></span>

* <span data-ttu-id="44e2a-250">На панели **проект** найдите скрипт **аттачтоконтроллер** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-250">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="44e2a-251">В результатах поиска дважды щелкните **аттачтоконтроллер** script, чтобы увидеть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44e2a-251">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="44e2a-252">**Сценарий Аттачтоконтроллер**</span><span class="sxs-lookup"><span data-stu-id="44e2a-252">**AttachToController script**</span></span>

<span data-ttu-id="44e2a-253">Скрипт **аттачтоконтроллер** предоставляет простой способ присоединения любых объектов к указанному контроллеру правой или левой и элементу.</span><span class="sxs-lookup"><span data-stu-id="44e2a-253">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="44e2a-254">В **аттачелементтоконтроллер ()** ,</span><span class="sxs-lookup"><span data-stu-id="44e2a-254">In **AttachElementToController()**,</span></span>

* <span data-ttu-id="44e2a-255">Проверьте правой или левой с помощью **мотионконтроллеринфо. правой или левой**</span><span class="sxs-lookup"><span data-stu-id="44e2a-255">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="44e2a-256">Получение конкретного элемента контроллера с помощью **мотионконтроллеринфо. трижетелемент ()**</span><span class="sxs-lookup"><span data-stu-id="44e2a-256">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="44e2a-257">После получения преобразования элемента из модели контроллера родительский объект наследуется от него и задается локальное расположение объекта, &ное вращение к нулю.</span><span class="sxs-lookup"><span data-stu-id="44e2a-257">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="44e2a-258">Самый простой способ использовать сценарий **аттачтоконтроллер** — это наследовать от него, как мы сделали в случае **колорпиккервхил.**</span><span class="sxs-lookup"><span data-stu-id="44e2a-258">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="44e2a-259">Просто переопределите функции **онаттачтоконтроллер** и **ондетачфромконтроллер** , чтобы выполнить настройку или декомпозицию при обнаружении или отключении контроллера.</span><span class="sxs-lookup"><span data-stu-id="44e2a-259">Simply override the **OnAttachToController** and **OnDetachFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="44e2a-260">**Водим**</span><span class="sxs-lookup"><span data-stu-id="44e2a-260">**Instructions**</span></span>

* <span data-ttu-id="44e2a-261">На панели **проект** введите в поле поиска **колорпиккервхил**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-261">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="44e2a-262">Его также можно найти в разделе Assets/Апппрефабс/.</span><span class="sxs-lookup"><span data-stu-id="44e2a-262">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="44e2a-263">Перетащите **колорпиккервхил** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-263">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-264">Щелкните **колорпиккервхил** prefab на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-264">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-265">На панели **инспектора** дважды щелкните сценарий **колорпиккервхил** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44e2a-265">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![Колорпиккервхил prefab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="44e2a-267">**Сценарий Колорпиккервхил**</span><span class="sxs-lookup"><span data-stu-id="44e2a-267">**ColorPickerWheel script**</span></span>

<span data-ttu-id="44e2a-268">Поскольку **колорпиккервхил** наследует **аттачтоконтроллер**, он отображает **правой или левой** и **элемент** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-268">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="44e2a-269">Мы будем прикреплять пользовательский интерфейс к элементу сенсорной панели на левом контроллере.</span><span class="sxs-lookup"><span data-stu-id="44e2a-269">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Сценарий Колорпиккервхил](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="44e2a-271">**Колорпиккервхил** переопределяет **онаттачтоконтроллер** и **ондетачфромконтроллер** для подписки на событие ввода, которое будет использоваться в следующей главе для выбора цвета с помощью ввода с сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="44e2a-271">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetachFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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

* <span data-ttu-id="44e2a-272">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-272">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="44e2a-273">**Альтернативный способ присоединения объектов к контроллерам**</span><span class="sxs-lookup"><span data-stu-id="44e2a-273">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="44e2a-274">Рекомендуется, чтобы сценарии наследовались от **аттачтоконтроллер** и переопределяют **онаттачтоконтроллер**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-274">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="44e2a-275">Однако это не всегда возможно.</span><span class="sxs-lookup"><span data-stu-id="44e2a-275">However, this may not always be possible.</span></span> <span data-ttu-id="44e2a-276">Альтернативой является использование его в качестве отдельного компонента.</span><span class="sxs-lookup"><span data-stu-id="44e2a-276">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="44e2a-277">Это может быть полезно, если необходимо подключить существующий prefab к контроллеру без рефакторинга скриптов.</span><span class="sxs-lookup"><span data-stu-id="44e2a-277">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="44e2a-278">Просто попросите своего класса присвоить параметру Attach значение true, прежде чем выполнять настройку.</span><span class="sxs-lookup"><span data-stu-id="44e2a-278">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="44e2a-279">Самый простой способ сделать это — использовать соподпрограмму для "Start."</span><span class="sxs-lookup"><span data-stu-id="44e2a-279">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="44e2a-280">Глава 3. Работа с вводом сенсорной панели</span><span class="sxs-lookup"><span data-stu-id="44e2a-280">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="44e2a-281">Задачи</span><span class="sxs-lookup"><span data-stu-id="44e2a-281">Objectives</span></span>

* <span data-ttu-id="44e2a-282">Узнайте, как получить события входных данных сенсорной панели</span><span class="sxs-lookup"><span data-stu-id="44e2a-282">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="44e2a-283">Узнайте, как использовать сведения о положении оси сенсорной панели для работы с приложением</span><span class="sxs-lookup"><span data-stu-id="44e2a-283">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="44e2a-284">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-284">Instructions</span></span>

* <span data-ttu-id="44e2a-285">На панели **Иерархия** щелкните **колорпиккервхил** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-285">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="44e2a-286">На панели **инспектора** в разделе **аниматор**дважды щелкните **колорпиккервхилконтроллер** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-286">In the **Inspector** panel, under **Animator**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="44e2a-287">Вы сможете увидеть открытую вкладку **аниматор**</span><span class="sxs-lookup"><span data-stu-id="44e2a-287">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="44e2a-288">**Отображение или скрытие пользовательского интерфейса с помощью контроллера анимации Unity**</span><span class="sxs-lookup"><span data-stu-id="44e2a-288">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="44e2a-289">Чтобы показать или скрыть пользовательский интерфейс **колорпиккервхил** с анимацией, мы используем [систему анимации Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="44e2a-289">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="44e2a-290">Установка значения true или false для свойства **Visible** объекта **колорпиккервхил**позволяет **Отображать** и **скрывать** триггеры анимации.</span><span class="sxs-lookup"><span data-stu-id="44e2a-290">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="44e2a-291">Параметры **отображения** и **скрытия** определяются в контроллере анимации **колорпиккервхилконтроллер** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-291">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Контроллер анимации Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="44e2a-293">**Водим**</span><span class="sxs-lookup"><span data-stu-id="44e2a-293">**Instructions**</span></span>

* <span data-ttu-id="44e2a-294">На панели **Иерархия** выберите **колорпиккервхил** prefab.</span><span class="sxs-lookup"><span data-stu-id="44e2a-294">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="44e2a-295">На панели **инспектора** дважды щелкните сценарий **колорпиккервхил** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44e2a-295">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="44e2a-296">**Сценарий Колорпиккервхил**</span><span class="sxs-lookup"><span data-stu-id="44e2a-296">**ColorPickerWheel script**</span></span>

<span data-ttu-id="44e2a-297">**Колорпиккервхил** подписывается на событие **интерактионсаурцеупдатед** Unity для прослушивания событий сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="44e2a-297">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="44e2a-298">В **интерактионсаурцеупдатед ()** сценарий сначала проверяет, чтобы убедиться, что он:</span><span class="sxs-lookup"><span data-stu-id="44e2a-298">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>

* <span data-ttu-id="44e2a-299">фактически является событием сенсорной панели (obj. State. **Таучпадтаучед**)</span><span class="sxs-lookup"><span data-stu-id="44e2a-299">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="44e2a-300">исходит от левого контроллера (obj. State. Source. **правой или левой**)</span><span class="sxs-lookup"><span data-stu-id="44e2a-300">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="44e2a-301">Если оба значения имеют значение true, расположение сенсорной панели (obj. State. **Таучпадпоситион**) назначается **селекторпоситион**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-301">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="44e2a-302">В **Update ()** , основанном на **видимом** свойстве, он запускает отображение и скрытие триггеров анимации в компоненте аниматор средства выбора цвета.</span><span class="sxs-lookup"><span data-stu-id="44e2a-302">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="44e2a-303">В **Update ()** **селекторпоситион** используется для приведения луча по отношению к конфликту сетчатого цветового круга, который возвращает UV-расположение.</span><span class="sxs-lookup"><span data-stu-id="44e2a-303">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="44e2a-304">Эта положение затем можно использовать для поиска координат пиксела и цвета текстуры цветового круга.</span><span class="sxs-lookup"><span data-stu-id="44e2a-304">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="44e2a-305">Это значение доступно для других скриптов через свойство **селектедколор** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-305">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Палитра выбора цвета колесо Райкастинг](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="44e2a-307">Глава 4. Переопределение модели контроллера</span><span class="sxs-lookup"><span data-stu-id="44e2a-307">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="44e2a-308">Задачи</span><span class="sxs-lookup"><span data-stu-id="44e2a-308">Objectives</span></span>

* <span data-ttu-id="44e2a-309">Узнайте, как переопределить модель контроллера с помощью настраиваемой трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="44e2a-309">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="44e2a-311">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-311">Instructions</span></span>

* <span data-ttu-id="44e2a-312">На панели **Иерархия** щелкните **мотионконтроллерс** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-312">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-313">Щелкните окружность справа от поля **альтернативный контроллер справа** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-313">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="44e2a-314">Введите **"брушконтроллер**" и выберите prefab из результата.</span><span class="sxs-lookup"><span data-stu-id="44e2a-314">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="44e2a-315">Его можно найти в разделе Assets/Апппрефабс/**брушконтроллер**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-315">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="44e2a-316">Проверка **всегда использовать другую правильную модель**</span><span class="sxs-lookup"><span data-stu-id="44e2a-316">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="44e2a-318">**Брушконтроллер** prefab не обязательно включать в панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-318">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="44e2a-319">Однако, чтобы извлечь его дочерние компоненты:</span><span class="sxs-lookup"><span data-stu-id="44e2a-319">However, to check out its child components:</span></span>

* <span data-ttu-id="44e2a-320">На панели **проект** введите **Брушконтроллер** и перетащите **брушконтроллер** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-320">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="44e2a-322">Вы найдете компонент **Tip** в **брушконтроллер**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-322">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="44e2a-323">Мы будем использовать его преобразование для запуска и завершения рисования линий.</span><span class="sxs-lookup"><span data-stu-id="44e2a-323">We will use its transform to start/stop drawing lines.</span></span>

* <span data-ttu-id="44e2a-324">Удалите **брушконтроллер** с панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-324">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-325">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-325">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="44e2a-326">Вы сможете увидеть, что модель кистей заменила правый контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="44e2a-326">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="44e2a-327">Глава 5. Рисование с помощью выбора входных данных</span><span class="sxs-lookup"><span data-stu-id="44e2a-327">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="44e2a-328">Задачи</span><span class="sxs-lookup"><span data-stu-id="44e2a-328">Objectives</span></span>

* <span data-ttu-id="44e2a-329">Узнайте, как использовать событие кнопки "выбрать" для запуска и завершения рисования линий</span><span class="sxs-lookup"><span data-stu-id="44e2a-329">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="44e2a-330">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-330">Instructions</span></span>

* <span data-ttu-id="44e2a-331">Выполните поиск по запросу **брушконтроллер** prefab на панели **проекта** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-331">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="44e2a-332">На панели **инспектора** дважды щелкните сценарий **брушконтроллер** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44e2a-332">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="44e2a-333">**Сценарий Брушконтроллер**</span><span class="sxs-lookup"><span data-stu-id="44e2a-333">**BrushController script**</span></span>

<span data-ttu-id="44e2a-334">**Брушконтроллер** подписывается на события **Интерактионсаурцепрессед** и **интерактионсаурцерелеасед** интерактионманажер.</span><span class="sxs-lookup"><span data-stu-id="44e2a-334">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="44e2a-335">При запуске события **интерактионсаурцепрессед** свойство **Draw** кисти устанавливается в значение true. При запуске события **интерактионсаурцерелеасед** свойство **Draw** кисти устанавливается в значение false.</span><span class="sxs-lookup"><span data-stu-id="44e2a-335">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="44e2a-336">Если параметр **Draw** имеет значение true, кисть создаст точки в экземпляре Unity **линерендерер**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-336">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="44e2a-337">Ссылка на этот prefab хранится в поле **Stroke prefab** кисти.</span><span class="sxs-lookup"><span data-stu-id="44e2a-337">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="44e2a-338">Чтобы использовать текущий выбранный цвет в пользовательском интерфейсе колесика выбора цвета, **брушконтроллер** должен иметь ссылку на объект **колорпиккервхил** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-338">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="44e2a-339">Так как экземпляр **брушконтроллер** prefab создается во время выполнения в качестве контроллера замены, все ссылки на объекты в сцене должны быть заданы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="44e2a-339">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="44e2a-340">В этом случае мы используем **GameObject. финдобжектофтипе** для размещения **колорпиккервхил**:</span><span class="sxs-lookup"><span data-stu-id="44e2a-340">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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

* <span data-ttu-id="44e2a-341">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-341">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="44e2a-342">Вы сможете рисовать линии и рисовать с помощью кнопки выбрать в правом контроллере.</span><span class="sxs-lookup"><span data-stu-id="44e2a-342">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="44e2a-343">Глава 6 — порождение объекта с помощью выбора входных данных</span><span class="sxs-lookup"><span data-stu-id="44e2a-343">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="44e2a-344">Задачи</span><span class="sxs-lookup"><span data-stu-id="44e2a-344">Objectives</span></span>

* <span data-ttu-id="44e2a-345">Узнайте, как использовать кнопки выбора и изучения событий ввода</span><span class="sxs-lookup"><span data-stu-id="44e2a-345">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="44e2a-346">Узнайте, как создавать экземпляры объектов</span><span class="sxs-lookup"><span data-stu-id="44e2a-346">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="44e2a-347">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-347">Instructions</span></span>

* <span data-ttu-id="44e2a-348">На панели **проект** введите **обжектспавнер** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="44e2a-348">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="44e2a-349">Его также можно найти в разделе Assets/Апппрефабс/</span><span class="sxs-lookup"><span data-stu-id="44e2a-349">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="44e2a-350">Перетащите **обжектспавнер** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-350">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-351">На панели **Иерархия** щелкните **обжектспавнер** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-351">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-352">**Обжектспавнер** имеет поле с именем **источник цвета**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-352">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="44e2a-353">На панели **Иерархия** перетащите ссылку **колорпиккервхил** в это поле.</span><span class="sxs-lookup"><span data-stu-id="44e2a-353">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

    ![Инспектор порождаемых объектов](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* <span data-ttu-id="44e2a-355">Щелкните **обжектспавнер** prefab на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-355">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-356">На панели **инспектора** дважды щелкните сценарий **обжектспавнер** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44e2a-356">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="44e2a-357">**Сценарий Обжектспавнер**</span><span class="sxs-lookup"><span data-stu-id="44e2a-357">**ObjectSpawner script**</span></span>

<span data-ttu-id="44e2a-358">**Обжектспавнер** создает в пространстве экземпляры копий примитивной сетки (куб, шар, цилиндр).</span><span class="sxs-lookup"><span data-stu-id="44e2a-358">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="44e2a-359">При обнаружении **интерактионсаурцепрессед** проверяет правой или левой и, если это событие **интерактионсаурцепресстипе.** поняли или **интерактионсаурцепресстипе. Select** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-359">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="44e2a-360">Для события с учетом **усвоения** он увеличивает индекс текущего типа сетки (шар, куб, цилиндр).</span><span class="sxs-lookup"><span data-stu-id="44e2a-360">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="44e2a-361">Для события **SELECT** в **спавнобжект ()** создается экземпляр нового объекта, не являющийся родительским и освобожденный в мире.</span><span class="sxs-lookup"><span data-stu-id="44e2a-361">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="44e2a-362">**Обжектспавнер** использует **колорпиккервхил** для установки цвета материала экранного объекта.</span><span class="sxs-lookup"><span data-stu-id="44e2a-362">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="44e2a-363">Порожденным объектам присваивается экземпляр этого материала, чтобы они сохраняли свой цвет.</span><span class="sxs-lookup"><span data-stu-id="44e2a-363">Spawned objects are given an instance of this material so they will retain their color.</span></span>

* <span data-ttu-id="44e2a-364">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-364">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="44e2a-365">Вы сможете изменить объекты с помощью кнопки "располагаться" и порождением объектов с помощью кнопки "выбрать".</span><span class="sxs-lookup"><span data-stu-id="44e2a-365">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="44e2a-366">Создание и развертывание приложения на портале смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="44e2a-366">Build and deploy app to Mixed Reality Portal</span></span>

* <span data-ttu-id="44e2a-367">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-367">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="44e2a-368">Нажмите кнопку **Добавить открытые сцены** , чтобы добавить текущую сцену в **сцена в сборке**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-368">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="44e2a-369">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-369">Click **Build**.</span></span>
* <span data-ttu-id="44e2a-370">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="44e2a-370">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="44e2a-371">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="44e2a-371">Single click the **App** folder.</span></span>
* <span data-ttu-id="44e2a-372">Щелкните элемент **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-372">Click **Select Folder**.</span></span>
* <span data-ttu-id="44e2a-373">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="44e2a-373">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="44e2a-374">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-374">Open the **App** folder.</span></span>
* <span data-ttu-id="44e2a-375">Дважды щелкните файл решения Visual Studio **йоурсцененаме. sln** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-375">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="44e2a-376">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-376">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="44e2a-377">Щелкните стрелку раскрывающегося списка рядом с кнопкой устройство и выберите **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-377">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="44e2a-378">Щелкните **Отладка-> запуск без отладки** в меню или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-378">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="44e2a-379">Теперь приложение создается и устанавливается на портале смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="44e2a-379">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="44e2a-380">Вы можете запустить его снова через меню "Пуск" на портале Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="44e2a-380">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="44e2a-381">Дополнительные инструменты проектирования и кисти с радиальным макетом</span><span class="sxs-lookup"><span data-stu-id="44e2a-381">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="44e2a-383">В этой главе вы узнаете, как заменить модель контроллера движения по умолчанию на коллекцию настраиваемых инструментов кисти.</span><span class="sxs-lookup"><span data-stu-id="44e2a-383">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="44e2a-384">Для справки можно найти завершенную сцену **MixedReality213Advanced** в папке **сцены** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-384">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="44e2a-385">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-385">Instructions</span></span>

* <span data-ttu-id="44e2a-386">На панели **проект** введите **брушселектор** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="44e2a-386">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="44e2a-387">Его также можно найти в разделе Assets/Апппрефабс/</span><span class="sxs-lookup"><span data-stu-id="44e2a-387">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="44e2a-388">Перетащите **брушселектор** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-388">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-389">Для организации создайте пустой GameObject с именем **кисти** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-389">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="44e2a-390">Перетащите следующие Prefabs с панели **проект** на **кисти** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-390">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="44e2a-391">Активы/Апппрефабс/**брушфат**</span><span class="sxs-lookup"><span data-stu-id="44e2a-391">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="44e2a-392">Активы/Апппрефабс/**брушсин**</span><span class="sxs-lookup"><span data-stu-id="44e2a-392">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="44e2a-393">Активы/Апппрефабс/**резинка**</span><span class="sxs-lookup"><span data-stu-id="44e2a-393">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="44e2a-394">Активы/Апппрефабс/**маркерфат**</span><span class="sxs-lookup"><span data-stu-id="44e2a-394">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="44e2a-395">Активы/Апппрефабс/**маркерсин**</span><span class="sxs-lookup"><span data-stu-id="44e2a-395">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="44e2a-396">Активы/Апппрефабс/**карандаш**</span><span class="sxs-lookup"><span data-stu-id="44e2a-396">Assets/AppPrefabs/**Pencil**</span></span>

    ![Кисти](images/mixedreality213-brushes-250px.png)

* <span data-ttu-id="44e2a-398">Щелкните **мотионконтроллерс** prefab на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-398">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="44e2a-399">На панели **инспектора** снимите флажок **всегда использовать другую правильную модель** на **визуализаторе контроллера движения** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-399">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="44e2a-400">На панели **Иерархия** щелкните **брушселектор** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-400">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="44e2a-401">**Брушселектор** содержит поле с именем **ColorPicker** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-401">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="44e2a-402">На панели « **Иерархия** » перетащите поле **колорпиккервхил** в **ColorPicker** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-402">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

    ![Назначение Колорпиккервхил селектору кисти](images/mr213-brushselector-500px.jpg)

* <span data-ttu-id="44e2a-404">На панели **Иерархия** в разделе **брушселектор** prefab выберите объект **меню** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-404">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="44e2a-405">На панели **инспектора** в разделе компонент **линеобжектколлектион** откройте раскрывающийся список массив **объектов** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-405">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="44e2a-406">Вы увидите 6 пустых слотов.</span><span class="sxs-lookup"><span data-stu-id="44e2a-406">You will see 6 empty slots.</span></span>
* <span data-ttu-id="44e2a-407">На панели **Иерархия** перетащите все Prefabs, наявляющиеся от **кистей** , GameObject в эти слоты в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="44e2a-407">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="44e2a-408">(Убедитесь, что вы перетаскивайте Prefabs из сцены, а не из Prefabs в папке проекта.)</span><span class="sxs-lookup"><span data-stu-id="44e2a-408">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Селектор кисти](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="44e2a-410">**Брушселектор prefab**</span><span class="sxs-lookup"><span data-stu-id="44e2a-410">**BrushSelector prefab**</span></span>

<span data-ttu-id="44e2a-411">Поскольку **брушселектор** наследует **аттачтоконтроллер**, он отображает параметры **правой или левой** и **element** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-411">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="44e2a-412">Мы выбрали **право** и назначите элемент «рука **», чтобы** присоединить средства кистей к правому контроллеру с прямым направлением.</span><span class="sxs-lookup"><span data-stu-id="44e2a-412">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="44e2a-413">**Брушселектор** использует две служебные программы:</span><span class="sxs-lookup"><span data-stu-id="44e2a-413">The **BrushSelector** makes use of two utilities:</span></span>

* <span data-ttu-id="44e2a-414">**Эллипс**: используется для создания точек в пространстве вдоль фигуры эллипса.</span><span class="sxs-lookup"><span data-stu-id="44e2a-414">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="44e2a-415">**Линеобжектколлектион**: распределяет объекты с помощью точек, созданных любым классом линии (например, эллипсом).</span><span class="sxs-lookup"><span data-stu-id="44e2a-415">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="44e2a-416">Именно так мы будем использовать для размещения наших кистей вдоль эллипса.</span><span class="sxs-lookup"><span data-stu-id="44e2a-416">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="44e2a-417">В сочетании эти служебные программы можно использовать для создания радиального меню.</span><span class="sxs-lookup"><span data-stu-id="44e2a-417">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="44e2a-418">**Сценарий Линеобжектколлектион**</span><span class="sxs-lookup"><span data-stu-id="44e2a-418">**LineObjectCollection script**</span></span>

<span data-ttu-id="44e2a-419">**Линеобжектколлектион** имеет элементы управления размером, расположением и поворотом объектов, распределенных вдоль линии.</span><span class="sxs-lookup"><span data-stu-id="44e2a-419">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="44e2a-420">Это полезно для создания радиальных меню, таких как селектор кисти.</span><span class="sxs-lookup"><span data-stu-id="44e2a-420">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="44e2a-421">Чтобы создать внешний вид кистей, которые не масштабируются по мере приближения к центру выбранной позиции, **обжектскале** кривая в центре и конусы на краях.</span><span class="sxs-lookup"><span data-stu-id="44e2a-421">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="44e2a-422">**Сценарий Брушселектор**</span><span class="sxs-lookup"><span data-stu-id="44e2a-422">**BrushSelector script**</span></span>

<span data-ttu-id="44e2a-423">В случае с **брушселектор**мы решили использовать метод анимации.</span><span class="sxs-lookup"><span data-stu-id="44e2a-423">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="44e2a-424">Во первых, модели кистей распределяются на эллипсе с помощью скрипта **линеобжектколлектион** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-424">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="44e2a-425">Затем каждая кисть несет ответственность за поддержание своего расположения в руки пользователя на основе его значения **DisplayMode** , которое изменяется в зависимости от выбора.</span><span class="sxs-lookup"><span data-stu-id="44e2a-425">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="44e2a-426">Мы выбрали подход к методу из-за того, что высокая вероятность того, что переходы по положению кисти прерываются, так как пользователь выбирает кисти.</span><span class="sxs-lookup"><span data-stu-id="44e2a-426">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="44e2a-427">Анимация меканим может правильно обрабатывать прерывания, но она, как правило, сложнее, чем простая операция Лерп.</span><span class="sxs-lookup"><span data-stu-id="44e2a-427">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="44e2a-428">**Брушселектор** использует сочетание обоих типов.</span><span class="sxs-lookup"><span data-stu-id="44e2a-428">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="44e2a-429">При обнаружении ввода сенсорной панели Параметры кисти становятся видимыми и масштабируются вдоль радиального меню.</span><span class="sxs-lookup"><span data-stu-id="44e2a-429">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="44e2a-430">По истечении времени ожидания (которое указывает, что пользователь сделал выбор) параметры кисти снова масштабируются, при этом остается только выбранная кисть.</span><span class="sxs-lookup"><span data-stu-id="44e2a-430">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="44e2a-431">**Визуализация ввода сенсорной панели**</span><span class="sxs-lookup"><span data-stu-id="44e2a-431">**Visualizing touchpad input**</span></span>

<span data-ttu-id="44e2a-432">Даже в тех случаях, когда модель контроллера была полностью заменена, может быть полезно отобразить входные данные исходной модели.</span><span class="sxs-lookup"><span data-stu-id="44e2a-432">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="44e2a-433">Это позволяет заземление действий пользователя в реальности.</span><span class="sxs-lookup"><span data-stu-id="44e2a-433">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="44e2a-434">Для **брушселектор** мы решили, чтобы сенсорная панель ненадолго отображалась при получении входных данных.</span><span class="sxs-lookup"><span data-stu-id="44e2a-434">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="44e2a-435">Это было сделано путем извлечения элемента сенсорной панели из контроллера, замены его материала на пользовательский материал, а затем применения градиента к цвету материала на основе последнего полученного ввода сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="44e2a-435">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="44e2a-436">**Выбор инструмента "кисть" с входными данными сенсорной панели**</span><span class="sxs-lookup"><span data-stu-id="44e2a-436">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="44e2a-437">Когда селектор кисти обнаруживает нажатую клавишу сенсорного ввода, он проверяет расположение входных данных, чтобы определить, было ли оно равно левому или правому.</span><span class="sxs-lookup"><span data-stu-id="44e2a-437">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="44e2a-438">**Толщина штриха с помощью Селектпресседамаунт**</span><span class="sxs-lookup"><span data-stu-id="44e2a-438">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="44e2a-439">Вместо события **интерактионсаурцепресстипе. Select** в **интерактионсаурцепрессед ()** можно получить значение аналогового значения выделенной суммы через **селектпресседамаунт**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-439">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="44e2a-440">Это значение можно получить в **интерактионсаурцеупдатед ()** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-440">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="44e2a-441">**Сценарий ластика**</span><span class="sxs-lookup"><span data-stu-id="44e2a-441">**Eraser script**</span></span>

<span data-ttu-id="44e2a-442">**Ластик** — это специальный тип кисти, переопределяющий функцию **дравовертиме ()** базовой **кисти**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-442">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="44e2a-443">Когда Draw имеет значение true, резинка проверяет, пересекается ли его Совет с любыми существующими мазками кистью.</span><span class="sxs-lookup"><span data-stu-id="44e2a-443">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="44e2a-444">Если это так, они добавляются в очередь для уменьшения и удаления.</span><span class="sxs-lookup"><span data-stu-id="44e2a-444">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="44e2a-445">Расширенный дизайн — локальная и локомотион</span><span class="sxs-lookup"><span data-stu-id="44e2a-445">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="44e2a-446">Если вы хотите разрешить пользователю перемещаться по сцене с помощью многопортового стика, используйте **микседреалитикамерапарент** вместо **микседреалитикамера**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-446">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="44e2a-447">Также необходимо добавить **InputManager** и **дефаулткурсор**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-447">You also need to add **InputManager** and **DefaultCursor**.</span></span> <span data-ttu-id="44e2a-448">Так **как микседреалитикамерапарент** уже включает **мотионконтроллерс** и **границу** как дочерние компоненты, следует удалить существующие prefab **мотионконтроллерс** и **среды** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-448">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="44e2a-449">Инструкция</span><span class="sxs-lookup"><span data-stu-id="44e2a-449">Instructions</span></span>

* <span data-ttu-id="44e2a-450">На панели **Иерархия** удалите **микседреалитикамера**, **Environment** и **мотионконтроллерс** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-450">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="44e2a-451">На **панели проект**найдите и перетащите следующий Prefabs на панель **Иерархия** :</span><span class="sxs-lookup"><span data-stu-id="44e2a-451">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="44e2a-452">Assets/Апппрефабс/input/Prefabs/**микседреалитикамерапарент**</span><span class="sxs-lookup"><span data-stu-id="44e2a-452">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="44e2a-453">Assets/Апппрефабс/input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="44e2a-453">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="44e2a-454">Assets/Апппрефабс/input/Prefabs/Cursor/**дефаулткурсор**</span><span class="sxs-lookup"><span data-stu-id="44e2a-454">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

    ![Родитель камеры смешанной реальности](images/mr213-cameraparent-300px.png)

* <span data-ttu-id="44e2a-456">На панели **Иерархия** щелкните **Диспетчер входов** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-456">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="44e2a-457">На панели **инспектора** прокрутите вниз до раздела **простой единичный селектор указателя** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-457">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="44e2a-458">На панели **Иерархия** перетащите **дефаулткурсор** INTO в поле **курсора** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-458">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

    ![Назначение Дефаулткурсор](images/mr213-defaultcursor-500px.png)

* <span data-ttu-id="44e2a-460">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="44e2a-460">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="44e2a-461">Вы сможете использовать аналоговый стик для поворота влево, вправо или телепортироваться.</span><span class="sxs-lookup"><span data-stu-id="44e2a-461">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="44e2a-462">Конец</span><span class="sxs-lookup"><span data-stu-id="44e2a-462">The end</span></span>

<span data-ttu-id="44e2a-463">И это окончание этого руководства.</span><span class="sxs-lookup"><span data-stu-id="44e2a-463">And that's the end of this tutorial!</span></span> <span data-ttu-id="44e2a-464">Вы узнали:</span><span class="sxs-lookup"><span data-stu-id="44e2a-464">You learned:</span></span>

* <span data-ttu-id="44e2a-465">Как работать с моделями контроллера движения в игровом режиме Unity и в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="44e2a-465">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="44e2a-466">Использование различных типов событий кнопок и их приложений.</span><span class="sxs-lookup"><span data-stu-id="44e2a-466">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="44e2a-467">Как наложение элементов пользовательского интерфейса поверх контроллера или его полная настройка.</span><span class="sxs-lookup"><span data-stu-id="44e2a-467">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="44e2a-468">Теперь вы готовы приступить к созданию своего собственного иммерсивного интерфейса с помощью контроллеров движения!</span><span class="sxs-lookup"><span data-stu-id="44e2a-468">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="44e2a-469">Завершенные сцены</span><span class="sxs-lookup"><span data-stu-id="44e2a-469">Completed scenes</span></span>

* <span data-ttu-id="44e2a-470">На панели **проекта** Unity щелкните папку " **сцены** ".</span><span class="sxs-lookup"><span data-stu-id="44e2a-470">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="44e2a-471">Вы обнаружите две сцены Unity **MixedReality213** и **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="44e2a-471">You will find two Unity scenes **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="44e2a-472">**MixedReality213**: завершено сцену с одной кистью</span><span class="sxs-lookup"><span data-stu-id="44e2a-472">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="44e2a-473">**MixedReality213Advanced**: завершенная сцена с несколькими кистями с примером суммы нажатия кнопки SELECT</span><span class="sxs-lookup"><span data-stu-id="44e2a-473">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="44e2a-474">См. также</span><span class="sxs-lookup"><span data-stu-id="44e2a-474">See also</span></span>

* [<span data-ttu-id="44e2a-475">Файлы проекта с вводом в MR 213</span><span class="sxs-lookup"><span data-stu-id="44e2a-475">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="44e2a-476">Набор средств для смешанной реальности — тестовая сцена контроллера движения</span><span class="sxs-lookup"><span data-stu-id="44e2a-476">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="44e2a-477">Набор средств для смешанной реальности — механики захвата</span><span class="sxs-lookup"><span data-stu-id="44e2a-477">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="44e2a-478">Рекомендации по разработке для контроллера движения</span><span class="sxs-lookup"><span data-stu-id="44e2a-478">Motion controller development guidelines</span></span>](motion-controllers.md)
