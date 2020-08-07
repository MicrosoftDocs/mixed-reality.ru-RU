---
title: 5. Добавление кнопки и сброс расположений фигур
description: Часть 5 (из 6) серии руководств по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств UX из набора средств для смешанной реальности
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, средства разработки пользовательского интерфейса, средства UX, документация
ms.openlocfilehash: e81da5a4550f258b629443df9b2b655d81108c21
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376366"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="fff70-104">5. Добавление кнопки и сброс расположений фигур</span><span class="sxs-lookup"><span data-stu-id="fff70-104">5. Adding a button & resetting piece locations</span></span>


## <a name="overview"></a><span data-ttu-id="fff70-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="fff70-105">Overview</span></span>

<span data-ttu-id="fff70-106">В предыдущем руководстве мы добавили субъекты взаимодействия с рукой к компонентам Pawn и Manipulator на шахматной доске, чтобы сделать оба эти компонента интерактивными.</span><span class="sxs-lookup"><span data-stu-id="fff70-106">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="fff70-107">В этом разделе мы продолжим работать с подключаемым модулем средств UX для смешанной реальности и развивать функциональность приложения для игры в шахматы.</span><span class="sxs-lookup"><span data-stu-id="fff70-107">In this section, you'll continue working with the Mixed Reality Toolkit UX Tools plugin by building out the features of your chess app.</span></span> <span data-ttu-id="fff70-108">В частности, нам предстоит создать еще одну функцию и научиться получать ссылки на субъекты на схеме.</span><span class="sxs-lookup"><span data-stu-id="fff70-108">This includes creating a new function and learning how to get references to Actors in a Blueprint.</span></span> <span data-ttu-id="fff70-109">К концу раздела у вас все будет готово к упаковке приложения смешанной реальности и его развертыванию на устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="fff70-109">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="fff70-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="fff70-110">Objectives</span></span>

* <span data-ttu-id="fff70-111">Добавление интерактивной кнопки.</span><span class="sxs-lookup"><span data-stu-id="fff70-111">Adding an interactive button</span></span>
* <span data-ttu-id="fff70-112">Создание функции для сброса расположения фигуры.</span><span class="sxs-lookup"><span data-stu-id="fff70-112">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="fff70-113">Подключение кнопки к триггеру, чтобы ее нажатие активировало созданную функцию.</span><span class="sxs-lookup"><span data-stu-id="fff70-113">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="fff70-114">Создание функции сброса</span><span class="sxs-lookup"><span data-stu-id="fff70-114">Creating a reset function</span></span>
<span data-ttu-id="fff70-115">Первым делом необходимо создать схему функции, которая сбрасывает расположение фигуры, возвращая ее на исходное место в сцене.</span><span class="sxs-lookup"><span data-stu-id="fff70-115">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span> 

1.  <span data-ttu-id="fff70-116">Откройте элемент **WhiteKing**. на панели **My Blueprint** нажмите кнопку **+** рядом с разделом **Functions** (Функции) и присвойте новой функции имя **Reset Location**.</span><span class="sxs-lookup"><span data-stu-id="fff70-116">Open **WhiteKing**, click the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span> 

2.  <span data-ttu-id="fff70-117">Перетащите закрепление выполнения из функции **Reset Location** в произвольное место сетки схемы, чтобы создать узел **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="fff70-117">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span> 
    * <span data-ttu-id="fff70-118">Эта функция задает для субъекта преобразование (расположение, поворот и масштабирование) относительно родительского элемента.</span><span class="sxs-lookup"><span data-stu-id="fff70-118">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="fff70-119">С помощью этой функции мы можем вернуть короля на доске в исходное место, даже если сама доска была перемещена.</span><span class="sxs-lookup"><span data-stu-id="fff70-119">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> 
    
3. <span data-ttu-id="fff70-120">Щелкните правой кнопкой мыши внутри графа событий, выберите **Make Transform** (Создать преобразование) и задайте для параметра **Location** (Расположение) значения **X = -26**, **Y = 4** и **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="fff70-120">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="fff70-121">Соедините закрепление **Return Value** (Возвращаемое значение) с закреплением **New Relative Transform** (Новое относительное преобразование) элемента **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="fff70-121">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span> 

![Функция сброса расположения](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="fff70-123">Скомпилируйте (**Compile**) и сохраните (**Save**) проект, после чего вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="fff70-123">**Compile** and **Save** the project before returning to the Main window.</span></span> 


## <a name="adding-a-button"></a><span data-ttu-id="fff70-124">Добавление кнопки</span><span class="sxs-lookup"><span data-stu-id="fff70-124">Adding a button</span></span>
<span data-ttu-id="fff70-125">Теперь, когда функция настроена, следующая задача — создать кнопку, при нажатии которой функция будет выполняться.</span><span class="sxs-lookup"><span data-stu-id="fff70-125">Now that the function is setup correctly, your next task is to create a button that fires it off when touched.</span></span> 

1.  <span data-ttu-id="fff70-126">Последовательно выберите **Add New > Blueprint Class** (Добавить > Класс схемы), разверните раздел **All Classes** (Все классы) и найдите в нем класс **SimpleButton**.</span><span class="sxs-lookup"><span data-stu-id="fff70-126">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **SimpleButton**.</span></span> 
    * <span data-ttu-id="fff70-127">Присвойте созданной кнопке имя **ResetButton** и дважды щелкните ее, чтобы открыть соответствующую схему.</span><span class="sxs-lookup"><span data-stu-id="fff70-127">Name it **ResetButton** and double click to open the Blueprint</span></span>

> [!NOTE]
> <span data-ttu-id="fff70-128">**SimpleButton** — это субъект-схема трехмерной кнопки, входящая в состав подключаемого модуля средств UX.</span><span class="sxs-lookup"><span data-stu-id="fff70-128">**SimpleButton** is a 3D button Blueprint Actor that's part of the UX Tools plugin.</span></span> <span data-ttu-id="fff70-129">.</span><span class="sxs-lookup"><span data-stu-id="fff70-129">.</span></span> 

![Создайте новую схему как подкласс SimpleButton](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="fff70-131">На панели **Components** (Компоненты) щелкните **Pressable Button (Inherited)** (Кнопка с возможностью нажатия (наследованная)) и прокрутите панель **Details** (Сведения) до раздела **Events** (События).</span><span class="sxs-lookup"><span data-stu-id="fff70-131">Click **Pressable Button (Inherited)** from the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span> 
    * <span data-ttu-id="fff70-132">Нажмите зеленую кнопку **+** рядом с событием **On Button Pressed** (По нажатию кнопки), чтобы добавить это событие в граф событий. Добавленное событие будет инициироваться при нажатии кнопки, которую мы создаем.</span><span class="sxs-lookup"><span data-stu-id="fff70-132">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span> 
    
<span data-ttu-id="fff70-133">Из этого события мы будем вызывать функцию **Reset Location** (Сброс расположения) элемента **WhiteKing**, для чего требуется ссылка на субъект **WhiteKing** на данном уровне.</span><span class="sxs-lookup"><span data-stu-id="fff70-133">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span> 

1.  <span data-ttu-id="fff70-134">В панели **My Blueprint** (Моя схема) перейдите к разделу **Variables** (Переменные), нажмите кнопку **+** и присвойте переменной имя **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="fff70-134">In the **My Blueprint** panel, navigate to the **Variables** section , click the **+** button and name the variable **WhiteKing**.</span></span> 
    * <span data-ttu-id="fff70-135">На панели **Details** (Сведения) щелкните раскрывающийся список рядом с полем **Variable Type** (Тип переменной), затем выполните поиск по слову **WhiteKing** и выберите **Object Reference** (Ссылка на объект).</span><span class="sxs-lookup"><span data-stu-id="fff70-135">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span> 
    * <span data-ttu-id="fff70-136">Установите флажок **Instance Editable** (Редактируемый экземпляр).</span><span class="sxs-lookup"><span data-stu-id="fff70-136">Check the box next to **Instance Editable**.</span></span> <span data-ttu-id="fff70-137">Это позволит задавать значение переменной из уровня Main.</span><span class="sxs-lookup"><span data-stu-id="fff70-137">This will allow the variable to be set from the Main Level.</span></span> 

![Создание переменной](images/unreal-uxt/5-var.PNG)

2.  <span data-ttu-id="fff70-139">Перетащите переменную WhiteKing из раздела **My Blueprint > Variables** (Моя схема > Переменные) на граф Reset Button Event Graph (Граф событий кнопки сброса) и выберите **Get WhiteKing** (Получить WhiteKing).</span><span class="sxs-lookup"><span data-stu-id="fff70-139">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span> 

## <a name="firing-the-function"></a><span data-ttu-id="fff70-140">Вызов функции</span><span class="sxs-lookup"><span data-stu-id="fff70-140">Firing the function</span></span>
<span data-ttu-id="fff70-141">Теперь осталось сделать так, чтобы при нажатии нашей кнопки вызывалась функция сброса.</span><span class="sxs-lookup"><span data-stu-id="fff70-141">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="fff70-142">Перетащите закрепление вывода WhiteKing и отпустите его для размещения нового узла.</span><span class="sxs-lookup"><span data-stu-id="fff70-142">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="fff70-143">Выберите функцию **Reset Location** (Сброс расположения).</span><span class="sxs-lookup"><span data-stu-id="fff70-143">Select the **Reset Location** function.</span></span> <span data-ttu-id="fff70-144">Наконец, перетащите выходное закрепление выполнения из события **On Button Pressed** (По нажатию кнопки) к входному закреплению выполнения функции **Reset Location** (Сброс расположения).</span><span class="sxs-lookup"><span data-stu-id="fff70-144">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="fff70-145">**Скомпилируйте** и **сохраните** схему ResetButton, а затем вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="fff70-145">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![Вызов функции сброса расположения из события нажатия кнопки](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="fff70-147">Перетащите элемент **ResetButton** в окно просмотра и задайте для него следующее расположение: **X = 50**, **Y = -25**, **Z = 10**.</span><span class="sxs-lookup"><span data-stu-id="fff70-147">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="fff70-148">В разделе **Default** (По умолчанию) задайте для переменной **WhiteKing** значение **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="fff70-148">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![Указание переменной](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="fff70-150">Запустите приложение, переместите фигуру, а затем нажмите большую розовую кнопку — и вы увидите, как работает функция сброс расположения.</span><span class="sxs-lookup"><span data-stu-id="fff70-150">Run the app, move the chess piece to a new location, and press the big pink button to see the reset logic in action!</span></span>

<span data-ttu-id="fff70-151">Теперь у вас есть приложение смешанной реальности с интерактивными шахматной фигурой и доской, а также кнопка, возвращающая фигуру в исходное место.</span><span class="sxs-lookup"><span data-stu-id="fff70-151">You now have a mixed reality app with a chess piece and board that you can interact with, as well as a fully functioning button that will reset the piece’s location.</span></span> <span data-ttu-id="fff70-152">Законченное приложение в том объеме, в котором оно реализовано к данному моменту, вы найдете в репозитории [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span><span class="sxs-lookup"><span data-stu-id="fff70-152">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="fff70-153">Вы можете не ограничиваться рамками этого руководства и настроить все остальные шахматные фигуры так, чтобы при нажатии этой кнопки вся доска принимала первоначальный вид.</span><span class="sxs-lookup"><span data-stu-id="fff70-153">Feel free to go beyond this tutorial and set up the remainder of the chess pieces so that the entire board is reset when the button is pressed.</span></span>

![Готовая сцена в окне просмотра](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="fff70-155">Теперь вы готовы к изучению последнего раздела, в котором вы научитесь правильно упаковывать приложение и развертывать его на устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="fff70-155">You're ready to move on to the final section of this tutorial where you'll learn how to correctly package and deploy the app to a device or emulator.</span></span>

[<span data-ttu-id="fff70-156">Следующий раздел: 6. Упаковка и развертывание на устройстве или в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="fff70-156">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
