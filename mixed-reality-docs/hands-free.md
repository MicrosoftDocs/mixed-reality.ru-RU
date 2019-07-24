---
title: Без помощи рук
description: Оптимизация приложения для работы без участия пользователя
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Смешанная реальность, без участия пользователя, взгляд, выбор целевой платформы, взаимодействие, проектирование
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414393"
---
# <a name="hands-free"></a><span data-ttu-id="4735e-104">Без помощи рук</span><span class="sxs-lookup"><span data-stu-id="4735e-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="4735e-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="4735e-105">Scenarios</span></span>

<span data-ttu-id="4735e-106">Как описано в [обзоре модели взаимодействия](interaction-fundamentals.md), определив пользователей и их цели, спросите, какие проблемы возникают в окружающей среде или ситуации, когда они работают для выполнения своих задач.</span><span class="sxs-lookup"><span data-stu-id="4735e-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="4735e-107">Например, многие пользователи должны использовать свои руки для выполнения реальных целей, а также испытывают трудности при взаимодействии с интерфейсом, основанным на контроллерах.</span><span class="sxs-lookup"><span data-stu-id="4735e-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="4735e-108">Некоторые конкретные сценарии могут быть:</span><span class="sxs-lookup"><span data-stu-id="4735e-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="4735e-109">Пошаговая задача, в то время как руки заняты</span><span class="sxs-lookup"><span data-stu-id="4735e-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="4735e-110">Ссылки на материалы, пока ваши руки заняты</span><span class="sxs-lookup"><span data-stu-id="4735e-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="4735e-111">Рука выносливости</span><span class="sxs-lookup"><span data-stu-id="4735e-111">Hand fatigue</span></span>
* <span data-ttu-id="4735e-112">Перчатки, которые не могут быть отслеживанием</span><span class="sxs-lookup"><span data-stu-id="4735e-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="4735e-113">Что-то</span><span class="sxs-lookup"><span data-stu-id="4735e-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="4735e-114">Бесплатный модальностей</span><span class="sxs-lookup"><span data-stu-id="4735e-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="4735e-115">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="4735e-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="4735e-116">Использование голоса для команды и управления интерфейсом может не только позволить пользователю выполнять хандсфри, но и пропустить несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="4735e-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="4735e-117">Использование этого модальности может варьироваться от предоставления пользователю возможности просто читать вслух любое имя кнопки, чтобы активировать ее, как показано в разделе «см. в.......», чтобы реализовать агент, который может выполнять задачи.</span><span class="sxs-lookup"><span data-stu-id="4735e-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="4735e-118">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="4735e-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="4735e-119">В некоторых ситуациях использование голоса не является идеальным или даже невозможным.</span><span class="sxs-lookup"><span data-stu-id="4735e-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="4735e-120">Все они могут быть ограничены громкими фабриками, конфиденциальностью или социальными нормами.</span><span class="sxs-lookup"><span data-stu-id="4735e-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="4735e-121">С помощью модели "головное взгляд + вдаваясь" пользователь может перемещаться по приложению, используя его вектор в виде головного элемента для указания, времени задержки или двеллинг на кнопке после определенного промежутка времени (обычно около 1 секунды).</span><span class="sxs-lookup"><span data-stu-id="4735e-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="4735e-122">Перевод в руки и выход из них</span><span class="sxs-lookup"><span data-stu-id="4735e-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="4735e-123">В этих сценариях вы освобождаете свои руки, которые могут поработать с голограммами для команд и переходов. это может привести к подлине абсолютного требования к работе приложения, а также к дополнительным требованиям, которые пользователь может переносить в любой Таймаут.</span><span class="sxs-lookup"><span data-stu-id="4735e-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="4735e-124">Если требуется, чтобы приложение всегда использовало практически бесплатно, используя вдаваясь, команды Voice или одну команду Voice, выберите "Select", а затем убедитесь, что в пользовательском интерфейсе есть соответствующие аккомодатионс.</span><span class="sxs-lookup"><span data-stu-id="4735e-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="4735e-125">Если целевой пользователь должен иметь возможность переключаться с руки на произвольный по собственному усмотрению, важно учитывать следующие принципы.</span><span class="sxs-lookup"><span data-stu-id="4735e-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="4735e-126">Предположим, что пользователь уже находится в режиме, на который нужно переключиться</span><span class="sxs-lookup"><span data-stu-id="4735e-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="4735e-127">Например, если пользователь находится в производстве фабрики, просматривает ссылку на видео о его Hololens и принимает решение гаечного ключа для начала работы, она, скорее всего, начнет работать в хандсфри, не отключая гаечного ключа для нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="4735e-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="4735e-128">Она должна иметь возможность вызвать голосовый сеанс с помощью голосовых команд, вдаваясь в уже видимом пользовательском интерфейсе, чтобы начать вдаваясь, или скажите слово «SELECT».</span><span class="sxs-lookup"><span data-stu-id="4735e-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="4735e-129">Пользователь должен иметь возможность:</span><span class="sxs-lookup"><span data-stu-id="4735e-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="4735e-130">Переключение на практически без участия</span><span class="sxs-lookup"><span data-stu-id="4735e-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="4735e-131">Переключение на руки</span><span class="sxs-lookup"><span data-stu-id="4735e-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="4735e-132">Переключение на контроллер с помощью контроллера</span><span class="sxs-lookup"><span data-stu-id="4735e-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="4735e-133">Создание избыточных способов переключения режимов</span><span class="sxs-lookup"><span data-stu-id="4735e-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="4735e-134">Первый принцип — о доступе, второй — о доступности.</span><span class="sxs-lookup"><span data-stu-id="4735e-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="4735e-135">Не нужно только один способ перехода в режим и из него.</span><span class="sxs-lookup"><span data-stu-id="4735e-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="4735e-136">Ниже приведены некоторые примеры.</span><span class="sxs-lookup"><span data-stu-id="4735e-136">Some examples would be:</span></span> 
* <span data-ttu-id="4735e-137">Кнопка для начала взаимодействия с голосовыми сообщениями</span><span class="sxs-lookup"><span data-stu-id="4735e-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="4735e-138">Голосовая команда для перехода с помощью команды "Взгляните + вдаваясь"</span><span class="sxs-lookup"><span data-stu-id="4735e-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="4735e-139">Добавление тире драма</span><span class="sxs-lookup"><span data-stu-id="4735e-139">Add a dash of drama</span></span>
<span data-ttu-id="4735e-140">Переключение режима — большое дело — важно, что когда эти переходы происходят в виде явного, даже незначительного коммутатора, чтобы пользователь мог узнать, что произошло.</span><span class="sxs-lookup"><span data-stu-id="4735e-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="4735e-141">Контрольный список для удобства использования</span><span class="sxs-lookup"><span data-stu-id="4735e-141">Usability checklist</span></span>

<span data-ttu-id="4735e-142">**Может ли пользователь выполнять все и все возможности без участия пользователя?**</span><span class="sxs-lookup"><span data-stu-id="4735e-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="4735e-143">Каждый интерактибле должен быть доступен практически без участия</span><span class="sxs-lookup"><span data-stu-id="4735e-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="4735e-144">Убедитесь в наличии замены для всех пользовательских жестов, таких как изменение размера, размещение, прокрутка, касания и т. д.</span><span class="sxs-lookup"><span data-stu-id="4735e-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="4735e-145">Убедитесь, что пользователь уверенно контролирует присутствие, размещение и детализацию пользовательского интерфейса в любое время.</span><span class="sxs-lookup"><span data-stu-id="4735e-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="4735e-146">Получение пользовательского интерфейса из пути</span><span class="sxs-lookup"><span data-stu-id="4735e-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="4735e-147">Адрес пользовательского интерфейса, который не является полем представления (фов)</span><span class="sxs-lookup"><span data-stu-id="4735e-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="4735e-148">Сколько я вижу, где, когда</span><span class="sxs-lookup"><span data-stu-id="4735e-148">How much I see, where, when</span></span>

<span data-ttu-id="4735e-149">**Является ли механика взаимодействия, которую вы научили и зааффорданцеси с помощью правильного объекта?**</span><span class="sxs-lookup"><span data-stu-id="4735e-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="4735e-150">Понимает ли пользователь...</span><span class="sxs-lookup"><span data-stu-id="4735e-150">Does the user understand ...</span></span>
* <span data-ttu-id="4735e-151">... В каком режиме они находятся?</span><span class="sxs-lookup"><span data-stu-id="4735e-151">... What mode they are in?</span></span>
* <span data-ttu-id="4735e-152">... Что можно сделать в этом режиме?</span><span class="sxs-lookup"><span data-stu-id="4735e-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="4735e-153">... Что такое текущее состояние?</span><span class="sxs-lookup"><span data-stu-id="4735e-153">... What is the current state?</span></span>
* <span data-ttu-id="4735e-154">... Как они могут переходить?</span><span class="sxs-lookup"><span data-stu-id="4735e-154">... How they can transition out?</span></span>
    
<span data-ttu-id="4735e-155">**Оптимизирован ли пользовательский интерфейс для работы без участия пользователя?**</span><span class="sxs-lookup"><span data-stu-id="4735e-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="4735e-156">Пример. Вдаваясь аффорданцес не встроены в стандартные 2D-шаблоны</span><span class="sxs-lookup"><span data-stu-id="4735e-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="4735e-157">Пример. Назначение голоса лучше с выделением объектов</span><span class="sxs-lookup"><span data-stu-id="4735e-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="4735e-158">Пример. При голосовом взаимодействии лучше использовать субтитры, которые должны быть включены</span><span class="sxs-lookup"><span data-stu-id="4735e-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="4735e-159">См. также</span><span class="sxs-lookup"><span data-stu-id="4735e-159">See also</span></span>
* [<span data-ttu-id="4735e-160">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="4735e-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="4735e-161">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="4735e-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4735e-162">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="4735e-162">Point and commit with hands</span></span>](point-and-commit.md)
