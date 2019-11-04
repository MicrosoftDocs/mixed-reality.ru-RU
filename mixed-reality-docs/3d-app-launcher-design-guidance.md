---
title: Руководство по проектированию средства запуска приложений 3D
description: Средство запуска 3D-приложений — это «физический» объект в мире смешанной реальности пользователя, который можно выбрать для запуска приложения.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, проектирование, средство запуска 3D-приложений, иммерсивное головной телефон, активный куб
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437230"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="b994f-104">Руководство по проектированию средства запуска приложений 3D</span><span class="sxs-lookup"><span data-stu-id="b994f-104">3D app launcher design guidance</span></span>

<span data-ttu-id="b994f-105">Когда вы Помещаетесь на головной телефон Windows Mixed Reality (VR), вы вводите домашнюю среду Windows Mixed Reality, Визуализация в качестве дома на клиффе, окружающей горы и воду (хотя можно [выбрать другие среды и даже создать собственные](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="b994f-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="b994f-106">В рамках этого дома пользователь может размещать и упорядочивать трехмерные объекты и приложения, которые им нужны.</span><span class="sxs-lookup"><span data-stu-id="b994f-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="b994f-107">**Средство запуска 3D-приложений** — это «физический» объект в мире смешанной реальности пользователя, который можно выбрать для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b994f-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="b994f-108">![пример: средство запуска многомерных приложений с плавающей запятой](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b994f-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="b994f-109">*Пример средства запуска приложения 3D с плавающей высоты (вымышленное приложение)*</span><span class="sxs-lookup"><span data-stu-id="b994f-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="b994f-110">процесс создания средства запуска приложений 3D</span><span class="sxs-lookup"><span data-stu-id="b994f-110">3D app launcher creation process</span></span>

<span data-ttu-id="b994f-111">Создание средства запуска 3D-приложений состоит из трех этапов.</span><span class="sxs-lookup"><span data-stu-id="b994f-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="b994f-112">Проектирование и концепция (в этой статье)</span><span class="sxs-lookup"><span data-stu-id="b994f-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="b994f-113">Моделирование и экспорт</span><span class="sxs-lookup"><span data-stu-id="b994f-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="b994f-114">Интеграция этого приложения в приложение:</span><span class="sxs-lookup"><span data-stu-id="b994f-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="b994f-115">Приложения UWP</span><span class="sxs-lookup"><span data-stu-id="b994f-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="b994f-116">Приложения Win32</span><span class="sxs-lookup"><span data-stu-id="b994f-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="b994f-117">Основные понятия проектирования</span><span class="sxs-lookup"><span data-stu-id="b994f-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="b994f-118">Самое хорошо знакомое</span><span class="sxs-lookup"><span data-stu-id="b994f-118">Fantastic yet familiar</span></span>

<span data-ttu-id="b994f-119">Среда Windows Mixed Reality, в которой находится средство запуска приложений, является знакомой, а часть — более понятная или Sci-Fi.</span><span class="sxs-lookup"><span data-stu-id="b994f-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="b994f-120">Лучшие средства запуска следуют правилам этого мира.</span><span class="sxs-lookup"><span data-stu-id="b994f-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="b994f-121">Подумайте о том, как можно взять привычный репрезентативный объект из своего приложения, но с изгибим некоторые правила фактической реальности.</span><span class="sxs-lookup"><span data-stu-id="b994f-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="b994f-122">Результат будет волшебным.</span><span class="sxs-lookup"><span data-stu-id="b994f-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="b994f-123">Точки</span><span class="sxs-lookup"><span data-stu-id="b994f-123">Intuitive</span></span>

<span data-ttu-id="b994f-124">При просмотре средства запуска приложения его назначение — запуск приложения — должно быть очевидным и не должно вызывать путаницы.</span><span class="sxs-lookup"><span data-stu-id="b994f-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="b994f-125">Например, убедитесь, что средство запуска является очевидным характером приложения, которое не будет путать с дéкором в Клифф дома.</span><span class="sxs-lookup"><span data-stu-id="b994f-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="b994f-126">Средство запуска приложений должно пригласить людей для касания или выбора.</span><span class="sxs-lookup"><span data-stu-id="b994f-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="b994f-127">![пример: новое примечание.](images/20171016-152145-mixedreality1-1200px-1000px.jpg) средство запуска приложений.</span><span class="sxs-lookup"><span data-stu-id="b994f-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="b994f-128">*Последнее Примечание. Пример средства запуска приложения 3D (вымышленное приложение)*</span><span class="sxs-lookup"><span data-stu-id="b994f-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="b994f-129">Масштаб домашней страницы</span><span class="sxs-lookup"><span data-stu-id="b994f-129">Home scale</span></span>

<span data-ttu-id="b994f-130">программы запуска 3D-приложений в Клифф дома и их размер по умолчанию должны иметь смысл с другими «физическими» объектами в пространстве.</span><span class="sxs-lookup"><span data-stu-id="b994f-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="b994f-131">Если вы размещаете средство запуска рядом, скажем, дома или в какой-либо мебели, оно должно иметь вид дома и на уровне.</span><span class="sxs-lookup"><span data-stu-id="b994f-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="b994f-132">Хорошей отправной точкой является просмотр того, как он выглядит на 30 кубических сантиметрах, но помните, что пользователи могут масштабировать его в любое время.</span><span class="sxs-lookup"><span data-stu-id="b994f-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="b994f-133">Собственное — возможно</span><span class="sxs-lookup"><span data-stu-id="b994f-133">Own-able</span></span>

<span data-ttu-id="b994f-134">Средство запуска приложений должно иметь такое же значение, как объект.</span><span class="sxs-lookup"><span data-stu-id="b994f-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="b994f-135">Они будут практически соседними с этими объектами, поэтому средство запуска должно быть похоже на то, что пользователь думал, чтобы находить и хранить поблизости.</span><span class="sxs-lookup"><span data-stu-id="b994f-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="b994f-136">![пример: астро деформации 3D App Launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b994f-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="b994f-137">*Пример средства запуска Астро деформации 3D-приложения (вымышленное приложение)*</span><span class="sxs-lookup"><span data-stu-id="b994f-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="b994f-138">Распознаваемое</span><span class="sxs-lookup"><span data-stu-id="b994f-138">Recognizable</span></span>

<span data-ttu-id="b994f-139">Программа запуска 3D-приложений должна мгновенно выразить "марку вашего приложения" пользователям, которые ее видят.</span><span class="sxs-lookup"><span data-stu-id="b994f-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="b994f-140">Если в приложении есть символ звездочки или особенно идентифицируемый объект, мы рекомендуем использовать его в качестве большой части проекта.</span><span class="sxs-lookup"><span data-stu-id="b994f-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="b994f-141">В мире смешанной реальности объект будет вырисовывать больше пользователей, чем только эмблема.</span><span class="sxs-lookup"><span data-stu-id="b994f-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="b994f-142">Распознаваемые объекты быстро и четко обмениваются торговыми марками.</span><span class="sxs-lookup"><span data-stu-id="b994f-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="b994f-143">Объемные</span><span class="sxs-lookup"><span data-stu-id="b994f-143">Volumetric</span></span>

<span data-ttu-id="b994f-144">Ваше приложение заслуживает больше, чем просто поместите эмблему на плоскую плоскость и вызовите ее в день.</span><span class="sxs-lookup"><span data-stu-id="b994f-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="b994f-145">Средство запуска должно иметь вид привлекательного, трехмерного, физического объекта в пространстве пользователя.</span><span class="sxs-lookup"><span data-stu-id="b994f-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="b994f-146">Хорошим подходом является Представьте, что ваше приложение помаци в день благодарения параде.</span><span class="sxs-lookup"><span data-stu-id="b994f-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="b994f-147">Спросите себя, что же в том, что люди на самом деле не поступили на улице?</span><span class="sxs-lookup"><span data-stu-id="b994f-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="b994f-148">Что будет великолепно выглядеть со всех углов просмотра?</span><span class="sxs-lookup"><span data-stu-id="b994f-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="b994f-149">![логотип только](images/20171016-140436-mixedreality-640px.jpg) *только с логотипом*</span><span class="sxs-lookup"><span data-stu-id="b994f-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b994f-150">![более понятное значение с помощью символа](images/20171016-140557-mixedreality-640px.jpg) *более понятного символа*</span><span class="sxs-lookup"><span data-stu-id="b994f-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        <span data-ttu-id="b994f-151">![неструктурированный подход, не удивительно,](images/20171016-155101-mixedreality-640px.jpg) *плоский подход, неудивительно, необычное*</span><span class="sxs-lookup"><span data-stu-id="b994f-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b994f-152">![подход объемные лучше демонстрирует ваше приложение](images/20171016-161407-mixedreality-640px.jpg) подход, который *лучше наглядно демонстрирует ваше приложение* .</span><span class="sxs-lookup"><span data-stu-id="b994f-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="b994f-153">Советы по использованию эффективных трехмерных моделей</span><span class="sxs-lookup"><span data-stu-id="b994f-153">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="b994f-154">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="b994f-154">Best practices</span></span>
* <span data-ttu-id="b994f-155">При планировании измерений для средства запуска приложений прокрутка примерно на 30cm куб.</span><span class="sxs-lookup"><span data-stu-id="b994f-155">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="b994f-156">Таким образом, соотношение размера 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="b994f-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="b994f-157">Модели должны иметь 10 000 многоугольников.</span><span class="sxs-lookup"><span data-stu-id="b994f-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="b994f-158">Дополнительные сведения о счетчиках и уровнях сведений о треугольниках (Лодс)</span><span class="sxs-lookup"><span data-stu-id="b994f-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="b994f-159">Протестируйте иммерсивное гарнитуру, когда это возможно.</span><span class="sxs-lookup"><span data-stu-id="b994f-159">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="b994f-160">Сведения о сборке в своей геометрической модели, где это возможно — не полагайтесь на текстуры для получения подробных сведений.</span><span class="sxs-lookup"><span data-stu-id="b994f-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="b994f-161">Создание закрытой геометрии с жесткой наводами.</span><span class="sxs-lookup"><span data-stu-id="b994f-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="b994f-162">Нет отверстий, которые не моделируются в.</span><span class="sxs-lookup"><span data-stu-id="b994f-162">No holes that are not modeled in.</span></span>
* <span data-ttu-id="b994f-163">Использование природных материалов в объекте.</span><span class="sxs-lookup"><span data-stu-id="b994f-163">Use natural materials in your object.</span></span> <span data-ttu-id="b994f-164">Представьте себе создание ИТ в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="b994f-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="b994f-165">Убедитесь, что модель хорошо читается на разных расстояниях и размерах.</span><span class="sxs-lookup"><span data-stu-id="b994f-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="b994f-166">Когда модель будет готова к работе, ознакомьтесь с [рекомендациями по экспорту ресурсов](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="b994f-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="b994f-167">![модель с незначительными сведениями в текстуре](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b994f-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="b994f-168">*Модель с незначительными деталями в текстуре*</span><span class="sxs-lookup"><span data-stu-id="b994f-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="b994f-169">Что следует избегать</span><span class="sxs-lookup"><span data-stu-id="b994f-169">What to avoid</span></span>
* <span data-ttu-id="b994f-170">Не используйте подробные сведения о высокой контрастности или небольшие, занятые шаблоны и текстуры.</span><span class="sxs-lookup"><span data-stu-id="b994f-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="b994f-171">Не используйте тонкую геометрию — она не работает на расстоянии, и псевдоним будет неплохой.</span><span class="sxs-lookup"><span data-stu-id="b994f-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="b994f-172">Не разрешите, чтобы части модели не превышают размер 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="b994f-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="b994f-173">При этом создаются проблемы масштабирования.</span><span class="sxs-lookup"><span data-stu-id="b994f-173">It will create scaling problems.</span></span>

<span data-ttu-id="b994f-174">![избежать высококонтрастных и мелких загруженных шаблонов](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b994f-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="b994f-175">*Избегайте высокой контрастности, мелких, занятых шаблонов*</span><span class="sxs-lookup"><span data-stu-id="b994f-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="b994f-176">Как обрабатывает тип</span><span class="sxs-lookup"><span data-stu-id="b994f-176">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="b994f-177">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="b994f-177">Best practices</span></span>
* <span data-ttu-id="b994f-178">Рекомендуется, чтобы ваш тип состоять из примерно 1/3 средства запуска приложения (или более).</span><span class="sxs-lookup"><span data-stu-id="b994f-178">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="b994f-179">Тип — это основная вещь, которая дает пользователям представление о том, что средство запуска, на самом деле, является средством запуска, чтобы было замечательно, если оно довольно существенно.</span><span class="sxs-lookup"><span data-stu-id="b994f-179">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="b994f-180">Старайтесь не делать этот тип очень широким — старайтесь не использовать его в пределах основных измерений запуска приложения (более или меньше).</span><span class="sxs-lookup"><span data-stu-id="b994f-180">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="b994f-181">Неструктурированный тип может работать, но имейте в виду, что он может быть трудно просматривать из определенных углов и в определенных средах.</span><span class="sxs-lookup"><span data-stu-id="b994f-181">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="b994f-182">Вы можете попытаться поместить его в сплошной объект или заднем плане, чтобы помочь в этом.</span><span class="sxs-lookup"><span data-stu-id="b994f-182">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="b994f-183">Добавление измерения к типу отлично выглядит в трехмерном виде.</span><span class="sxs-lookup"><span data-stu-id="b994f-183">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="b994f-184">Заливка сторон типа, более темного цвета, может помочь в удобочитаемости.</span><span class="sxs-lookup"><span data-stu-id="b994f-184">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="b994f-185">![неструктурированный тип без задника может быть трудно просматривать из определенных углов и в определенных средах](images/flattype-640px.png) *плоский тип без задника может быть трудно просматривать из определенных углов и в определенных средах* .</span><span class="sxs-lookup"><span data-stu-id="b994f-185">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b994f-186">Тип ![с помощью встроенного задния может работать правильно](images/flattypeandbkg-640px.png) *тип с помощью встроенного задния может работать правильно*</span><span class="sxs-lookup"><span data-stu-id="b994f-186">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b994f-187">![вытянутый тип может хорошо работать, если заливка сторон](images/20171016-160221-mixedreality-640px.jpg) *вытянутый тип может быть хорошо работать при затенении сторон*</span><span class="sxs-lookup"><span data-stu-id="b994f-187">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::


<span data-ttu-id="b994f-188">**Введите цвета, которые работают**</span><span class="sxs-lookup"><span data-stu-id="b994f-188">**Type colors that work**</span></span>
* <span data-ttu-id="b994f-189">Белый</span><span class="sxs-lookup"><span data-stu-id="b994f-189">White</span></span>
* <span data-ttu-id="b994f-190">экран</span><span class="sxs-lookup"><span data-stu-id="b994f-190">Black</span></span>
* <span data-ttu-id="b994f-191">Яркий насыщенный цвет</span><span class="sxs-lookup"><span data-stu-id="b994f-191">Bright semi-saturated color</span></span>

<span data-ttu-id="b994f-192">![цвета типа.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b994f-192">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="b994f-193">*Введите цвета, которые работают*</span><span class="sxs-lookup"><span data-stu-id="b994f-193">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="b994f-194">Что следует избегать</span><span class="sxs-lookup"><span data-stu-id="b994f-194">What to avoid</span></span>

<span data-ttu-id="b994f-195">**Типы цветов, вызывающие проблемы**</span><span class="sxs-lookup"><span data-stu-id="b994f-195">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="b994f-196">Средние тона</span><span class="sxs-lookup"><span data-stu-id="b994f-196">Mid-tones</span></span>
* <span data-ttu-id="b994f-197">Gray</span><span class="sxs-lookup"><span data-stu-id="b994f-197">Gray</span></span>
* <span data-ttu-id="b994f-198">Чрезмерно насыщенные цвета или ненасыщенные цвета</span><span class="sxs-lookup"><span data-stu-id="b994f-198">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="b994f-199">![цвета типа, которые вызывают проблемы.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b994f-199">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="b994f-200">*Типы цветов, вызывающие проблемы*</span><span class="sxs-lookup"><span data-stu-id="b994f-200">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="b994f-201">Освещение</span><span class="sxs-lookup"><span data-stu-id="b994f-201">Lighting</span></span>

<span data-ttu-id="b994f-202">Освещение для программы запуска приложений поступает из среды Клифф House.</span><span class="sxs-lookup"><span data-stu-id="b994f-202">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="b994f-203">Обязательно протестируйте средство запуска в нескольких местах дома, чтобы оно хорошо выглядело как светлое, так и темнее.</span><span class="sxs-lookup"><span data-stu-id="b994f-203">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="b994f-204">Хорошая новость состоит в том, что, если вы использовали другие рекомендации по проектированию в этом документе, средство запуска должно быть достаточно хорошим для большинства освещения в Клифф дома.</span><span class="sxs-lookup"><span data-stu-id="b994f-204">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="b994f-205">Для проверки того, как средство запуска выполняет поиск различных источников света в среде, это среда, комната мультимедиа, где-то вне и обратно патио (конкретная область с зеленая трава).</span><span class="sxs-lookup"><span data-stu-id="b994f-205">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="b994f-206">Еще один хороший тест — поместив его на половину светлой и половинной тени и посмотрим, как он выглядит.</span><span class="sxs-lookup"><span data-stu-id="b994f-206">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="b994f-207">![убедитесь, что средство запуска хорошо смотрится как в светлых, так и в тенях.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b994f-207">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="b994f-208">*Убедитесь, что средство запуска хорошо смотрится как на светлой, так и в тенях.*</span><span class="sxs-lookup"><span data-stu-id="b994f-208">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="b994f-209">Текстуризации</span><span class="sxs-lookup"><span data-stu-id="b994f-209">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="b994f-210">Создание текстур</span><span class="sxs-lookup"><span data-stu-id="b994f-210">Authoring your textures</span></span>

<span data-ttu-id="b994f-211">В качестве конечного формата средства запуска 3D-приложений будет использоваться файл. GLBA, который выполняется с помощью конвейера PBR (с физическим рендерингом).</span><span class="sxs-lookup"><span data-stu-id="b994f-211">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="b994f-212">Это может быть непростой процесс. Теперь вы можете использовать технический исполнитель, если вы еще этого не сделали.</span><span class="sxs-lookup"><span data-stu-id="b994f-212">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="b994f-213">Если вы дивный DIY-ER, то сможете [исследовать и изучать терминологию PBR](https://wiki.polycount.com/wiki/PBR) , а также узнать о том, что происходит, прежде чем приступать к работе, поможет избежать распространенных ошибок.</span><span class="sxs-lookup"><span data-stu-id="b994f-213">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="b994f-214">![пример: новое приложение для заметок](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="b994f-214">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="b994f-215">*Последнее Примечание. Пример средства запуска приложения 3D (вымышленное приложение)*</span><span class="sxs-lookup"><span data-stu-id="b994f-215">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="b994f-216">**Рекомендуемое средство разработки**</span><span class="sxs-lookup"><span data-stu-id="b994f-216">**Recommended authoring tool**</span></span>

<span data-ttu-id="b994f-217">Мы рекомендуем использовать [веществ по образцу](https://www.allegorithmic.com/products/substance-painter) аллегорисмик для создания окончательного файла.</span><span class="sxs-lookup"><span data-stu-id="b994f-217">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="b994f-218">Если вы не знакомы с созданием шейдеров PBR в веществ по образцу, ознакомьтесь с [руководством](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="b994f-218">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="b994f-219">(Как вариант [трехмерной](https://3dcoat.com/home/), так и [куиксел Suite 2](https://quixel.se/suite2/)или [Мармосет тулбаг](https://www.marmoset.co/toolbag/) также будут работать, если вы более знакомы с одним из них.)</span><span class="sxs-lookup"><span data-stu-id="b994f-219">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="b994f-220">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="b994f-220">Best practices</span></span>

* <span data-ttu-id="b994f-221">Если объект запуска приложения был создан для PBR, он должен просто преобразовать его для среды Клифф House.</span><span class="sxs-lookup"><span data-stu-id="b994f-221">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="b994f-222">Наш шейдер ожидает рабочий поток "металл/грубая" — недействительный шейдер PBR является закрытым факсом.</span><span class="sxs-lookup"><span data-stu-id="b994f-222">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="b994f-223">При экспорте текстур не забывайте о [рекомендуемых размерах текстур](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .</span><span class="sxs-lookup"><span data-stu-id="b994f-223">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="b994f-224">Не забудьте собрать объекты для освещения в режиме реального времени — это означает:</span><span class="sxs-lookup"><span data-stu-id="b994f-224">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="b994f-225">Избегайте помогут теней — или нарисованных теней</span><span class="sxs-lookup"><span data-stu-id="b994f-225">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="b994f-226">Предотвращение помогут освещения текстур</span><span class="sxs-lookup"><span data-stu-id="b994f-226">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="b994f-227">Используйте один из пакетов для создания данных типа PBR, чтобы получить правильные карты, созданные для нашего шейдера.</span><span class="sxs-lookup"><span data-stu-id="b994f-227">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="b994f-228">См. также</span><span class="sxs-lookup"><span data-stu-id="b994f-228">See also</span></span>

* [<span data-ttu-id="b994f-229">Создание трехмерных моделей для использования на домашней странице смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="b994f-229">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="b994f-230">Реализация средств запуска трехмерных приложений (приложения UWP)</span><span class="sxs-lookup"><span data-stu-id="b994f-230">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="b994f-231">Реализация средств запуска трехмерных приложений (приложения Win32)</span><span class="sxs-lookup"><span data-stu-id="b994f-231">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
