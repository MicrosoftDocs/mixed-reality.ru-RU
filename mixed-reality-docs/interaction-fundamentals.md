---
title: Обзор мультимодальных взаимодействий
description: Обзор мультимодальных взаимодействий
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Смешанная реальность, взгляд, нацеливание взглядом, взаимодействие, конструктор, HoloLens, MMR, мультимодальный
ms.openlocfilehash: 7b04141c832597be4bb58447629e0ef6e248dc2b
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415251"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="fd4bd-104">Знакомство с инстинктивным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="fd4bd-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="fd4bd-105">Платформа Mixed Reality построена на принципах простого инстинктивного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-105">The philosophy of simple, instinctual interactions is interwoven throughout the Mixed Reality platform.</span></span>  <span data-ttu-id="fd4bd-106">Мы сделали три шага, чтобы разработчики и конструкторы приложений могли предоставлять своим клиентам простые и понятные механизмы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="fd4bd-107">Во-первых, мы объединили наши датчики и технологии ввода (включая отслеживание рук, отслеживание взгляда и естественный язык) в эффективные мультимодальные модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  <span data-ttu-id="fd4bd-108">Мы ведем исследования, создаем проекты и разрабатываем решения на базе мультимодальной платформы, а не на основе единичных входных данных. Такой подход — ключ к созданию возможностей инстинктивного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-108">Based on our research, designing and developing within a multimodal framework, and not based on single inputs, is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="fd4bd-109">Во-вторых, мы учитываем, что многие разработчики ориентированы на несколько устройств HoloLens, таких как HoloLens 2 и HoloLens (1-го поколения) или HoloLens и виртуальная реальность.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="fd4bd-110">Поэтому мы разработали модели взаимодействия для работы на разных устройствах, даже если технология ввода зависит от устройства.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  <span data-ttu-id="fd4bd-111">Например, при удаленном взаимодействии гарнитуры Windows Immersive с контроллером 6DoF и при удаленном взаимодействии с HoloLens 2 используются одинаковые возможности и шаблоны. Это упрощает разработку приложений на нескольких устройствах и обеспечивает естественное взаимодействие с пользователем.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use  identical affordances and patterns, making it easy for cross-device application development that provides a natural feel to end-user interactions.</span></span> 

<span data-ttu-id="fd4bd-112">В смешанной реальности (MR) возможны тысячи способов эффективного, увлекательного и впечатляющего взаимодействия. Но мы обнаружили, что целенаправленное использование в приложении единой модели взаимодействия на всех этапах — это лучший способ обеспечить успешную и удобную работу пользователей.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in mixed reality (MR), we've found that intentionally employing a single interaction model, end-to-end, in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="fd4bd-113">Поэтому в это руководство по взаимодействию мы включили три вещи.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="fd4bd-114">Это руководство структурировано в соответствии с тремя основными моделями взаимодействия, а также компонентами и шаблонами, необходимыми для каждой из них.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-114">This guidance is structured around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="fd4bd-115">Кроме того, здесь описаны другие преимущества, которые предоставляет наша платформа, и</span><span class="sxs-lookup"><span data-stu-id="fd4bd-115">Supplemental guidance has been included about other benefits that our platform provides.</span></span>
* <span data-ttu-id="fd4bd-116">приведены инструкции по выбору подходящей модели взаимодействия для конкретного сценария.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-116">Guidance has also been included to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="fd4bd-117">Модели мультимодальных взаимодействий</span><span class="sxs-lookup"><span data-stu-id="fd4bd-117">Multimodal interaction models</span></span>

<span data-ttu-id="fd4bd-118">Основываясь на наших исследованиях и отзывах клиентов, мы определили, что для реализации возможностей смешанной реальности подходят три основные модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-118">Based on our research as well as feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="fd4bd-119">Во многих отношениях модель взаимодействия — это модель мышления пользователя для завершения своих потоков.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-119">In many ways, the interaction model is the user's mental model for completing their flows.</span></span> <span data-ttu-id="fd4bd-120">Каждая из них оптимизирована в соответствии с набором потребностей клиентов.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-120">Each of these interaction models is optimized for a set of customer needs.</span></span> <span data-ttu-id="fd4bd-121">Каждая из них по-своему удобна, производительна и функциональна.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-121">Each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="fd4bd-122">Диаграмма ниже представляет собой упрощенный обзор.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="fd4bd-123">Подробная информация об использовании каждой модели взаимодействия приведена ниже на страницах с изображениями и примерами кода.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fd4bd-124"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="fd4bd-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="fd4bd-125"><strong>Примеры сценариев</strong></span><span class="sxs-lookup"><span data-stu-id="fd4bd-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="fd4bd-126"><strong>Совпадение</strong></span><span class="sxs-lookup"><span data-stu-id="fd4bd-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="fd4bd-127"><strong>Оборудование</strong></span><span class="sxs-lookup"><span data-stu-id="fd4bd-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="fd4bd-128"><a href="hands-and-tools.md">Руки и контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="fd4bd-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="fd4bd-129">Возможности трехмерного пространства, такие как пространственная структура и конструктор, манипулирование содержимым или симуляция.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="fd4bd-130">В сочетании с системой голосовой связи, отслеживанием взгляда или направления головы отлично подходит для новых пользователей.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="fd4bd-131">Низкий порог вхождения.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-131">Low learning curve.</span></span> <span data-ttu-id="fd4bd-132">Последовательное взаимодействие с пользователем для отслеживания рук и контроллеров 6DoF.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="fd4bd-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fd4bd-133">HoloLens 2</span></span><br><span data-ttu-id="fd4bd-134">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="fd4bd-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="fd4bd-135"><a href="hands-free.md">Режимы без использования рук</a></span><span class="sxs-lookup"><span data-stu-id="fd4bd-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="fd4bd-136">Контекстуальные возможности, когда руки пользователя заняты, например, обучением на рабочем месте и обслуживанием.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning, and maintenance.</span></span></td>
        <td><span data-ttu-id="fd4bd-137">Требуется некоторое обучение.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-137">Some learning required.</span></span> <span data-ttu-id="fd4bd-138">Если руки должны быть свободны, устройство обеспечивает удобное управление с помощью голоса и естественного языка.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="fd4bd-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fd4bd-139">HoloLens 2</span></span><br><span data-ttu-id="fd4bd-140">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="fd4bd-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="fd4bd-141">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="fd4bd-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="fd4bd-142"><a href="gaze-and-commit.md">Направление головы и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="fd4bd-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="fd4bd-143">Возможности перехода по ссылке, например 3D презентации, демоверсии.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="fd4bd-144">Требуется обучение на HMD, но не на мобильном.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="fd4bd-145">Лучшее для доступных контроллеров.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-145">Best for accessible controllers.</span></span> <span data-ttu-id="fd4bd-146">Лучшее для HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="fd4bd-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="fd4bd-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fd4bd-147">HoloLens 2</span></span><br><span data-ttu-id="fd4bd-148">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="fd4bd-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="fd4bd-149">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="fd4bd-149">Immersive headsets</span></span><br><span data-ttu-id="fd4bd-150">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="fd4bd-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="fd4bd-151">Чтобы избежать несоответствий или недочетов в механизме взаимодействия с пользователем, на всех этапах следуйте инструкциям, касающимся одной и той же модели.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-151">To ensure that there are no gaps or holes in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="fd4bd-152">Чтобы ускорить проектирование и разработку, мы приводим подробную информацию, ссылки на изображения и примеры кода при описании каждой модели.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-152">To speed up design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="fd4bd-153">В следующих разделах рассматриваются этапы выбора и реализации одной из этих моделей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-153">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="fd4bd-154">К концу этой страницы вы будете основательно понимать следующие руководства.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="fd4bd-155">Выбор модели взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="fd4bd-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="fd4bd-156">Использование руководства по модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="fd4bd-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="fd4bd-157">Переход между моделями взаимодействия</span><span class="sxs-lookup"><span data-stu-id="fd4bd-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="fd4bd-158">Следующие шаги конструктора</span><span class="sxs-lookup"><span data-stu-id="fd4bd-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="fd4bd-159">Выберите модель взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="fd4bd-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="fd4bd-160">Как правило, разработчики и проектировщики решений продумывают типы взаимодействия, ориентируясь на потребности клиента.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-160">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="fd4bd-161">Чтобы поощрить такой подход к проектированию, мы рекомендуем следовать приведенным ниже инструкциям по выбору модели взаимодействия, оптимизированной для вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-161">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="fd4bd-162">Почему нужно следовать руководству?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-162">Why follow this guidance?</span></span>

* <span data-ttu-id="fd4bd-163">Наши модели взаимодействия проверяются по объективным и субъективным критериям, таким как физические и когнитивные трудозатраты, интуиция и обучаемость.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-163">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="fd4bd-164">Так как есть множество способов взаимодействия, визуальные и звуковые возможности, а также поведение объекта отличаются в зависимости от конкретной модели.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-164">Because interactions differ, visual and audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="fd4bd-165">Объединение частей нескольких моделей взаимодействия создает риск конкурирующих возможностей, таких как одновременное срабатывание телекинеза и курсора направления головы, что может быть сложным для восприятия пользователей.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-165">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor that can overwhelm and confuse users.</span></span>

<span data-ttu-id="fd4bd-166">Ниже приведены несколько примеров того, как возможности и расширения функциональности оптимизируются для каждой модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="fd4bd-167">Мы часто видим, что у новых пользователей возникают похожие вопросы, например: "Как я узнаю, что система работает, как мне узнать, что я могу сделать, и как узнать, поняла ли она, что я только что сделала?"</span><span class="sxs-lookup"><span data-stu-id="fd4bd-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fd4bd-168"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="fd4bd-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="fd4bd-169"><strong>Как мне узнать, что она работает?</strong></span><span class="sxs-lookup"><span data-stu-id="fd4bd-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="fd4bd-170"><strong>Как мне узнать, что я могу сделать?</strong></span><span class="sxs-lookup"><span data-stu-id="fd4bd-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="fd4bd-171"><strong>Как мне узнать, что я только что сделал?</strong></span><span class="sxs-lookup"><span data-stu-id="fd4bd-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="fd4bd-172"><a href="hands-and-tools.md">Руки и контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="fd4bd-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="fd4bd-173">Я вижу виртуальную руку, я вижу возможность курсора кончика пальца или телекинеза либо лучей контроллера движений.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-173">I see a hand mesh, I see a fingertip affordance or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="fd4bd-174">Когда моя рука рядом, я вижу захватные дескрипторы или появление ограничительной рамки.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="fd4bd-175">Я слышу звуковые сигналы и вижу анимацию при захвате и выпуске.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="fd4bd-176"><a href="gaze-and-commit.md">Направление головы и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="fd4bd-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="fd4bd-177">Я вижу курсор в центре моей видимой зоны.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="fd4bd-178">Курсор направления головы изменяет состояние над определенными объектами.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="fd4bd-179">Я вижу/слышу визуальные и звуковые подтверждения, когда принимаю меры.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="fd4bd-180"><a href="hands-free.md">Без использования рук (Направление головы и остановка)</a></span><span class="sxs-lookup"><span data-stu-id="fd4bd-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="fd4bd-181">Я вижу курсор в центре моей видимой зоны.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="fd4bd-182">Я вижу индикатор хода выполнения, когда останавливаюсь на интерактивном объекте.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="fd4bd-183">Я вижу визуальные подтверждения или слышу звуковые подтверждения при определенных действиях.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="fd4bd-184"><a href="hands-free.md">Без использования рук (Голосовые команды)</a></span><span class="sxs-lookup"><span data-stu-id="fd4bd-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="fd4bd-185">Я вижу индикатор прослушивания и заголовки, которые показывают, что слышала система.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="fd4bd-186">Я получаю голосовые приглашения и указания.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-186">I get voice prompts and hints.</span></span> <span data-ttu-id="fd4bd-187">Когда я говорю: "Что я могу сказать?",</span><span class="sxs-lookup"><span data-stu-id="fd4bd-187">When I say: "what can I say?"</span></span> <span data-ttu-id="fd4bd-188">Я вижу отзыв.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="fd4bd-189">Я вижу/слышу визуальные и звуковые подтверждения, когда даю команду, или получаю устранение неоднозначности при взаимодействии с пользователем, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="fd4bd-190">Ниже приведены вопросы, которые мы нашли, чтобы помочь рабочей группе выбрать модель взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="fd4bd-191">Вопрос.  Хотят ли мои пользователи хотят дотрагиваться до голограмм и выполнять точные голографические операции?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="fd4bd-192">Ответ.  Если это так, проверьте модель взаимодействия "Руки и контроллеры движений" на предмет точности нацеливания и операций с руками или контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="fd4bd-193">Вопрос.  Должны ли руки пользователей быть свободны, чтобы они могли выполнять определенные задачи в реальности?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="fd4bd-194">Ответ.  Если это так, обратите внимание на модель "Без использования рук", которая обеспечивает отличные возможности взаимодействия на основе направления взгляда и голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="fd4bd-195">Вопрос.  У моих пользователей есть время, чтобы освоить работу с моим приложением MR, или им нужно взаимодействие с минимальным периодом обучения?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="fd4bd-196">Ответ.  Рекомендуем использовать модель "Руки и контроллеры движений". Обучение работе с ней не занимает много времени, и она обеспечивает наиболее интуитивное взаимодействие, если пользователи могут задействовать руки.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-196">A:  We recommend the Hands and motion controllers model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="fd4bd-197">Вопрос.  Используют ли мои пользователи контроллеры движения для указывания и операций?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="fd4bd-198">Ответ.  Для модели "Руки и контроллеры движений" предоставляются полные инструкции, которые обеспечат успешную работу с контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="fd4bd-199">Вопрос.  Используют ли мои пользователи контроллер специальных возможностей или обычный контроллер Bluetooth, такой как кликер?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="fd4bd-200">Ответ.  Мы рекомендуем использовать модель "Направление головы и подтверждение" для всех контроллеров, которые не отслеживаются.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="fd4bd-201">Она обеспечивает полное взаимодействие пользователя с системой с помощью простого механизма нацеливания и подтверждения.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="fd4bd-202">Вопрос. Мои пользователи будут работать только с помощью "переходов" (например, в среде, похожей на слайд-шоу в трехмерном пространстве), не используя навигацию по многоуровневым элементам управления пользовательского интерфейса?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="fd4bd-203">Ответ.  Если пользователям не нужно контролировать большой объем пользовательского интерфейса, "Направление головы и фиксация" предлагают удобный для изучения вариант, когда им не нужно беспокоиться о нацеливании.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="fd4bd-204">Вопрос.  Используют ли мои пользователи как HoloLens (1-го поколения), так и HoloLens 2 или иммерсивные гарнитуры (гарнитуры виртуальной реальности) Windows Mixed Reality?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="fd4bd-205">Ответ.  Так как "Направление головы и подтверждение" — это модель взаимодействия для HoloLens (1-го поколения), мы рекомендуем, чтобы разработчики, которые используют HoloLens (1-го поколения), применяли модель "Направление головы и фиксацию" для любых функций или режимов, которые пользователи будут применять на гарнитуре HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="fd4bd-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="fd4bd-206">Пожалуйста, обратитесь к следующему разделу ниже *Переходные модели взаимодействия* для получения подробных сведений о том, что нужно для комфортного пользования несколькими поколениями HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="fd4bd-207">Вопрос. Есть ли различия между моделями для пользователей, которые обычно работают в большом пространстве или перемещаются между разными пространствами, и пользователей, которые, как правило, работают в одном пространстве?</span><span class="sxs-lookup"><span data-stu-id="fd4bd-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="fd4bd-208">Ответ.  Любая из моделей взаимодействия подойдет этим пользователям.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="fd4bd-209">[В ближайшее время](index.md#news-and-notes) появятся дополнительные руководства, касающиеся дизайна приложения.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="fd4bd-210">Переходные модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="fd4bd-210">Transitioning interaction models</span></span>
<span data-ttu-id="fd4bd-211">Иногда нужно использовать более одной модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="fd4bd-212">Например, при создании приложения используется модель "Руки и контроллеры движения", но вам нужно применить режим "Без использования рук" для выездных техников.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-212">For example, your application's creation flow utilizes the Hands and motion controllers interaction model, but you want to employ a hands-free mode for field technicians.</span></span>  

<span data-ttu-id="fd4bd-213">Мы обнаружили, что при использовании нескольких моделей взаимодействия многим пользователям трудно переходить между ними. Особенно это касается тех, кто только начинает работать с технологиями смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-213">If your experience does require multiple interaction models, keep in mind that many end users might encounter difficulty when transitioning from one model to another--especially for users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="fd4bd-214">Мы постоянно предоставляем разработчикам и дизайнерам дополнительные рекомендации относительно способов, сценариев и целей использования нескольких моделей взаимодействия MR.</span><span class="sxs-lookup"><span data-stu-id="fd4bd-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="fd4bd-215">См. также</span><span class="sxs-lookup"><span data-stu-id="fd4bd-215">See also</span></span>
* [<span data-ttu-id="fd4bd-216">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="fd4bd-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="fd4bd-217">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="fd4bd-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="fd4bd-218">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="fd4bd-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="fd4bd-219">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="fd4bd-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="fd4bd-220">Жесты</span><span class="sxs-lookup"><span data-stu-id="fd4bd-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="fd4bd-221">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="fd4bd-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="fd4bd-222">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="fd4bd-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="fd4bd-223">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="fd4bd-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="fd4bd-224">Проектирование пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="fd4bd-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="fd4bd-225">Комфорт</span><span class="sxs-lookup"><span data-stu-id="fd4bd-225">Comfort</span></span>](comfort.md)

