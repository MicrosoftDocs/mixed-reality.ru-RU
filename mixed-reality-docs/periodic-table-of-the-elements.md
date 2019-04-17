---
title: Периодическая таблица элементов
description: Периодическая таблица элементов — это приложение пример с открытым исходным кодом корпорации Майкрософт смешанной реальности разработки лабораторных занятий где рассказывается, как для размещения является массивом объектов в трехмерном пространстве с различными типами поверхности, с помощью коллекции объектов.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, разработки, пример приложения, элементы управления
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604112"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="fb71d-104">Периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="fb71d-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="fb71d-105">В этой статье рассматривается пример произвольного тестирования, мы создали в [смешанной реальности разработки Labs](https://github.com/Microsoft/MRDesignLabs_Unity), это место, мы передаем результатов работы о и подсказок для смешанного реальности разработки приложений.</span><span class="sxs-lookup"><span data-stu-id="fb71d-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="fb71d-106">Наши статьи, связанных с проектированием и код будет развиваться, как мы появления новых.</span><span class="sxs-lookup"><span data-stu-id="fb71d-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="fb71d-107">[Периодическая таблица элементов](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) — это пример открытым исходным кодом приложения лабораторных занятий смешанной реальности разработки корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="fb71d-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="fb71d-108">С этим проектом, рассказывается, как для размещения является массивом объектов в трехмерном пространстве с различными типами поверхности, с помощью  **[коллекции объектов](object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="fb71d-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="fb71d-109">Также вы научитесь создавать элементом объекты, которые отвечают на стандартные входные данные из HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb71d-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="fb71d-110">Компоненты этого проекта можно использовать для создания собственных смешанного приложения дополненной реальности.</span><span class="sxs-lookup"><span data-stu-id="fb71d-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Периода таблице элементы приложения](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="fb71d-112">О приложении</span><span class="sxs-lookup"><span data-stu-id="fb71d-112">About the app</span></span>

<span data-ttu-id="fb71d-113">Периодическая таблица элементов визуализирует химических элементы и все их свойства в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="fb71d-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="fb71d-114">Оно включает основные взаимодействия HoloLens, например tap взглядом и air.</span><span class="sxs-lookup"><span data-stu-id="fb71d-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="fb71d-115">Пользователи могли узнать об элементах с анимированных трехмерными моделями.</span><span class="sxs-lookup"><span data-stu-id="fb71d-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="fb71d-116">Они могут визуально понять оболочка electron элемента его ядра - которого представляет собой протонов и neutrons.</span><span class="sxs-lookup"><span data-stu-id="fb71d-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="fb71d-117">Фон</span><span class="sxs-lookup"><span data-stu-id="fb71d-117">Background</span></span>

<span data-ttu-id="fb71d-118">После во-первых, я столкнулся HoloLens, приложение периодической таблицы было идеей, которой я знал, что я хотел поэкспериментировать с в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="fb71d-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="fb71d-119">Так как каждый элемент имеет большое число точек данных, в которых отображается текст, я подумал, что было бы отличным предмету для изучения типографических композиции в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="fb71d-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="fb71d-120">Возможность визуализировать модели electron элемента был другой интересной частью этого проекта.</span><span class="sxs-lookup"><span data-stu-id="fb71d-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="fb71d-121">Оформление</span><span class="sxs-lookup"><span data-stu-id="fb71d-121">Design</span></span>

<span data-ttu-id="fb71d-122">Вид по умолчанию периодической таблицы я себе представить трехмерные поля, которые будет содержать модель electron каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="fb71d-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="fb71d-123">Каждое поле в область будет прозрачным, таким образом, пользователь может получить грубое представление о том этого элемента.</span><span class="sxs-lookup"><span data-stu-id="fb71d-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="fb71d-124">Нажатием взглядом и air пользователь может открыть подробное представление для каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="fb71d-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="fb71d-125">Для перехода между табличное представление и подробное представление smooth и естественным, я сделал его аналогичную физического взаимодействия окна для открытия в реальной жизни.</span><span class="sxs-lookup"><span data-stu-id="fb71d-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="fb71d-126">![Эскиз разработки](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="fb71d-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="fb71d-127">*Проектирование чертежей*</span><span class="sxs-lookup"><span data-stu-id="fb71d-127">*Design sketches*</span></span>

<span data-ttu-id="fb71d-128">В подробном представлении я хотел визуализации сведений каждого элемента с прекрасно оформленную текста в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="fb71d-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="fb71d-129">Анимированного трехмерного electron модель отображается в центральной области и можно просмотреть под различными углами зрения.</span><span class="sxs-lookup"><span data-stu-id="fb71d-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Тип взаимодействия](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="fb71d-131">![Прототипы](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="fb71d-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="fb71d-132">*Прототипы взаимодействия*</span><span class="sxs-lookup"><span data-stu-id="fb71d-132">*Interaction prototypes*</span></span>

<span data-ttu-id="fb71d-133">Пользователь может изменить тип поверхности по воздуху, коснувшись кнопки в нижней части таблицы — их можно переключаться между плоскости, цилиндр, шар и точечной.</span><span class="sxs-lookup"><span data-stu-id="fb71d-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="fb71d-134">Обычные элементы управления и шаблоны, используемые в этом приложении</span><span class="sxs-lookup"><span data-stu-id="fb71d-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="fb71d-135">Элементом объекта (кнопка)</span><span class="sxs-lookup"><span data-stu-id="fb71d-135">Interactable object (button)</span></span>

<span data-ttu-id="fb71d-136">[Элементом объекта](interactable-object.md) — это объект, который может отвечать на основные входные параметры HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb71d-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="fb71d-137">Предоставляется в виде готового блока или сценарий, который легко можно применять к любому объекту.</span><span class="sxs-lookup"><span data-stu-id="fb71d-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="fb71d-138">Например можно сделать элементом чашку кофе в сцене и реагировать на них входных данных, например взглядом, жест касания, перехода и обработки жестов.</span><span class="sxs-lookup"><span data-stu-id="fb71d-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="fb71d-139">Подробнее</span><span class="sxs-lookup"><span data-stu-id="fb71d-139">Learn more</span></span>](interactable-object.md)

![Объект nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="fb71d-141">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="fb71d-141">Object collection</span></span>

<span data-ttu-id="fb71d-142">[Коллекции объектов](object-collection.md) — это объект, которое помогает в создании нескольких объектов в различные фигуры.</span><span class="sxs-lookup"><span data-stu-id="fb71d-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="fb71d-143">Он поддерживает плоскости, цилиндр, шар и точечной.</span><span class="sxs-lookup"><span data-stu-id="fb71d-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="fb71d-144">Можно настроить дополнительные параметры, такие как radius, количество строк и расстояние.</span><span class="sxs-lookup"><span data-stu-id="fb71d-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="fb71d-145">Подробнее</span><span class="sxs-lookup"><span data-stu-id="fb71d-145">Learn more</span></span>](object-collection.md)

![Коллекция объектов](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="fb71d-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="fb71d-147">Fitbox</span></span>

<span data-ttu-id="fb71d-148">По умолчанию голограммы будут помещены в расположение, где пользователь gazing на данный момент приложение запускается.</span><span class="sxs-lookup"><span data-stu-id="fb71d-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="fb71d-149">Это иногда приводит к нежелательного результата, например голограммы распространяются за стены или в середине таблицы.</span><span class="sxs-lookup"><span data-stu-id="fb71d-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="fb71d-150">Fitbox пользователь может использовать для определения расположения, где будут размещаться голограмма взглядом.</span><span class="sxs-lookup"><span data-stu-id="fb71d-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="fb71d-151">Он устанавливается с использованием простого текстуры изображения PNG, которого можно легко настроить с помощью собственных образов или трехмерные объекты.</span><span class="sxs-lookup"><span data-stu-id="fb71d-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="fb71d-153">Технические подробности</span><span class="sxs-lookup"><span data-stu-id="fb71d-153">Technical details</span></span>

<span data-ttu-id="fb71d-154">Сценарии и prefabs можно найти для периодической таблицы приложения элементы на [смешанной реальности разработки Labs на сайте GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="fb71d-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="fb71d-155">Примеры приложений</span><span class="sxs-lookup"><span data-stu-id="fb71d-155">Application examples</span></span>

<span data-ttu-id="fb71d-156">Далее приведено несколько идей для как можно создать за счет использования компонентов в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="fb71d-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="fb71d-157">Приложения для визуализации биржевых данных</span><span class="sxs-lookup"><span data-stu-id="fb71d-157">Stock data visualization app</span></span>

<span data-ttu-id="fb71d-158">С помощью тех же элементов управления и модель взаимодействия как периодической таблицы элементов примера, можно построить приложение, визуализация данных фондовой биржи.</span><span class="sxs-lookup"><span data-stu-id="fb71d-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="fb71d-159">Для размещения биржевых данных сферическую фигуры в этом примере используется объект коллекции элемент управления.</span><span class="sxs-lookup"><span data-stu-id="fb71d-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="fb71d-160">Вы можете представить подробное представление, где Дополнительные сведения о каждой из них может отображаться весьма интересным образом.</span><span class="sxs-lookup"><span data-stu-id="fb71d-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Пример приложения. Процент (1 из 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Пример приложения. Процент (2 из 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="fb71d-163">![Пример приложения. Процент (3 из 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="fb71d-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="fb71d-164">*Пример того, как коллекции объектов, используемых в таблице периодически элементов примера приложения может использовать в приложении finance*</span><span class="sxs-lookup"><span data-stu-id="fb71d-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="fb71d-165">Спорт приложения</span><span class="sxs-lookup"><span data-stu-id="fb71d-165">Sports app</span></span>

<span data-ttu-id="fb71d-166">Ниже приведен пример визуализации данных спорта, с помощью коллекции объектов и других компонентов из таблицы периодически элементов примера приложения.</span><span class="sxs-lookup"><span data-stu-id="fb71d-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Пример приложения. Спорт (1 из 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Пример приложения. Спорт (2 из 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="fb71d-169">![Пример приложения. Спорт (3 из 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="fb71d-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="fb71d-170">*Пример использования коллекции объектов в таблице периодически appcould пример элементов использоваться в приложении Спорт*</span><span class="sxs-lookup"><span data-stu-id="fb71d-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="fb71d-171">Об авторе</span><span class="sxs-lookup"><span data-stu-id="fb71d-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="fb71d-172"><b>Park Yoon донг</b></span><span class="sxs-lookup"><span data-stu-id="fb71d-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="fb71d-173">Конструктор UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb71d-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="fb71d-174">См. также</span><span class="sxs-lookup"><span data-stu-id="fb71d-174">See also</span></span>

* [<span data-ttu-id="fb71d-175">Элементом объекта</span><span class="sxs-lookup"><span data-stu-id="fb71d-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fb71d-176">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="fb71d-176">Object collection</span></span>](object-collection.md)
