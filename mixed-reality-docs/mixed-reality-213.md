---
title: Ввод MR 213
description: Следуйте этому руководству по программированию с помощью Unity, Visual Studio и впечатляющих головных телефонов для получения сведений об контроллерах движения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, иммерсивное, контроллер движения, Academy, руководство
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516418"
---
>[!NOTE]
><span data-ttu-id="78767-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="78767-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="78767-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="78767-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="78767-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="78767-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="78767-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="78767-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="78767-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="78767-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="78767-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="78767-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="78767-110">Ввод MR 213: Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="78767-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="78767-111">Контроллеры движения в мире смешанной реальности добавляют еще один уровень интерактивности.</span><span class="sxs-lookup"><span data-stu-id="78767-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="78767-112">Используя [контроллеры движения](motion-controllers.md), мы можем напрямую взаимодействовать с объектами более естественным образом, аналогично нашим физическим взаимодействиям в реальном времени, повышая иммерсивное и удовлетворения запросов в работе приложения.</span><span class="sxs-lookup"><span data-stu-id="78767-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="78767-113">В MR input 213 мы рассмотрим события ввода контроллера движения, создав простой интерфейс для пространственного рисования.</span><span class="sxs-lookup"><span data-stu-id="78767-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="78767-114">С помощью этого приложения пользователи могут закрашивать трехмерное пространство с помощью различных типов кистей и цветов.</span><span class="sxs-lookup"><span data-stu-id="78767-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="78767-115">Темы, описанные в этом руководстве</span><span class="sxs-lookup"><span data-stu-id="78767-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="78767-119">**Визуализация контроллера**</span><span class="sxs-lookup"><span data-stu-id="78767-119">**Controller visualization**</span></span>|<span data-ttu-id="78767-120">**События ввода контроллера**</span><span class="sxs-lookup"><span data-stu-id="78767-120">**Controller input events**</span></span>|<span data-ttu-id="78767-121">**Пользовательский контроллер и пользовательский интерфейс**</span><span class="sxs-lookup"><span data-stu-id="78767-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="78767-122">Узнайте, как визуализировать модели контроллеров движения в игровом режиме и среде выполнения Unity.</span><span class="sxs-lookup"><span data-stu-id="78767-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="78767-123">Изучите различные типы событий кнопок и их приложений.</span><span class="sxs-lookup"><span data-stu-id="78767-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="78767-124">Узнайте, как наложение элементов пользовательского интерфейса поверх контроллера или его полная настройка.</span><span class="sxs-lookup"><span data-stu-id="78767-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="78767-125">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="78767-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="78767-126">Хождение</span><span class="sxs-lookup"><span data-stu-id="78767-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="78767-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="78767-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="78767-128"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="78767-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="78767-129">Ввод MR 213: Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="78767-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="78767-130">✔️</span><span class="sxs-lookup"><span data-stu-id="78767-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="78767-131">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="78767-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="78767-132">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="78767-132">Prerequisites</span></span>

<span data-ttu-id="78767-133">См. Контрольный список установки для впечатляющих головных телефонов на [этой странице](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="78767-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="78767-134">Для работы с этим руководством требуется [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="78767-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="78767-135">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="78767-135">Project files</span></span>

* <span data-ttu-id="78767-136">[Скачайте файлы](https://github.com/Microsoft/MixedReality213/archive/master.zip) , необходимые для проекта, и извлеките файлы на Рабочий стол.</span><span class="sxs-lookup"><span data-stu-id="78767-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="78767-137">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="78767-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="78767-138">Установка Unity</span><span class="sxs-lookup"><span data-stu-id="78767-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="78767-139">Цели</span><span class="sxs-lookup"><span data-stu-id="78767-139">Objectives</span></span>

* <span data-ttu-id="78767-140">Оптимизация Unity для разработки Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="78767-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="78767-141">Настройка камеры смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="78767-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="78767-142">Среда установки</span><span class="sxs-lookup"><span data-stu-id="78767-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="78767-143">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-143">Instructions</span></span>

* <span data-ttu-id="78767-144">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="78767-144">Start Unity.</span></span>
* <span data-ttu-id="78767-145">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="78767-145">Select **Open**.</span></span>
* <span data-ttu-id="78767-146">Перейдите к рабочему столу и найдите папку **MixedReality213-Master** , которая ранее была неархивирована.</span><span class="sxs-lookup"><span data-stu-id="78767-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="78767-147">Щелкните элемент **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="78767-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="78767-148">После того как Unity закончит загрузку файлов проекта, вы сможете увидеть редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="78767-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="78767-149">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="78767-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="78767-151">Выберите **универсальная платформа Windows** в списке **платформа** и нажмите кнопку **переключателя платформы** .</span><span class="sxs-lookup"><span data-stu-id="78767-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="78767-152">Задать целевое устройство для **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="78767-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="78767-153">Задать для типа сборки **D3D**</span><span class="sxs-lookup"><span data-stu-id="78767-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="78767-154">Установить **последний установленный** пакет SDK</span><span class="sxs-lookup"><span data-stu-id="78767-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="78767-155">Проверка **проектов C# Unity**</span><span class="sxs-lookup"><span data-stu-id="78767-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="78767-156">Это позволяет изменять файлы скриптов в проекте Visual Studio без перестроения проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="78767-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="78767-157">Щелкните **Параметры проигрывателя**.</span><span class="sxs-lookup"><span data-stu-id="78767-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="78767-158">Прокрутите  панель инспектора вниз до конца</span><span class="sxs-lookup"><span data-stu-id="78767-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="78767-159">В параметрах XR проверьте, **поддерживается ли виртуальная реальность**</span><span class="sxs-lookup"><span data-stu-id="78767-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="78767-160">В разделе пакеты SDK для Virtual Reality выберите **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="78767-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="78767-162">Закройте окно **параметров сборки** .</span><span class="sxs-lookup"><span data-stu-id="78767-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="78767-163">Структура проекта</span><span class="sxs-lookup"><span data-stu-id="78767-163">Project structure</span></span>

<span data-ttu-id="78767-164">В этом руководстве используется **[набор средств для смешанной реальности — Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** .</span><span class="sxs-lookup"><span data-stu-id="78767-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="78767-165">Выпуски можно найти на [этой странице](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="78767-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![прожектструктуре](images/mr213-projectstructure-650px.png)

<span data-ttu-id="78767-167">**Завершенные монтажные кадры для справки**</span><span class="sxs-lookup"><span data-stu-id="78767-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="78767-168">В папке **сцены** вы найдете два завершенных сцен Unity.</span><span class="sxs-lookup"><span data-stu-id="78767-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="78767-169">**MixedReality213**: Завершенная сцена с одной кистью</span><span class="sxs-lookup"><span data-stu-id="78767-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="78767-170">**MixedReality213Advanced**: Готовая сцена для расширенного проектирования с несколькими кистями</span><span class="sxs-lookup"><span data-stu-id="78767-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="78767-171">**Настройка новой сцены для учебника**</span><span class="sxs-lookup"><span data-stu-id="78767-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="78767-172">В Unity щелкните **файл > создать сцену** .</span><span class="sxs-lookup"><span data-stu-id="78767-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="78767-173">Удаление **основной камеры** и **направленного освещения**</span><span class="sxs-lookup"><span data-stu-id="78767-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="78767-174">На **панели проект**найдите и перетащите следующий Prefabs на панель Иерархия:</span><span class="sxs-lookup"><span data-stu-id="78767-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="78767-175">Assets/Холотулкит/input/Prefabs/**микседреалитикамера**</span><span class="sxs-lookup"><span data-stu-id="78767-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="78767-176">Активы/Апппрефабс/**Среда**</span><span class="sxs-lookup"><span data-stu-id="78767-176">Assets/AppPrefabs/**Environment**</span></span>

![Камера и среда](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="78767-178">В наборе средств Mixed Reality есть два Prefabs камеры:</span><span class="sxs-lookup"><span data-stu-id="78767-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="78767-179">**Микседреалитикамера. prefab**: Только Камера</span><span class="sxs-lookup"><span data-stu-id="78767-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="78767-180">**Микседреалитикамерапарент. prefab**: Камера + номер для передачи + граница</span><span class="sxs-lookup"><span data-stu-id="78767-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="78767-181">В этом учебнике мы будем использовать **микседреалитикамера** без функции телепереноса.</span><span class="sxs-lookup"><span data-stu-id="78767-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="78767-182">По этой причине мы добавили простой prefab **среды** , который содержит базовое основание для того, чтобы пользователь был заземлен.</span><span class="sxs-lookup"><span data-stu-id="78767-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="78767-183">Дополнительные сведения о сопоставлении с **микседреалитикамерапарент**см. в статье [Расширенный Дизайн — телесхема и локомотион](#advanced-design---teleportation-and-locomotion) .</span><span class="sxs-lookup"><span data-stu-id="78767-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="78767-184">**Установка скибокс**</span><span class="sxs-lookup"><span data-stu-id="78767-184">**Skybox setup**</span></span>
* <span data-ttu-id="78767-185">Щелкните **окно > освещение > параметры**</span><span class="sxs-lookup"><span data-stu-id="78767-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="78767-186">Щелкните окружность справа от **поля Скибокс Material (материальный материал** ).</span><span class="sxs-lookup"><span data-stu-id="78767-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="78767-187">Введите "серый" и выберите **скибоксграй**</span><span class="sxs-lookup"><span data-stu-id="78767-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="78767-188">(Assets/Апппрефабс/support/Materials/Скибоксграй. Asset)</span><span class="sxs-lookup"><span data-stu-id="78767-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Настройка скибокс](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="78767-190">Проверьте параметр **скибокс** , чтобы увидеть назначенный серый градиент скибокс</span><span class="sxs-lookup"><span data-stu-id="78767-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Переключить параметр скибокс](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="78767-192">Сцена с Микседреалитикамера, средой и серым скибокс будет выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="78767-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![Среда MixedReality213](images/mr213-environment-600px.jpg)
* <span data-ttu-id="78767-194">Щелкните **файл > сохранить сцену как** .</span><span class="sxs-lookup"><span data-stu-id="78767-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="78767-195">**Сохраните** сцену в папке сцены с любым именем.</span><span class="sxs-lookup"><span data-stu-id="78767-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="78767-196">Глава 1. Визуализация контроллера</span><span class="sxs-lookup"><span data-stu-id="78767-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="78767-197">Цели</span><span class="sxs-lookup"><span data-stu-id="78767-197">Objectives</span></span>

* <span data-ttu-id="78767-198">Узнайте, как визуализировать модели контроллеров движения в игровом режиме Unity и во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="78767-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="78767-199">Windows Mixed Reality предоставляет анимированную модель контроллера для визуализации контроллера.</span><span class="sxs-lookup"><span data-stu-id="78767-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="78767-200">Существует несколько подходов, которые можно предпринять для визуализации контроллера в приложении:</span><span class="sxs-lookup"><span data-stu-id="78767-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="78767-201">По умолчанию — использование контроллера по умолчанию без изменения</span><span class="sxs-lookup"><span data-stu-id="78767-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="78767-202">Гибридный — использование контроллера по умолчанию, но настройка некоторых его элементов или переверстка компонентов пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="78767-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="78767-203">Замена. с помощью собственной настраиваемой трехмерной модели контроллера</span><span class="sxs-lookup"><span data-stu-id="78767-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="78767-204">В этой главе мы рассмотрим примеры этих настроек контроллера.</span><span class="sxs-lookup"><span data-stu-id="78767-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="78767-205">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-205">Instructions</span></span>

* <span data-ttu-id="78767-206">На панели **проект** введите **мотионконтроллерс** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="78767-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="78767-207">Его также можно найти в разделе Assets/Холотулкит/input/Prefabs/.</span><span class="sxs-lookup"><span data-stu-id="78767-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="78767-208">Перетащите **мотионконтроллерс** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-209">Щелкните **мотионконтроллерс** prefab на панели Иерархия  .</span><span class="sxs-lookup"><span data-stu-id="78767-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="78767-210">**Мотионконтроллерс prefab**</span><span class="sxs-lookup"><span data-stu-id="78767-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="78767-211">**Мотионконтроллерс** prefab содержит скрипт **мотионконтроллервисуализер** , который предоставляет слоты для альтернативных моделей контроллера.</span><span class="sxs-lookup"><span data-stu-id="78767-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="78767-212">Если вы назначили собственные настраиваемые трехмерные модели, такие как рука или технологий, и установите флажок "всегда использовать альтернативную левую или правую модель", вы увидите их вместо модели по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="78767-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="78767-213">Мы будем использовать этот слот в главе 4 для замены модели контроллера на кисть.</span><span class="sxs-lookup"><span data-stu-id="78767-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="78767-215">**Водим**</span><span class="sxs-lookup"><span data-stu-id="78767-215">**Instructions**</span></span>
* <span data-ttu-id="78767-216">На панели **инспектора** дважды щелкните сценарий **мотионконтроллервисуализер** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78767-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="78767-217">**Сценарий Мотионконтроллервисуализер**</span><span class="sxs-lookup"><span data-stu-id="78767-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="78767-218">Классы **мотионконтроллервисуализер** и **мотионконтроллеринфо** предоставляют средства для доступа к & изменения моделей контроллеров по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="78767-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="78767-219">**Мотионконтроллервисуализер** подписывается на событие **интерактионсаурцедетектед** Unity и автоматически создает экземпляры моделей контроллеров при их обнаружении.</span><span class="sxs-lookup"><span data-stu-id="78767-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="78767-220">Модели контроллера доставляются в соответствии со [спецификацией глтф](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="78767-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="78767-221">Этот формат был создан для предоставления общего формата, в то же время улучшая процесс передачи и распаковки трехмерных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="78767-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="78767-222">В этом случае нам нужно извлечь и загрузить модели контроллера во время выполнения, так как мы хотим сделать работу пользователя максимально эффективной, а также не гарантируется, какая версия контроллеров движения может использоваться пользователем.</span><span class="sxs-lookup"><span data-stu-id="78767-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="78767-223">В этом курсе с помощью набора средств Mixed Reality используется версия [проекта Унитиглтф](https://github.com/KhronosGroup/UnityGLTF)группы кхронос.</span><span class="sxs-lookup"><span data-stu-id="78767-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="78767-224">После доставки контроллера скрипты могут использовать **мотионконтроллеринфо** для поиска преобразований для конкретных элементов контроллера, чтобы они могли правильно позиционироваться.</span><span class="sxs-lookup"><span data-stu-id="78767-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="78767-225">В следующей главе будет показано, как использовать эти скрипты для присоединения элементов пользовательского интерфейса к контроллерам.</span><span class="sxs-lookup"><span data-stu-id="78767-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="78767-226">*В некоторых сценариях вы найдете блоки кода с **#if! UNITY_EDITOR** или **UNITY_WSA**. Эти блоки кода выполняются только в среде выполнения UWP при развертывании в Windows. Это обусловлено тем, что набор интерфейсов API, используемых редактором Unity и средой выполнения приложений UWP, отличается.*</span><span class="sxs-lookup"><span data-stu-id="78767-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="78767-227">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="78767-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="78767-228">Вы увидите сцену с контроллерами движения на гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="78767-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="78767-229">Можно просмотреть подробные анимации для нажатий кнопок, движения аналогового стика и выделения сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="78767-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller визуализации по умолчанию](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="78767-231">Глава 2. присоединение элементов пользовательского интерфейса к контроллеру</span><span class="sxs-lookup"><span data-stu-id="78767-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="78767-232">Цели</span><span class="sxs-lookup"><span data-stu-id="78767-232">Objectives</span></span>

* <span data-ttu-id="78767-233">Сведения об элементах контроллеров Motion</span><span class="sxs-lookup"><span data-stu-id="78767-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="78767-234">Сведения о присоединении объектов к конкретным частям контроллеров</span><span class="sxs-lookup"><span data-stu-id="78767-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="78767-235">В этой главе вы узнаете, как добавлять элементы пользовательского интерфейса к контроллеру, к которому пользователь может легко получать доступ и работать в любое время.</span><span class="sxs-lookup"><span data-stu-id="78767-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="78767-236">Вы также узнаете, как добавить простой пользовательский интерфейс выбора цвета с помощью сенсорной панели ввода.</span><span class="sxs-lookup"><span data-stu-id="78767-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="78767-237">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-237">Instructions</span></span>

* <span data-ttu-id="78767-238">На панели **проект** найдите скрипт **мотионконтроллеринфо** .</span><span class="sxs-lookup"><span data-stu-id="78767-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="78767-239">В результатах поиска дважды щелкните **мотионконтроллеринфо** script, чтобы увидеть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78767-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="78767-240">**Сценарий Мотионконтроллеринфо**</span><span class="sxs-lookup"><span data-stu-id="78767-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="78767-241">Первым шагом является выбор элемента контроллера, к которому должен быть присоединен пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="78767-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="78767-242">Эти элементы определяются в **контроллерелементенум** в **MotionControllerInfo.CS**.</span><span class="sxs-lookup"><span data-stu-id="78767-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 Мотионконтроллерелементс](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="78767-244">**Домом**</span><span class="sxs-lookup"><span data-stu-id="78767-244">**Home**</span></span>
* <span data-ttu-id="78767-245">**Меню**</span><span class="sxs-lookup"><span data-stu-id="78767-245">**Menu**</span></span>
* <span data-ttu-id="78767-246">**Осознавать**</span><span class="sxs-lookup"><span data-stu-id="78767-246">**Grasp**</span></span>
* <span data-ttu-id="78767-247">**Джойстик**</span><span class="sxs-lookup"><span data-stu-id="78767-247">**Thumbstick**</span></span>
* <span data-ttu-id="78767-248">**Выбрать**</span><span class="sxs-lookup"><span data-stu-id="78767-248">**Select**</span></span>
* <span data-ttu-id="78767-249">**Сенсорная панель**</span><span class="sxs-lookup"><span data-stu-id="78767-249">**Touchpad**</span></span>
* <span data-ttu-id="78767-250">**Указание** элемента "элемент" — Этот пункт представляет собой Совет контроллера, указывающего направление вперед.</span><span class="sxs-lookup"><span data-stu-id="78767-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="78767-251">**Водим**</span><span class="sxs-lookup"><span data-stu-id="78767-251">**Instructions**</span></span>
* <span data-ttu-id="78767-252">На панели **проект** найдите скрипт **аттачтоконтроллер** .</span><span class="sxs-lookup"><span data-stu-id="78767-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="78767-253">В результатах поиска дважды щелкните **аттачтоконтроллер** script, чтобы увидеть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78767-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="78767-254">**Сценарий Аттачтоконтроллер**</span><span class="sxs-lookup"><span data-stu-id="78767-254">**AttachToController script**</span></span>

<span data-ttu-id="78767-255">Скрипт **аттачтоконтроллер** предоставляет простой способ присоединения любых объектов к указанному контроллеру правой или левой и элементу.</span><span class="sxs-lookup"><span data-stu-id="78767-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="78767-256">В **аттачелементтоконтроллер ()** ,</span><span class="sxs-lookup"><span data-stu-id="78767-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="78767-257">Проверьте правой или левой с помощью **мотионконтроллеринфо. правой или левой**</span><span class="sxs-lookup"><span data-stu-id="78767-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="78767-258">Получение конкретного элемента контроллера с помощью **мотионконтроллеринфо. трижетелемент ()**</span><span class="sxs-lookup"><span data-stu-id="78767-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="78767-259">После получения преобразования элемента из модели контроллера родительский объект наследуется от него и задается локальное расположение объекта, &ное вращение к нулю.</span><span class="sxs-lookup"><span data-stu-id="78767-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="78767-260">Самый простой способ использовать сценарий **аттачтоконтроллер** — это наследовать от него, как мы сделали в случае **колорпиккервхил.**</span><span class="sxs-lookup"><span data-stu-id="78767-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="78767-261">Просто переопределите функции **онаттачтоконтроллер** и **ондетатчфромконтроллер** , чтобы выполнить настройку или декомпозицию при обнаружении или отключении контроллера.</span><span class="sxs-lookup"><span data-stu-id="78767-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="78767-262">**Водим**</span><span class="sxs-lookup"><span data-stu-id="78767-262">**Instructions**</span></span>
* <span data-ttu-id="78767-263">На панели **проект** введите в поле поиска **колорпиккервхил**.</span><span class="sxs-lookup"><span data-stu-id="78767-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="78767-264">Его также можно найти в разделе Assets/Апппрефабс/.</span><span class="sxs-lookup"><span data-stu-id="78767-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="78767-265">Перетащите **колорпиккервхил** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-266">Щелкните **колорпиккервхил** prefab на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-267">На панели **инспектора** дважды щелкните сценарий **колорпиккервхил** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78767-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![Колорпиккервхил prefab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="78767-269">**Сценарий Колорпиккервхил**</span><span class="sxs-lookup"><span data-stu-id="78767-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="78767-270">Поскольку **колорпиккервхил** наследует **аттачтоконтроллер**, он отображает **правой или левой** и **элемент** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="78767-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="78767-271">Мы будем прикреплять пользовательский интерфейс к элементу сенсорной панели на левом контроллере.</span><span class="sxs-lookup"><span data-stu-id="78767-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Сценарий Колорпиккервхил](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="78767-273">**Колорпиккервхил** переопределяет **онаттачтоконтроллер** и **ондетатчфромконтроллер** для подписки на событие ввода, которое будет использоваться в следующей главе для выбора цвета с помощью ввода с сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="78767-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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
* <span data-ttu-id="78767-274">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="78767-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="78767-275">**Альтернативный способ присоединения объектов к контроллерам**</span><span class="sxs-lookup"><span data-stu-id="78767-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="78767-276">Рекомендуется, чтобы сценарии наследовались от **аттачтоконтроллер** и переопределяют **онаттачтоконтроллер**.</span><span class="sxs-lookup"><span data-stu-id="78767-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="78767-277">Однако это не всегда возможно.</span><span class="sxs-lookup"><span data-stu-id="78767-277">However, this may not always be possible.</span></span> <span data-ttu-id="78767-278">Альтернативой является использование его в качестве отдельного компонента.</span><span class="sxs-lookup"><span data-stu-id="78767-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="78767-279">Это может быть полезно, если необходимо подключить существующий prefab к контроллеру без рефакторинга скриптов.</span><span class="sxs-lookup"><span data-stu-id="78767-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="78767-280">Просто попросите своего класса присвоить параметру Attach значение true, прежде чем выполнять настройку.</span><span class="sxs-lookup"><span data-stu-id="78767-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="78767-281">Самый простой способ сделать это — использовать соподпрограмму для "Start."</span><span class="sxs-lookup"><span data-stu-id="78767-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="78767-282">Глава 3. Работа с вводом сенсорной панели</span><span class="sxs-lookup"><span data-stu-id="78767-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="78767-283">Цели</span><span class="sxs-lookup"><span data-stu-id="78767-283">Objectives</span></span>

* <span data-ttu-id="78767-284">Узнайте, как получить события входных данных сенсорной панели</span><span class="sxs-lookup"><span data-stu-id="78767-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="78767-285">Узнайте, как использовать сведения о положении оси сенсорной панели для работы с приложением</span><span class="sxs-lookup"><span data-stu-id="78767-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="78767-286">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-286">Instructions</span></span>

* <span data-ttu-id="78767-287">На панели **Иерархия** щелкните **колорпиккервхил** .</span><span class="sxs-lookup"><span data-stu-id="78767-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="78767-288">На панели **инспектора** в разделе **Аниматиор**дважды щелкните **колорпиккервхилконтроллер** .</span><span class="sxs-lookup"><span data-stu-id="78767-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="78767-289">Вы сможете увидеть открытую вкладку **аниматор**</span><span class="sxs-lookup"><span data-stu-id="78767-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="78767-290">**Отображение или скрытие пользовательского интерфейса с помощью контроллера анимации Unity**</span><span class="sxs-lookup"><span data-stu-id="78767-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="78767-291">Чтобы показать или скрыть пользовательский интерфейс **колорпиккервхил** с анимацией, мы используем [систему анимации Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="78767-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="78767-292">Установка значения true или false для свойства **Visible** объекта **колорпиккервхил**позволяет **Отображать** и **скрывать** триггеры анимации.</span><span class="sxs-lookup"><span data-stu-id="78767-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="78767-293">Параметры **отображения** и **скрытия** определяются в контроллере анимации **колорпиккервхилконтроллер** .</span><span class="sxs-lookup"><span data-stu-id="78767-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Контроллер анимации Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="78767-295">**Водим**</span><span class="sxs-lookup"><span data-stu-id="78767-295">**Instructions**</span></span>
* <span data-ttu-id="78767-296">На панели **Иерархия** выберите **колорпиккервхил** prefab.</span><span class="sxs-lookup"><span data-stu-id="78767-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="78767-297">На панели **инспектора** дважды щелкните сценарий **колорпиккервхил** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78767-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="78767-298">**Сценарий Колорпиккервхил**</span><span class="sxs-lookup"><span data-stu-id="78767-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="78767-299">**Колорпиккервхил** подписывается на событие **интерактионсаурцеупдатед** Unity для прослушивания событий сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="78767-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="78767-300">В **интерактионсаурцеупдатед ()** сценарий сначала проверяет, чтобы убедиться, что он:</span><span class="sxs-lookup"><span data-stu-id="78767-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="78767-301">фактически является событием сенсорной панели (obj. State. **Таучпадтаучед**)</span><span class="sxs-lookup"><span data-stu-id="78767-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="78767-302">исходит от левого контроллера (obj. State. Source. **правой или левой**)</span><span class="sxs-lookup"><span data-stu-id="78767-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="78767-303">Если оба значения имеют значение true, расположение сенсорной панели (obj. State. **Таучпадпоситион**) назначается **селекторпоситион**.</span><span class="sxs-lookup"><span data-stu-id="78767-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="78767-304">В **Update ()** , основанном  на видимом свойстве, он запускает отображение и скрытие триггеров анимации в компоненте аниматор средства выбора цвета.</span><span class="sxs-lookup"><span data-stu-id="78767-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="78767-305">В **Update ()** **селекторпоситион** используется для приведения луча по отношению к конфликту сетчатого цветового круга, который возвращает UV-расположение.</span><span class="sxs-lookup"><span data-stu-id="78767-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="78767-306">Эта положение затем можно использовать для поиска координат пиксела и цвета текстуры цветового круга.</span><span class="sxs-lookup"><span data-stu-id="78767-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="78767-307">Это значение доступно для других скриптов через свойство **селектедколор** .</span><span class="sxs-lookup"><span data-stu-id="78767-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="78767-309">Глава 4. Переопределение модели контроллера</span><span class="sxs-lookup"><span data-stu-id="78767-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="78767-310">Цели</span><span class="sxs-lookup"><span data-stu-id="78767-310">Objectives</span></span>

* <span data-ttu-id="78767-311">Узнайте, как переопределить модель контроллера с помощью настраиваемой трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="78767-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="78767-313">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-313">Instructions</span></span>

* <span data-ttu-id="78767-314">На панели Иерархия  щелкните **мотионконтроллерс** .</span><span class="sxs-lookup"><span data-stu-id="78767-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-315">Щелкните окружность справа от поля **альтернативный контроллер справа** .</span><span class="sxs-lookup"><span data-stu-id="78767-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="78767-316">Введите **"брушконтроллер**" и выберите prefab из результата.</span><span class="sxs-lookup"><span data-stu-id="78767-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="78767-317">Его можно найти в разделе Assets/Апппрефабс/**брушконтроллер**.</span><span class="sxs-lookup"><span data-stu-id="78767-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="78767-318">Проверка **всегда использовать другую правильную модель**</span><span class="sxs-lookup"><span data-stu-id="78767-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="78767-320">**Брушконтроллер** prefab не обязательно включать в панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="78767-321">Однако, чтобы извлечь его дочерние компоненты:</span><span class="sxs-lookup"><span data-stu-id="78767-321">However, to check out its child components:</span></span>
* <span data-ttu-id="78767-322">На панели **проект** введите **Брушконтроллер** и перетащите **брушконтроллер** prefab на панель Иерархия.</span><span class="sxs-lookup"><span data-stu-id="78767-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="78767-324">Вы найдете компонент **Tip** в **брушконтроллер**.</span><span class="sxs-lookup"><span data-stu-id="78767-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="78767-325">Мы будем использовать его преобразование для запуска и завершения рисования линий.</span><span class="sxs-lookup"><span data-stu-id="78767-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="78767-326">Удалите **брушконтроллер** с панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-327">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="78767-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="78767-328">Вы сможете увидеть, что модель кистей заменила правый контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="78767-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="78767-329">Глава 5. Рисование с помощью выбора входных данных</span><span class="sxs-lookup"><span data-stu-id="78767-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="78767-330">Цели</span><span class="sxs-lookup"><span data-stu-id="78767-330">Objectives</span></span>

* <span data-ttu-id="78767-331">Узнайте, как использовать событие кнопки "выбрать" для запуска и завершения рисования линий</span><span class="sxs-lookup"><span data-stu-id="78767-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="78767-332">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-332">Instructions</span></span>

* <span data-ttu-id="78767-333">Выполните поиск по запросу **брушконтроллер** prefab на панели **проекта** .</span><span class="sxs-lookup"><span data-stu-id="78767-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="78767-334">На панели **инспектора** дважды щелкните сценарий **брушконтроллер** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78767-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="78767-335">**Сценарий Брушконтроллер**</span><span class="sxs-lookup"><span data-stu-id="78767-335">**BrushController script**</span></span>

<span data-ttu-id="78767-336">**Брушконтроллер** подписывается на события **Интерактионсаурцепрессед** и **интерактионсаурцерелеасед** интерактионманажер.</span><span class="sxs-lookup"><span data-stu-id="78767-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="78767-337">При запуске события **интерактионсаурцепрессед** свойство **Draw** кисти устанавливается в значение true. При запуске события **интерактионсаурцерелеасед** свойство **Draw** кисти устанавливается в значение false.</span><span class="sxs-lookup"><span data-stu-id="78767-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="78767-338">Если параметр **Draw** имеет значение true, кисть создаст точки в экземпляре Unity **линерендерер**.</span><span class="sxs-lookup"><span data-stu-id="78767-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="78767-339">Ссылка на этот prefab хранится в поле **Stroke prefab** кисти.</span><span class="sxs-lookup"><span data-stu-id="78767-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="78767-340">Чтобы использовать текущий выбранный цвет в пользовательском интерфейсе колесика выбора цвета, **брушконтроллер** должен иметь ссылку на объект **колорпиккервхил** .</span><span class="sxs-lookup"><span data-stu-id="78767-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="78767-341">Так как экземпляр **брушконтроллер** prefab создается во время выполнения в качестве контроллера замены, все ссылки на объекты в сцене должны быть заданы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="78767-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="78767-342">В этом случае мы используем **GameObject. финдобжектофтипе** для размещения **колорпиккервхил**:</span><span class="sxs-lookup"><span data-stu-id="78767-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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
* <span data-ttu-id="78767-343">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="78767-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="78767-344">Вы сможете рисовать линии и рисовать с помощью кнопки выбрать в правом контроллере.</span><span class="sxs-lookup"><span data-stu-id="78767-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="78767-345">Глава 6 — порождение объекта с помощью выбора входных данных</span><span class="sxs-lookup"><span data-stu-id="78767-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="78767-346">Цели</span><span class="sxs-lookup"><span data-stu-id="78767-346">Objectives</span></span>

* <span data-ttu-id="78767-347">Узнайте, как использовать кнопки выбора и изучения событий ввода</span><span class="sxs-lookup"><span data-stu-id="78767-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="78767-348">Узнайте, как создавать экземпляры объектов</span><span class="sxs-lookup"><span data-stu-id="78767-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="78767-349">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-349">Instructions</span></span>

* <span data-ttu-id="78767-350">На панели **проект** введите **обжектспавнер** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="78767-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="78767-351">Его также можно найти в разделе Assets/Апппрефабс/</span><span class="sxs-lookup"><span data-stu-id="78767-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="78767-352">Перетащите **обжектспавнер** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-353">На панели Иерархия  щелкните **обжектспавнер** .</span><span class="sxs-lookup"><span data-stu-id="78767-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-354">**Обжектспавнер** имеет поле с именем **источник цвета**.</span><span class="sxs-lookup"><span data-stu-id="78767-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="78767-355">На панели **Иерархия** перетащите ссылку **колорпиккервхил** в это поле.</span><span class="sxs-lookup"><span data-stu-id="78767-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![Инспектор порождаемых объектов](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="78767-357">Щелкните **обжектспавнер** prefab на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-358">На панели **инспектора** дважды щелкните сценарий **обжектспавнер** , чтобы просмотреть код в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78767-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="78767-359">**Сценарий Обжектспавнер**</span><span class="sxs-lookup"><span data-stu-id="78767-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="78767-360">**Обжектспавнер** создает в пространстве экземпляры копий примитивной сетки (куб, шар, цилиндр).</span><span class="sxs-lookup"><span data-stu-id="78767-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="78767-361">При обнаружении **интерактионсаурцепрессед** проверяет правой или левой и, если это событие **интерактионсаурцепресстипе.** поняли или **интерактионсаурцепресстипе. Select** .</span><span class="sxs-lookup"><span data-stu-id="78767-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="78767-362">Для события  с учетом усвоения он увеличивает индекс текущего типа сетки (шар, куб, цилиндр).</span><span class="sxs-lookup"><span data-stu-id="78767-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="78767-363">Для события **SELECT** в **спавнобжект ()** создается экземпляр нового объекта, не являющийся родительским и освобожденный в мире.</span><span class="sxs-lookup"><span data-stu-id="78767-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

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

<span data-ttu-id="78767-364">**Обжектспавнер** использует **колорпиккервхил** для установки цвета материала экранного объекта.</span><span class="sxs-lookup"><span data-stu-id="78767-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="78767-365">Порожденным объектам присваивается экземпляр этого материала, чтобы они сохраняли свой цвет.</span><span class="sxs-lookup"><span data-stu-id="78767-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="78767-366">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="78767-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="78767-367">Вы сможете изменить объекты с помощью кнопки "располагаться" и порождением объектов с помощью кнопки "выбрать".</span><span class="sxs-lookup"><span data-stu-id="78767-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="78767-368">Создание и развертывание приложения на портале смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="78767-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="78767-369">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="78767-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="78767-370">Нажмите кнопку **Добавить открытые сцены** , чтобы добавить текущую сцену в **сцена в сборке**.</span><span class="sxs-lookup"><span data-stu-id="78767-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="78767-371">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="78767-371">Click **Build**.</span></span>
* <span data-ttu-id="78767-372">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="78767-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="78767-373">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="78767-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="78767-374">Щелкните элемент **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="78767-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="78767-375">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="78767-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="78767-376">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="78767-376">Open the **App** folder.</span></span>
* <span data-ttu-id="78767-377">Дважды щелкните файл решения Visual Studio **йоурсцененаме. sln** .</span><span class="sxs-lookup"><span data-stu-id="78767-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="78767-378">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.</span><span class="sxs-lookup"><span data-stu-id="78767-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="78767-379">Щелкните стрелку раскрывающегося списка рядом с кнопкой устройство и выберите **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="78767-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="78767-380">Щелкните **Отладка-> запуск без отладки** в меню или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="78767-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="78767-381">Теперь приложение создается и устанавливается на портале смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="78767-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="78767-382">Вы можете запустить его снова через меню "Пуск" на портале Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="78767-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="78767-383">Дополнительные инструменты проектирования и кисти с радиальным макетом</span><span class="sxs-lookup"><span data-stu-id="78767-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="78767-385">В этой главе вы узнаете, как заменить модель контроллера движения по умолчанию на коллекцию настраиваемых инструментов кисти.</span><span class="sxs-lookup"><span data-stu-id="78767-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="78767-386">Для справки можно найти завершенную сцену **MixedReality213Advanced** в папке **сцены** .</span><span class="sxs-lookup"><span data-stu-id="78767-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="78767-387">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-387">Instructions</span></span>

* <span data-ttu-id="78767-388">На панели **проект** введите **брушселектор** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="78767-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="78767-389">Его также можно найти в разделе Assets/Апппрефабс/</span><span class="sxs-lookup"><span data-stu-id="78767-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="78767-390">Перетащите **брушселектор** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-391">Для организации создайте пустой GameObject с именем **кисти** .</span><span class="sxs-lookup"><span data-stu-id="78767-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="78767-392">Перетащите следующие Prefabs с панели **проект** на **кисти** .</span><span class="sxs-lookup"><span data-stu-id="78767-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="78767-393">Активы/Апппрефабс/**брушфат**</span><span class="sxs-lookup"><span data-stu-id="78767-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="78767-394">Активы/Апппрефабс/**брушсин**</span><span class="sxs-lookup"><span data-stu-id="78767-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="78767-395">Активы/Апппрефабс/**резинка**</span><span class="sxs-lookup"><span data-stu-id="78767-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="78767-396">Активы/Апппрефабс/**маркерфат**</span><span class="sxs-lookup"><span data-stu-id="78767-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="78767-397">Активы/Апппрефабс/**маркерсин**</span><span class="sxs-lookup"><span data-stu-id="78767-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="78767-398">Активы/Апппрефабс/**карандаш**</span><span class="sxs-lookup"><span data-stu-id="78767-398">Assets/AppPrefabs/**Pencil**</span></span>

![Кисти](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="78767-400">Щелкните **мотионконтроллерс** prefab на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="78767-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="78767-401">На панели **инспектора** снимите флажок **всегда использовать другую правильную модель** на **визуализаторе контроллера движения** .</span><span class="sxs-lookup"><span data-stu-id="78767-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="78767-402">На панели **Иерархия** щелкните **брушселектор** .</span><span class="sxs-lookup"><span data-stu-id="78767-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="78767-403">**Брушселектор** содержит поле с именем **ColorPicker** .</span><span class="sxs-lookup"><span data-stu-id="78767-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="78767-404">На панели  «иерархия» перетащите поле **колорпиккервхил** в **ColorPicker** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="78767-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![Назначение Колорпиккервхил селектору кисти](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="78767-406">На панели **Иерархия** в разделе **брушселектор** prefab выберите объект **меню** .</span><span class="sxs-lookup"><span data-stu-id="78767-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="78767-407">На панели **инспектора** в разделе компонент **линеобжектколлектион** откройте раскрывающийся список массив **объектов** .</span><span class="sxs-lookup"><span data-stu-id="78767-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="78767-408">Вы увидите 6 пустых слотов.</span><span class="sxs-lookup"><span data-stu-id="78767-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="78767-409">На панели **Иерархия** перетащите все Prefabs, наявляющиеся от кистей,  GameObject в эти слоты в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="78767-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="78767-410">(Убедитесь, что вы перетаскивайте Prefabs из сцены, а не из Prefabs в папке проекта.)</span><span class="sxs-lookup"><span data-stu-id="78767-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Селектор кисти](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="78767-412">**Брушселектор prefab**</span><span class="sxs-lookup"><span data-stu-id="78767-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="78767-413">Поскольку **брушселектор** наследует **аттачтоконтроллер**, он отображает параметры **правой или левой** и **element** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="78767-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="78767-414">Мы выбрали **право** и  назначите элемент «рука», чтобы присоединить средства кистей к правому контроллеру с прямым направлением.</span><span class="sxs-lookup"><span data-stu-id="78767-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="78767-415">**Брушселектор** использует две служебные программы:</span><span class="sxs-lookup"><span data-stu-id="78767-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="78767-416">**Эллипс**: используется для создания точек в пространстве вдоль фигуры эллипса.</span><span class="sxs-lookup"><span data-stu-id="78767-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="78767-417">**Линеобжектколлектион**: распределяет объекты с помощью точек, созданных любым классом линии (например, эллипсом).</span><span class="sxs-lookup"><span data-stu-id="78767-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="78767-418">Именно так мы будем использовать для размещения наших кистей вдоль эллипса.</span><span class="sxs-lookup"><span data-stu-id="78767-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="78767-419">В сочетании эти служебные программы можно использовать для создания радиального меню.</span><span class="sxs-lookup"><span data-stu-id="78767-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="78767-420">**Сценарий Линеобжектколлектион**</span><span class="sxs-lookup"><span data-stu-id="78767-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="78767-421">**Линеобжектколлектион** имеет элементы управления размером, расположением и поворотом объектов, распределенных вдоль линии.</span><span class="sxs-lookup"><span data-stu-id="78767-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="78767-422">Это полезно для создания радиальных меню, таких как селектор кисти.</span><span class="sxs-lookup"><span data-stu-id="78767-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="78767-423">Чтобы создать внешний вид кистей, которые не масштабируются по мере приближения к центру выбранной позиции, **обжектскале** кривая в центре и конусы на краях.</span><span class="sxs-lookup"><span data-stu-id="78767-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="78767-424">**Сценарий Брушселектор**</span><span class="sxs-lookup"><span data-stu-id="78767-424">**BrushSelector script**</span></span>

<span data-ttu-id="78767-425">В случае с **брушселектор**мы решили использовать метод анимации.</span><span class="sxs-lookup"><span data-stu-id="78767-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="78767-426">Во первых, модели кистей распределяются на эллипсе с помощью скрипта **линеобжектколлектион** .</span><span class="sxs-lookup"><span data-stu-id="78767-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="78767-427">Затем каждая кисть несет ответственность за поддержание своего расположения в руки пользователя на основе его значения **DisplayMode** , которое изменяется в зависимости от выбора.</span><span class="sxs-lookup"><span data-stu-id="78767-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="78767-428">Мы выбрали подход к методу из-за того, что высокая вероятность того, что переходы по положению кисти прерываются, так как пользователь выбирает кисти.</span><span class="sxs-lookup"><span data-stu-id="78767-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="78767-429">Анимация меканим может правильно обрабатывать прерывания, но она, как правило, сложнее, чем простая операция Лерп.</span><span class="sxs-lookup"><span data-stu-id="78767-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="78767-430">**Брушселектор** использует сочетание обоих типов.</span><span class="sxs-lookup"><span data-stu-id="78767-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="78767-431">При обнаружении ввода сенсорной панели Параметры кисти становятся видимыми и масштабируются вдоль радиального меню.</span><span class="sxs-lookup"><span data-stu-id="78767-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="78767-432">По истечении времени ожидания (которое указывает, что пользователь сделал выбор) параметры кисти снова масштабируются, при этом остается только выбранная кисть.</span><span class="sxs-lookup"><span data-stu-id="78767-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="78767-433">**Визуализация ввода сенсорной панели**</span><span class="sxs-lookup"><span data-stu-id="78767-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="78767-434">Даже в тех случаях, когда модель контроллера была полностью заменена, может быть полезно отобразить входные данные исходной модели.</span><span class="sxs-lookup"><span data-stu-id="78767-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="78767-435">Это позволяет заземление действий пользователя в реальности.</span><span class="sxs-lookup"><span data-stu-id="78767-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="78767-436">Для **брушселектор** мы решили, чтобы сенсорная панель ненадолго отображалась при получении входных данных.</span><span class="sxs-lookup"><span data-stu-id="78767-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="78767-437">Это было сделано путем извлечения элемента сенсорной панели из контроллера, замены его материала на пользовательский материал, а затем применения градиента к цвету материала на основе последнего полученного ввода сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="78767-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="78767-438">**Выбор инструмента "кисть" с входными данными сенсорной панели**</span><span class="sxs-lookup"><span data-stu-id="78767-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="78767-439">Когда селектор кисти обнаруживает нажатую клавишу сенсорного ввода, он проверяет расположение входных данных, чтобы определить, было ли оно равно левому или правому.</span><span class="sxs-lookup"><span data-stu-id="78767-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="78767-440">**Толщина штриха с помощью Селектпресседамаунт**</span><span class="sxs-lookup"><span data-stu-id="78767-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="78767-441">Вместо события **интерактионсаурцепресстипе. Select** в **интерактионсаурцепрессед ()** можно получить значение аналогового значения выделенной суммы через **селектпресседамаунт**.</span><span class="sxs-lookup"><span data-stu-id="78767-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="78767-442">Это значение можно получить в **интерактионсаурцеупдатед ()** .</span><span class="sxs-lookup"><span data-stu-id="78767-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="78767-443">**Сценарий ластика**</span><span class="sxs-lookup"><span data-stu-id="78767-443">**Eraser script**</span></span>

<span data-ttu-id="78767-444">**Ластик** — это специальный тип кисти, переопределяющий функцию **дравовертиме ()** базовой **кисти**.</span><span class="sxs-lookup"><span data-stu-id="78767-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="78767-445">Когда Draw имеет значение true, резинка проверяет, пересекается ли его Совет с любыми существующими мазками кистью.</span><span class="sxs-lookup"><span data-stu-id="78767-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="78767-446">Если это так, они добавляются в очередь для уменьшения и удаления.</span><span class="sxs-lookup"><span data-stu-id="78767-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="78767-447">Расширенный дизайн — локальная и локомотион</span><span class="sxs-lookup"><span data-stu-id="78767-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="78767-448">Если вы хотите разрешить пользователю перемещаться по сцене с помощью многопортового стика, используйте **микседреалитикамерапарент** вместо **микседреалитикамера**.</span><span class="sxs-lookup"><span data-stu-id="78767-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="78767-449">Также необходимо добавить **InputManager** и **дефаулткусор**.</span><span class="sxs-lookup"><span data-stu-id="78767-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="78767-450">Так **как микседреалитикамерапарент** уже включает **мотионконтроллерс** и **границу** как дочерние компоненты, следует удалить существующие prefab **мотионконтроллерс** и **среды** .</span><span class="sxs-lookup"><span data-stu-id="78767-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="78767-451">Инструкция</span><span class="sxs-lookup"><span data-stu-id="78767-451">Instructions</span></span>

* <span data-ttu-id="78767-452">На панели **Иерархия** удалите **микседреалитикамера**, **Environment** и **мотионконтроллерс** .</span><span class="sxs-lookup"><span data-stu-id="78767-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="78767-453">На **панели проект**найдите и перетащите следующий Prefabs на панель Иерархия:</span><span class="sxs-lookup"><span data-stu-id="78767-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="78767-454">Assets/Апппрефабс/input/Prefabs/**микседреалитикамерапарент**</span><span class="sxs-lookup"><span data-stu-id="78767-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="78767-455">Assets/Апппрефабс/input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="78767-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="78767-456">Assets/Апппрефабс/input/Prefabs/Cursor/**дефаулткурсор**</span><span class="sxs-lookup"><span data-stu-id="78767-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Родитель камеры смешанной реальности](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="78767-458">На панели **Иерархия** щелкните **Диспетчер входов** .</span><span class="sxs-lookup"><span data-stu-id="78767-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="78767-459">На панели **инспектора** прокрутите вниз до раздела **простой единичный селектор указателя** .</span><span class="sxs-lookup"><span data-stu-id="78767-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="78767-460">На панели **Иерархия** перетащите **дефаулткурсор** INTO в поле **курсора** .</span><span class="sxs-lookup"><span data-stu-id="78767-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![Назначение Дефаулткурсор](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="78767-462">**Сохраните** сцену и нажмите кнопку **воспроизвести** .</span><span class="sxs-lookup"><span data-stu-id="78767-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="78767-463">Вы сможете использовать аналоговый стик для поворота влево, вправо или телепортироваться.</span><span class="sxs-lookup"><span data-stu-id="78767-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="78767-464">Конец</span><span class="sxs-lookup"><span data-stu-id="78767-464">The end</span></span>

<span data-ttu-id="78767-465">И это окончание этого руководства.</span><span class="sxs-lookup"><span data-stu-id="78767-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="78767-466">Вы узнали:</span><span class="sxs-lookup"><span data-stu-id="78767-466">You learned:</span></span>
* <span data-ttu-id="78767-467">Как работать с моделями контроллера движения в игровом режиме Unity и в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="78767-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="78767-468">Использование различных типов событий кнопок и их приложений.</span><span class="sxs-lookup"><span data-stu-id="78767-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="78767-469">Как наложение элементов пользовательского интерфейса поверх контроллера или его полная настройка.</span><span class="sxs-lookup"><span data-stu-id="78767-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="78767-470">Теперь вы готовы приступить к созданию своего собственного иммерсивного интерфейса с помощью контроллеров движения!</span><span class="sxs-lookup"><span data-stu-id="78767-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="78767-471">Завершенные сцены</span><span class="sxs-lookup"><span data-stu-id="78767-471">Completed scenes</span></span>

* <span data-ttu-id="78767-472">На панели **проекта** Unity щелкните папку " **сцены** ".</span><span class="sxs-lookup"><span data-stu-id="78767-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="78767-473">Вы обнаружите два сцеенсов Unity и **MixedReality213** и **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="78767-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="78767-474">**MixedReality213**: Завершенная сцена с одной кистью</span><span class="sxs-lookup"><span data-stu-id="78767-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="78767-475">**MixedReality213Advanced**: Завершенная сцена с несколькими кистями с примером объема нажатия кнопки "выбрать"</span><span class="sxs-lookup"><span data-stu-id="78767-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="78767-476">См. также</span><span class="sxs-lookup"><span data-stu-id="78767-476">See also</span></span>

* [<span data-ttu-id="78767-477">Файлы проекта с вводом в MR 213</span><span class="sxs-lookup"><span data-stu-id="78767-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="78767-478">Набор средств для смешанной реальности — тестовая сцена контроллера движения</span><span class="sxs-lookup"><span data-stu-id="78767-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="78767-479">Набор средств для смешанной реальности — механики захвата</span><span class="sxs-lookup"><span data-stu-id="78767-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="78767-480">Рекомендации по разработке для контроллера движения</span><span class="sxs-lookup"><span data-stu-id="78767-480">Motion controller development guidelines</span></span>](motion-controllers.md)
