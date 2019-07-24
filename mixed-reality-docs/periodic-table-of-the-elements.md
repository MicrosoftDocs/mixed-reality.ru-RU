---
title: Периодическая таблица элементов
description: Периодическая таблица элементов — это пример приложения с открытым исходным кодом от лабораторных занятий корпорации Майкрософт по проектированию смешанной реальности, где можно научиться размещать массив объектов в трехмерном пространстве с различными типами поверхностей, используя коллекцию объектов.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, проектирование, пример приложения, элементы управления
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525346"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="19589-104">Периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="19589-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="19589-105">В этой статье рассматривается исследовательская выборка, созданная в [лабораторных занятиях по смешанной реальности](https://github.com/Microsoft/MRDesignLabs_Unity), где мы предоставляем наши знания и предложения по разработке приложений для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="19589-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="19589-106">Наши статьи и код, относящиеся к проектированию, будут развиваться по мере внесения новых обнаружений.</span><span class="sxs-lookup"><span data-stu-id="19589-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="19589-107">[Периодическая таблица элементов](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) — это пример приложения с открытым исходным кодом от лабораторных занятий корпорации Майкрософт по проектированию смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="19589-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="19589-108">С помощью этого проекта можно научиться размещать массив объектов в трехмерном пространстве с различными типами поверхностей, используя **[коллекцию объектов](object-collection.md)** .</span><span class="sxs-lookup"><span data-stu-id="19589-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="19589-109">Также Узнайте, как создавать взаимодействующие объекты, реагирующие на стандартные входные данные HoloLens.</span><span class="sxs-lookup"><span data-stu-id="19589-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="19589-110">Вы можете использовать компоненты этого проекта, чтобы создать собственный интерфейс приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="19589-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Таблица периодов приложения элементов](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="19589-112">Сведения о приложении</span><span class="sxs-lookup"><span data-stu-id="19589-112">About the app</span></span>

<span data-ttu-id="19589-113">Периодическая таблица элементов визуализирует химические элементы и все их свойства в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="19589-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="19589-114">Он включает основные взаимодействия HoloLens, таких как взгляд и воздушный нажим.</span><span class="sxs-lookup"><span data-stu-id="19589-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="19589-115">Пользователи могут узнать об элементах с анимированными трехмерными моделями.</span><span class="sxs-lookup"><span data-stu-id="19589-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="19589-116">Они могут визуально понять электронную оболочку элемента и ее всегда, которая состоит из прочего и неутронс.</span><span class="sxs-lookup"><span data-stu-id="19589-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="19589-117">Фон</span><span class="sxs-lookup"><span data-stu-id="19589-117">Background</span></span>

<span data-ttu-id="19589-118">После первого изучения HoloLens было бы ясно, что я знаю, что я хотел бы поэкспериментировать с в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="19589-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="19589-119">Поскольку каждый элемент имеет много точек данных, отображаемых с текстом, я думал, что это было бы очень удобно для изучения типографской композиции в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="19589-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="19589-120">Возможность визуализировать модель электронности элемента была еще одной интересной частью этого проекта.</span><span class="sxs-lookup"><span data-stu-id="19589-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="19589-121">Оформление</span><span class="sxs-lookup"><span data-stu-id="19589-121">Design</span></span>

<span data-ttu-id="19589-122">Для представления периодической таблицы по умолчанию я предполагаю трехмерные поля, которые будут содержать электронную модель каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="19589-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="19589-123">Поверхность каждого поля будет прозрачной, чтобы пользователь мог получить грубое представление о том элемента.</span><span class="sxs-lookup"><span data-stu-id="19589-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="19589-124">С помощью взгляда и касания Air пользователь может открыть подробное представление каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="19589-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="19589-125">Чтобы переход между табличным представлением и подробным представлением был плавно и естественным, я сделал это как физическое взаимодействие флажка, открывающегося в реальной жизни.</span><span class="sxs-lookup"><span data-stu-id="19589-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="19589-126">![Эскиз проектирования](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="19589-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="19589-127">*Разработка набросков*</span><span class="sxs-lookup"><span data-stu-id="19589-127">*Design sketches*</span></span>

<span data-ttu-id="19589-128">В подробном представлении я хотел визуализировать информацию каждого элемента с помощью элегантноного текста в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="19589-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="19589-129">В центральной области отображается анимированная трехмерная модель электронов, которую можно просмотреть с разных углов.</span><span class="sxs-lookup"><span data-stu-id="19589-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Тип взаимодействия](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="19589-131">![Прототипы](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="19589-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="19589-132">*Прототипы взаимодействия*</span><span class="sxs-lookup"><span data-stu-id="19589-132">*Interaction prototypes*</span></span>

<span data-ttu-id="19589-133">Пользователь может изменить тип поверхности, коснувшись кнопок в нижней части таблицы — они могут переключаться между плоскостью, цилиндром, сферой и точечной.</span><span class="sxs-lookup"><span data-stu-id="19589-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="19589-134">Общие элементы управления и шаблоны, используемые в этом приложении</span><span class="sxs-lookup"><span data-stu-id="19589-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="19589-135">Взаимодействующий объект (кнопка)</span><span class="sxs-lookup"><span data-stu-id="19589-135">Interactable object (button)</span></span>

<span data-ttu-id="19589-136">[Взаимодействующий объект](interactable-object.md) — это объект, который может отвечать на базовые входные данные HoloLens.</span><span class="sxs-lookup"><span data-stu-id="19589-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="19589-137">Он предоставляется в виде prefab или сценария, который можно легко применить к любому объекту.</span><span class="sxs-lookup"><span data-stu-id="19589-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="19589-138">Например, можно сделать чашку кофе в сцене интерактивной и реагировать на такие входные данные, как взгляд, касание, переходы и жесты манипуляции.</span><span class="sxs-lookup"><span data-stu-id="19589-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="19589-139">Подробнее</span><span class="sxs-lookup"><span data-stu-id="19589-139">Learn more</span></span>](interactable-object.md)

![Объект нтерактабле](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="19589-141">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="19589-141">Object collection</span></span>

<span data-ttu-id="19589-142">[Коллекция объектов](object-collection.md) — это объект, который помогает размещать несколько объектов в различных фигурах.</span><span class="sxs-lookup"><span data-stu-id="19589-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="19589-143">Он поддерживает плоскость, цилиндр, сферу и точечную диаграмму.</span><span class="sxs-lookup"><span data-stu-id="19589-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="19589-144">Можно настроить дополнительные свойства, такие как радиус, число строк и расстояния.</span><span class="sxs-lookup"><span data-stu-id="19589-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="19589-145">Подробнее</span><span class="sxs-lookup"><span data-stu-id="19589-145">Learn more</span></span>](object-collection.md)

![Коллекция объектов](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="19589-147">фитбокс</span><span class="sxs-lookup"><span data-stu-id="19589-147">Fitbox</span></span>

<span data-ttu-id="19589-148">По умолчанию голограммы помещаются в место, где пользователь облаками на момент запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="19589-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="19589-149">Это иногда приводит к нежелательным результатам, например к голограммам, размещаемым позади стены или в середине таблицы.</span><span class="sxs-lookup"><span data-stu-id="19589-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="19589-150">Фитбокс позволяет пользователю использовать взгляд, чтобы определить место, куда будет помещена голограмма.</span><span class="sxs-lookup"><span data-stu-id="19589-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="19589-151">Он создается с помощью простой текстуры изображения PNG, которую можно легко настроить с помощью собственных изображений или трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="19589-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![фитбокс](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="19589-153">Технические подробности</span><span class="sxs-lookup"><span data-stu-id="19589-153">Technical details</span></span>

<span data-ttu-id="19589-154">Вы можете найти сценарии и Prefabs для периодической таблицы приложения Elements в лаборатории по [проектированию смешанной реальности в GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="19589-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="19589-155">Примеры приложений</span><span class="sxs-lookup"><span data-stu-id="19589-155">Application examples</span></span>

<span data-ttu-id="19589-156">Ниже приведены некоторые идеи, которые можно создать с помощью компонентов в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="19589-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="19589-157">Приложение для визуализации данных с акциями</span><span class="sxs-lookup"><span data-stu-id="19589-157">Stock data visualization app</span></span>

<span data-ttu-id="19589-158">С помощью тех же элементов управления и модели взаимодействия, что и в периодической таблице примера Elements, можно создать приложение, которое визуализирует данные по финансовым рынкам.</span><span class="sxs-lookup"><span data-stu-id="19589-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="19589-159">В этом примере используется элемент управления "Коллекция объектов" для размещения данных о акции в сферической форме.</span><span class="sxs-lookup"><span data-stu-id="19589-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="19589-160">Вы можете представить подробное представление, где дополнительные сведения о каждой акции могут быть отображены интересным образом.</span><span class="sxs-lookup"><span data-stu-id="19589-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Пример приложения: Финансы (1 из 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Пример приложения: Финансы (2 из 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="19589-163">![Пример приложения: Финансы (3 из 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="19589-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="19589-164">*Пример того, как коллекция объектов, используемая в периодической таблице примера приложения Elements, может использоваться в финансовом приложении*</span><span class="sxs-lookup"><span data-stu-id="19589-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="19589-165">Спортивное приложение</span><span class="sxs-lookup"><span data-stu-id="19589-165">Sports app</span></span>

<span data-ttu-id="19589-166">Это пример визуализации спортивных данных с помощью коллекции объектов и других компонентов из периодической таблицы примера приложения Elements.</span><span class="sxs-lookup"><span data-stu-id="19589-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Пример приложения: Спорт (1 из 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Пример приложения: Спорт (2 из 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="19589-169">![Пример приложения: Спорт (3 из 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="19589-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="19589-170">*Пример того, как коллекция объектов, используемая в периодической таблице примера элементов аппкаулд, должна использоваться в спортивном приложении.*</span><span class="sxs-lookup"><span data-stu-id="19589-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="19589-171">Об авторе</span><span class="sxs-lookup"><span data-stu-id="19589-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="19589-172"><b>Донг Йоон</b></span><span class="sxs-lookup"><span data-stu-id="19589-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="19589-173">Конструктор UX@Microsoft</span><span class="sxs-lookup"><span data-stu-id="19589-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="19589-174">См. также</span><span class="sxs-lookup"><span data-stu-id="19589-174">See also</span></span>

* [<span data-ttu-id="19589-175">Активный объект</span><span class="sxs-lookup"><span data-stu-id="19589-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="19589-176">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="19589-176">Object collection</span></span>](object-collection.md)
