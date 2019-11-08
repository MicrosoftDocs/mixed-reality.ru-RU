---
title: Инстинктивное взаимодействие
description: Платформа Mixed Reality построена на принципах простого инстинктивного взаимодействия.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Смешанная реальность, взгляд, нацеливание взглядом, взаимодействие, конструктор, HoloLens, MMR, мультимодальный
ms.openlocfilehash: abd82947be08a2f6aecc4462abc34c4674abfb7a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437974"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="dc6eb-104">Знакомство с инстинктивным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="dc6eb-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="dc6eb-105">Платформа Mixed Reality (MR) построена на принципах простого инстинктивного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-105">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="dc6eb-106">Мы сделали три шага, чтобы разработчики и конструкторы приложений могли предоставлять своим клиентам простые и понятные механизмы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="dc6eb-107">Во-первых, мы объединили наши датчики и технологии ввода (включая отслеживание рук, отслеживание взгляда и естественный язык) в эффективные мультимодальные модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  
<span data-ttu-id="dc6eb-108">Мы ведем исследования, создаем проекты и разрабатываем решения на базе мультимодальной платформы, а не на основе индивидуальных входных данных. Такой подход — ключ к созданию возможностей инстинктивного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-108">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="dc6eb-109">Во-вторых, мы учитываем, что многие разработчики ориентированы на несколько устройств HoloLens, таких как HoloLens 2 и HoloLens (1-го поколения) или HoloLens и виртуальная реальность.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  
<span data-ttu-id="dc6eb-110">Поэтому мы разработали модели взаимодействия для работы на разных устройствах, даже если технология ввода зависит от устройства.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  
<span data-ttu-id="dc6eb-111">Например, при удаленном взаимодействии гарнитуры Windows Immersive с контроллером 6DoF и при удаленном взаимодействии с HoloLens 2 используются одинаковые возможности и шаблоны. Это упрощает разработку приложений на нескольких устройствах и обеспечивает естественное взаимодействие с пользователем.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use identical affordances and patterns, making it easy for cross-device application development and providing a natural feel to user interactions.</span></span> 

<span data-ttu-id="dc6eb-112">Хотя мы признаем, что в смешанной реальности возможны тысячи эффективных, увлекательных и магических взаимодействий, мы обнаружили, что преднамеренное использование единой модели взаимодействия от начала до конца в приложении — это лучший способ обеспечить успешную работу пользователей и комфортное пользование.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model end-to-end in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="dc6eb-113">Поэтому в это руководство по взаимодействию мы включили три вещи.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="dc6eb-114">Специальные указания по трем основным моделям взаимодействия, а также по компонентам и шаблонам, необходимым для каждого.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-114">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="dc6eb-115">Дополнительное описание других преимуществ, которые предоставляет наша платформа.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-115">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="dc6eb-116">Общие инструкции по выбору подходящей модели взаимодействия для конкретного сценария разработки.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-116">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="dc6eb-117">Модели мультимодальных взаимодействий</span><span class="sxs-lookup"><span data-stu-id="dc6eb-117">Multimodal interaction models</span></span>

<span data-ttu-id="dc6eb-118">Основываясь на наших исследованиях и отзывах клиентов, мы определили, что для реализации возможностей смешанной реальности подходят три основные модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-118">Based on our research and feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span> <span data-ttu-id="dc6eb-119">Во многих отношениях модель взаимодействия — это модель мышления пользователя для выполнения своего рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-119">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="dc6eb-120">Каждая из этих моделей взаимодействия оптимизирована для ряда потребностей клиентов. При правильном применении каждая из них является простой, мощной и удобной в использовании.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-120">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="dc6eb-121">Диаграмма ниже представляет собой упрощенный обзор.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-121">The chart below is a simplified overview.</span></span> <span data-ttu-id="dc6eb-122">Подробная информация об использовании каждой модели взаимодействия приведена ниже на страницах с изображениями и примерами кода.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-122">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dc6eb-123"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="dc6eb-123"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="dc6eb-124"><strong>Примеры сценариев</strong></span><span class="sxs-lookup"><span data-stu-id="dc6eb-124"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="dc6eb-125"><strong>Совпадение</strong></span><span class="sxs-lookup"><span data-stu-id="dc6eb-125"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="dc6eb-126"><strong>Оборудование</strong></span><span class="sxs-lookup"><span data-stu-id="dc6eb-126"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dc6eb-127"><a href="hands-and-tools.md">Руки и контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="dc6eb-127"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="dc6eb-128">Возможности трехмерного пространства, такие как пространственная структура и конструктор, манипулирование содержимым или симуляция.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-128">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="dc6eb-129">В сочетании с системой голосовой связи, отслеживанием взгляда или направления головы отлично подходит для новых пользователей.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-129">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="dc6eb-130">Низкий порог вхождения.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-130">Low learning curve.</span></span> <span data-ttu-id="dc6eb-131">Последовательное взаимодействие с пользователем для отслеживания рук и контроллеров 6DoF.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-131">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="dc6eb-132">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dc6eb-132">HoloLens 2</span></span><br><span data-ttu-id="dc6eb-133">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="dc6eb-133">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dc6eb-134"><a href="hands-free.md">Режимы без использования рук</a></span><span class="sxs-lookup"><span data-stu-id="dc6eb-134"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="dc6eb-135">Контекстуальные возможности, когда руки пользователя заняты, например, обучением на рабочем месте и обслуживанием.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-135">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="dc6eb-136">Требуется некоторое обучение.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-136">Some learning required.</span></span> <span data-ttu-id="dc6eb-137">Если руки должны быть свободны, устройство обеспечивает удобное управление с помощью голоса и естественного языка.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-137">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="dc6eb-138">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dc6eb-138">HoloLens 2</span></span><br><span data-ttu-id="dc6eb-139">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="dc6eb-139">HoloLens (1st gen)</span></span><br><span data-ttu-id="dc6eb-140">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="dc6eb-140">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dc6eb-141"><a href="gaze-and-commit.md">Взгляд и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="dc6eb-141"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="dc6eb-142">Возможности перехода по ссылке, например 3D презентации, демоверсии.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-142">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="dc6eb-143">Требуется обучение на HMD, но не на мобильном.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-143">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="dc6eb-144">Лучшее для доступных контроллеров.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-144">Best for accessible controllers.</span></span> <span data-ttu-id="dc6eb-145">Лучшее для HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="dc6eb-145">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="dc6eb-146">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dc6eb-146">HoloLens 2</span></span><br><span data-ttu-id="dc6eb-147">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="dc6eb-147">HoloLens (1st gen)</span></span><br><span data-ttu-id="dc6eb-148">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="dc6eb-148">Immersive headsets</span></span><br><span data-ttu-id="dc6eb-149">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="dc6eb-149">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="dc6eb-150">Чтобы избежать несоответствий в механизме взаимодействия с пользователем, на всех этапах следуйте инструкциям, касающимся одной и той же модели.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-150">To ensure that there are no gaps in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="dc6eb-151">В следующих разделах рассматриваются этапы выбора и реализации одной из этих моделей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-151">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="dc6eb-152">К концу этой страницы вы будете основательно понимать следующие руководства.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-152">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="dc6eb-153">Выбор модели взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="dc6eb-153">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="dc6eb-154">Реализация модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="dc6eb-154">Implementing the interaction model</span></span>
* <span data-ttu-id="dc6eb-155">Переход между моделями взаимодействия</span><span class="sxs-lookup"><span data-stu-id="dc6eb-155">Transitioning between interaction models</span></span>
* <span data-ttu-id="dc6eb-156">Следующие шаги конструктора</span><span class="sxs-lookup"><span data-stu-id="dc6eb-156">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="dc6eb-157">Выберите модель взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="dc6eb-157">Choose an interaction model for your customer</span></span>

<span data-ttu-id="dc6eb-158">Как правило, разработчики и проектировщики решений продумывают типы взаимодействия, ориентируясь на потребности клиента.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-158">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="dc6eb-159">Чтобы поощрить такой подход к проектированию, мы рекомендуем следовать приведенным ниже инструкциям по выбору модели взаимодействия, оптимизированной для вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-159">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="dc6eb-160">Почему нужно следовать руководству?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-160">Why follow this guidance?</span></span>

* <span data-ttu-id="dc6eb-161">Наши модели взаимодействия проверяются по объективным и субъективным критериям, таким как физические и когнитивные трудозатраты, интуиция и обучаемость.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-161">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="dc6eb-162">Так как есть множество способов взаимодействия, визуальные и звуковые возможности, а также поведение объекта отличаются в зависимости от конкретной модели.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-162">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="dc6eb-163">Объединение частей нескольких моделей взаимодействия создает риск конкурирующих возможностей, таких как одновременное срабатывание телекинеза и курсора направления головы.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-163">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="dc6eb-164">Это может быть сложным для восприятия пользователей.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-164">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="dc6eb-165">Ниже приведены несколько примеров того, как возможности и расширения функциональности оптимизируются для каждой модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-165">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="dc6eb-166">Мы часто видим, что у новых пользователей возникают похожие вопросы, например: "_Как я узнаю, что система работает_, _как мне узнать, что я могу сделать_, и _как узнать, поняла ли она мое действие?_ "</span><span class="sxs-lookup"><span data-stu-id="dc6eb-166">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dc6eb-167"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="dc6eb-167"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="dc6eb-168"><strong>Как мне узнать, что она работает?</strong></span><span class="sxs-lookup"><span data-stu-id="dc6eb-168"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="dc6eb-169"><strong>Как мне узнать, что я могу сделать?</strong></span><span class="sxs-lookup"><span data-stu-id="dc6eb-169"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="dc6eb-170"><strong>Как мне узнать, что я только что сделал?</strong></span><span class="sxs-lookup"><span data-stu-id="dc6eb-170"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dc6eb-171"><a href="hands-and-tools.md">Руки и контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="dc6eb-171"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="dc6eb-172">Я вижу виртуальную руку, возможность курсора для кончика пальца или телекинез либо лучи контроллера движений.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-172">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="dc6eb-173">Когда моя рука рядом с объектом, я вижу захватные маркеры или появление ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-173">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="dc6eb-174">Я слышу звуковые сигналы и вижу анимацию при захвате и выпуске.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-174">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dc6eb-175"><a href="gaze-and-commit.md">Направление головы и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="dc6eb-175"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="dc6eb-176">Я вижу курсор в центре моей видимой зоны.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-176">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="dc6eb-177">Курсор изменяется над определенными объектами.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-177">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="dc6eb-178">Я вижу визуальные подтверждения или слышу звуковые подтверждения при определенных действиях.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-178">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="dc6eb-179"><a href="hands-free.md">Без использования рук (Направление головы и остановка)</a></span><span class="sxs-lookup"><span data-stu-id="dc6eb-179"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="dc6eb-180">Я вижу курсор в центре моей видимой зоны.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-180">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="dc6eb-181">Я вижу индикатор хода выполнения, когда останавливаюсь на интерактивном объекте.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-181">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="dc6eb-182">Я вижу визуальные подтверждения или слышу звуковые подтверждения при определенных действиях.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-182">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dc6eb-183"><a href="hands-free.md">Без использования рук (Голосовые команды)</a></span><span class="sxs-lookup"><span data-stu-id="dc6eb-183"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="dc6eb-184">Я вижу индикатор прослушивания и заголовки, которые показывают, что слышала система.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-184">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="dc6eb-185">Я получаю голосовые приглашения и указания.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-185">I get voice prompts and hints.</span></span> <span data-ttu-id="dc6eb-186">Когда я говорю: "Что можно говорить?"</span><span class="sxs-lookup"><span data-stu-id="dc6eb-186">When I say: "What can I say?"</span></span> <span data-ttu-id="dc6eb-187">Я вижу отзыв.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-187">I see feedback.</span></span></td>
        <td><span data-ttu-id="dc6eb-188">Я вижу или слышу визуальные и звуковые подтверждения, когда даю команду, или пользовательский интерфейс устраняет неоднозначность, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-188">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="dc6eb-189">Ниже приведены вопросы, которые, по нашему мнению, помогут командам выбрать модель взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-189">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="dc6eb-190">Вопрос.  Хотят ли мои пользователи хотят дотрагиваться до голограмм и выполнять точные голографические операции?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-190">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="dc6eb-191">Ответ.  Если это так, ознакомьтесь с моделью взаимодействия "Руки и контроллеры движений" для точного нацеливания и манипулирования.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-191">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="dc6eb-192">Вопрос.  Должны ли руки пользователей быть свободны, чтобы они могли выполнять определенные задачи в реальности?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-192">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="dc6eb-193">Ответ.  Если это так, обратите внимание на модель "Без использования рук", которая обеспечивает отличные возможности взаимодействия на основе направления взгляда и голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-193">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="dc6eb-194">Вопрос.  У моих пользователей есть время, чтобы освоить работу с моим приложением MR, или им нужно взаимодействие с минимальным периодом обучения?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-194">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="dc6eb-195">Ответ.  Рекомендуем использовать модель "Руки и контроллеры движений". Обучение работе с ней не занимает много времени, и она обеспечивает наиболее интуитивное взаимодействие, если пользователи могут задействовать руки.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-195">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="dc6eb-196">Вопрос.  Используют ли мои пользователи контроллеры движения для указывания и операций?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-196">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="dc6eb-197">Ответ.  Для модели "Руки и контроллеры движений" предоставляются полные инструкции, которые обеспечат успешную работу с контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-197">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="dc6eb-198">Вопрос.  Используют ли мои пользователи контроллер специальных возможностей или обычный контроллер Bluetooth, такой как кликер?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-198">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="dc6eb-199">Ответ.  Мы рекомендуем использовать модель "Направление головы и подтверждение" для всех контроллеров, которые не отслеживаются.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-199">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="dc6eb-200">Она обеспечивает полное взаимодействие пользователя с системой с помощью простого механизма нацеливания и подтверждения.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-200">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="dc6eb-201">Вопрос. Мои пользователи будут работать только с помощью "переходов" (например, в среде, похожей на слайд-шоу в трехмерном пространстве), не используя навигацию по многоуровневым элементам управления пользовательского интерфейса?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-201">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="dc6eb-202">Ответ.  Если пользователям не нужно контролировать большой объем пользовательского интерфейса, "Направление головы и фиксация" предлагают удобный для изучения вариант, когда им не нужно беспокоиться о нацеливании.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-202">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="dc6eb-203">Вопрос.  Используют ли мои пользователи как HoloLens (1-го поколения), так и HoloLens 2 или иммерсивные гарнитуры (гарнитуры виртуальной реальности) Windows Mixed Reality?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-203">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="dc6eb-204">Ответ.  Так как "Направление головы и подтверждение" — это модель взаимодействия для HoloLens (1-го поколения), мы рекомендуем, чтобы разработчики, которые используют HoloLens (1-го поколения), применяли модель "Направление головы и фиксацию" для любых функций или режимов, которые пользователи будут применять на гарнитуре HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="dc6eb-204">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="dc6eb-205">Пожалуйста, обратитесь к следующему разделу ниже *Переходные модели взаимодействия* для получения подробных сведений о том, что нужно для комфортного пользования несколькими поколениями HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-205">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="dc6eb-206">Вопрос. Есть ли различия между моделями для пользователей, которые обычно работают в большом пространстве или перемещаются между разными пространствами, и пользователей, которые, как правило, работают в одном пространстве?</span><span class="sxs-lookup"><span data-stu-id="dc6eb-206">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="dc6eb-207">Ответ.  Любая из моделей взаимодействия подойдет этим пользователям.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-207">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="dc6eb-208">[В ближайшее время](news.md) появятся дополнительные руководства, касающиеся дизайна приложения.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-208">More guidance specific to app design [coming soon](news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="dc6eb-209">Переходные модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="dc6eb-209">Transitioning interaction models</span></span>
<span data-ttu-id="dc6eb-210">Иногда нужно использовать более одной модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-210">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="dc6eb-211">Например, при создании приложения используется модель _Руки и контроллеры движений_, но вам нужно применить режим "Без использования рук" для выездных техников.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-211">For example, your application's creation flow utilizes the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span>
<span data-ttu-id="dc6eb-212">Мы обнаружили, что при использовании нескольких моделей взаимодействия многим пользователям трудно переходить с одной на другую. Особенно это касается тех, кто только начинает работать с технологиями смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-212">If your experience does require multiple interaction models, please keep in mind that many users might encounter difficulty when transitioning from one model to another, especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="dc6eb-213">Мы постоянно предоставляем разработчикам и дизайнерам дополнительные рекомендации относительно способов, сценариев и целей использования нескольких моделей взаимодействия MR.</span><span class="sxs-lookup"><span data-stu-id="dc6eb-213">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="dc6eb-214">См. также</span><span class="sxs-lookup"><span data-stu-id="dc6eb-214">See also</span></span>
* [<span data-ttu-id="dc6eb-215">Комфорт</span><span class="sxs-lookup"><span data-stu-id="dc6eb-215">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="dc6eb-216">Взаимодействие на основе глаз</span><span class="sxs-lookup"><span data-stu-id="dc6eb-216">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="dc6eb-217">Отслеживание глаз в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dc6eb-217">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="dc6eb-218">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="dc6eb-218">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="dc6eb-219">Взгляд и остановка</span><span class="sxs-lookup"><span data-stu-id="dc6eb-219">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="dc6eb-220">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="dc6eb-220">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="dc6eb-221">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="dc6eb-221">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="dc6eb-222">Руки: наведение и фиксация</span><span class="sxs-lookup"><span data-stu-id="dc6eb-222">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="dc6eb-223">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="dc6eb-223">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="dc6eb-224">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="dc6eb-224">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="dc6eb-225">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="dc6eb-225">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="dc6eb-226">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="dc6eb-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="dc6eb-227">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="dc6eb-227">Voice input</span></span>](voice-input.md)


