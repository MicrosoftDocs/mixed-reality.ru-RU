---
title: Серия руководств по началу работы, часть 6. Создание пользовательских интерфейсов
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a7c4ea140a9c27f1a92680da6bbe1fb3a4bdc233
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306250"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="bbf91-105">6. Создание пользовательских интерфейсов</span><span class="sxs-lookup"><span data-stu-id="bbf91-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="bbf91-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="bbf91-106">Overview</span></span>

<span data-ttu-id="bbf91-107">В этом учебнике показано, как создать простой пользовательский интерфейс, используя кнопки MRTK и заготовки меню вместе с компонентом Unity TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="bbf91-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="bbf91-108">Кроме того, здесь приведены сведения о том, как настроить кнопки для запуска событий и добавить динамические элементы интерфейса подсказки, чтобы предоставить пользователю дополнительную информацию.</span><span class="sxs-lookup"><span data-stu-id="bbf91-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="bbf91-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="bbf91-109">Objectives</span></span>

* <span data-ttu-id="bbf91-110">Упорядочивание кнопок в коллекции</span><span class="sxs-lookup"><span data-stu-id="bbf91-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="bbf91-111">Использование заготовок меню MRTK</span><span class="sxs-lookup"><span data-stu-id="bbf91-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="bbf91-112">Взаимодействие с голограммами через кнопки и меню элементов пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="bbf91-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="bbf91-113">Добавление текстовых элементов</span><span class="sxs-lookup"><span data-stu-id="bbf91-113">Learn how to add text elements</span></span>
* <span data-ttu-id="bbf91-114">Динамическое создание подсказок для объектов</span><span class="sxs-lookup"><span data-stu-id="bbf91-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="bbf91-115">Создание статической панели кнопок</span><span class="sxs-lookup"><span data-stu-id="bbf91-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="bbf91-116">В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **RoverExplorer** и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в качестве дочернего объекта RoverExplorer, присвойте имя объекту **Buttons** (Кнопки) и настройте компонент **Transform** (Преобразование), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="bbf91-117">**Position** (Положение): X = –0,6, Y = 0,036, Z = –0,5</span><span class="sxs-lookup"><span data-stu-id="bbf91-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="bbf91-118">**Rotation** (Поворот): X = 90, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="bbf91-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="bbf91-119">**Scale** (Масштаб): X = 1, Y = 1, Z = 1.</span><span class="sxs-lookup"><span data-stu-id="bbf91-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="bbf91-121">В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, щелкните и перетащите заготовку **PressableRoundButton** к объекту **Buttons** (Кнопки), затем щелкните правой кнопкой мыши объект PressableRoundButton и выберите **Duplicate** (Дублировать), чтобы создать копию. Повторяйте эти действия до тех пор, пока у вас не будет три объекта PressableRoundButton:</span><span class="sxs-lookup"><span data-stu-id="bbf91-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="bbf91-123">В окне Hierarchy (Иерархия) выберите объект **Buttons** (Кнопки), затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **GridObjectCollection** и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="bbf91-124">**Sort Type** (Тип сортировки): Child Order (В порядке дочерних объектов)</span><span class="sxs-lookup"><span data-stu-id="bbf91-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="bbf91-125">**Layout** (Макет): По горизонтали</span><span class="sxs-lookup"><span data-stu-id="bbf91-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="bbf91-126">**Cell Width** (Ширина ячейки): 0,2</span><span class="sxs-lookup"><span data-stu-id="bbf91-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="bbf91-127">**Anchor** (Привязка): Посередине слева</span><span class="sxs-lookup"><span data-stu-id="bbf91-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="bbf91-128">Затем нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы обновить положение дочерних объектов объекта Buttons (Кнопки):</span><span class="sxs-lookup"><span data-stu-id="bbf91-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="bbf91-130">В окне Hierarchy (Иерархия) присвойте имя кнопкам **Hints** (Подсказки), **Explode** (Развернуть) и **Reset** (Сброс).</span><span class="sxs-lookup"><span data-stu-id="bbf91-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="bbf91-131">Для каждой кнопки выберите дочерний объект **SeeItSayItLabel** > **TextMeshPro**, а затем в окне Inspector (Инспектор) измените текст соответствующего компонента **TextMeshPro - Text** (TextMeshPro — текст), чтобы он соответствовал именам кнопок:</span><span class="sxs-lookup"><span data-stu-id="bbf91-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="bbf91-133">После этого сверните дочерние объекты объекта Buttons (Кнопки).</span><span class="sxs-lookup"><span data-stu-id="bbf91-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="bbf91-134">В окне Hierarchy (Иерархия) выберите объект кнопки **Hints** (Подсказки), затем в окне Inspector (Инспектор) настройте интерактивное событие **OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="bbf91-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="bbf91-135">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="bbf91-136">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **PlacementHintsController** > **TogglePlacementHints ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="bbf91-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

<span data-ttu-id="bbf91-138">В окне Hierarchy (Иерархия) выберите объект кнопки **Explode** (Развернуть), затем в окне Inspector (Инспектор) настройте интерактивное событие **OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="bbf91-138">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="bbf91-139">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-139">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="bbf91-140">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ExplodedViewController** > **ToggleExplodedView ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="bbf91-140">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="bbf91-142">Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим. Затем нажмите и удерживайте клавишу пробела, чтобы активировать руку, и с помощью мыши нажмите кнопку **Hints** (Подсказки), чтобы переключить видимость объектов с подсказками о размещении:</span><span class="sxs-lookup"><span data-stu-id="bbf91-142">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="bbf91-144">и кнопку **Explode** (Развернуть) для включения и выключения развернутого представления:</span><span class="sxs-lookup"><span data-stu-id="bbf91-144">and the **Explode** button to toggle the exploded view on and off:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="bbf91-146">Создание динамического меню, которое следует за пользователем</span><span class="sxs-lookup"><span data-stu-id="bbf91-146">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="bbf91-147">В окне Project (Проект) перейдите к папке **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus**, щелкните и перетащите заготовку **NearMenu4x1** в окно Hierarchy (Иерархия), установите для параметра преобразования **Position** (Позиция) значение X = 0, Y = –0,4, Z = 0 и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-147">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="bbf91-148">Убедитесь, что для параметра **Tracked Target Type** (Тип отслеживаемой цели) компонента **SolverHandler** указано значение **Head** (Головной).</span><span class="sxs-lookup"><span data-stu-id="bbf91-148">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="bbf91-149">Установите флажок рядом с компонентом Solver **RadialView**, чтобы он был включен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bbf91-149">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="bbf91-151">В окне Hierarchy (Иерархия) переименуйте объект в **Menu** (Меню), затем разверните его дочерний объект **ButtonCollection**, чтобы открыть четыре кнопки:</span><span class="sxs-lookup"><span data-stu-id="bbf91-151">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="bbf91-153">Переименуйте первую кнопку на **Indicator** (Индикатор), затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-153">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="bbf91-154">Измените значение для параметра **Main Label Text** (Текст основной метки), чтобы он соответствовал названию кнопки.</span><span class="sxs-lookup"><span data-stu-id="bbf91-154">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="bbf91-155">В поле **None (Object)** (Отсутствует (Объект)) укажите объект **Indicator** (Индикатор).</span><span class="sxs-lookup"><span data-stu-id="bbf91-155">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="bbf91-156">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **GameObject** > **SetActive (bool)** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="bbf91-156">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="bbf91-157">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-157">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="bbf91-158">Измените параметр **Icon** (Значок) на значок поиска.</span><span class="sxs-lookup"><span data-stu-id="bbf91-158">Change the **Icon** to the 'search' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="bbf91-160">В окне Hierarchy (Иерархия) выберите объект **Indicator** (Индикатор), затем в окне Inspector (Инспектор) снимите флажок рядом с его именем, чтобы сделать его неактивным по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="bbf91-160">In the Hierarchy window, select the **Indicator** object, then in the Inspector window, uncheck the checkbox next to its name to make it inactive by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="bbf91-162">Теперь после запуска приложения объект Indicator (Индикатор) будет по умолчанию отключен (его можно включить с помощью кнопки Indicator (Индикатор)).</span><span class="sxs-lookup"><span data-stu-id="bbf91-162">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="bbf91-163">Переименуйте вторую кнопку на **TapToPlace**, затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-163">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="bbf91-164">Измените значение для параметра **Main Label Text** (Текст основной метки), чтобы он соответствовал названию кнопки.</span><span class="sxs-lookup"><span data-stu-id="bbf91-164">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="bbf91-165">В поле **None (Object)** (Отсутствует (Объект)) укажите объект RoverExplorer > **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-165">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="bbf91-166">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **TapToPlace** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="bbf91-166">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="bbf91-167">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-167">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="bbf91-168">Измените параметр **Icon** (Значок) на значок руки с лучом.</span><span class="sxs-lookup"><span data-stu-id="bbf91-168">Change the **Icon** to the 'hand with ray' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="bbf91-170">В окне Hierarchy (Иерархия) выберите объект **RoverAssembly**, затем в окне Inspector (Инспектор) настройте компонент **Tap To Place (Script)** (Размещение касанием — скрипт), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-170">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="bbf91-171">Снимите флажок рядом с его именем, чтобы сделать его неактивным по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bbf91-171">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="bbf91-172">В разделе события **On Placing Started ()** щелкните значок **+** , чтобы добавить новое событие.</span><span class="sxs-lookup"><span data-stu-id="bbf91-172">In the **On Placing Started ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="bbf91-173">В поле **None (Object)** (Отсутствует (Объект)) укажите объект RoverExplorer > **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-173">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="bbf91-174">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **TapToPlace** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="bbf91-174">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="bbf91-175">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-175">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="bbf91-177">Теперь при запуске приложения функция Tap to Place (Размещение касанием) будет отключена по умолчанию (ее можно включить с помощью кнопки Tap to Place (Размещение касанием)).</span><span class="sxs-lookup"><span data-stu-id="bbf91-177">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="bbf91-178">Кроме того, когда операция размещения нажатием завершена, функция отключится автоматически.</span><span class="sxs-lookup"><span data-stu-id="bbf91-178">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="bbf91-179">Добавление текста в сцену</span><span class="sxs-lookup"><span data-stu-id="bbf91-179">Adding text to the scene</span></span>

<span data-ttu-id="bbf91-180">В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **Table** (Таблица) и выберите **3D Object** (Трехмерный объект) > **Text - TextMeshPro** (Текст — TextMeshPro), чтобы добавить текстовый объект в качестве дочернего для объекта Table (Таблица), а затем в окне Inspector (Инспектор) настройте компонент **Rect Transform** (Прямоугольное преобразование), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-180">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="bbf91-181">Укажите для параметра **Pos Y** (Позиция Y) значение 1.</span><span class="sxs-lookup"><span data-stu-id="bbf91-181">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="bbf91-182">Укажите для параметра **Width** (Ширина) значение 1.</span><span class="sxs-lookup"><span data-stu-id="bbf91-182">Change **Width** to 1</span></span>
* <span data-ttu-id="bbf91-183">Укажите для параметра **Height** (Высота) значение 1.</span><span class="sxs-lookup"><span data-stu-id="bbf91-183">Change **Height** to 1</span></span>
* <span data-ttu-id="bbf91-184">Укажите для параметра **Rotation X** (Поворот X) значение 90.</span><span class="sxs-lookup"><span data-stu-id="bbf91-184">Change **Rotation X** to 90</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="bbf91-186">Затем настройте компонент **TextMeshPro - Text** (TextMeshPro — текст), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-186">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="bbf91-187">Укажите для параметра **Text** (Текст) значение Rover Explorer.</span><span class="sxs-lookup"><span data-stu-id="bbf91-187">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="bbf91-188">Укажите для параметра **Font Style** (Стиль шрифта) значение "Полужирный".</span><span class="sxs-lookup"><span data-stu-id="bbf91-188">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="bbf91-189">Укажите для параметра **Font Size** (Размер шрифта) значение 1.</span><span class="sxs-lookup"><span data-stu-id="bbf91-189">Change **Font Size** to 1</span></span>
* <span data-ttu-id="bbf91-190">Укажите для параметра Extra Settings (Дополнительные параметры) > **Margins** (Поля) значение 0,03.</span><span class="sxs-lookup"><span data-stu-id="bbf91-190">Change Extra Settings > **Margins** to 0.03</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="bbf91-192">Добавление подсказок</span><span class="sxs-lookup"><span data-stu-id="bbf91-192">Adding tooltips</span></span>

<span data-ttu-id="bbf91-193">В окне Project (Проект) перейдите в папку **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip**, чтобы найти заготовки подсказок:</span><span class="sxs-lookup"><span data-stu-id="bbf91-193">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="bbf91-195">В окне Hierarchy (Иерархия) разверните объект RoverExplorer > **RoverParts** и выберите все его дочерние объекты лунохода, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить **ToolTipSpawner** ко всем выбранным объектам и настроить его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-195">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="bbf91-196">Убедитесь, что установлен флажок **Focus Enabled** (Фокус включен), чтобы пользователь смог посмотреть на часть, где должна появиться подсказка.</span><span class="sxs-lookup"><span data-stu-id="bbf91-196">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="bbf91-197">Укажите заготовку **Simple Line ToolTip** (Подсказка в отдельной строке) из окна Project (Проект) в поле **Tool Tip Prefab** (Заготовка подсказки).</span><span class="sxs-lookup"><span data-stu-id="bbf91-197">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="bbf91-198">Измените значение параметра ToolTip Override Settings (Параметры переопределения подсказок) > **Settings Mode** (Режим параметров) на значение **Override** (Переопределение).</span><span class="sxs-lookup"><span data-stu-id="bbf91-198">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="bbf91-199">Измените значение параметра ToolTip Override Settings (Параметры переопределения подсказок) > **Manual Pivot Location Position Y** (Позиция по оси Y расположения ручного поворота) на **1,5**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-199">Change the ToolTip Override Settings > **Manual Pivot Location Position Y** to **1.5**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="bbf91-201">В окне Hierarchy (Иерархия) выберите первую часть лунохода (RoverParts > **Camera_Part**) и настройте компонент **ToolTipSpawner**, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-201">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="bbf91-202">Измените параметр **Tool Tip Text** (Текст подсказки), чтобы в нем было указано имя части (например, **Camera** (Камера)).</span><span class="sxs-lookup"><span data-stu-id="bbf91-202">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="bbf91-204">**Повторите** этот шаг для каждого из объектов частей лунохода, чтобы настроить компонент **ToolTipSpawner**, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="bbf91-204">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="bbf91-205">Для объекта **Generator_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Generator**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-205">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="bbf91-206">Для объекта **Lights_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Lights**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-206">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="bbf91-207">Для объекта **UHFAntenna_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на поле **UHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-207">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="bbf91-208">Для объекта **Spectrometer_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Spectrometer**.</span><span class="sxs-lookup"><span data-stu-id="bbf91-208">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="bbf91-209">Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим, а затем нажмите и удерживайте правую кнопку мыши, перемещая указатель мыши, пока не будет нажата одна из частей и не отобразится подсказка для этой части:</span><span class="sxs-lookup"><span data-stu-id="bbf91-209">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="bbf91-211">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="bbf91-211">Congratulations</span></span>

<span data-ttu-id="bbf91-212">Из этого учебника вы узнали, как создать простой пользовательский интерфейс с помощью предоставляемых кнопок MRTK и заготовок меню вместе с компонентом Unity TextMeshPro, а также как настроить кнопки для запуска событий при их нажатии.</span><span class="sxs-lookup"><span data-stu-id="bbf91-212">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="bbf91-213">Вы также узнали, как добавлять динамические элементы интерфейса подсказки, чтобы предоставить пользователю дополнительную информацию.</span><span class="sxs-lookup"><span data-stu-id="bbf91-213">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="bbf91-214">Следующее руководство: 7. Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="bbf91-214">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)
