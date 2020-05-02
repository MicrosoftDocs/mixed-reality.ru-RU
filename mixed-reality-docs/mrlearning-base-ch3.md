---
title: Серия учебников по началу работы, часть 4. Размещение динамического содержимого и использование решателей
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362038"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="94754-105">4. Размещение динамического содержимого и использование решателей</span><span class="sxs-lookup"><span data-stu-id="94754-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="94754-106">Голограммы реализуются в HoloLens 2, когда они интуитивно следуют за пользователем и помещаются в физическую среду способом, который делает взаимодействие простым и изящным.</span><span class="sxs-lookup"><span data-stu-id="94754-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="94754-107">В этом учебнике мы рассмотрим способы динамического помещения голограмм с помощью доступных инструментов размещения MRTK, известных как "решатели" и предназначенных для сложных сценариев пространственного размещения.</span><span class="sxs-lookup"><span data-stu-id="94754-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="94754-108">В MRTK решатели — это система сценариев и поведений, которые мы используем, чтобы разрешить элементам пользовательского интерфейса следовать за вами, пользователем или другими игровыми объектами на сцене.</span><span class="sxs-lookup"><span data-stu-id="94754-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="94754-109">С их помощью также можно быстро выполнить прикрепление к определенной позиции, что делает приложение интуитивно понятным.</span><span class="sxs-lookup"><span data-stu-id="94754-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="94754-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="94754-110">Objectives</span></span>

* <span data-ttu-id="94754-111">Знакомство с решателями MRTK.</span><span class="sxs-lookup"><span data-stu-id="94754-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="94754-112">Использование решателей для того, чтобы коллекция кнопок следовала за пользователем.</span><span class="sxs-lookup"><span data-stu-id="94754-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="94754-113">Использование решателей для того, чтобы игровой объект следовал за отслеживаемыми руками пользователя.</span><span class="sxs-lookup"><span data-stu-id="94754-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="94754-114">Расположение решателей в MRTK</span><span class="sxs-lookup"><span data-stu-id="94754-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="94754-115">Решатели MRTK размещаются в папке пакета SDK MRTK.</span><span class="sxs-lookup"><span data-stu-id="94754-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="94754-116">Чтобы просмотреть доступные в проекте решатели, в окне проекта перейдите к разделу **Assets** (Активы) > **MixedRealityToolkit.SDK** > **Features** (Функции) > **Utilities** (Служебные программы) > **Solvers** (Решатели):</span><span class="sxs-lookup"><span data-stu-id="94754-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="94754-118">В этом уроке мы рассмотрим реализацию решателей Orbital и RadialView.</span><span class="sxs-lookup"><span data-stu-id="94754-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="94754-119">Чтобы получить дополнительную информацию о полном наборе решателей, доступных в MRTK, воспользуйтесь ссылкой разделом [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) (Решатели) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="94754-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="94754-120">Использование решателя для настройки следования за пользователем</span><span class="sxs-lookup"><span data-stu-id="94754-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="94754-121">В этом разделе вы улучшите созданную в предыдущем учебнике коллекцию кнопок так, чтобы она следовала за направлением взгляда пользователя.</span><span class="sxs-lookup"><span data-stu-id="94754-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="94754-122">Кроме того, вы настроите решатель так, чтобы коллекция кнопок постоянно соответствовала следующим условиям:</span><span class="sxs-lookup"><span data-stu-id="94754-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="94754-123">развернута параллельно плоскости чтения для пользователя, в направлении естественного чтения слева направо;</span><span class="sxs-lookup"><span data-stu-id="94754-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="94754-124">размещена ниже направления горизонтального взгляда пользователя, чтобы не закрывать объекты, которые вы добавите позднее при работе с этим руководством;</span><span class="sxs-lookup"><span data-stu-id="94754-124">Positioned below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="94754-125">расположена на расстоянии примерно длины руки от пользователя, чтобы кнопки было удобно нажимать.</span><span class="sxs-lookup"><span data-stu-id="94754-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="94754-126">Для этих целей вы примените **решатель Orbital**, который фиксирует объект в указанном положении и на указанном расстоянии от некоторого объекта.</span><span class="sxs-lookup"><span data-stu-id="94754-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="94754-127">1. Добавление решателя Orbital</span><span class="sxs-lookup"><span data-stu-id="94754-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="94754-128">В окне Hierarchy (Иерархия) выберите объект **ButtonCollection**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Orbital (Script)** к объекту ButtonCollection.</span><span class="sxs-lookup"><span data-stu-id="94754-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="94754-129">При добавлении решателя (Orbital (Script) в нашем примере) автоматически добавляется еще и компонент Solver Handler (Script) (Обработчик решателя — скрипт), который является обязательным для решателя.</span><span class="sxs-lookup"><span data-stu-id="94754-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="94754-130">2. Настройка решателя Orbital</span><span class="sxs-lookup"><span data-stu-id="94754-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="94754-131">Настройте компонент **Solver Handler (Script)** (Обработчик решателя — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="94754-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="94754-132">Убедитесь, что для параметра **Tracked Target Type** (Тип отслеживаемой цели) указано значение **Head** (Голова).</span><span class="sxs-lookup"><span data-stu-id="94754-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="94754-133">Настройте компонент **Orbital (Script)** (Orbital — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="94754-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="94754-134">Убедитесь, что для параметра **Orientation Type** (Тип ориентации) установлено значение **Follow Tracked Object** (Следовать за отслеживаемым объектом).</span><span class="sxs-lookup"><span data-stu-id="94754-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="94754-135">Для **Local Offset** (Локальное смещение) установите значения X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="94754-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="94754-136">Для **World Offset** (Глобальное смещение) установите значения X = 0, Y = –0,4, Z = 0,3.</span><span class="sxs-lookup"><span data-stu-id="94754-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="94754-138">3. Тестирование решателя Orbital с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="94754-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="94754-139">Нажмите кнопку Play (Играть), чтобы перейти в игровой режим, затем нажмите и удерживайте правую кнопку мыши, чтобы повернуть направление взгляда и проверить следующее поведение.</span><span class="sxs-lookup"><span data-stu-id="94754-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="94754-140">Положение преобразования для ButtonCollection теперь определяется параметрами решателя.</span><span class="sxs-lookup"><span data-stu-id="94754-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="94754-141">Объект Cube (Куб), на который не действуют параметры решателя, всегда остается в одном положении.</span><span class="sxs-lookup"><span data-stu-id="94754-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="94754-143">Если вы не видите в окне Scene (Сцена) луч направления камеры, проверьте, включено ли меню Gizmos (Манипуляторы).</span><span class="sxs-lookup"><span data-stu-id="94754-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="94754-144">Дополнительные сведения о меню Gizmos (Манипуляторы) и его применении для оптимизации представления сцены вы можете найти в <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">этом разделе</a> документации.</span><span class="sxs-lookup"><span data-stu-id="94754-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="94754-145">Чтобы отобразить окна Scene (Сцена) и Game (Игра) рядом друг с другом, как на изображении ниже, перетащите окно "Игра" и поместите его справа от окна Scene (Сцена).</span><span class="sxs-lookup"><span data-stu-id="94754-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="94754-146">Чтобы получить дополнительные сведения о настройке рабочего пространства, вы можете изучить <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">этот раздел</a> документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="94754-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="94754-147">Настройка следования объектов за отслеживаемыми руками</span><span class="sxs-lookup"><span data-stu-id="94754-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="94754-148">В этом разделе вы настроите созданный в предыдущем учебнике объект Cube (Куб) так, чтобы он следовал за отслеживаемыми руками, в частности за запястьем правой руки.</span><span class="sxs-lookup"><span data-stu-id="94754-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="94754-149">Кроме того, вы настроите решатель так, чтобы куб постоянно соответствовал следующим условиям:</span><span class="sxs-lookup"><span data-stu-id="94754-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="94754-150">Ориентация изменяется синхронно с вращением руки пользователя.</span><span class="sxs-lookup"><span data-stu-id="94754-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="94754-151">Расположение привязано к положению запястья пользователя.</span><span class="sxs-lookup"><span data-stu-id="94754-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="94754-152">Кроме того, вы примените **решатель Radial View**, который постоянно удерживает объект в конусе взгляда относительно указанного объекта.</span><span class="sxs-lookup"><span data-stu-id="94754-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="94754-153">1. Добавление решателя Radial View</span><span class="sxs-lookup"><span data-stu-id="94754-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="94754-154">В окне Hierarchy (Иерархия) выберите объект **Cube** (Куб), а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Radial View (Script)** к объекту Cube (Куб).</span><span class="sxs-lookup"><span data-stu-id="94754-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="94754-155">2. Настройка решателя Radial View</span><span class="sxs-lookup"><span data-stu-id="94754-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="94754-156">Настройте компонент **Solver Handler (Script)** (Обработчик решателя — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="94754-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="94754-157">Для параметра **Tracked Target Type** (Тип отслеживаемой цели) задайте значение **Hand Joint** (Сустав руки).</span><span class="sxs-lookup"><span data-stu-id="94754-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="94754-158">Для параметра **Tracked Handness** (Отслеживаемая рука) установите значение **Right** (Правая).</span><span class="sxs-lookup"><span data-stu-id="94754-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="94754-159">Для параметра **Tracked Hand Joint** (Отслеживаемый сустав руки) установите значение **Wrist** (Запястье).</span><span class="sxs-lookup"><span data-stu-id="94754-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="94754-160">Настройте компонент **Radial View (Script)** (Radial View — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="94754-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="94754-161">Для параметра **Reference Direction** (Направление привязки) установите значение **Object Oriented** (Ориентация объекта), затем установите флажок **Orient To Reference Direction** (Ориентировать по направлению указанного объекта).</span><span class="sxs-lookup"><span data-stu-id="94754-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="94754-162">Для параметров **Min Distance** (Минимальная дистанция) и **Max Distance** (Максимальная дистанция) установите значения 0.</span><span class="sxs-lookup"><span data-stu-id="94754-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="94754-164">3. Тестирование решателя Radial View с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="94754-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="94754-165">Нажмите кнопку Play (Играть), чтобы перейти в игровой режим, затем нажмите и удерживайте клавишу ПРОБЕЛ, чтобы поднять руку.</span><span class="sxs-lookup"><span data-stu-id="94754-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="94754-166">Перемещайте курсор мыши, чтобы управлять этой рукой, а также перемещайте мышь при нажатой и удерживаемой левой кнопке мыши, чтобы вращать эту руку.</span><span class="sxs-lookup"><span data-stu-id="94754-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="94754-168">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="94754-168">Congratulations</span></span>

<span data-ttu-id="94754-169">В этом руководстве вы узнали, как использовать решатели MRTK, чтобы пользовательский интерфейс интуитивно следовал за пользователем.</span><span class="sxs-lookup"><span data-stu-id="94754-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="94754-170">Вы также узнали, как присоединить решатель к объекту (например, кубу), чтобы объект следовал за отслеживаемыми руками пользователя.</span><span class="sxs-lookup"><span data-stu-id="94754-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="94754-171">Чтобы получить дополнительные сведения об этих и других решателях в составе MRTK, посетите руководство [Решатели](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="94754-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="94754-172">Следующее руководство: 5. Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="94754-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
