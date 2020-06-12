---
title: 3. Настройка проекта для смешанной реальности
description: Часть 3 (из 6) серии руководств по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств разработки пользовательского интерфейса (UX) из набора средств для смешанной реальности
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, средства разработки пользовательского интерфейса, средства UX, документация
ms.openlocfilehash: d22c3d8c9048f53171298642768877d7bcdcb972
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330305"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="4edfc-104">3. Настройка проекта для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="4edfc-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="4edfc-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="4edfc-105">Overview</span></span>

<span data-ttu-id="4edfc-106">В предыдущем разделе мы настроили проект приложения для игры в шахматы.</span><span class="sxs-lookup"><span data-stu-id="4edfc-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="4edfc-107">В этом разделе мы настроем приложение для разработки в контексте смешанной реальности, то есть добавим в него сеанс дополненной реальности.</span><span class="sxs-lookup"><span data-stu-id="4edfc-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="4edfc-108">Для этого мы воспользуемся ресурсом данных ARSessionConfig, который содержит множество полезных параметров для настройки функций дополненной реальности, таких как пространственное сопоставление и загораживание.</span><span class="sxs-lookup"><span data-stu-id="4edfc-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="4edfc-109">Если вы хотите глубже изучить вопрос, в документации по Unreal Engine приведены подробные сведения о ресурсе [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) и классе [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="4edfc-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="4edfc-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="4edfc-110">Objectives</span></span>
* <span data-ttu-id="4edfc-111">Работа с параметрами дополненной реальности Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="4edfc-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="4edfc-112">Использование ресурса данных ARSessionConfig.</span><span class="sxs-lookup"><span data-stu-id="4edfc-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="4edfc-113">Настройка объекта Pawn и игрового режима.</span><span class="sxs-lookup"><span data-stu-id="4edfc-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="4edfc-114">Добавление ресурса для сеанса.</span><span class="sxs-lookup"><span data-stu-id="4edfc-114">Adding the session asset</span></span>
<span data-ttu-id="4edfc-115">Сеансы дополненной реальности в Unreal не возникают сами по себе.</span><span class="sxs-lookup"><span data-stu-id="4edfc-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="4edfc-116">Для работы с сеансом необходим ресурс данных ARSessionConfig, который мы сейчас и добавим:</span><span class="sxs-lookup"><span data-stu-id="4edfc-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="4edfc-117">В обозревателе контента (**Content Browser**) выберите **Add New > Miscellaneous > Data Asset** (Добавить > Разное > Ресурс данных).</span><span class="sxs-lookup"><span data-stu-id="4edfc-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="4edfc-118">Выйдите на уровень корневой папки **Content**.</span><span class="sxs-lookup"><span data-stu-id="4edfc-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="4edfc-119">Выберите **ARSessionConfig**, нажмите кнопку **Select** (Выбрать) и присвойте ресурсу имя **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="4edfc-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Создание ресурса данных](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="4edfc-121">Дважды щелкните ресурс **ARSessionConfig**, чтобы открыть его, оставьте параметры по умолчанию и нажмите кнопку **Save** (Сохранить).</span><span class="sxs-lookup"><span data-stu-id="4edfc-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="4edfc-122">Вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="4edfc-122">Return to the Main window.</span></span> 

![Конфигурация сеанса дополненной реальности](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="4edfc-124">Следующий шаг — настроить запуск сеанса дополненной реальности так, чтобы он происходил при загрузке уровня.</span><span class="sxs-lookup"><span data-stu-id="4edfc-124">With that done, your next step is to make sure that the AR session starts when the level loads.</span></span> <span data-ttu-id="4edfc-125">К счастью, для этого в Unreal есть специальная схема **Level Blueprint** (Схема уровня), работающая как глобальный граф событий в масштабах уровня.</span><span class="sxs-lookup"><span data-stu-id="4edfc-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="4edfc-126">Если подключить ресурс ARSessionConfig на схеме **Level Blueprint** (Схема уровня), сеанс дополненной реальности будет гарантированно стартовать в момент начала игры.</span><span class="sxs-lookup"><span data-stu-id="4edfc-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="4edfc-127">В панели инструментов редактора выберите **Blueprints > Open Level Blueprint** (Схемы > Открыть схему уровня):</span><span class="sxs-lookup"><span data-stu-id="4edfc-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![Открытие схемы уровня](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="4edfc-129">Перетащите закрепление выполнения (ориентированную вправо стрелку) из узла **Event BeginPlay** и отпустите его.</span><span class="sxs-lookup"><span data-stu-id="4edfc-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="4edfc-130">Найдите узел **Start AR Session** (Запуск сеанса дополненной реальности) и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="4edfc-130">Search for the **Start AR Session** and hit enter.</span></span>  
    * <span data-ttu-id="4edfc-131">В разделе **Session Config** (Параметры сеанса) щелкните стрелку раскрывающегося списка **Select Asset** (Выбор ресурса) и выберите ресурс **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="4edfc-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 
    * <span data-ttu-id="4edfc-132">Нажмите кнопку **Compile** (Компилировать), а затем **Save** (Сохранить), после чего вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="4edfc-132">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Запуск сеанса дополненной реальности](images/unreal-uxt/3-start-ar-session.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="4edfc-134">Создание элемента Pawn</span><span class="sxs-lookup"><span data-stu-id="4edfc-134">Create a Pawn</span></span>
<span data-ttu-id="4edfc-135">Пока что в проекте недостает объекта-игрока.</span><span class="sxs-lookup"><span data-stu-id="4edfc-135">At this point, the project still needs a player object.</span></span> <span data-ttu-id="4edfc-136">В Unreal объект **Pawn** представляет игрока в игре, но в нашем случае вместо игры будет взаимодействие в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4edfc-136">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="4edfc-137">В папке **Content** выберите **Add New > Blueprint Class** (Добавить > Класс схемы) и разверните расположенный внизу раздел **All Classes** (Все классы).</span><span class="sxs-lookup"><span data-stu-id="4edfc-137">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="4edfc-138">Найдите элемент **DefaultPawn**, нажмите кнопку **Select** (Выбрать) и дважды щелкните новый ресурс, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="4edfc-138">Search for **DefaultPawn**, click **Select** and double-click the asset to open.</span></span> 

![Создание нового объекта Pawn, наследующего от DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="4edfc-140">По умолчанию у объектов Pawn есть компоненты, представляющие трехмерную сетку и столкновение.</span><span class="sxs-lookup"><span data-stu-id="4edfc-140">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="4edfc-141">В большинстве проектов Unreal объекты Pawn — это твердые предметы, которые могут сталкиваться с другими компонентами.</span><span class="sxs-lookup"><span data-stu-id="4edfc-141">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="4edfc-142">Поскольку в смешанной реальности объект Pawn и пользователь представляют собой одно и то же, необходимо, чтобы игрок мог проходить сквозь голограммы без столкновений.</span><span class="sxs-lookup"><span data-stu-id="4edfc-142">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="4edfc-143">В панели **Components** (Компоненты) выберите компонент **CollisionComponent**, а затем в панели **Details** (Сведения) прокрутите вниз до раздела **Collision** (Столкновение).</span><span class="sxs-lookup"><span data-stu-id="4edfc-143">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="4edfc-144">Щелкните стрелку раскрывающегося списка **Collision Presets** (Предустановленные режимы столкновения) и выберите в нем значение **NoCollision**.</span><span class="sxs-lookup"><span data-stu-id="4edfc-144">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="4edfc-145">Проделайте то же самое с компонентом **MeshComponent**, а затем скомпилируйте (**Compile**) и сохраните (**Save**) схему.</span><span class="sxs-lookup"><span data-stu-id="4edfc-145">Do the same for the **MeshComponent**, then **Compile** and **Save** the Blueprint.</span></span> 

![Изменение параметров столкновения для объекта Pawn](images/unreal-uxt/3-nocollision.PNG)

<span data-ttu-id="4edfc-147">Закончив с этим, вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="4edfc-147">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="4edfc-148">Создание игрового режима</span><span class="sxs-lookup"><span data-stu-id="4edfc-148">Create a Game Mode</span></span>
<span data-ttu-id="4edfc-149">Последний аспект настройки приложения для смешанной реальности — это игровой режим (Game Mode).</span><span class="sxs-lookup"><span data-stu-id="4edfc-149">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="4edfc-150">Он определяет целый ряд параметров игры или взаимодействия, включая объект Pawn по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4edfc-150">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="4edfc-151">В папке **Content** выберите **Add New > Blueprint Class** (Добавить > Класс схемы) и разверните расположенный внизу раздел **All Classes** (Все классы).</span><span class="sxs-lookup"><span data-stu-id="4edfc-151">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="4edfc-152">Найдите элемент **Game Mode Base** (Базовый игровой режим), присвойте ему имя **MRGameMode** и дважды щелкните его для открытия.</span><span class="sxs-lookup"><span data-stu-id="4edfc-152">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![MRGameMode в обозревателе содержимого](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="4edfc-154">В панели **Details** (Сведения) перейдите в раздел **Classes** (Классы) и поменяйте значение параметра **Default Pawn Class** (Класс Pawn по умолчанию) на **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="4edfc-154">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="4edfc-155">Нажмите кнопку **Compile** (Компилировать), а затем **Save** (Сохранить), после чего вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="4edfc-155">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![Установка класса Pawn по умолчанию](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="4edfc-157">Выберите **Edit > Projects Settings** (Правка > Параметры проекта) и щелкните пункт **Maps & Modes** (Карты и режимы) в левом списке.</span><span class="sxs-lookup"><span data-stu-id="4edfc-157">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="4edfc-158">Разверните раздел **Default Modes** (Режимы по умолчанию) и поменяйте значение параметра **Default Game Mode** (Игровой режим по умолчанию) на **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="4edfc-158">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="4edfc-159">Разверните раздел **Default Maps** (Карты по умолчанию) и вместо значений **EditorStartupMap** и **GameDefaultMap** выберите значение **Main**.</span><span class="sxs-lookup"><span data-stu-id="4edfc-159">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="4edfc-160">Теперь, если вы закроете и снова откроете редактор, по умолчанию будет выбрана карта Main.</span><span class="sxs-lookup"><span data-stu-id="4edfc-160">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![Параметры проекта — Карты и режимы](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="4edfc-162">Проект настроен для смешанной реальности. Теперь можно переходить к следующему разделу, в котором мы начнем добавлять в сцену функциональность пользовательского ввода.</span><span class="sxs-lookup"><span data-stu-id="4edfc-162">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="4edfc-163">Следующий раздел: 4. Настройка интерактивной сцены</span><span class="sxs-lookup"><span data-stu-id="4edfc-163">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)