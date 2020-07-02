---
title: 2. Инициализация проекта и первое приложение
description: Часть 2 (из 6) серии руководств по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств UX из набора средств для смешанной реальности
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, средства разработки пользовательского интерфейса, средства UX, документация
ms.openlocfilehash: 150fee721bb9cd72d287737aca4262bd87dccba8
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345734"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="c5ec4-104">2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="c5ec4-104">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="c5ec4-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="c5ec4-105">Overview</span></span>

<span data-ttu-id="c5ec4-106">В этом руководстве мы начнем работу с создания приложения Unreal для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-106">In this first tutorial, you'll get started with a new Unreal application for HoloLens 2.</span></span> <span data-ttu-id="c5ec4-107">Нам предстоит добавить подключаемый модуль HoloLens, создать уровень, задать его освещение, а также добавить на него шахматную доску и фигуру.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-107">This is going to include adding the HoloLens plugin, creating and lighting a level, and populating it with a game board and chess piece.</span></span> <span data-ttu-id="c5ec4-108">Для этого мы воспользуемся готовыми ресурсами для трехмерной шахматной фигуры и материалов, так что можно не беспокоиться — создавать модели с нуля не придется.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-108">You'll be using pre-made assets for the 3D chess piece and object materials, so don't worry about modeling anything from scratch.</span></span> <span data-ttu-id="c5ec4-109">Когда вы выполните все описанное в руководстве, у вас будет пустой холст, готовый для размещения объектов смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-109">By the end of this tutorial you'll have a blank canvas that's ready for mixed reality.</span></span>

<span data-ttu-id="c5ec4-110">Прежде чем продолжать, убедитесь, что у вас есть все необходимое из списка на странице [Начало работы](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-110">Before continuing, make sure you have all the prerequisites from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="c5ec4-111">Задачи</span><span class="sxs-lookup"><span data-stu-id="c5ec4-111">Objectives</span></span>
* <span data-ttu-id="c5ec4-112">Настройка проекта Unreal с целью разработки для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-112">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="c5ec4-113">Импорт ресурсов и настройка сцены.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-113">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="c5ec4-114">Создание субъектов и событий уровня скрипта.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-114">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="c5ec4-115">Создание проекта Unreal.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-115">Creating a new Unreal project</span></span>
<span data-ttu-id="c5ec4-116">Первое, что вам понадобится для работы — это проект.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="c5ec4-117">Если вы впервые создаете приложение Unreal для HoloLens, вам потребуется [скачать вспомогательные файлы](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) из Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-117">If this is your first time creating an Unreal app for HoloLens, you'll need to [download supporting files](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) from the Epic Launcher.</span></span>

1. <span data-ttu-id="c5ec4-118">Запуск Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="c5ec4-118">Launch Unreal Engine</span></span>

2. <span data-ttu-id="c5ec4-119">В разделе **New Project Categories** (Категории для нового проекта) выберите **Games** (Игры) и щелкните **Next** (Далее).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-119">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Выбор шаблона проекта Games (Игры)](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="c5ec4-121">Выберите пустой (**Blank**) шаблон и нажмите кнопку **Next** (Далее).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-121">Select the **Blank** Template and click **Next**.</span></span> 

![Выбор пустого шаблона](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="c5ec4-123">В разделе **Project Settings** (Параметры проекта) выберите пункты **C++** , **Scalable 3D or 2D** (Масштабируемый трехмерный или двухмерный), Mobile / Tablet (Мобильное устройство или планшет) и **No Starter Content** (Без начального содержимого).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-123">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**.</span></span> 
    * <span data-ttu-id="c5ec4-124">Выберите папку для сохранения и нажмите кнопку **Create Project** (Создать проект).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-124">Choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="c5ec4-125">Выберите проект C++, а не проект шаблона, чтобы создать подключаемый модуль средств UX, который вы настроите позже (в разделе 4).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-125">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Начальные параметры проекта](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="c5ec4-127">Проект должен автоматически открыться в редакторе Unreal, и тогда можно перейти к следующему этапу.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-127">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="c5ec4-128">Включение необходимых подключаемых модулей</span><span class="sxs-lookup"><span data-stu-id="c5ec4-128">Enabling required plugins</span></span>
<span data-ttu-id="c5ec4-129">Прежде чем добавлять объекты в сцену, необходимо включить два подключаемых модуля.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-129">Before you start adding objects to the scene you'll need to enable two plugins.</span></span>

1. <span data-ttu-id="c5ec4-130">Выберите **Edit > Plugins** (Правка > Подключаемые модули) и выберите вариант **Augmented Reality** (Дополненная реальность) в списке встроенных категорий.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-130">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="c5ec4-131">Прокрутите список до пункта **HoloLens** и установите флажок **Enabled** (Включено).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-131">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Включение подключаемых модулей HoloLens](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="c5ec4-133">Выберите вариант **Virtual Reality** (Виртуальная реальность) в списке встроенных категорий.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-133">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="c5ec4-134">Прокрутите список до пункта **Microsoft Windows Mixed Reality**, установите для него флажок **Enabled** (Включено) и перезапустите редактор.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-134">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Включение подключаемого модуля Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="c5ec4-136">Оба подключаемых модуля обязательны при разработке для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-136">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="c5ec4-137">Теперь у вас есть пустой уровень, который можно чем-нибудь заполнить.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-137">With that done your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="c5ec4-138">Создание уровня</span><span class="sxs-lookup"><span data-stu-id="c5ec4-138">Creating a level</span></span>
<span data-ttu-id="c5ec4-139">Следующая задача — создать простую игровую обстановку с начальной точкой и кубом, задающим начало отсчета и масштаб.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-139">Your next task is to create a simple player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="c5ec4-140">Выберите **File > New Level** (Файл > Создать уровень), а затем **Empty Level** (Пустой уровень).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-140">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="c5ec4-141">В окне просмотра должна отображаться пустая сцена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-141">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="c5ec4-142">На вкладке **Modes** (Режимы) выберите **Basic** (Основные) и перетащите в сцену элемент **PlayerStart**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-142">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="c5ec4-143">На вкладке **Details** (Сведения) установите для параметра **Location** (Расположение) значения **X = 0**, **Y = 0** и **Z = 0**, чтобы после запуска приложения пользователь начинал игру в центре сцены.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-143">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab. This sets the user at the center of the scene when the app starts up.</span></span>

![Окно просмотра с элементом PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="c5ec4-145">Перетащите в сцену элемент **Cube** (Куб) с вкладки **Basic** (Основные).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-145">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="c5ec4-146">Установите для параметра **Location** (Расположение) значения **X = 50**, **Y = 0** и **Z = 0**,</span><span class="sxs-lookup"><span data-stu-id="c5ec4-146">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="c5ec4-147">чтобы в начале игры куб располагался в 50 см от игрока.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-147">This positions the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="c5ec4-148">Установите для параметра **Scale** (Масштаб) значения **X = 0,2**, **Y = 0,2** и **Z = 0,2**, чтобы уменьшить размеры куба.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-148">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="c5ec4-149">Куб не будет виден, пока в сцену не добавлен источник света. Это и будет нашей последней задачей перед тем, как протестировать сцену.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-149">You won’t be able to see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="c5ec4-150">Перейдите на вкладку **Lights** (Свет) на панели **Modes** (Режимы) и перетащите в сцену элемент **Directional Light** (Направленный свет),</span><span class="sxs-lookup"><span data-stu-id="c5ec4-150">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="c5ec4-151">разместив его над элементом **PlayerStart**, чтобы он был виден.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-151">Position the light above **PlayerStart** so you can see it.</span></span>

![Окно просмотра после добавления света](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="c5ec4-153">Выберите **File > Save Current** (Файл > Сохранить текущий), присвойте уровню имя **Main** (Главный) и нажмите кнопку **Save** (Сохранить).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-153">Go to **File > Save Current**, name your level **Main**, and click **Save**.</span></span> 

<span data-ttu-id="c5ec4-154">Сцена готова. Чтобы увидеть куб в действии, нажмите кнопку **Play** (Воспроизвести) на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-154">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="c5ec4-155">Когда будете готовы действовать дальше, нажмите клавишу **ESC**, чтобы остановить приложение.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-155">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Куб в окне просмотра](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="c5ec4-157">В настроенную сцену можно теперь добавить шахматную доску и фигуру, чтобы получилась законченная пространственная среда приложения.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-157">Now that the scene is setup, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="c5ec4-158">Импорт ресурсов</span><span class="sxs-lookup"><span data-stu-id="c5ec4-158">Importing assets</span></span>
<span data-ttu-id="c5ec4-159">Пустая сцена выглядит скучновато, но мы сейчас это исправим, импортировав в проект готовые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-159">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="c5ec4-160">Скачайте с [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) и распакуйте папку с ресурсами.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-160">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder.</span></span>

2. <span data-ttu-id="c5ec4-161">В обозревателе содержимого (**Content Browser**) выберите **Add New > New Folder** (Добавить > Папка) и присвойте новой папке имя **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-161">Click **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="c5ec4-162">Дважды щелкните созданную только что папку — в нее мы будем импортировать трехмерные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-162">Double-click the new folder - this is where you'll import the 3D assets.</span></span>

![Отображение и скрытие панели источников](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="c5ec4-164">В обозревателе содержимого (**Content Browser**) нажмите кнопку **Import** (Импорт), выберите все элементы из папки с распакованными ресурсами и нажмите кнопку **Open** (Открыть).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-164">Click **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="c5ec4-165">Папка содержит файлы трехмерных сеток шахматной доски и фигур в формате FBX, а также файлы текстурных карт в формате TGA, на основе которых мы создадим материалы для доски и фигур.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-165">This folder contains the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="c5ec4-166">Когда откроется всплывающее окно FBX Import Options (Параметры импорта FBX-файлов), разверните раздел **Material** (Материал) и смените значение параметра **Material Import Method** (Метод импорта материала) на **Do Not Create Material** (Не создавать материал).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-166">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="c5ec4-167">Нажмите кнопку **Import All** (Импортировать все).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-167">Click **Import All**.</span></span>

![Параметры импорта FBX-файлов](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="c5ec4-169">Это все, что нужно для импорта ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-169">That's all you need to do for the assets.</span></span> <span data-ttu-id="c5ec4-170">Следующая группа задач — создать элементарные блоки, из которых будет строиться приложение, с использованием схем.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-170">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="c5ec4-171">Добавление схем</span><span class="sxs-lookup"><span data-stu-id="c5ec4-171">Adding blueprints</span></span>

1. <span data-ttu-id="c5ec4-172">В обозревателе содержимого (**Content Browser**) выберите **Add New > New Folder** (Добавить > Папка) и присвойте новой папке имя **Content Browser**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-172">Click **Add New > New Folder** in the **Content Browser** and name it **Content Browser**.</span></span> 

> [!NOTE]
> <span data-ttu-id="c5ec4-173">[Схемы](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) — это специальные ресурсы, позволяющие создавать новые типы субъектов и события уровня скрипта с помощью интерфейса на основе узлов.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-173">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="c5ec4-174">Дважды щелкните папку **Blueprints**, затем щелкните правой кнопкой мыши и выберите **Blueprint Class** (Класс схемы).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-174">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="c5ec4-175">Выберите **Actor** (Субъект) и присвойте новой схеме имя **Board**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-175">Select **Actor** and name the blueprint **Board**.</span></span> 

![Выбор родительского класса для новой схемы](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="c5ec4-177">Новая схема **Board** появится в папке **Blueprints**, как можно видеть на следующем снимке экрана.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-177">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Новая схема для шахматной доски](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="c5ec4-179">Теперь можно добавлять материалы к созданным объектам.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-179">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="c5ec4-180">Работа с материалами</span><span class="sxs-lookup"><span data-stu-id="c5ec4-180">Working with materials</span></span>
<span data-ttu-id="c5ec4-181">По умолчанию созданные объекты имеют серый цвет, а хотелось бы чего-то повеселее.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-181">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="c5ec4-182">Последняя группа задач в этом руководстве — добавление материалов и сеток к объектам.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-182">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="c5ec4-183">Дважды щелкните схему **Board**, чтобы открыть редактор схем.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-183">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="c5ec4-184">На панели **Components** (Компоненты) выберите **Add Component > Scene** (Добавить компонент > Сцена) и присвойте новой сцене имя **Root**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-184">Click **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="c5ec4-185">Обратите внимание, что **Root** отобразится как дочерний объект элемента **DefaultSceneRoot** (см. снимок экрана ниже).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-185">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Замена главного элемента](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="c5ec4-187">Перетащите элемент **Root** на **DefaultSceneRoot**, чтобы заменить последний и избавиться от шара в окне просмотра.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-187">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Замена главного элемента](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="c5ec4-189">На панели **Components** (Компоненты) выберите **Add Component > Static Mesh** (Добавить компонент > Статическая сетка) и присвойте новой сетке имя **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-189">Click **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="c5ec4-190">Она отобразится как дочерний объект элемента **Root**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-190">It will appear as a child object under **Root**.</span></span>

![Добавление статической сетки](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="c5ec4-192">Щелкните элемент **SM_Board**, прокрутите панель **Details** (Сведения) до раздела **Static Mesh** (Статическая сетка) и выберите в раскрывающемся списке вариант **ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-192">Click **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Сетка шахматной доски в окне просмотра](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="c5ec4-194">В той же панели **Details** (Сведения) разверните раздел **Materials** (Материалы) и выберите в раскрывающемся списке **Create New Asset > Material** (Создать ресурс > Материал).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-194">Still in the **Details** panel, expand the **Materials** section and click **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="c5ec4-195">Присвойте новому материалу имя **M_ChessBoard** и сохраните его в папке **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-195">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Создание нового материала](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="c5ec4-197">Дважды щелкните материал **M_ChessBoard**, чтобы открыть редактор материалов.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-197">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Открытие редактора материалов](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="c5ec4-199">В окне Material Editor (Редактор материалов) щелкните правой кнопкой мыши и найдите узел **Texture Sample** (Пример текстуры).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-199">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="c5ec4-200">На панели **Details** (Сведения) разверните раздел **Material Expression Texture Base** (Основа текстуры для выражения материала) и установите для параметра **Texture** (Текстура) значение **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-200">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="c5ec4-201">Перетащите маркер вывода **RGB** на маркер Base Color (Основной цвет) элемента **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-201">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Установка основного цвета](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="c5ec4-203">Повторите предыдущий шаг еще четыре раза и создайте четыре новых узла **Texture Sample** (Пример текстуры), настроив их следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c5ec4-203">Repeat the previous step four more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="c5ec4-204">Установите для параметра **Texture** (Текстура) значение **ChessBoard_AO** и свяжите закрепление **RGB** с закреплением **Ambient Occlusion** (Рассеянное затенение).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-204">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="c5ec4-205">Установите для параметра **Texture** (Текстура) значение **ChessBoard_Metal** и свяжите закрепление **RGB** с закреплением **Metallic** (Металлик).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-205">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="c5ec4-206">Установите для параметра **Texture** (Текстура) значение **ChessBoard_Normal** и свяжите закрепление **RGB** с закреплением **Normal** (Обычный).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-206">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="c5ec4-207">Установите для параметра **Texture** (Текстура) значение **ChessBoard_Rough** и свяжите закрепление **RGB** с закреплением **Roughness** (Шероховатость).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-207">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="c5ec4-208">Нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-208">Click **Save**.</span></span> 

![Подключение оставшихся текстур](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="c5ec4-210">Прежде чем продолжать, убедитесь, что материал настроен так, как показано на снимке экрана выше.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-210">Make sure the your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="c5ec4-211">Заполнение сцены</span><span class="sxs-lookup"><span data-stu-id="c5ec4-211">Populating the scene</span></span>
<span data-ttu-id="c5ec4-212">Если вы вернетесь к схеме **Board**, то увидите, что к ней уже применен созданный только что материал.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-212">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="c5ec4-213">Осталось только настроить сцену.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-213">All that's left is setting up the scene!</span></span> <span data-ttu-id="c5ec4-214">Сначала изменим свойства, как описано ниже, чтобы придать доске разумные размеры и расположить ее под правильным углом в сцене:</span><span class="sxs-lookup"><span data-stu-id="c5ec4-214">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="c5ec4-215">Установите для параметра **Scale** (Масштаб) значение **(0,05, 0,05, 0,05)** , а для параметра **Z Rotation** (Поворот по оси Z) — значение **90**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-215">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="c5ec4-216">Нажмите кнопку **Compile** (Компилировать) в верхней панели инструментов, а затем кнопку **Save** (Сохранить), после чего вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-216">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Шахматная доска после применения материалов](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="c5ec4-218">Щелкните правой кнопкой мыши **Cube > Edit > Delete** (Куб > Изменить > Удалить) и перетащите элемент **Board** из обозревателя контента (**Content Browser**) в окно просмотра.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-218">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="c5ec4-219">Установите для параметра **Location** (Расположение) значения **X = 80**, **Y = 0** и **Z = -20**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-219">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="c5ec4-220">Нажмите кнопку **Play** (Воспроизведение), чтобы просмотреть созданную доску на уровне.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-220">Click the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="c5ec4-221">Нажмите клавишу **ESC**, чтобы вернуться в редактор.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-221">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="c5ec4-222">Теперь по тому же алгоритму, что и с доской, создадим шахматную фигуру:</span><span class="sxs-lookup"><span data-stu-id="c5ec4-222">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="c5ec4-223">Дважды щелкните папку **Blueprints**, щелкните правой кнопкой мыши и выберите **Blueprint Class** (Класс схемы), а затем **Actor** (Субъект).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-223">Go to the **Blueprints** folder, right-click and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="c5ec4-224">Присвойте субъекту имя **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-224">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="c5ec4-225">Дважды щелкните элемент **WhiteKing**, чтобы открыть его в редакторе схем, выберите **Add Component > Scene** (Добавить компонент > Сцена) и присвойте сцене имя **Root**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-225">Double click **WhiteKing** to open it in the Blueprint Editor, click **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="c5ec4-226">Замените элемент **DefaultSceneRoot**, перетащив на него элемент **Root**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-226">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="c5ec4-227">Выберите **Add Component > Static Mesh** (Добавить компонент > Статическая сетка) и присвойте компоненту имя **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-227">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="c5ec4-228">На панели Details (Сведения) установите для параметра **Static Mesh** (Статическая сетка) значение **Chess_King**, а для параметра **Material** (Материал) — значение **M_ChessWhite**, соответствующее новому материалу.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-228">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="c5ec4-229">Откройте материал **M_ChessWhite** в редакторе материалов и подключите узлы **Texture Sample** (Пример текстуры) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c5ec4-229">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
    * <span data-ttu-id="c5ec4-230">Установите для параметра **Texture** (Текстура) значение **ChessWhite_AO** и свяжите закрепление **RGB** с закреплением **Ambient Occlusion** (Рассеянное затенение).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-230">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="c5ec4-231">Установите для параметра **Texture** (Текстура) значение **ChessWhite_Metal** и свяжите закрепление **RGB** с закреплением **Metallic** (Металлик).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-231">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="c5ec4-232">Установите для параметра **Texture** (Текстура) значение **ChessWhite_Normal** и свяжите закрепление **RGB** с закреплением **Normal** (Обычный).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-232">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="c5ec4-233">Установите для параметра **Texture** (Текстура) значение **ChessWhite_Rough** и свяжите закрепление **RGB** с закреплением **Roughness** (Шероховатость).</span><span class="sxs-lookup"><span data-stu-id="c5ec4-233">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="c5ec4-234">Нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-234">Click **Save**.</span></span> 

<span data-ttu-id="c5ec4-235">Прежде чем продолжать, убедитесь, что материал **M_ChessKing** настроен, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-235">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Создание материала для шахматного короля](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="c5ec4-237">Все почти готово, осталось лишь добавить новую шахматную фигуру в сцену:</span><span class="sxs-lookup"><span data-stu-id="c5ec4-237">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="c5ec4-238">Откройте схему **WhiteKing** и установите для параметра **Scale** (Масштаб) значение **(0,05, 0,05, 0,05)** , а для параметра **Z Rotation** (Поворот по оси Z) — значение **90**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-238">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="c5ec4-239">Скомпилируйте схему и сохраните ее, а затем вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-239">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="c5ec4-240">Перетащите элемент **WhiteKing** в окно просмотра, переключитесь на панель **World Outliner** (Структура мира) и перетащите элемент **WhiteKing** на элемент **Board** в качестве дочернего объекта.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-240">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Структура мира](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="c5ec4-242">На панели **Details** (Сведения) в разделе **Transform** (Преобразование) установите для параметра **Location** (Расположение) элемента **WhiteKing** значения **X = -26**, **Y = 4** и **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-242">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="c5ec4-243">Готово!</span><span class="sxs-lookup"><span data-stu-id="c5ec4-243">That's a wrap!</span></span> <span data-ttu-id="c5ec4-244">Нажмите кнопку **Play** (Воспроизведение), чтобы увидеть заполненный уровень в действии, а когда захотите выйти, нажмите клавишу **ESC**.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-244">Click **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="c5ec4-245">В этом руководстве подробно описано создание простого проекта. Следующая часть серии посвящена настройке проекта для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="c5ec4-245">This tutorial covered a lot of ground creating a simple project, but your project is ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="c5ec4-246">Следующий раздел: 3. Настройка проекта для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="c5ec4-246">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)
