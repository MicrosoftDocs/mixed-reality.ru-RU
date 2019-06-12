---
title: Обзор мультимодальных взаимодействий
description: Обзор мультимодальных взаимодействий
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Смешанная реальность, взгляд, нацеливание взглядом, взаимодействие, конструктор, HoloLens, MMR, мультимодальный
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516024"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="1697a-104">Знакомство с инстинктивным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="1697a-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="1697a-105">Философия простых, инстинктивных взаимодействий вплетена в платформу Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1697a-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="1697a-106">Мы предприняли три шага, чтобы разработчики и конструкторы приложений могли предоставлять своим клиентам простые и понятные взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="1697a-107">Во-первых, мы убедились, что наши удивительные датчики и технология ввода, включая отслеживание руки, отслеживание взгляда и естественный язык, объединяются в эффективные мультимодальные модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="1697a-108">Базирование на наших исследованиях, проектировании и разработке мультимодально, а не на основе одного входа — это ключ к созданию инстинктивных возможностей.</span><span class="sxs-lookup"><span data-stu-id="1697a-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="1697a-109">Во-вторых, мы признаем, что многие разработчики ориентированы на несколько устройств, будь то HoloLens 2 и HoloLens (1-го поколения) или HoloLens и виртуальная реальность.</span><span class="sxs-lookup"><span data-stu-id="1697a-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="1697a-110">Итак, мы разработали наши модели взаимодействия для работы на разных устройствах (даже если технология ввода зависит от устройства).</span><span class="sxs-lookup"><span data-stu-id="1697a-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="1697a-111">Например, при удаленном взаимодействии гарнитуры Windows Immersive с контроллером 6DOF и при удаленном взаимодействии с HoloLens 2 используются одинаковые возможности и шаблоны, что упрощает работу приложений на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="1697a-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="1697a-112">Это удобно не только для разработчиков и конструкторов, но и для пользователей.</span><span class="sxs-lookup"><span data-stu-id="1697a-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="1697a-113">Наконец, хотя мы признаем, что в MR (смешанной реальности) возможны тысячи эффективных, увлекательных и магических взаимодействий, мы обнаружили, что преднамеренное использование единой модели взаимодействия от начала до конца в приложении — это лучший способ обеспечить успешную работу пользователей и комфортное пользование.</span><span class="sxs-lookup"><span data-stu-id="1697a-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="1697a-114">Поэтому в это руководство по взаимодействию мы включили три вещи.</span><span class="sxs-lookup"><span data-stu-id="1697a-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="1697a-115">Мы структурировали это руководство вокруг трех основных моделей взаимодействия, компонентов и шаблонов, необходимых для каждого.</span><span class="sxs-lookup"><span data-stu-id="1697a-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="1697a-116">Мы включили дополнительное руководство по другим преимуществам, которые предоставляет наша платформа.</span><span class="sxs-lookup"><span data-stu-id="1697a-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="1697a-117">Мы включили руководство, чтобы помочь выбрать подходящую модель взаимодействия под ваш сценарий.</span><span class="sxs-lookup"><span data-stu-id="1697a-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="1697a-118">Модели мультимодальных взаимодействий</span><span class="sxs-lookup"><span data-stu-id="1697a-118">Multimodal interaction models</span></span>

<span data-ttu-id="1697a-119">Основываясь на наших исследованиях и работе с клиентами на сегодняшний день, мы обнаружили, что три основные модели взаимодействия подходят для функциональных возможностей смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1697a-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="1697a-120">Во многих отношениях модель взаимодействия — это модель мышления пользователя для завершения своих потоков.</span><span class="sxs-lookup"><span data-stu-id="1697a-120">In many ways, the interaction model is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="1697a-121">Каждая из этих моделей взаимодействия оптимизирована для ряда потребностей клиентов. Каждая из них — простая, с широкими возможностями и удобная в использовании.</span><span class="sxs-lookup"><span data-stu-id="1697a-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="1697a-122">Диаграмма ниже представляет собой упрощенный обзор.</span><span class="sxs-lookup"><span data-stu-id="1697a-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="1697a-123">Подробная информация об использовании каждой модели взаимодействия приведена ниже на страницах с изображениями и примерами кода.</span><span class="sxs-lookup"><span data-stu-id="1697a-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1697a-124"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="1697a-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="1697a-125"><strong>Примеры сценариев</strong></span><span class="sxs-lookup"><span data-stu-id="1697a-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="1697a-126"><strong>Совпадение</strong></span><span class="sxs-lookup"><span data-stu-id="1697a-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="1697a-127"><strong>Оборудование</strong></span><span class="sxs-lookup"><span data-stu-id="1697a-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1697a-128"><a href="hands-and-tools.md">Руки и контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="1697a-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="1697a-129">Возможности трехмерного пространства, например пространственная структура и конструктор, манипулирование содержимым или симуляция.</span><span class="sxs-lookup"><span data-stu-id="1697a-129">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="1697a-130">Отлично подходит для новых пользователей, в сочетании с системой голосовой связи, отслеживанием взгляда или направления головы.</span><span class="sxs-lookup"><span data-stu-id="1697a-130">Great for new users, coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="1697a-131">Низкий порог вхождения.</span><span class="sxs-lookup"><span data-stu-id="1697a-131">Low learning curve.</span></span> <span data-ttu-id="1697a-132">Последовательное взаимодействие с пользователем для отслеживания рук и контроллеров 6 DoF.</span><span class="sxs-lookup"><span data-stu-id="1697a-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span></td>
        <td><span data-ttu-id="1697a-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1697a-133">HoloLens 2</span></span><br><span data-ttu-id="1697a-134">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="1697a-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1697a-135"><a href="hands-free.md">Режимы без использования рук</a></span><span class="sxs-lookup"><span data-stu-id="1697a-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="1697a-136">Контекстуальные возможности, когда руки пользователя заняты, например, обучением на рабочем месте, обслуживанием.</span><span class="sxs-lookup"><span data-stu-id="1697a-136">Contextual experiences where a user's hands are occupied, e.g. on-the-job learning, maintenance.</span></span></td>
        <td><span data-ttu-id="1697a-137">Требуется некоторое обучение.</span><span class="sxs-lookup"><span data-stu-id="1697a-137">Some learning required.</span></span> <span data-ttu-id="1697a-138">Если руки недоступны, есть пары, хорошо сочетающиеся с системами голосовой связи и естественным языком.</span><span class="sxs-lookup"><span data-stu-id="1697a-138">If hands are unavailable pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="1697a-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1697a-139">HoloLens 2</span></span><br><span data-ttu-id="1697a-140">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="1697a-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="1697a-141">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="1697a-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1697a-142"><a href="gaze-and-commit.md">Направление головы и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="1697a-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="1697a-143">Возможности перехода по ссылке, например 3D презентации, демоверсии.</span><span class="sxs-lookup"><span data-stu-id="1697a-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="1697a-144">Требуется обучение на HMD, но не на мобильном.</span><span class="sxs-lookup"><span data-stu-id="1697a-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="1697a-145">Лучшее для доступных контроллеров.</span><span class="sxs-lookup"><span data-stu-id="1697a-145">Best for accessible controllers.</span></span> <span data-ttu-id="1697a-146">Лучшее для HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="1697a-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="1697a-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1697a-147">HoloLens 2</span></span><br><span data-ttu-id="1697a-148">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="1697a-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="1697a-149">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="1697a-149">Immersive headsets</span></span><br><span data-ttu-id="1697a-150">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="1697a-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="1697a-151">Лучший способ убедиться, что в взаимодействии для ваших возможностей нет несоответствий или брешей, — следовать руководству для одной модели от начала до конца.</span><span class="sxs-lookup"><span data-stu-id="1697a-151">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="1697a-152">Для ускорения проектирования и разработки мы включили подробную информацию, ссылки на изображения и примеры кода в нашем охвате каждой модели.</span><span class="sxs-lookup"><span data-stu-id="1697a-152">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="1697a-153">Но сначала в следующих разделах описываются этапы выбора и реализации одной из этих моделей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-153">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="1697a-154">К концу этой страницы вы будете основательно понимать следующие руководства.</span><span class="sxs-lookup"><span data-stu-id="1697a-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="1697a-155">Выбор модели взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="1697a-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="1697a-156">Использование руководства по модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="1697a-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="1697a-157">Переход между моделями взаимодействия</span><span class="sxs-lookup"><span data-stu-id="1697a-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="1697a-158">Следующие шаги конструктора</span><span class="sxs-lookup"><span data-stu-id="1697a-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="1697a-159">Выберите модель взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="1697a-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="1697a-160">Скорее всего, разработчики и создатели уже имеют на примете некоторые виды возможностей взаимодействия, которые они хотят, чтобы имели их пользователи.</span><span class="sxs-lookup"><span data-stu-id="1697a-160">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="1697a-161">Чтобы поощрить ориентированный на клиента подход к проектированию, мы рекомендуем следовать приведенным ниже инструкциям, чтобы выбрать модель взаимодействия, оптимизированную для вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="1697a-161">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="1697a-162">Почему нужно следовать руководству?</span><span class="sxs-lookup"><span data-stu-id="1697a-162">Why follow this guidance?</span></span>

* <span data-ttu-id="1697a-163">Наши модели взаимодействия проверяются на предметные и субъективные критерии, такие как физические и когнитивные трудозатраты, интуицию и обучаемость.</span><span class="sxs-lookup"><span data-stu-id="1697a-163">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="1697a-164">Поскольку взаимодействия отличаются, визуальные и звуковые возможности, поведение объекта также могут отличаться между моделями взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-164">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="1697a-165">Объединение частей нескольких моделей взаимодействия вместе создает риск конкурирующих возможностей, таких как одновременные лучи руки и курсор направления головы, которые могут обескуражить и запутать пользователей.</span><span class="sxs-lookup"><span data-stu-id="1697a-165">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which can overwhelm and confuse users.</span></span>

<span data-ttu-id="1697a-166">Ниже приведены несколько примеров того, как возможности и расширения функциональности оптимизируются для каждой модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="1697a-167">Мы часто видим, что у новых пользователей возникают похожие вопросы, например: "Как я узнаю, что система работает, как мне узнать, что я могу сделать, и как узнать, поняла ли она, что я только что сделала?"</span><span class="sxs-lookup"><span data-stu-id="1697a-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1697a-168"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="1697a-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="1697a-169"><strong>Как мне узнать, что она работает?</strong></span><span class="sxs-lookup"><span data-stu-id="1697a-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="1697a-170"><strong>Как мне узнать, что я могу сделать?</strong></span><span class="sxs-lookup"><span data-stu-id="1697a-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="1697a-171"><strong>Как мне узнать, что я только что сделал?</strong></span><span class="sxs-lookup"><span data-stu-id="1697a-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1697a-172"><a href="hands-and-tools.md">Руки и контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="1697a-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="1697a-173">Я вижу сетку руки, я вижу возможности легкого прикосновения или лучей руки/контроллера.</span><span class="sxs-lookup"><span data-stu-id="1697a-173">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="1697a-174">Когда моя рука рядом, я вижу захватные дескрипторы или появление ограничительной рамки.</span><span class="sxs-lookup"><span data-stu-id="1697a-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="1697a-175">Я слышу звуковые сигналы и вижу анимацию при захвате и выпуске.</span><span class="sxs-lookup"><span data-stu-id="1697a-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1697a-176"><a href="gaze-and-commit.md">Направление головы и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="1697a-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="1697a-177">Я вижу курсор в центре моей видимой зоны.</span><span class="sxs-lookup"><span data-stu-id="1697a-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="1697a-178">Курсор направления головы изменяет состояние над определенными объектами.</span><span class="sxs-lookup"><span data-stu-id="1697a-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="1697a-179">Я вижу/слышу визуальные и звуковые подтверждения, когда принимаю меры.</span><span class="sxs-lookup"><span data-stu-id="1697a-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="1697a-180"><a href="hands-free.md">Без использования рук (Направление головы и остановка)</a></span><span class="sxs-lookup"><span data-stu-id="1697a-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="1697a-181">Я вижу курсор в центре моей видимой зоны.</span><span class="sxs-lookup"><span data-stu-id="1697a-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="1697a-182">Я вижу индикатор хода выполнения, когда останавливаюсь на интерактивном объекте.</span><span class="sxs-lookup"><span data-stu-id="1697a-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="1697a-183">Я вижу/слышу визуальные и звуковые подтверждения, когда принимаю меры.</span><span class="sxs-lookup"><span data-stu-id="1697a-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1697a-184"><a href="hands-free.md">Без использования рук (Голосовые команды)</a></span><span class="sxs-lookup"><span data-stu-id="1697a-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="1697a-185">Я вижу индикатор прослушивания и заголовки, которые показывают, что слышала система.</span><span class="sxs-lookup"><span data-stu-id="1697a-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="1697a-186">Я получаю голосовые приглашения и указания.</span><span class="sxs-lookup"><span data-stu-id="1697a-186">I get voice prompts and hints.</span></span>  <span data-ttu-id="1697a-187">Когда я говорю: "Что я могу сказать?"</span><span class="sxs-lookup"><span data-stu-id="1697a-187">When I say "what can I say?"</span></span> <span data-ttu-id="1697a-188">Я вижу отзыв.</span><span class="sxs-lookup"><span data-stu-id="1697a-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="1697a-189">Я вижу/слышу визуальные и звуковые подтверждения, когда даю команду, или получаю устранение неоднозначности при взаимодействии с пользователем, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="1697a-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="1697a-190">Ниже приведены вопросы, которые мы нашли, чтобы помочь рабочей группе выбрать модель взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="1697a-191">Вопрос.  Хотят ли мои пользователи хотят дотрагиваться до голограмм и выполнять точные голографические операции?</span><span class="sxs-lookup"><span data-stu-id="1697a-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="1697a-192">Ответ.  Если это так, проверьте модель взаимодействия "Руки и инструменты" для точного нацеливания и операций с руками или контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="1697a-192">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="1697a-193">Вопрос.  Должны ли мои пользователи не использовать руки для реальных задач?</span><span class="sxs-lookup"><span data-stu-id="1697a-193">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="1697a-194">Ответ.  Если это так, взгляните на модель взаимодействия в режиме "Без использования рук", которая обеспечивает отличные возможности в режиме "Без использования рук" с помощью взаимодействия на основе направления и голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="1697a-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="1697a-195">Вопрос.  У моих пользователей есть время, чтобы изучить взаимодействия для моего приложения смешанной реальности, или им нужно взаимодействие с минимально возможным порогом вхождения?</span><span class="sxs-lookup"><span data-stu-id="1697a-195">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="1697a-196">Ответ.  Мы рекомендуем модель "Руки и инструменты" для самой низкого порога вхождения и наиболее интуитивного взаимодействия, если пользователи могут использовать свои руки для взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-196">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="1697a-197">Вопрос.  Используют ли мои пользователи контроллеры движения для указывания и операций?</span><span class="sxs-lookup"><span data-stu-id="1697a-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="1697a-198">Ответ.  Модель "Руки и инструменты" включает в себя все руководство для успешной работы с контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="1697a-198">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="1697a-199">Вопрос.  Используют ли мои пользователи контроллер специальных возможностей или обычный контроллер Bluetooth, такой как кликер?</span><span class="sxs-lookup"><span data-stu-id="1697a-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="1697a-200">Ответ.  Мы рекомендуем модель "Направление головы и фиксация" для всех не отслеживаемых контроллеров.</span><span class="sxs-lookup"><span data-stu-id="1697a-200">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="1697a-201">Ее разработано, чтобы позволить пользователю пройти весь жизненный путь объекта с помощью простого "целевого и фиксированного" оператора.</span><span class="sxs-lookup"><span data-stu-id="1697a-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="1697a-202">Вопрос. Могут ли мои пользователи развиваться, только во время "переходов" (например, в среде, похожей на слайд-шоу в 3D), в отличие от навигации по плотным макетам элементов управления пользовательского интерфейса?</span><span class="sxs-lookup"><span data-stu-id="1697a-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="1697a-203">Ответ.  Если пользователям не нужно контролировать большой объем пользовательского интерфейса, "Направление головы и фиксация" предлагают удобный для изучения вариант, когда им не нужно беспокоиться о нацеливании.</span><span class="sxs-lookup"><span data-stu-id="1697a-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="1697a-204">Вопрос.  Используют ли мои пользователи как HoloLens (1-го поколения), так и HoloLens 2 / Windows Immersive (VR-гарнитуры)</span><span class="sxs-lookup"><span data-stu-id="1697a-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="1697a-205">Ответ.  Поскольку "Направление головы и фиксация" является моделью взаимодействия для HoloLens (1-го поколения), мы рекомендуем, чтобы создатели, которые поддерживают HoloLens (1-го поколения), использовали "Направление головы и фиксацию" для любых функций или режимов, которые пользователи могут испытывать на гарнитуре HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="1697a-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="1697a-206">Пожалуйста, обратитесь к следующему разделу ниже *Переходные модели взаимодействия* для получения подробных сведений о том, что нужно для комфортного пользования несколькими поколениями HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1697a-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="1697a-207">Вопрос. А как насчет пользователей, которые обычно являются мобильными (занимают большое пространство или перемещаются между ними), по сравнению с пользователями, которые, как правило, работают в одном пространстве?</span><span class="sxs-lookup"><span data-stu-id="1697a-207">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="1697a-208">Ответ.  Любая из моделей взаимодействия подойдет этим пользователям.</span><span class="sxs-lookup"><span data-stu-id="1697a-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="1697a-209">[В ближайшее время](index.md#news-and-notes) появятся дополнительные руководства, касающиеся дизайна приложения.</span><span class="sxs-lookup"><span data-stu-id="1697a-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="1697a-210">Переходные модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="1697a-210">Transition interaction models</span></span>
<span data-ttu-id="1697a-211">Есть также случаи, когда ваши варианты использования могут потребовать использования более чем одной модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-211">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="1697a-212">Например, "поток создания" вашего приложения использует модель взаимодействия "Руки и контроллеры движения", но вы хотите использовать режим "Без использования рук" для выездных техников.</span><span class="sxs-lookup"><span data-stu-id="1697a-212">For example, your app's "creation flow" utilizes the Hands and motion controllers interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="1697a-213">Если ваш опыт требует нескольких моделей взаимодействия, мы обнаружили, что многие пользователи могут столкнуться с трудностями при переходе от одной модели к другой, особенно пользователи, которые являются новичками в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1697a-213">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="1697a-214">Чтобы помочь конструкторам и разработчикам в выборе, который может быть сложным в MR (смешанной реальности), мы работаем над дополнительными рекомендациями по использованию нескольких моделей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1697a-214">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="1697a-215">См. также</span><span class="sxs-lookup"><span data-stu-id="1697a-215">See also</span></span>
* [<span data-ttu-id="1697a-216">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="1697a-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="1697a-217">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="1697a-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="1697a-218">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="1697a-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1697a-219">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="1697a-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="1697a-220">Жесты</span><span class="sxs-lookup"><span data-stu-id="1697a-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="1697a-221">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="1697a-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="1697a-222">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="1697a-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="1697a-223">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="1697a-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="1697a-224">Проектирование пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="1697a-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="1697a-225">Комфорт</span><span class="sxs-lookup"><span data-stu-id="1697a-225">Comfort</span></span>](comfort.md)

