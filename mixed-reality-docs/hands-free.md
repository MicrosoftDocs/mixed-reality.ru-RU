---
title: Без помощи рук
description: Оптимизация приложения для без участия пользователя
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Смешанной реальности, без участия пользователя, помощи и помощи, предназначенных для взаимодействия с разработки
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414393"
---
# <a name="hands-free"></a><span data-ttu-id="cd2d1-104">Без помощи рук</span><span class="sxs-lookup"><span data-stu-id="cd2d1-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="cd2d1-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="cd2d1-105">Scenarios</span></span>

<span data-ttu-id="cd2d1-106">Как описано в [Общие сведения о модели взаимодействия](interaction-fundamentals.md), после определения пользователей и их целей, задайте себе с какими сложностями окружающей среды или ситуации в масштабах, они могут возникнуть при работе для выполнения своих задач.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="cd2d1-107">Например, многие пользователи должны использовать опускают руки для достижения своих целей реальных и затруднит взаимодействия с интерфейсом на основе руки и контроллеры.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="cd2d1-108">Возможно, некоторые сценарии:</span><span class="sxs-lookup"><span data-stu-id="cd2d1-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="cd2d1-109">Ходу задачу, хотя заняты руки</span><span class="sxs-lookup"><span data-stu-id="cd2d1-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="cd2d1-110">Ссылки на материалы, хотя заняты рук</span><span class="sxs-lookup"><span data-stu-id="cd2d1-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="cd2d1-111">Усталости вручную</span><span class="sxs-lookup"><span data-stu-id="cd2d1-111">Hand fatigue</span></span>
* <span data-ttu-id="cd2d1-112">Перчатки, не отслеживается</span><span class="sxs-lookup"><span data-stu-id="cd2d1-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="cd2d1-113">Что-то на хранение</span><span class="sxs-lookup"><span data-stu-id="cd2d1-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="cd2d1-114">Методы без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="cd2d1-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="cd2d1-115">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="cd2d1-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="cd2d1-116">С помощью голоса для контроля и управления, интерфейс можно не только позволяет пользователю работать беспроводной, но также пропустить несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="cd2d1-117">Использование этого модальность могут варьироваться от позволяя пользователю просто прочитать имя любой кнопки вслух для того, чтобы активировать его, как в см. в разделе it-say it, чтобы обменивающиеся данными с агентом, кто может выполнять задачи для вас.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="cd2d1-118">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="cd2d1-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="cd2d1-119">В некоторых ситуациях без участия пользователя с помощью голоса не идеальный или даже возможно.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="cd2d1-120">Громкий производственной среде, конфиденциальности и социальных сетей нормы может быть ограничений.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="cd2d1-121">Заголовок помощи + вдаваясь модель позволяет пользователю переходить в приложение с помощью их головной вектор к точке, во время ожидание, или перебои на кнопке будет активации системы после определенного времени, обычно около 1 секунды или около того.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="cd2d1-122">Переход и из него без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="cd2d1-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="cd2d1-123">Для этих сценариев освобождение рук взаимодействовать с голограммы для выполнение команд и навигации находятся в диапазоне не является обязательным требованием для эксплуатации приложения, end-to-end, более удобным, пользователь может перейти в и из любой время.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="cd2d1-124">Если требования приложения, он всегда будет использоваться без участия пользователя, с помощью простой, голосовые команды или одной голосовых команд, «select», а затем убедитесь в том сделать соответствующие accomodations в пользовательский Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="cd2d1-125">Если данные пользователя должен иметь возможность перейти от руки к без участия пользователя по своему усмотрению, затем важно учитывать следующие принципы.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="cd2d1-126">Предположим, что пользователь уже в режиме, который нужно переключиться в режим</span><span class="sxs-lookup"><span data-stu-id="cd2d1-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="cd2d1-127">Например если пользователь на заводской площадке, просмотра видео ссылку на свой Hololens и решает взять гаечного ключа, чтобы приступить к работе, она скорее будет приступить к работе в беспроводной без необходимости положит гаечного ключа, чтобы нажать кнопку.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="cd2d1-128">Она должна иметь возможность вызвать сеанс голоса с помощью голосовых команд, буду распространяться на уже видимого пользовательского интерфейса, чтобы начать простоя или Предположим, что слово «select».</span><span class="sxs-lookup"><span data-stu-id="cd2d1-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="cd2d1-129">Пользователь должен иметь возможность:</span><span class="sxs-lookup"><span data-stu-id="cd2d1-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="cd2d1-130">Переключиться в режим без участия пользователя во время без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="cd2d1-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="cd2d1-131">Переключиться в режим с помощью рук</span><span class="sxs-lookup"><span data-stu-id="cd2d1-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="cd2d1-132">Перейдите к контроллеру, с помощью контроллера</span><span class="sxs-lookup"><span data-stu-id="cd2d1-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="cd2d1-133">Создание избыточных способы переключения между режимами</span><span class="sxs-lookup"><span data-stu-id="cd2d1-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="cd2d1-134">Хотя сведения о доступе первый принцип, второй — о доступности.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="cd2d1-135">Не должно просто быть единый способ перехода и из него режим.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="cd2d1-136">Некоторые примеры будет следующим:</span><span class="sxs-lookup"><span data-stu-id="cd2d1-136">Some examples would be:</span></span> 
* <span data-ttu-id="cd2d1-137">Кнопку для инициирования речевое взаимодействие</span><span class="sxs-lookup"><span data-stu-id="cd2d1-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="cd2d1-138">Голосовых команд для перехода к использованию взглядом + простоя</span><span class="sxs-lookup"><span data-stu-id="cd2d1-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="cd2d1-139">Добавление штриха "Драма"</span><span class="sxs-lookup"><span data-stu-id="cd2d1-139">Add a dash of drama</span></span>
<span data-ttu-id="cd2d1-140">Переключение режима — серьезное мероприятие — очень важно, что при возникновении эти переходы, они быть явных, даже значительное коммутатора, чтобы позволить пользователю знать, что произошло.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="cd2d1-141">Контрольный список применимости</span><span class="sxs-lookup"><span data-stu-id="cd2d1-141">Usability checklist</span></span>

<span data-ttu-id="cd2d1-142">**Пользователь может сделать все, что и все, что без участия пользователя, end-to-end?**</span><span class="sxs-lookup"><span data-stu-id="cd2d1-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="cd2d1-143">Каждый interactible должны быть доступны без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="cd2d1-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="cd2d1-144">Убедитесь в наличии замены для всех пользовательских жестов, таких как изменение размера, размещая, вставляет, касания и т. д.</span><span class="sxs-lookup"><span data-stu-id="cd2d1-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="cd2d1-145">Убедитесь, что пользователь имеет уверены в том, элемент управления пользовательского интерфейса присутствия, размещения и уровень детализации все время</span><span class="sxs-lookup"><span data-stu-id="cd2d1-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="cd2d1-146">Начало пользовательского интерфейса в сторону</span><span class="sxs-lookup"><span data-stu-id="cd2d1-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="cd2d1-147">Адресация пользовательский Интерфейс, который выходит за пределы поля of обзора</span><span class="sxs-lookup"><span data-stu-id="cd2d1-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="cd2d1-148">Насколько я вижу, где, когда</span><span class="sxs-lookup"><span data-stu-id="cd2d1-148">How much I see, where, when</span></span>

<span data-ttu-id="cd2d1-149">**Такое механизм взаимодействия при изучении и подтверждалась пользователями с правом читаемости**</span><span class="sxs-lookup"><span data-stu-id="cd2d1-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="cd2d1-150">Пользователь понимает...</span><span class="sxs-lookup"><span data-stu-id="cd2d1-150">Does the user understand ...</span></span>
* <span data-ttu-id="cd2d1-151">... Режим, они находятся в?</span><span class="sxs-lookup"><span data-stu-id="cd2d1-151">... What mode they are in?</span></span>
* <span data-ttu-id="cd2d1-152">... Их возможности в этом режиме?</span><span class="sxs-lookup"><span data-stu-id="cd2d1-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="cd2d1-153">... Что такое текущее состояние?</span><span class="sxs-lookup"><span data-stu-id="cd2d1-153">... What is the current state?</span></span>
* <span data-ttu-id="cd2d1-154">... Как они могут выведены?</span><span class="sxs-lookup"><span data-stu-id="cd2d1-154">... How they can transition out?</span></span>
    
<span data-ttu-id="cd2d1-155">**Пользовательский Интерфейс, обеспечивающее без участия пользователя?**</span><span class="sxs-lookup"><span data-stu-id="cd2d1-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="cd2d1-156">Пример. Читаемости простоя не предусмотрены для типичных шаблонов поведения 2D</span><span class="sxs-lookup"><span data-stu-id="cd2d1-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="cd2d1-157">Пример. Нацеливание голосовой лучше поддерживается выделение объекта</span><span class="sxs-lookup"><span data-stu-id="cd2d1-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="cd2d1-158">Пример. Речевое взаимодействие предпочтительнее с подписями, которые должны быть включен</span><span class="sxs-lookup"><span data-stu-id="cd2d1-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="cd2d1-159">См. также</span><span class="sxs-lookup"><span data-stu-id="cd2d1-159">See also</span></span>
* [<span data-ttu-id="cd2d1-160">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="cd2d1-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="cd2d1-161">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="cd2d1-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cd2d1-162">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="cd2d1-162">Point and commit with hands</span></span>](point-and-commit.md)
