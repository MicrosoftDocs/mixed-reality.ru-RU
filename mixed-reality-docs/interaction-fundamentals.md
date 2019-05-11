---
title: Общие сведения о Многорежимные взаимодействия
description: Обзор Многорежимные взаимодействия
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Смешанной реальности, взглядом, взглядом, предназначенные для взаимодействия, проектирование
ms.openlocfilehash: 8c578d9a67f6809df69fb132f4c46a381726596e
ms.sourcegitcommit: d6d96d552ec10cd7e6502fbbc1905432e2878325
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524339"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="d1c35-104">Знакомство с instinctual взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d1c35-104">Introducing instinctual interactions</span></span>
<span data-ttu-id="d1c35-105">Философии простой, instinctual взаимодействия является вовлеченным во всей платформе Microsoft смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d1c35-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="d1c35-106">Мы получили три действия, чтобы убедиться, что приложение проектировщикам и разработчикам может предоставить простой и понятный взаимодействие для своих клиентов.</span><span class="sxs-lookup"><span data-stu-id="d1c35-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="d1c35-107">Во-первых мы внесли том, что наши удивительные датчиков и входной технологии, включая отслеживание вручную, отслеживания и естественного языка, объединить беспрепятственного взаимодействия Многорежимные моделей.</span><span class="sxs-lookup"><span data-stu-id="d1c35-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="d1c35-108">Исходя из нашего исследования, проектирование и разработка multimodally--и не зависит от отдельных входных данных — является ключом к возможности instinctual.</span><span class="sxs-lookup"><span data-stu-id="d1c35-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="d1c35-109">Во-вторых, мы понимаем, что многие разработчики нескольких устройств, используется ли HoloLens 2 и HoloLens (1-го поколения) или HoloLens, так и виртуальной Реальности.</span><span class="sxs-lookup"><span data-stu-id="d1c35-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="d1c35-110">Поэтому мы разработали наших моделей взаимодействия для работы на устройствах (даже если технологии ввода меняется на каждом устройстве).</span><span class="sxs-lookup"><span data-stu-id="d1c35-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="d1c35-111">К примеру дальней взаимодействия на Windows Иммерсивных гарнитура с контроллером 6DoF и дальней взаимодействия для HoloLens 2 оба используют одинаковые читаемости и шаблоны, что упрощает для приложений между устройствами.</span><span class="sxs-lookup"><span data-stu-id="d1c35-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="d1c35-112">Не только удобна этом для разработчиков и конструкторов, но является естественным для конечных пользователей.</span><span class="sxs-lookup"><span data-stu-id="d1c35-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="d1c35-113">Наконец, хотя мы понимаем, что существуют тысячи вступают в силу, привлекательными и магического взаимодействия в MR, мы пришли к выводу, намеренно применение модели одно взаимодействие сквозного в приложение — лучший способ обеспечить, организовать и более удобной.</span><span class="sxs-lookup"><span data-stu-id="d1c35-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="d1c35-114">С этой целью мы включили три действия в этом руководстве взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="d1c35-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="d1c35-115">Мы структурировали этот о будущем три модели основного механизма взаимодействия и компонентов, а также шаблоны для каждого</span><span class="sxs-lookup"><span data-stu-id="d1c35-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="d1c35-116">Сюда включены дополнительные указания на других преимуществ, предоставляемых нашей платформы</span><span class="sxs-lookup"><span data-stu-id="d1c35-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="d1c35-117">Мы включили в рекомендации, помогающие выбрать модель соответствующие взаимодействия для вашего сценария</span><span class="sxs-lookup"><span data-stu-id="d1c35-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>


## <a name="three-multimodal-interaction-models"></a><span data-ttu-id="d1c35-118">Три модели Многорежимные взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d1c35-118">Three multimodal interaction models</span></span>
<span data-ttu-id="d1c35-119">На основе нашей исследований и работы с клиентами для даты, мы узнали, что три модели основного механизма взаимодействия соответствии большинство функций, смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d1c35-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of Mixed Reality experiences.</span></span>

<span data-ttu-id="d1c35-120">Во многих отношениях модель взаимодействия является ментальной модели пользователя для выполнения своих потоков.</span><span class="sxs-lookup"><span data-stu-id="d1c35-120">In many ways, the interaction model  is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="d1c35-121">Каждая из этих моделей взаимодействия оптимизирован для набора потребности клиентов, и каждый является удобным, эффективные и может использоваться сама по себе.</span><span class="sxs-lookup"><span data-stu-id="d1c35-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="d1c35-122">На представленной ниже диаграмме представляет собой упрощенный Обзор.</span><span class="sxs-lookup"><span data-stu-id="d1c35-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="d1c35-123">Подробные сведения по использованию каждой модели взаимодействия связана в последовательности страниц ниже с изображениями и примеры кода.</span><span class="sxs-lookup"><span data-stu-id="d1c35-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span>  

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d1c35-124"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="d1c35-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="d1c35-125"><strong>Примеры сценариев</strong></span><span class="sxs-lookup"><span data-stu-id="d1c35-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="d1c35-126"><strong>по размеру</strong></span><span class="sxs-lookup"><span data-stu-id="d1c35-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="d1c35-127"><strong>Оборудование</strong></span><span class="sxs-lookup"><span data-stu-id="d1c35-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d1c35-128"><a href="hands-and-tools.md">Руки и средства</a></span><span class="sxs-lookup"><span data-stu-id="d1c35-128"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="d1c35-129">Трехмерные эффекты пространственных</span><span class="sxs-lookup"><span data-stu-id="d1c35-129">3D spatial experiences</span></span><br><span data-ttu-id="d1c35-130">Например пространственных макета и проектирования, обработка содержимого или моделирования</span><span class="sxs-lookup"><span data-stu-id="d1c35-130">e.g. spatial layout and design, content manipulation, or simulation</span></span></td>
        <td><span data-ttu-id="d1c35-131">Отлично подходят для новых пользователей</span><span class="sxs-lookup"><span data-stu-id="d1c35-131">Great for new users</span></span><br><span data-ttu-id="d1c35-132">Короткое время обучения</span><span class="sxs-lookup"><span data-stu-id="d1c35-132">Low learning curve</span></span><br><span data-ttu-id="d1c35-133">На основе точных легко читаемости visual</span><span class="sxs-lookup"><span data-stu-id="d1c35-133">Grounded in easy visual affordances</span></span><br><span data-ttu-id="d1c35-134">Согласованное UX в наличии отслеживания и контроллеры 6DoF</span><span class="sxs-lookup"><span data-stu-id="d1c35-134">Consistent UX across hand tracking and 6DoF controllers</span></span><br><span data-ttu-id="d1c35-135">Отлично, в сочетании с voice, отслеживания, head или помощи</span><span class="sxs-lookup"><span data-stu-id="d1c35-135">Great when coupled with voice, eye tracking, or head gaze</span></span></td>
        <td><span data-ttu-id="d1c35-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d1c35-136">HoloLens 2</span></span><br><span data-ttu-id="d1c35-137">Windows Иммерсивных с 6DoF контроллеров</span><span class="sxs-lookup"><span data-stu-id="d1c35-137">Windows Immersive w/ 6DoF Controllers</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d1c35-138"><a href="hands-free.md">Режимы без использования рук</a></span><span class="sxs-lookup"><span data-stu-id="d1c35-138"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="d1c35-139">Контекстные взаимодействия, где руки пользователя будут заняты например на обучение, обслуживание задания</span><span class="sxs-lookup"><span data-stu-id="d1c35-139">Contextual experiences where a user's hands are occupied e.g. on the-job learning, maintenance</span></span></td>
        <td><span data-ttu-id="d1c35-140">Некоторые обучения требуется</span><span class="sxs-lookup"><span data-stu-id="d1c35-140">Some learning required</span></span><br><span data-ttu-id="d1c35-141">Если руки недоступны</span><span class="sxs-lookup"><span data-stu-id="d1c35-141">If hands are unavailable</span></span><br><span data-ttu-id="d1c35-142">пары для поддержки голосовых вызовов и естественного языка</span><span class="sxs-lookup"><span data-stu-id="d1c35-142">pairs well with voice and natural language</span></span></td>
        <td><span data-ttu-id="d1c35-143">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d1c35-143">HoloLens 2</span></span><br><span data-ttu-id="d1c35-144">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="d1c35-144">HoloLens (1st gen)</span></span><br> <span data-ttu-id="d1c35-145">Насыщенные Windows</span><span class="sxs-lookup"><span data-stu-id="d1c35-145">Windows Immersive</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d1c35-146"><a href="gaze-and-commit.md">Направление головы и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="d1c35-146"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="d1c35-147">По щелчку возникает например 3D презентаций, демонстраций</span><span class="sxs-lookup"><span data-stu-id="d1c35-147">Click-through experiences e.g. 3D presentations, demos</span></span></td>
        <td><span data-ttu-id="d1c35-148">Требуется обучению на HMDs, но не на мобильных устройствах</span><span class="sxs-lookup"><span data-stu-id="d1c35-148">Requires training on HMDs but not on mobile</span></span><br><span data-ttu-id="d1c35-149">Лучше всего подходит для контроллеров доступны</span><span class="sxs-lookup"><span data-stu-id="d1c35-149">Best for accessible controllers</span></span><br><span data-ttu-id="d1c35-150">Наилучшим образом подходит для HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="d1c35-150">Best for HoloLens (1st gen)</span></span></td>
        <td><span data-ttu-id="d1c35-151">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d1c35-151">HoloLens 2</span></span><br><span data-ttu-id="d1c35-152">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="d1c35-152">HoloLens (1st gen)</span></span><br> <span data-ttu-id="d1c35-153">Насыщенные Windows</span><span class="sxs-lookup"><span data-stu-id="d1c35-153">Windows Immersive</span></span><br> <span data-ttu-id="d1c35-154">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="d1c35-154">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="d1c35-155">Чтобы убедиться, что нет промежутков или отверстия взаимодействие для работы рекомендуется следовать руководству по одной модели от начала до конца.</span><span class="sxs-lookup"><span data-stu-id="d1c35-155">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="d1c35-156">Для повышения скорости проектирования и разработки, мы включили подробные сведения и ссылки на образы и примеры кода в темах нашего журнала каждой модели.</span><span class="sxs-lookup"><span data-stu-id="d1c35-156">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="d1c35-157">Но во-первых, в следующих разделах рассматриваются действия для выбора и реализация одного из этих моделей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d1c35-157">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="d1c35-158">К концу этой странице вы сможете понять наше руководство на:</span><span class="sxs-lookup"><span data-stu-id="d1c35-158">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="d1c35-159">Выбор модели взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="d1c35-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="d1c35-160">С помощью инструкций модель взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d1c35-160">Using the interaction model guidance</span></span>
* <span data-ttu-id="d1c35-161">Переход между моделей взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d1c35-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="d1c35-162">Дальнейшие действия конструктора</span><span class="sxs-lookup"><span data-stu-id="d1c35-162">Design next steps</span></span>

## <a name="choosing-an-interaction-model-for-your-customer"></a><span data-ttu-id="d1c35-163">Выбор модели взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="d1c35-163">Choosing an interaction model for your customer</span></span>

<span data-ttu-id="d1c35-164">Скорее всего у разработчиков и дизайнеров некоторые идеи помнить видов взаимодействие, нужных для своих пользователей.</span><span class="sxs-lookup"><span data-stu-id="d1c35-164">Most likely, developers and creators already have some ideas in mind of the kinds of interaction experience they want for their users.</span></span>
<span data-ttu-id="d1c35-165">Чтобы стимулировать подход, ориентированный на клиента, для разработки, мы рекомендуем следовать указанных ниже инструкций для выбора модели взаимодействия, которая оптимизирована для вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="d1c35-165">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="d1c35-166">Почему следуйте инструкциям этого руководства?</span><span class="sxs-lookup"><span data-stu-id="d1c35-166">Why follow this guidance?</span></span>

* <span data-ttu-id="d1c35-167">Для цели и субъективные критерии, такие как физического и когнитивной усилия, intuitiveness и learnability тестируется наших моделей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d1c35-167">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="d1c35-168">Поскольку взаимодействие отличается, звуковые и читаемости и поведение объекта может также отличаться между моделями взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d1c35-168">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="d1c35-169">Объединение частей несколько моделей взаимодействия создает риск конкурирующих читаемости, например лучи одновременных вручную и взглядом курсора, которые перегрузки и запутывания пользователей.</span><span class="sxs-lookup"><span data-stu-id="d1c35-169">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="d1c35-170">Ниже приведены некоторые примеры как оптимизировать читаемости и поведение для каждой модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d1c35-170">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="d1c35-171">Мы часто см. в разделе новых пользователей как похожие вопросы, такие как «как узнать, работает система, как узнать, что можно сделать, и как узнать, если понимать, что я только что сделал?»</span><span class="sxs-lookup"><span data-stu-id="d1c35-171">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d1c35-172"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="d1c35-172"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="d1c35-173"><strong>Как узнать, она работает?</strong></span><span class="sxs-lookup"><span data-stu-id="d1c35-173"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="d1c35-174"><strong>Как узнать, что можно сделать?</strong></span><span class="sxs-lookup"><span data-stu-id="d1c35-174"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="d1c35-175"><strong>Как узнать, что я только что сделал?</strong></span><span class="sxs-lookup"><span data-stu-id="d1c35-175"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d1c35-176"><a href="hands-and-tools.md">Руки и средства</a></span><span class="sxs-lookup"><span data-stu-id="d1c35-176"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="d1c35-177">Я вижу mesh руки, я вижу срезах affordance или наличии / лучи контроллера.</span><span class="sxs-lookup"><span data-stu-id="d1c35-177">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="d1c35-178">Я вижу grabbable дескрипторы или отображаются, когда приближается к мою руку ограничивающий прямоугольник.</span><span class="sxs-lookup"><span data-stu-id="d1c35-178">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="d1c35-179">Я услышать звуковые сигналы и анимации см. в разделе о захвата и выпуска.</span><span class="sxs-lookup"><span data-stu-id="d1c35-179">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d1c35-180"><a href="gaze-and-commit.md">Направление головы и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="d1c35-180"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="d1c35-181">Я вижу курсора в центре моей поле зрения.</span><span class="sxs-lookup"><span data-stu-id="d1c35-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="d1c35-182">Курсор взглядом меняет состояние при превышении определенных объектов.</span><span class="sxs-lookup"><span data-stu-id="d1c35-182">The gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="d1c35-183">Я см. в разделе / услышать visual и звуковые подтверждений, когда действия.</span><span class="sxs-lookup"><span data-stu-id="d1c35-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="d1c35-184"><a href="hands-free.md">Без участия пользователя (взглядом и простоя)</a></span><span class="sxs-lookup"><span data-stu-id="d1c35-184"><a href="hands-free.md">Hands-free (Gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="d1c35-185">Я вижу курсора в центре моей поле зрения.</span><span class="sxs-lookup"><span data-stu-id="d1c35-185">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="d1c35-186">Я вижу индикатор хода выполнения, когда я буду распространяться элементом объекта.</span><span class="sxs-lookup"><span data-stu-id="d1c35-186">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="d1c35-187">Я см. в разделе / услышать visual и звуковые подтверждений, когда действия.</span><span class="sxs-lookup"><span data-stu-id="d1c35-187">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d1c35-188"><a href="hands-free.md">Автоматическая (голосовые команды)</a></span><span class="sxs-lookup"><span data-stu-id="d1c35-188"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="d1c35-189">Я вижу, что признак прослушивания и заголовки, которые показывают системе слышали.</span><span class="sxs-lookup"><span data-stu-id="d1c35-189">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="d1c35-190">Я получаю голосовых запросов и подсказки.</span><span class="sxs-lookup"><span data-stu-id="d1c35-190">I get voice prompts and hints.</span></span>  <span data-ttu-id="d1c35-191">Когда я говорю «что можно сказать?»</span><span class="sxs-lookup"><span data-stu-id="d1c35-191">When I say "what can I say?"</span></span> <span data-ttu-id="d1c35-192">Я вижу обратной связи.</span><span class="sxs-lookup"><span data-stu-id="d1c35-192">I see feedback.</span></span></td>
        <td><span data-ttu-id="d1c35-193">Я см. в разделе / услышать visual и звуковые подтверждений при отдадите команду, или получить устранения неоднозначности UX, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="d1c35-193">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="d1c35-194">Ниже приведены вопросы, что выяснилось, что выбор команд справки модель взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d1c35-194">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="d1c35-195">Вопрос.  Хотите ли мои пользователи затронуты голограммы и манипуляций со holographic точности?</span><span class="sxs-lookup"><span data-stu-id="d1c35-195">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span>
<span data-ttu-id="d1c35-196">Ответ.  Если это так, ознакомьтесь с модель взаимодействия руки и средства целевая точность и манипуляции с руки или контроллеров движения.</span><span class="sxs-lookup"><span data-stu-id="d1c35-196">A:  If so, check out the Hands and Tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="d1c35-197">Вопрос.  Необходимо сохранить опускают руки, бесплатно, для реальных задач моих пользователей?</span><span class="sxs-lookup"><span data-stu-id="d1c35-197">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span>
<span data-ttu-id="d1c35-198">Ответ.  Если это так, рассмотрим модель взаимодействия без участия пользователя, то есть отличный вариант без участия пользователя при взаимодействии на основе взглядом и голоса.</span><span class="sxs-lookup"><span data-stu-id="d1c35-198">A:  If so, take a look at the Hands-Free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="d1c35-199">Вопрос.  У пользователей есть времени на изучение взаимодействия для моего приложения смешанной реальности или этого требуется взаимодействие с наименьшей кривой обучения возможно?</span><span class="sxs-lookup"><span data-stu-id="d1c35-199">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span>
<span data-ttu-id="d1c35-200">Ответ.  Мы советуем использовать модель руки и средства, наименьшей кривой обучения и интуитивно взаимодействий, до тех пор, пока пользователи имеют возможность использовать опускают руки к взаимодействию.</span><span class="sxs-lookup"><span data-stu-id="d1c35-200">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="d1c35-201">Вопрос.  Следует ли пользователи использовать контроллеры движения для команды и управление</span><span class="sxs-lookup"><span data-stu-id="d1c35-201">Q:  Do my users use motion controllers for pointing and manipulation?</span></span>
<span data-ttu-id="d1c35-202">Ответ.  Модель руки и средств включает все рекомендации для удобной с контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="d1c35-202">A:  The Hands and Tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="d1c35-203">Вопрос.  Следует ли пользователи использовать контроллеру специальных возможностей или общие контроллер Bluetooth, например clicker?</span><span class="sxs-lookup"><span data-stu-id="d1c35-203">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span>
<span data-ttu-id="d1c35-204">Ответ.  Мы рекомендуем взглядом Head, чтобы зафиксировать модели для всех контроллеров не отслеживаются.</span><span class="sxs-lookup"><span data-stu-id="d1c35-204">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="d1c35-205">Она разработана, чтобы разрешить пользователю проходить весь опыт простой механику «целевой объект и фиксации».</span><span class="sxs-lookup"><span data-stu-id="d1c35-205">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="d1c35-206">Вопрос. Дальнейших действий, Мои пользователи только посредством интерфейса, «щелкая» (например, в, 3d слайд-шоу среду), в отличие от перехода плотных макеты элементов управления пользовательского интерфейса?</span><span class="sxs-lookup"><span data-stu-id="d1c35-206">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span>
<span data-ttu-id="d1c35-207">Ответ.  Если пользователям не нужно управлять массу пользовательского интерфейса, взглядом Head, чтобы зафиксировать предлагает стремящихся параметр, где пользователям не нужно беспокоиться о целевой настройке.</span><span class="sxs-lookup"><span data-stu-id="d1c35-207">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="d1c35-208">Вопрос.  Следует ли пользователи использовать оба HoloLens (1-го поколения) и HoloLens 2 / Windows Иммерсивных (VR гарнитуры) ответ  Поскольку модель взаимодействия для HoloLens взглядом Head, чтобы зафиксировать (1-го поколения), мы рекомендуем creators, осуществляющих поддержку HoloLens (1-го поколения) использовать Head взглядом и фиксации для любой функции или режимы, могут столкнуться пользователи на HoloLens (1-го поколения) гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="d1c35-208">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets) A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="d1c35-209">См. ниже в разделе на *переход моделей взаимодействия* Дополнительные сведения о внесении удобной для нескольких поколений HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d1c35-209">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="d1c35-210">Вопрос. Как насчет для пользователей, которые обычно мобильных (охватывающий большое пространство или перемещать между пробелы), и пользователи, как правило, выполняются в одном месте?</span><span class="sxs-lookup"><span data-stu-id="d1c35-210">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span>  
<span data-ttu-id="d1c35-211">Ответ.  Любой модели взаимодействия будет работать для этих пользователей.</span><span class="sxs-lookup"><span data-stu-id="d1c35-211">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="d1c35-212">Дополнительные рекомендации для разработки приложений для [ожидается в ближайшее время](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="d1c35-212">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="d1c35-213">Переход моделей взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d1c35-213">Transition interaction models</span></span>
<span data-ttu-id="d1c35-214">Также встречаются случаи, где, используя несколько моделей взаимодействия может потребоваться вашего варианта использования.</span><span class="sxs-lookup"><span data-stu-id="d1c35-214">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="d1c35-215">Например приложения «создание потока» использует модель взаимодействия руки и средства, но вы хотите использовать режим без участия пользователя для технических специалистов.</span><span class="sxs-lookup"><span data-stu-id="d1c35-215">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="d1c35-216">Если для работы требуется несколько моделей взаимодействия, мы обнаружили, что многие пользователи могут возникнуть сложности, перевод из одной модели в другой — особенно для конечных пользователей, незнакомых с MR.</span><span class="sxs-lookup"><span data-stu-id="d1c35-216">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="d1c35-217">Чтобы помочь руководство проектировщикам и разработчикам через варианты, которые могут быть сложны в MR, мы работаем над Дополнительные рекомендации по использованию нескольких моделей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d1c35-217">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="d1c35-218">См. также</span><span class="sxs-lookup"><span data-stu-id="d1c35-218">See also</span></span>
* [<span data-ttu-id="d1c35-219">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="d1c35-219">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d1c35-220">Непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="d1c35-220">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d1c35-221">Наведение и фиксация</span><span class="sxs-lookup"><span data-stu-id="d1c35-221">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="d1c35-222">Нацеливание взглядом</span><span class="sxs-lookup"><span data-stu-id="d1c35-222">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="d1c35-223">Жесты</span><span class="sxs-lookup"><span data-stu-id="d1c35-223">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="d1c35-224">Проектирование голосового взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d1c35-224">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="d1c35-225">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="d1c35-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="d1c35-226">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="d1c35-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="d1c35-227">Проектирование пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="d1c35-227">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="d1c35-228">Комфорт</span><span class="sxs-lookup"><span data-stu-id="d1c35-228">Comfort</span></span>](comfort.md)
