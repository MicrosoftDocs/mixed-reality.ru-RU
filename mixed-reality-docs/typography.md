---
title: Оформление
description: Текст — важный элемент для представления сведений в интерфейсе приложения.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, разработки, стиль, шрифта, оформление, пользовательского интерфейса, ux
ms.openlocfilehash: b4bac35cbc412ec7102748350c2f5c1e236c2f7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603248"
---
# <a name="typography"></a><span data-ttu-id="de050-104">Оформление</span><span class="sxs-lookup"><span data-stu-id="de050-104">Typography</span></span>

<span data-ttu-id="de050-105">Текст — важный элемент для представления сведений в интерфейсе приложения.</span><span class="sxs-lookup"><span data-stu-id="de050-105">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="de050-106">Так же, как оформление на экранах 2D и призван быть четкими.</span><span class="sxs-lookup"><span data-stu-id="de050-106">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="de050-107">С помощью трехмерных аспектом смешанной реальности, есть возможность повлиять на текст и пользователей в целом возможности еще больше способом.</span><span class="sxs-lookup"><span data-stu-id="de050-107">With the three-dimensional aspect of mixed reality, there is an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="de050-108">![Пример типографическая разметка в HoloLens](images/640px-typography-hero2.jpg)</span><span class="sxs-lookup"><span data-stu-id="de050-108">![Typography example in HoloLens](images/640px-typography-hero2.jpg)</span></span><br>
<span data-ttu-id="de050-109">*Пример типографическая разметка в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="de050-109">*Typography example in HoloLens*</span></span>

<span data-ttu-id="de050-110">Когда мы говорим о типе в трехмерном пространстве, мы склонны думать вытянутый, объемные трехмерного текста.</span><span class="sxs-lookup"><span data-stu-id="de050-110">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="de050-111">За исключением некоторых проектах эмблема и некоторые другие ограниченные приложения вытянутый текст обычно ухудшить читаемость текста.</span><span class="sxs-lookup"><span data-stu-id="de050-111">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="de050-112">Несмотря на то, что мы разработке взаимодействия для 3D, так как это более читаемым и простым для чтения мы используем 2D для типа.</span><span class="sxs-lookup"><span data-stu-id="de050-112">Even though we are designing experiences for 3D, we use 2D for the type because it is more legible and easier to read.</span></span>

<span data-ttu-id="de050-113">В HoloLens тип создается с помощью голограммы, с помощью на основе системы аддитивные цвет света.</span><span class="sxs-lookup"><span data-stu-id="de050-113">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="de050-114">Так же, как другие голограммы типа можно поместить в реальной среде может быть заблокирован и наблюдения из любой угол.</span><span class="sxs-lookup"><span data-stu-id="de050-114">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="de050-115">[Фокусировки](https://en.wikipedia.org/wiki/Parallax) эффект между типом и среде также добавляет глубину в интерфейс.</span><span class="sxs-lookup"><span data-stu-id="de050-115">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="de050-116">Оформление в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="de050-116">Typography in mixed reality</span></span>

<span data-ttu-id="de050-117">Типографских правил в смешанной реальности ничем не отличаются от любого другого места.</span><span class="sxs-lookup"><span data-stu-id="de050-117">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="de050-118">Текст в реальном мире и виртуальный мир должна быть разборчивым и для чтения.</span><span class="sxs-lookup"><span data-stu-id="de050-118">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="de050-119">Текст может быть на стене или наложены друг на друга в объекте физического.</span><span class="sxs-lookup"><span data-stu-id="de050-119">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="de050-120">Он может с плавающей запятой вместе с цифровой пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="de050-120">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="de050-121">Вне зависимости от контекста мы применяем те же правила типографических для чтения и распознавания.</span><span class="sxs-lookup"><span data-stu-id="de050-121">Regardless of the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="de050-122">Создать четкую иерархию</span><span class="sxs-lookup"><span data-stu-id="de050-122">Create clear hierarchy</span></span>

<span data-ttu-id="de050-123">Создавайте контрастности и иерархии с помощью размеры разных типов и значений веса.</span><span class="sxs-lookup"><span data-stu-id="de050-123">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="de050-124">Определение ramp типа и следующий за ним работы приложения предоставляют удобную работу пользователя с иерархией согласованные сведения.</span><span class="sxs-lookup"><span data-stu-id="de050-124">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="de050-125">![Примеры типов увеличения](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="de050-125">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="de050-126">*Примеры типов увеличения*</span><span class="sxs-lookup"><span data-stu-id="de050-126">*Type ramp examples*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="de050-127">Ограничить шрифты</span><span class="sxs-lookup"><span data-stu-id="de050-127">Limit your fonts</span></span>

<span data-ttu-id="de050-128">Избегайте использования более двух семейств шрифтов в одном контексте.</span><span class="sxs-lookup"><span data-stu-id="de050-128">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="de050-129">Это нарушит гармонии и согласованность испытаний и усложнить как процесс использования информации.</span><span class="sxs-lookup"><span data-stu-id="de050-129">This will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="de050-130">В HoloLens так как данные накладывается поверх физической среды, с помощью слишком много стили шрифтов ухудшит работу.</span><span class="sxs-lookup"><span data-stu-id="de050-130">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="de050-131">Segoe UI — шрифт для Microsoft рисунки.</span><span class="sxs-lookup"><span data-stu-id="de050-131">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="de050-132">Она согласованно используется в оболочке Windows смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="de050-132">It is used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="de050-133">Вы можете скачать файл шрифт Segoe UI из [странице набора средств разработки Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).</span><span class="sxs-lookup"><span data-stu-id="de050-133">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="de050-134">Дополнительные сведения о шрифт Segoe UI</span><span class="sxs-lookup"><span data-stu-id="de050-134">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="de050-135">Избегайте весовые коэффициенты тонкой шрифта</span><span class="sxs-lookup"><span data-stu-id="de050-135">Avoid thin font weights</span></span>

<span data-ttu-id="de050-136">Избегайте использования Вес шрифта светлой или semilight размеры типов в разделе 42pt так, как тонкие вертикальной штрихи будет «Вибрация» и привести к снижению удобства чтения.</span><span class="sxs-lookup"><span data-stu-id="de050-136">Avoid using light or semilight font weights for type sizes under 42pt since thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="de050-137">Современные шрифтов с достаточно толщина штриха работают хорошо.</span><span class="sxs-lookup"><span data-stu-id="de050-137">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="de050-138">Например Helvetica и Arial читаются очень в HoloLens с использованием взвешенных значений с равномерным или полужирным шрифтом.</span><span class="sxs-lookup"><span data-stu-id="de050-138">For example, Helvetica and Arial are very legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="de050-139">Color</span><span class="sxs-lookup"><span data-stu-id="de050-139">Color</span></span>

<span data-ttu-id="de050-140">В HoloLens поскольку голограммы создаются с системой аддитивные света белым текстом хорошо читаемых.</span><span class="sxs-lookup"><span data-stu-id="de050-140">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="de050-141">Вы найдете примеры белый текст на меню «Пуск» и панели приложения.</span><span class="sxs-lookup"><span data-stu-id="de050-141">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="de050-142">Несмотря на то, что белым текстом работает без назад формы для HoloLens, сложными фоновыми физических может затруднить тип для чтения.</span><span class="sxs-lookup"><span data-stu-id="de050-142">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="de050-143">Чтобы повысить пользователя фокус и свести к минимуму отвлекаясь от физических фона, рекомендуется использовать белый текст на темно- или цветной обратно форме.</span><span class="sxs-lookup"><span data-stu-id="de050-143">To improve the user's focus and minimize the distraction from a physical background, we recommend using white text on a dark or colored back plate.</span></span>

<br>


![Мы рекомендуем использовать белый текст на темно- или цветной назад форме.](images/typography-whiteonblack2-1000px.jpg)

<span data-ttu-id="de050-145">Мы рекомендуем использовать белый текст на темно- или цветной назад форме.</span><span class="sxs-lookup"><span data-stu-id="de050-145">We recommend using white text on a dark or colored back plate.</span></span>

<br>


![Примеры черный текст](images/640px-typography-textcolors.jpg)

<span data-ttu-id="de050-147">Использовать темно-текст, чтобы сделать доступной для чтения следует использовать ярко-назад формы.</span><span class="sxs-lookup"><span data-stu-id="de050-147">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="de050-148">В системах аддитивные цветом отображается как прозрачный черный.</span><span class="sxs-lookup"><span data-stu-id="de050-148">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="de050-149">Это означает, что вы не сможете см. в разделе черный текст без цветные резервного формы.</span><span class="sxs-lookup"><span data-stu-id="de050-149">This means you will not be able to see the black text without a colored back plate.</span></span>

<br>


![Примеры черный текст](images/640px-typography-blackonwhite.jpg)

<span data-ttu-id="de050-151">Вы найдете примеры черный текст в приложениях универсальной платформы Windows, например Store или параметры.</span><span class="sxs-lookup"><span data-stu-id="de050-151">You can find examples of black text in UWP apps such as the Store or Settings.</span></span>

## <a name="recommended-font-size"></a><span data-ttu-id="de050-152">Рекомендованный размер шрифта</span><span class="sxs-lookup"><span data-stu-id="de050-152">Recommended font size</span></span>

![Два счетчика является оптимальной расстояние для отображения текста.](images/typography-distance-1000px.jpg)

<span data-ttu-id="de050-154">Два счетчика является оптимальной расстояние для отображения текста.</span><span class="sxs-lookup"><span data-stu-id="de050-154">Two meters is the optimal distance for displaying text.</span></span>

<span data-ttu-id="de050-155">Так как смешанной реальности подразумевает трехмерной глубины, это не всегда легко обмениваться данными размер шрифта.</span><span class="sxs-lookup"><span data-stu-id="de050-155">Since mixed reality involves three-dimensional depth, it is not always easy to communicate the size of the font.</span></span> <span data-ttu-id="de050-156">Для удобства пользователя два счетчика является оптимальной расстояние для размещения голограммы.</span><span class="sxs-lookup"><span data-stu-id="de050-156">For the user's comfort, two meters is the optimal distance for placing holograms.</span></span> <span data-ttu-id="de050-157">Это расстояние можно использовать в качестве основы для поиска оптимального размера.</span><span class="sxs-lookup"><span data-stu-id="de050-157">We can use this distance as a basis to find the optimal font size.</span></span>

<span data-ttu-id="de050-158">Как можно ожидать, размеры типов, которые мы используем на ПК или планшете (обычно от 12 – 32pt) выглядеть довольно небольшой на расстоянии 2 метров.</span><span class="sxs-lookup"><span data-stu-id="de050-158">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="de050-159">Это зависит от характеристик каждого шрифта, но в общем случае размер Рекомендуемый минимальный тип — для удобства чтения без вибрация stroke составляет около 30pt.</span><span class="sxs-lookup"><span data-stu-id="de050-159">It depends on the characteristics of each font, but in general, the recommended minimum type size for legibility without stroke vibration is around 30pt.</span></span> <span data-ttu-id="de050-160">Если приложения должны использоваться на расстоянии более подробно, может использоваться меньшего размера типа.</span><span class="sxs-lookup"><span data-stu-id="de050-160">If your app is supposed to be used at a closer distance, smaller type sizes could be used.</span></span> <span data-ttu-id="de050-161">**Размер основан на Unity 3D Mesh текст и текст пользовательского интерфейса. Подробные метрики и коэффициенты масштабирования, см. в статье [текста в Unity](text-in-unity.md).**</span><span class="sxs-lookup"><span data-stu-id="de050-161">**The point size is based on the Unity's 3D Text Mesh and UI Text. For the detailed metrics and scaling factors, please refer to [Text in Unity](text-in-unity.md).**</span></span>

## <a name="resources"></a><span data-ttu-id="de050-162">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="de050-162">Resources</span></span>
* [<span data-ttu-id="de050-163">Segoe шрифты</span><span class="sxs-lookup"><span data-stu-id="de050-163">Segoe fonts</span></span>](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [<span data-ttu-id="de050-164">HoloLens шрифта</span><span class="sxs-lookup"><span data-stu-id="de050-164">HoloLens font</span></span>](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![Шрифт HoloLens дает символ глифы, которые используются в Windows Mixed Reality](images/300px-hololensmdl2symbols.jpg)

<span data-ttu-id="de050-166">Шрифт HoloLens предоставляет символ глифы, которые используются в смешанной реальности Windows.</span><span class="sxs-lookup"><span data-stu-id="de050-166">The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.</span></span>

## <a name="see-also"></a><span data-ttu-id="de050-167">См. также</span><span class="sxs-lookup"><span data-stu-id="de050-167">See also</span></span>
* [<span data-ttu-id="de050-168">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="de050-168">Text in Unity</span></span>](http://holodocsfuture/index.php?title=Text_in_Unity&action=edit&redlink=1)
* [<span data-ttu-id="de050-169">Цвет, свет и материалы</span><span class="sxs-lookup"><span data-stu-id="de050-169">Color, light and materials</span></span>](color,-light-and-materials.md)
