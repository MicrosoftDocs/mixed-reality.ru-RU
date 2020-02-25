---
title: Учебники по началу работы — 4. Размещение динамического содержимого и использование поисковых решений
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 5463f363291790fd5e5d76ffa322a61ca7bf8e31
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553902"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="92464-105">4. размещение динамического содержимого и использование поисковых решений</span><span class="sxs-lookup"><span data-stu-id="92464-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="92464-106">Голограммы приходят на жизнь в HoloLens 2, когда они интуитивно следуют за пользователем и помещаются в физическую среду таким образом, что упрощает и элегантное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="92464-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="92464-107">В этом руководстве мы рассмотрим способы динамического размещения голограмм с помощью доступных средств размещения МРТК, известных как поиск решения, для решения сложных сценариев пространственного размещения.</span><span class="sxs-lookup"><span data-stu-id="92464-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="92464-108">В МРТК Поиск решения — это система сценариев и поведений, которая позволяет элементам пользовательского интерфейса следовать за вами, пользователем или другими игровыми объектами в сцене.</span><span class="sxs-lookup"><span data-stu-id="92464-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="92464-109">С их помощью также можно быстро выполнить прикрепление к определенной позиции, что делает приложение интуитивно понятным.</span><span class="sxs-lookup"><span data-stu-id="92464-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="92464-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="92464-110">Objectives</span></span>

* <span data-ttu-id="92464-111">Знакомство с поиском решений МРТК</span><span class="sxs-lookup"><span data-stu-id="92464-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="92464-112">Использование поиска решений для работы с набором кнопок после пользователя</span><span class="sxs-lookup"><span data-stu-id="92464-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="92464-113">Использование поиска решений для работы с объектом Игры после отслеживания руки пользователя</span><span class="sxs-lookup"><span data-stu-id="92464-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="92464-114">Расположение поиска решений в МРТК</span><span class="sxs-lookup"><span data-stu-id="92464-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="92464-115">Поисковые решения МРТК находятся в папке пакета SDK МРТК.</span><span class="sxs-lookup"><span data-stu-id="92464-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="92464-116">Чтобы просмотреть доступные решения в проекте, в окне проекта перейдите к разделу **активы** > **микседреалититулкит. SDK** > **функции** > **Служебные программы** > **поиска решения**:</span><span class="sxs-lookup"><span data-stu-id="92464-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="92464-118">В этом учебнике мы рассмотрим реализацию решения Орбитал и решения радиального представления.</span><span class="sxs-lookup"><span data-stu-id="92464-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="92464-119">Дополнительные сведения о полном наборе решений, доступных в МРТК, можно найти в руководстве по [поиску решений](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) на [портале документации мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="92464-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="92464-120">Использование поиска решения для отслеживания пользователя</span><span class="sxs-lookup"><span data-stu-id="92464-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="92464-121">В этом разделе вы улучшите коллекцию кнопок, созданную в предыдущем учебном курсе, чтобы она применяет направление взгляда пользователя.</span><span class="sxs-lookup"><span data-stu-id="92464-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="92464-122">Кроме того, вы также настроите Поиск решения, чтобы коллекция кнопок всегда была такой:</span><span class="sxs-lookup"><span data-stu-id="92464-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="92464-123">Повернуто параллельно с направлением чтения пользователя, для естественного чтения слева направо</span><span class="sxs-lookup"><span data-stu-id="92464-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="92464-124">Размещается немного под направлением горизонтального взгляда, поэтому это не повлияет на другие объекты, которые будут добавлены далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="92464-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="92464-125">Размещается приблизительно в половину от пользователя, поэтому кнопки можно легко нажать</span><span class="sxs-lookup"><span data-stu-id="92464-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="92464-126">Для этого вы будете использовать **Орбитал Solver** , который блокирует объект с заданной позицией и смещением от упоминаемого объекта.</span><span class="sxs-lookup"><span data-stu-id="92464-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="92464-127">1. Добавление решения Орбитал</span><span class="sxs-lookup"><span data-stu-id="92464-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="92464-128">В окне Иерархия выберите объект **буттонколлектион** , а затем в окне инспектора нажмите кнопку **Добавить компонент** , чтобы добавить компонент **Орбитал (script)** в объект буттонколлектион.</span><span class="sxs-lookup"><span data-stu-id="92464-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="92464-129">При добавлении решения в этом случае компонент Орбитал (script) автоматически добавляется, так как он необходим для поиска решения.</span><span class="sxs-lookup"><span data-stu-id="92464-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="92464-130">2. Настройка решения Орбитал</span><span class="sxs-lookup"><span data-stu-id="92464-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="92464-131">Настройка компонента **обработчика поиска решений (script)** :</span><span class="sxs-lookup"><span data-stu-id="92464-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="92464-132">Убедитесь, что для **отслеживающего целевого типа** задано значение **head** .</span><span class="sxs-lookup"><span data-stu-id="92464-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="92464-133">Настройте компонент **Орбитал (script)** :</span><span class="sxs-lookup"><span data-stu-id="92464-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="92464-134">Убедитесь, что для **типа ориентации** задано значение **следовать за объектом Tracked** .</span><span class="sxs-lookup"><span data-stu-id="92464-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="92464-135">Сбросить **локальное смещение** до X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="92464-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="92464-136">Изменить **мировое смещение** на X = 0, Y =-0,4, Z = 0,3</span><span class="sxs-lookup"><span data-stu-id="92464-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="92464-138">3. тестирование решения Орбитал с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="92464-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="92464-139">Нажмите кнопку "Воспроизведение", чтобы перейти в режим игры, и нажмите и удерживайте правую кнопку мыши, чтобы повернуть направление взгляда, и обратите внимание на следующее:</span><span class="sxs-lookup"><span data-stu-id="92464-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="92464-140">Теперь расположение преобразования Буттонколлектион определяется параметрами поиска решения.</span><span class="sxs-lookup"><span data-stu-id="92464-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="92464-141">На куб, который не влияет на поиск решения, остается в той же должности</span><span class="sxs-lookup"><span data-stu-id="92464-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="92464-143">Если в окне сцены не отображается луч камеры, убедитесь, что меню приспособлений включено.</span><span class="sxs-lookup"><span data-stu-id="92464-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="92464-144">Чтобы узнать больше о меню приспособлений и его использовании для оптимизации представления сцены, можно посетить документацию по <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">меню приспособлений</a> Unity.</span><span class="sxs-lookup"><span data-stu-id="92464-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="92464-145">Чтобы отобразить сцену и игровое окно рядом, как показано на рисунке выше, просто перетащите окно игры на правую сторону окна сцены.</span><span class="sxs-lookup"><span data-stu-id="92464-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="92464-146">Дополнительные сведения о настройке рабочей области см. в документации по <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">настройке вашей рабочей области</a> Unity.</span><span class="sxs-lookup"><span data-stu-id="92464-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="92464-147">Включение объектов для отслеживания руки</span><span class="sxs-lookup"><span data-stu-id="92464-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="92464-148">В этом разделе вы настроите объект Куба, созданный в предыдущем учебном курсе, чтобы он применяет направленные пользователем руки, в частности, правый ручной.</span><span class="sxs-lookup"><span data-stu-id="92464-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="92464-149">Кроме того, вы также настроите Поиск решения, чтобы куб:</span><span class="sxs-lookup"><span data-stu-id="92464-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="92464-150">Изменяет ориентацию с поворотом руки пользователя</span><span class="sxs-lookup"><span data-stu-id="92464-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="92464-151">Помещается на себя пользователя</span><span class="sxs-lookup"><span data-stu-id="92464-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="92464-152">Для этого вы будете использовать **радиальный поисковый** элемент, который сохраняет объект в представлении с конусом, указанным объектом, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="92464-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="92464-153">1. Добавление решения для радиального представления</span><span class="sxs-lookup"><span data-stu-id="92464-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="92464-154">В окне Иерархия выберите объект **куба** , а затем в окне инспектора нажмите кнопку **Добавить компонент** , чтобы добавить объект куба " **радиальное представление (скрипт)** ".</span><span class="sxs-lookup"><span data-stu-id="92464-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="92464-155">2. Настройка решения для радиального представления</span><span class="sxs-lookup"><span data-stu-id="92464-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="92464-156">Настройка компонента **обработчика поиска решений (script)** :</span><span class="sxs-lookup"><span data-stu-id="92464-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="92464-157">Изменить **тип отслеживания** **несвязных** объектов на соединение</span><span class="sxs-lookup"><span data-stu-id="92464-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="92464-158">Изменить **отслеживающую руку** на **правую**</span><span class="sxs-lookup"><span data-stu-id="92464-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="92464-159">Изменение **отслеживания соединения руки**</span><span class="sxs-lookup"><span data-stu-id="92464-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="92464-160">Настройте компонент **радиального представления (скрипт)** :</span><span class="sxs-lookup"><span data-stu-id="92464-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="92464-161">Изменить **направление ссылки** на **объектно ориентированный**, установите флажок **ориентации на направление ссылки**</span><span class="sxs-lookup"><span data-stu-id="92464-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="92464-162">Изменить **минимальное расстояние** и **Максимальное расстояние** до 0</span><span class="sxs-lookup"><span data-stu-id="92464-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="92464-164">3. тестирование решения радиального представления с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="92464-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="92464-165">Нажмите кнопку Воспроизведение, чтобы перейти в режим игры, а затем нажмите и удерживайте клавишу пробел, чтобы отобразить руку.</span><span class="sxs-lookup"><span data-stu-id="92464-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="92464-166">Наведите курсор мыши, чтобы переместить руку, и нажмите и удерживайте левую кнопку мыши, чтобы повернуть руку:</span><span class="sxs-lookup"><span data-stu-id="92464-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="92464-168">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="92464-168">Congratulations</span></span>

<span data-ttu-id="92464-169">В этом учебнике вы узнали, как использовать поисковые решения МРТК, чтобы пользовательский интерфейс был интуитивно понятен пользователю.</span><span class="sxs-lookup"><span data-stu-id="92464-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="92464-170">Вы также узнали, как присоединить поисковый элемент к объекту (т. е. Кубу), чтобы отслеживать руки пользователя.</span><span class="sxs-lookup"><span data-stu-id="92464-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="92464-171">Дополнительные сведения об этих и других решениях, входящих в состав МРТК, можно найти в руководстве по [поиску решений](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) на [портале документации мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="92464-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="92464-172">Следующее руководство: 5. взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="92464-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
