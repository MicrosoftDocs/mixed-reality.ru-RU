---
title: Оптимизация приложения для без участия пользователя
description: Оптимизация приложения для без участия пользователя
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Смешанной реальности, без участия пользователя, помощи и помощи, предназначенных для взаимодействия с разработки
ms.openlocfilehash: b64dec802d8ed2886021a54f302ba4a948c4f5b9
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581034"
---
# <a name="optimizing-your-app-for-hands-free"></a><span data-ttu-id="9101b-104">Оптимизация приложения для без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="9101b-104">Optimizing your app for hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="9101b-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="9101b-105">Scenarios</span></span>

<span data-ttu-id="9101b-106">Как описано в [Общие сведения о модели взаимодействия](interaction-fundamentals.md), после определения пользователей и их целей, задайте себе с какими сложностями окружающей среды или ситуации в масштабах, они могут возникнуть при работе для выполнения своих задач.</span><span class="sxs-lookup"><span data-stu-id="9101b-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="9101b-107">Например, многие пользователи должны использовать опускают руки для достижения своих целей реальных и будет трудно взаимодействия с интерфейсом на основе руки и контроллеры.</span><span class="sxs-lookup"><span data-stu-id="9101b-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="9101b-108">Возможно, некоторые сценарии:</span><span class="sxs-lookup"><span data-stu-id="9101b-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="9101b-109">Ходу задачу, хотя заняты руки</span><span class="sxs-lookup"><span data-stu-id="9101b-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="9101b-110">Ссылки на материалы, хотя заняты рук</span><span class="sxs-lookup"><span data-stu-id="9101b-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="9101b-111">Усталости вручную</span><span class="sxs-lookup"><span data-stu-id="9101b-111">Hand fatigue</span></span>
* <span data-ttu-id="9101b-112">Перчатки, не отслеживается</span><span class="sxs-lookup"><span data-stu-id="9101b-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="9101b-113">Что-то на хранение</span><span class="sxs-lookup"><span data-stu-id="9101b-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="9101b-114">Методы без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="9101b-114">Hands-free modalities</span></span>

### <a name="voice-commanding"></a><span data-ttu-id="9101b-115">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="9101b-115">Voice commanding</span></span>

<span data-ttu-id="9101b-116">С помощью голоса для контроля и управления, интерфейс можно не только позволяет пользователю работать беспроводной, но также пропустить несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="9101b-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="9101b-117">Использование этого модальность могут варьироваться от позволяя пользователю имя любой кнопки, прочитав вслух для того активировать его, как в см. в разделе it-say it, чтобы обменивающиеся данными с агентом, кто может выполнять задачи для вас.</span><span class="sxs-lookup"><span data-stu-id="9101b-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>

* [<span data-ttu-id="9101b-118">Проектирование голосового взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9101b-118">Voice design</span></span>](voice-design.md)


### <a name="head-gaze-and-dwell"></a><span data-ttu-id="9101b-119">HEAD взглядом и простоя</span><span class="sxs-lookup"><span data-stu-id="9101b-119">Head gaze and dwell</span></span>

<span data-ttu-id="9101b-120">В некоторых ситуациях без участия пользователя с помощью голоса не идеальный или даже возможно.</span><span class="sxs-lookup"><span data-stu-id="9101b-120">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="9101b-121">Громкий производственной среде, конфиденциальности и социальных сетей нормы может быть ограничений.</span><span class="sxs-lookup"><span data-stu-id="9101b-121">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="9101b-122">Заголовок помощи + вдаваясь модель позволяет пользователю переходить в приложение с помощью их головной вектор к точке, во время ожидание, или перебои на кнопке будет активировать его истечении определенного времени (обычно около 1 секунды или около того).</span><span class="sxs-lookup"><span data-stu-id="9101b-122">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 

* [<span data-ttu-id="9101b-123">Взглядом и простоя</span><span class="sxs-lookup"><span data-stu-id="9101b-123">Gaze and dwell</span></span>](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="9101b-124">Переход и из него без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="9101b-124">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="9101b-125">В таких случаях освобождение рук взаимодействовать с голограммы для команд и перемещения могут варьироваться от которого является обязательным требованием для эксплуатации приложения, end-to-end, чтобы более удобным, пользователь может перейти в и из в любое время.</span><span class="sxs-lookup"><span data-stu-id="9101b-125">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="9101b-126">Если требования приложения, он всегда будет использоваться без участия пользователя, с помощью простой, голосовые команды или одной голосовых команд, «select», а затем убедитесь в том сделать соответствующие accomodations в пользовательский Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9101b-126">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="9101b-127">Если данные пользователя должен иметь возможность перейти от руки к без участия пользователя по своему усмотрению, затем очень важно учитывать эти принципы:</span><span class="sxs-lookup"><span data-stu-id="9101b-127">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="9101b-128">Предположим, что пользователь уже в режиме, который нужно переключиться в режим</span><span class="sxs-lookup"><span data-stu-id="9101b-128">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="9101b-129">Например если пользователь находится на заводской площадке, просмотра видео ссылку на свой Hololens, решает взять гаечного ключа, чтобы приступить к работе, она скорее хотите для начала работы с беспроводной без необходимости положит гаечного ключа, чтобы нажать кнопку.</span><span class="sxs-lookup"><span data-stu-id="9101b-129">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="9101b-130">Она должна иметь возможность вызвать сеанс голоса с помощью голосовых команд, буду распространяться на уже видимого пользовательского интерфейса, чтобы начать простоя или Предположим, что слово «select».</span><span class="sxs-lookup"><span data-stu-id="9101b-130">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="9101b-131">Пользователь должен иметь возможность:</span><span class="sxs-lookup"><span data-stu-id="9101b-131">The user should have the ability to:</span></span> 
* <span data-ttu-id="9101b-132">Переключиться в режим беспроводной при беспроводной</span><span class="sxs-lookup"><span data-stu-id="9101b-132">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="9101b-133">Переключиться в режим с помощью рук</span><span class="sxs-lookup"><span data-stu-id="9101b-133">Switch to hands with your hands</span></span>
* <span data-ttu-id="9101b-134">Перейдите к контроллеру, с помощью контроллера</span><span class="sxs-lookup"><span data-stu-id="9101b-134">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="9101b-135">Создание избыточных способы переключения между режимами</span><span class="sxs-lookup"><span data-stu-id="9101b-135">Create redundant ways to switch modes</span></span>
<span data-ttu-id="9101b-136">Хотя сведения о доступе первый принцип, второй — о доступности.</span><span class="sxs-lookup"><span data-stu-id="9101b-136">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="9101b-137">Не должно просто быть единый способ перехода и из него режим.</span><span class="sxs-lookup"><span data-stu-id="9101b-137">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="9101b-138">Некоторые примеры будет следующим:</span><span class="sxs-lookup"><span data-stu-id="9101b-138">Some examples would be:</span></span> 
* <span data-ttu-id="9101b-139">Кнопку для инициирования речевое взаимодействие</span><span class="sxs-lookup"><span data-stu-id="9101b-139">A button to begin voice interactions</span></span>
* <span data-ttu-id="9101b-140">Голосовых команд для перехода к использованию взглядом + простоя</span><span class="sxs-lookup"><span data-stu-id="9101b-140">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="9101b-141">Добавление штриха "Драма"</span><span class="sxs-lookup"><span data-stu-id="9101b-141">Add a dash of drama</span></span>
<span data-ttu-id="9101b-142">Переключение режима является проблема – очень важно, когда происходит эти переходы, что они быть явных, даже значительное коммутатора, чтобы позволить пользователю знать, что произошло.</span><span class="sxs-lookup"><span data-stu-id="9101b-142">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="9101b-143">Контрольный список применимости</span><span class="sxs-lookup"><span data-stu-id="9101b-143">Usability checklist</span></span>

<span data-ttu-id="9101b-144">**Пользователь может сделать все, что и все, что без участия пользователя, end-to-end?**</span><span class="sxs-lookup"><span data-stu-id="9101b-144">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="9101b-145">Каждый interactible должны быть доступны без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="9101b-145">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="9101b-146">Убедитесь в наличии замены для всех пользовательских жестов, таких как изменение размера, размещая, вставляет, касания и т. д.</span><span class="sxs-lookup"><span data-stu-id="9101b-146">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="9101b-147">Убедитесь, что пользователь имеет уверены в том, элемент управления пользовательского интерфейса присутствия, размещение, уровень детализации все время</span><span class="sxs-lookup"><span data-stu-id="9101b-147">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="9101b-148">Начало пользовательского интерфейса в сторону</span><span class="sxs-lookup"><span data-stu-id="9101b-148">Getting UI out of the way</span></span>
    * <span data-ttu-id="9101b-149">Адресация пользовательский Интерфейс, который выходит за пределы поля of обзора</span><span class="sxs-lookup"><span data-stu-id="9101b-149">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="9101b-150">Насколько я вижу, где, когда</span><span class="sxs-lookup"><span data-stu-id="9101b-150">How much I see, where, when</span></span>

<span data-ttu-id="9101b-151">**Такое механизм взаимодействия при изучении и подтверждалась пользователями с правом читаемости**</span><span class="sxs-lookup"><span data-stu-id="9101b-151">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="9101b-152">Пользователь понимает...</span><span class="sxs-lookup"><span data-stu-id="9101b-152">Does the user understand ...</span></span>
* <span data-ttu-id="9101b-153">... Режим, они находятся в?</span><span class="sxs-lookup"><span data-stu-id="9101b-153">... What mode they are in?</span></span>
* <span data-ttu-id="9101b-154">... Их возможности в этом режиме?</span><span class="sxs-lookup"><span data-stu-id="9101b-154">... What they can do in this mode?</span></span>
* <span data-ttu-id="9101b-155">... Что такое текущее состояние?</span><span class="sxs-lookup"><span data-stu-id="9101b-155">... What is the current state?</span></span>
* <span data-ttu-id="9101b-156">... Как они могут выведены?</span><span class="sxs-lookup"><span data-stu-id="9101b-156">... How they can transition out?</span></span>
    
<span data-ttu-id="9101b-157">**Пользовательский Интерфейс, обеспечивающее без участия пользователя?**</span><span class="sxs-lookup"><span data-stu-id="9101b-157">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="9101b-158">Пример:</span><span class="sxs-lookup"><span data-stu-id="9101b-158">Ex.</span></span> <span data-ttu-id="9101b-159">Читаемости простоя не предусмотрены для типичных шаблонов поведения 2D</span><span class="sxs-lookup"><span data-stu-id="9101b-159">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="9101b-160">Пример:</span><span class="sxs-lookup"><span data-stu-id="9101b-160">Ex.</span></span> <span data-ttu-id="9101b-161">Нацеливание голосовой лучше поддерживается выделение объекта</span><span class="sxs-lookup"><span data-stu-id="9101b-161">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="9101b-162">Пример:</span><span class="sxs-lookup"><span data-stu-id="9101b-162">Ex.</span></span> <span data-ttu-id="9101b-163">Речевое взаимодействие предпочтительнее с подписями, которые должны быть включен</span><span class="sxs-lookup"><span data-stu-id="9101b-163">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="9101b-164">См. также</span><span class="sxs-lookup"><span data-stu-id="9101b-164">See also</span></span>
* [<span data-ttu-id="9101b-165">Взглядом и фиксации</span><span class="sxs-lookup"><span data-stu-id="9101b-165">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="9101b-166">Прямые манипуляции</span><span class="sxs-lookup"><span data-stu-id="9101b-166">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9101b-167">Точки и фиксации</span><span class="sxs-lookup"><span data-stu-id="9101b-167">Point and commit</span></span>](point-and-commit.md)
