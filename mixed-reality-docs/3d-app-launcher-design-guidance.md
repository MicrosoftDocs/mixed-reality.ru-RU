---
title: Руководство по проектированию приложения трехмерной запуска
description: Запуск приложения трехмерной является «физический» объектом в смешанной реальности домик пользователя, который пользователи могут выбрать для запуска приложения.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, разработки, запуска трехмерных приложений, иммерсивных гарнитура live куба
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598549"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="4f96f-104">Руководство по проектированию приложения трехмерной запуска</span><span class="sxs-lookup"><span data-stu-id="4f96f-104">3D app launcher design guidance</span></span>

<span data-ttu-id="4f96f-105">Поместить на гарнитуры смешанной реальности Windows иммерсивных (VR), вводится Windows Mixed Reality дома, представить в виде дом на со скалы заключенных в горы и воды (хотя вы можете [выберите других средах и даже создавать собственные](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="4f96f-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="4f96f-106">В пространстве это дома, пользователь может упорядочивания и организации трехмерные объекты и приложения, которые их интересуют любым способом, нужные им.</span><span class="sxs-lookup"><span data-stu-id="4f96f-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="4f96f-107">Объект **запуска трехмерных приложений** — объект «физический» пользователь смешанном реальности домик, который пользователи могут выбрать для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="4f96f-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="4f96f-108">![Пример: Floaty запуска Bird трехмерных приложений](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f96f-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4f96f-109">*Пример запуска трехмерного приложения floaty Bird (вымышленной приложение)*</span><span class="sxs-lookup"><span data-stu-id="4f96f-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="4f96f-110">Процесс создания приложения трехмерной запуска</span><span class="sxs-lookup"><span data-stu-id="4f96f-110">3D app launcher creation process</span></span>

<span data-ttu-id="4f96f-111">Существует 3 шага к созданию запуска трехмерных приложений:</span><span class="sxs-lookup"><span data-stu-id="4f96f-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="4f96f-112">Проектирование и concepting (Эта статья)</span><span class="sxs-lookup"><span data-stu-id="4f96f-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="4f96f-113">Моделирование и экспорт</span><span class="sxs-lookup"><span data-stu-id="4f96f-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="4f96f-114">Интеграции его в приложении:</span><span class="sxs-lookup"><span data-stu-id="4f96f-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="4f96f-115">Приложения UWP</span><span class="sxs-lookup"><span data-stu-id="4f96f-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="4f96f-116">Приложения Win32</span><span class="sxs-lookup"><span data-stu-id="4f96f-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="4f96f-117">Принципы проектирования</span><span class="sxs-lookup"><span data-stu-id="4f96f-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="4f96f-118">Отлично, но знакомый</span><span class="sxs-lookup"><span data-stu-id="4f96f-118">Fantastic yet familiar</span></span>

<span data-ttu-id="4f96f-119">Живет в средстве запуска приложений в Windows Mixed Reality среды — часть знакомых, часть фантастических/sci-fi.</span><span class="sxs-lookup"><span data-stu-id="4f96f-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="4f96f-120">Лучшие средства запуска следуют правилам этот мир.</span><span class="sxs-lookup"><span data-stu-id="4f96f-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="4f96f-121">Можно рассматривать как можно занять объект знакомая и репрезентативной из приложения, но приспособить некоторые правила фактическое реальностью.</span><span class="sxs-lookup"><span data-stu-id="4f96f-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="4f96f-122">Волшебная приведет к.</span><span class="sxs-lookup"><span data-stu-id="4f96f-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="4f96f-123">Интуитивно понятный</span><span class="sxs-lookup"><span data-stu-id="4f96f-123">Intuitive</span></span>

<span data-ttu-id="4f96f-124">Если взглянуть на ваши средства запуска приложений, его назначение — для запуска приложения - должно быть очевидно и не будет вызывать путаницу.</span><span class="sxs-lookup"><span data-stu-id="4f96f-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="4f96f-125">Например убедитесь, что ваши средства запуска является очевидным достаточно представителем своего приложения, не следует путать части обстановки в доме со скалы.</span><span class="sxs-lookup"><span data-stu-id="4f96f-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="4f96f-126">В средстве запуска приложений следует пригласить участников сенсорного ввода или выбирать его.</span><span class="sxs-lookup"><span data-stu-id="4f96f-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="4f96f-127">![Пример: Новые средства запуска приложения трехмерной Примечание](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f96f-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4f96f-128">*Пример запуска трехмерного приложения новой Примечание (вымышленной приложение)*</span><span class="sxs-lookup"><span data-stu-id="4f96f-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="4f96f-129">Домашний масштабирования</span><span class="sxs-lookup"><span data-stu-id="4f96f-129">Home scale</span></span>

<span data-ttu-id="4f96f-130">Средствах запуска приложений 3D live со скалы дома и их размер по умолчанию должна быть вам понятной относительно других объектов «физический» в пространстве.</span><span class="sxs-lookup"><span data-stu-id="4f96f-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="4f96f-131">Если ваши средства запуска рядом с полем, скажем, на предприятии дома или некоторые мебель, все должно быть дома, size-wise.</span><span class="sxs-lookup"><span data-stu-id="4f96f-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="4f96f-132">Чтобы посмотреть, как он выглядит в сантиметрах 30 третьего, но помните, что пользователям можно масштабировать его вверх или вниз при является хорошей отправной точкой.</span><span class="sxs-lookup"><span data-stu-id="4f96f-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="4f96f-133">Может владеть</span><span class="sxs-lookup"><span data-stu-id="4f96f-133">Own-able</span></span>

<span data-ttu-id="4f96f-134">Средство запуска приложений следует считать объект, который пользователь будет рады принять в своем пространстве.</span><span class="sxs-lookup"><span data-stu-id="4f96f-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="4f96f-135">Они будут практически вокруг сами подобными вещами, поэтому средство запуска должно быть так, как будто мысль пользователя было достаточно желательным, поиска и оставить рядом.</span><span class="sxs-lookup"><span data-stu-id="4f96f-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="4f96f-136">![Пример: Средство запуска Astro деформации трехмерных приложений](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f96f-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4f96f-137">*Пример запуска трехмерного приложения Astro Warp (вымышленной приложение)*</span><span class="sxs-lookup"><span data-stu-id="4f96f-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="4f96f-138">Распознаваемые</span><span class="sxs-lookup"><span data-stu-id="4f96f-138">Recognizable</span></span>

<span data-ttu-id="4f96f-139">Средство запуска вашего приложения трехмерной мгновенно должна отображать «приложения-brand» пользователям, см. в разделе, он.</span><span class="sxs-lookup"><span data-stu-id="4f96f-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="4f96f-140">Если в приложении имеется символ типа "звезда" или объект особенно характера, рекомендуется использовать, как часть проекта.</span><span class="sxs-lookup"><span data-stu-id="4f96f-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="4f96f-141">В современном мире, смешанной реальности объект будет рисования больший интерес от пользователей, чем просто логотип отдельно.</span><span class="sxs-lookup"><span data-stu-id="4f96f-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="4f96f-142">Узнаваемых объектов взаимодействия торговой марки, легко и быстро.</span><span class="sxs-lookup"><span data-stu-id="4f96f-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="4f96f-143">Объемные</span><span class="sxs-lookup"><span data-stu-id="4f96f-143">Volumetric</span></span>

<span data-ttu-id="4f96f-144">Приложение заслуживает больше, чем просто поместить ваш логотип на плоскость и чем уверовать.</span><span class="sxs-lookup"><span data-stu-id="4f96f-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="4f96f-145">Ваши средства запуска следует считать замечательных, 3D и физического объекта в пространстве пользователя.</span><span class="sxs-lookup"><span data-stu-id="4f96f-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="4f96f-146">Представьте, что приложение будет иметь всплывающую в первые ряды Парада День благодарения Macy — Хороший подход.</span><span class="sxs-lookup"><span data-stu-id="4f96f-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="4f96f-147">Задайте себе вопрос: что бы действительно wow людей как он указан на улице?</span><span class="sxs-lookup"><span data-stu-id="4f96f-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="4f96f-148">Будет выглядеть отлично со всех сторон просмотра?</span><span class="sxs-lookup"><span data-stu-id="4f96f-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="4f96f-149">Советы по хорошие трехмерной модели</span><span class="sxs-lookup"><span data-stu-id="4f96f-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="4f96f-150">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4f96f-150">Best practices</span></span>
* <span data-ttu-id="4f96f-151">При планировании аналитики для запуска вашего приложения, ограничить это примерно 30cm куба.</span><span class="sxs-lookup"><span data-stu-id="4f96f-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="4f96f-152">Таким образом, 1: соотношением 1:1.</span><span class="sxs-lookup"><span data-stu-id="4f96f-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="4f96f-153">Модели должны быть уровнем ниже 10 000 многоугольников.</span><span class="sxs-lookup"><span data-stu-id="4f96f-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="4f96f-154">Дополнительные сведения о треугольник счетчики и уровни подробности (LODs)</span><span class="sxs-lookup"><span data-stu-id="4f96f-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="4f96f-155">Проверка в иммерсивных гарнитура, когда это возможно.</span><span class="sxs-lookup"><span data-stu-id="4f96f-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="4f96f-156">Сведения о сборке в вашей модели geometry, где это возможно, не полагайтесь на текстур для детализации.</span><span class="sxs-lookup"><span data-stu-id="4f96f-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="4f96f-157">Создание геометрического объекта в «water тесной» закрыто.</span><span class="sxs-lookup"><span data-stu-id="4f96f-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="4f96f-158">Нет дыр, которые не моделируются в.</span><span class="sxs-lookup"><span data-stu-id="4f96f-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="4f96f-159">Используйте natural материалы в объекте.</span><span class="sxs-lookup"><span data-stu-id="4f96f-159">Use natural materials in your object.</span></span> <span data-ttu-id="4f96f-160">Представьте себе, создания его в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="4f96f-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="4f96f-161">Убедитесь, что модель считывает хорошо на различных расстояниях и размеры.</span><span class="sxs-lookup"><span data-stu-id="4f96f-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="4f96f-162">Когда модель готова к работе, чтение [Экспорт активы рекомендации](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="4f96f-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="4f96f-163">![Модель с тонких моментов в текстуре](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f96f-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4f96f-164">*Модель с тонких моментов в текстуре*</span><span class="sxs-lookup"><span data-stu-id="4f96f-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="4f96f-165">Чего следует избегать</span><span class="sxs-lookup"><span data-stu-id="4f96f-165">What to avoid</span></span>
* <span data-ttu-id="4f96f-166">Не используйте сведения о высокой контрастности или шаблоны небольшой, занят и текстур.</span><span class="sxs-lookup"><span data-stu-id="4f96f-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="4f96f-167">Не использовать тонкую geometry-он не работают хорошо на расстоянии и будет плохо псевдоним.</span><span class="sxs-lookup"><span data-stu-id="4f96f-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="4f96f-168">Не позволяйте частями модели расширения слишком много, помимо 1: соотношением 1:1.</span><span class="sxs-lookup"><span data-stu-id="4f96f-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="4f96f-169">Он создаст проблемы масштабирования.</span><span class="sxs-lookup"><span data-stu-id="4f96f-169">It will create scaling problems.</span></span>

<span data-ttu-id="4f96f-170">![Избегайте высокой контрастности, "мелкая" занят шаблоны](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f96f-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4f96f-171">*Избегайте высокой контрастности, small, занят шаблоны*</span><span class="sxs-lookup"><span data-stu-id="4f96f-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="4f96f-172">Как обрабатывать тип</span><span class="sxs-lookup"><span data-stu-id="4f96f-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="4f96f-173">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4f96f-173">Best practices</span></span>
* <span data-ttu-id="4f96f-174">Мы рекомендуем вашего типа состоит из примерно треть из вашего средства запуска приложений (или больше).</span><span class="sxs-lookup"><span data-stu-id="4f96f-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="4f96f-175">Тип — главное, что предоставляет сотрудникам идею, ваши средства запуска, на самом деле, запуска, поэтому весьма удобно, если это довольно значительной.</span><span class="sxs-lookup"><span data-stu-id="4f96f-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="4f96f-176">Избежать создания очень широкий тип — попытаться сохранить его в пределах средствах запуска приложений core измерения (больше или меньше).</span><span class="sxs-lookup"><span data-stu-id="4f96f-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="4f96f-177">Плоский тип можно работать, но имейте в виду, что он может быть трудно просмотреть определенные углами и в некоторых средах.</span><span class="sxs-lookup"><span data-stu-id="4f96f-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="4f96f-178">Окончательная объемный предмет или backdrop за его, чтобы помочь в этом может потребоваться.</span><span class="sxs-lookup"><span data-stu-id="4f96f-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="4f96f-179">Добавление измерений к типу выглядит неплохо в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="4f96f-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="4f96f-180">Заливка сторон типа другой, более темный оттенок цвета можно способствует повышению удобочитаемости.</span><span class="sxs-lookup"><span data-stu-id="4f96f-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="4f96f-181">**Тип цвета, которые работают**</span><span class="sxs-lookup"><span data-stu-id="4f96f-181">**Type colors that work**</span></span>
* <span data-ttu-id="4f96f-182">Белый</span><span class="sxs-lookup"><span data-stu-id="4f96f-182">White</span></span>
* <span data-ttu-id="4f96f-183">Черный</span><span class="sxs-lookup"><span data-stu-id="4f96f-183">Black</span></span>
* <span data-ttu-id="4f96f-184">Ярко-частично насыщенный оттенок</span><span class="sxs-lookup"><span data-stu-id="4f96f-184">Bright semi-saturated color</span></span>

<span data-ttu-id="4f96f-185">![Тип цвета, которые работают.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f96f-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4f96f-186">*Тип цвета, которые работают*</span><span class="sxs-lookup"><span data-stu-id="4f96f-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="4f96f-187">Чего следует избегать</span><span class="sxs-lookup"><span data-stu-id="4f96f-187">What to avoid</span></span>

<span data-ttu-id="4f96f-188">**Тип цвета, вызывающие проблемы**</span><span class="sxs-lookup"><span data-stu-id="4f96f-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="4f96f-189">Среднего тона</span><span class="sxs-lookup"><span data-stu-id="4f96f-189">Mid-tones</span></span>
* <span data-ttu-id="4f96f-190">Серый</span><span class="sxs-lookup"><span data-stu-id="4f96f-190">Gray</span></span>
* <span data-ttu-id="4f96f-191">Чрезмерно загруженных цветов или после приведения к серому цветов</span><span class="sxs-lookup"><span data-stu-id="4f96f-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="4f96f-192">![Тип цвета, вызывающие проблемы.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f96f-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4f96f-193">*Тип цвета, вызывающие проблемы*</span><span class="sxs-lookup"><span data-stu-id="4f96f-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="4f96f-194">Освещение</span><span class="sxs-lookup"><span data-stu-id="4f96f-194">Lighting</span></span>

<span data-ttu-id="4f96f-195">Освещение для запуска вашего приложения поступающие от среды со скалы дома.</span><span class="sxs-lookup"><span data-stu-id="4f96f-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="4f96f-196">Не забудьте проверить ваши средства запуска в нескольких местах в помещении, так выглядит неплохо света и теней.</span><span class="sxs-lookup"><span data-stu-id="4f96f-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="4f96f-197">Хорошая новость состоит, если вы выполнили другие рекомендации в этом документе, в средство запуска должен быть довольно правильно настроены для большинства освещения в доме со скалы.</span><span class="sxs-lookup"><span data-stu-id="4f96f-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="4f96f-198">Хорошим материалом для тестирования, как выглядят ваши средства запуска в различные источники света в среде являются Studio комнате мультимедиа, в любом месте за пределами и обратно во дворе дома (конкретные области с помощью пользуясь).</span><span class="sxs-lookup"><span data-stu-id="4f96f-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="4f96f-199">Еще один хороший тест — поместить его в половину свет и тень половину и см. в разделе, как выглядит.</span><span class="sxs-lookup"><span data-stu-id="4f96f-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="4f96f-200">![Убедитесь, что ваши средства запуска вас устраивает света и теней.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f96f-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4f96f-201">*Убедитесь, что ваши средства запуска вас устраивает света и теней*</span><span class="sxs-lookup"><span data-stu-id="4f96f-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="4f96f-202">Ускорение текстур</span><span class="sxs-lookup"><span data-stu-id="4f96f-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="4f96f-203">Создание текстуры</span><span class="sxs-lookup"><span data-stu-id="4f96f-203">Authoring your textures</span></span>

<span data-ttu-id="4f96f-204">Конечный формат вашего запуска трехмерных приложений будет файл .glb, который выполняется с помощью конвейера PBR (физически основе визуализации).</span><span class="sxs-lookup"><span data-stu-id="4f96f-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="4f96f-205">Это может быть сложным процессом - пришло, пора использовать Технический исполнителя, если у вас еще нет.</span><span class="sxs-lookup"><span data-stu-id="4f96f-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="4f96f-206">Если вас хватит смелости с НУЛЯ er, уделили [анализом и этой статье объясняется терминология PBR](http://wiki.polycount.com/wiki/PBR) и что происходит за кулисами, перед началом работы поможет вам избежать распространенных ошибок.</span><span class="sxs-lookup"><span data-stu-id="4f96f-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="4f96f-207">![Пример: Примечание новые приложения](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="4f96f-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="4f96f-208">*Пример запуска трехмерного приложения новой Примечание (вымышленной приложение)*</span><span class="sxs-lookup"><span data-stu-id="4f96f-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="4f96f-209">**Рекомендуется использовать средство разработки**</span><span class="sxs-lookup"><span data-stu-id="4f96f-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="4f96f-210">Мы рекомендуем использовать [вещества образцу](https://www.allegorithmic.com/products/substance-painter) по Allegorithmic для создания окончательного файла.</span><span class="sxs-lookup"><span data-stu-id="4f96f-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="4f96f-211">Если вы не знакомы с созданием шейдеров PBR в вещества художника, здесь [руководстве](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="4f96f-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="4f96f-212">(Можно также [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), или [Marmoset Toolbag](https://www.marmoset.co/toolbag/) также будет работать, если вы более подробно ознакомиться с одним из них.)</span><span class="sxs-lookup"><span data-stu-id="4f96f-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="4f96f-213">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4f96f-213">Best practices</span></span>

* <span data-ttu-id="4f96f-214">Если объект запуска вашего приложения был создан для PBR, оно должно быть довольно просто, для преобразования его в среде со скалы дома.</span><span class="sxs-lookup"><span data-stu-id="4f96f-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="4f96f-215">Закрыть факсимильное наших шейдера ожидает рабочего процесса без операционной системы/неровности прежнюю Unreal PBR шейдера.</span><span class="sxs-lookup"><span data-stu-id="4f96f-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="4f96f-216">При экспорте текстуры Сохранить [рекомендуемые размеры текстуры](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) в виду.</span><span class="sxs-lookup"><span data-stu-id="4f96f-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="4f96f-217">Убедитесь, что для создания объектов для освещения в режиме реального времени — это означает, что:</span><span class="sxs-lookup"><span data-stu-id="4f96f-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="4f96f-218">Избегайте архивированные тени — или закрашиваемой shadows</span><span class="sxs-lookup"><span data-stu-id="4f96f-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="4f96f-219">Избегайте архивированные освещения в текстуры</span><span class="sxs-lookup"><span data-stu-id="4f96f-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="4f96f-220">Использовать один PBR материала, разработка пакетов, чтобы установить правой карты, созданные для наших шейдера</span><span class="sxs-lookup"><span data-stu-id="4f96f-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="4f96f-221">См. также</span><span class="sxs-lookup"><span data-stu-id="4f96f-221">See also</span></span>

* [<span data-ttu-id="4f96f-222">Создавать трехмерные модели для использования в смешанной реальности home</span><span class="sxs-lookup"><span data-stu-id="4f96f-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="4f96f-223">Реализовать средствах запуска трехмерных приложений (приложения UWP)</span><span class="sxs-lookup"><span data-stu-id="4f96f-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="4f96f-224">Реализовать средствах запуска трехмерных приложений (приложения Win32)</span><span class="sxs-lookup"><span data-stu-id="4f96f-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
