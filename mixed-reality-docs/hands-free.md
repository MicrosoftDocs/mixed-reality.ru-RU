---
title: Без помощи рук
description: Оптимизация приложения для работы без участия пользователя
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Смешанная реальность, без участия пользователя, взгляд, выбор целевой платформы, взаимодействие, проектирование
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435073"
---
# <a name="hands-free"></a><span data-ttu-id="3faf8-104">Без помощи рук</span><span class="sxs-lookup"><span data-stu-id="3faf8-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="3faf8-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="3faf8-105">Scenarios</span></span>

<span data-ttu-id="3faf8-106">Как описано в [обзоре модели взаимодействия](interaction-fundamentals.md), если вы определили пользователей и их цели, спросите себя о проблемах, связанных с окружающей средой или ситуацией, которые могут быть выполнены для выполнения своих задач.</span><span class="sxs-lookup"><span data-stu-id="3faf8-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="3faf8-107">Например, многим пользователям необходимо использовать свои руки для выполнения реальных целей, и они будут испытывать трудности при взаимодействии с интерфейсом, основанным на контроллерах.</span><span class="sxs-lookup"><span data-stu-id="3faf8-107">For example, many users need to use their hands to accomplish their real-world goals, and they will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="3faf8-108">Ниже перечислены некоторые конкретные сценарии.</span><span class="sxs-lookup"><span data-stu-id="3faf8-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="3faf8-109">Пошаговая задача, в то время как руки пользователя заняты</span><span class="sxs-lookup"><span data-stu-id="3faf8-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="3faf8-110">Обращение к материалам в то время, когда руки пользователя заняты</span><span class="sxs-lookup"><span data-stu-id="3faf8-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="3faf8-111">Рука выносливости</span><span class="sxs-lookup"><span data-stu-id="3faf8-111">Hand fatigue</span></span>
* <span data-ttu-id="3faf8-112">Перчатки, которые не могут быть отслеживанием</span><span class="sxs-lookup"><span data-stu-id="3faf8-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="3faf8-113">Поставить что-нибудь в руки</span><span class="sxs-lookup"><span data-stu-id="3faf8-113">Carrying something in their hands</span></span>
* <span data-ttu-id="3faf8-114">Неудобства социальных сетей для выполнения больших жестов</span><span class="sxs-lookup"><span data-stu-id="3faf8-114">Social awkwardness to perform large hand gestures</span></span>
* <span data-ttu-id="3faf8-115">Ограниченные пробелы</span><span class="sxs-lookup"><span data-stu-id="3faf8-115">Tight spaces</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="3faf8-116">Бесплатный модальностей</span><span class="sxs-lookup"><span data-stu-id="3faf8-116">Hands-free modalities</span></span>

### <a name="voice-inputvoice-inputmd"></a>[<span data-ttu-id="3faf8-117">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="3faf8-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="3faf8-118">Использование голоса для команды и управления интерфейсом предоставляет удобный способ для работы без участия пользователя и использования сочетаний клавиш для гибкого пропуска нескольких шагов при необходимости.</span><span class="sxs-lookup"><span data-stu-id="3faf8-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to flexibly skip multiple steps if desired.</span></span> <span data-ttu-id="3faf8-119">С помощью голосового ввода пользователь может просто прочитать любое имя кнопки со звуком, чтобы активировать его _("Просмотреть", сказать ")"_ и противоречить с цифровым агентом, который может выполнять задачи.</span><span class="sxs-lookup"><span data-stu-id="3faf8-119">With voice input, the user can simply read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="3faf8-120">Взгляд и остановка</span><span class="sxs-lookup"><span data-stu-id="3faf8-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="3faf8-121">В некоторых ситуациях использование голоса не является идеальным или даже невозможным.</span><span class="sxs-lookup"><span data-stu-id="3faf8-121">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="3faf8-122">Все они могут быть ограничены громкими фабриками, конфиденциальностью или социальными нормами.</span><span class="sxs-lookup"><span data-stu-id="3faf8-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="3faf8-123">Модель "наблюдатель + вдаваясь" позволяет пользователю перемещаться по приложению без каких-либо дополнительных входных данных, помимо взгляда на глаза или головного взгляда: пользователь просто сохраняет облаками (с их головой или глазами) на целевом объекте и сохраняет его в течение некоторого времени.</span><span class="sxs-lookup"><span data-stu-id="3faf8-123">The gaze + dwell model allows the user to navigate an app without any additional input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="3faf8-124">Дополнительные сведения о конкретных аспектах проектирования для взгляда на вдаваясь см. в статье [взгляд — взгляд + вдаваясь](gaze-and-dwell-eyes.md) и [head-взгляд + вдаваясь](gaze-and-dwell-head.md).</span><span class="sxs-lookup"><span data-stu-id="3faf8-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="3faf8-125">Перевод в руки и выход из них</span><span class="sxs-lookup"><span data-stu-id="3faf8-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="3faf8-126">В этих сценариях вы освобождаете свои руки, которые могут поработать с голограммами для команд и переходов. это может привести к подлине абсолютного требования к работе приложения, а также к дополнительным требованиям, которые пользователь может переносить в любой Таймаут.</span><span class="sxs-lookup"><span data-stu-id="3faf8-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="3faf8-127">Если требуется, чтобы приложение всегда использовало практически бесплатно, с помощью вдаваясь, настраиваемых речевых команд или одной команды Voice, выберите "Select", а затем убедитесь, что в пользовательском интерфейсе нужны соответствующие места.</span><span class="sxs-lookup"><span data-stu-id="3faf8-127">If the requirement of the application is that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="3faf8-128">Если целевой пользователь должен иметь возможность переключаться с руки на произвольный по собственному усмотрению, важно учитывать следующие принципы.</span><span class="sxs-lookup"><span data-stu-id="3faf8-128">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="3faf8-129">Предположим, что пользователь уже находится в режиме, на который нужно переключиться</span><span class="sxs-lookup"><span data-stu-id="3faf8-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="3faf8-130">Например, если пользователь находится в производстве фабрики, просматривает ссылку на видео на его HoloLens и принимает решение гаечного ключа для начала работы, она, скорее всего, начнет работать практически без необходимости, не выполняя гаечного ключа для нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="3faf8-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="3faf8-131">Она должна иметь возможность вызвать голосовый сеанс с помощью голосовых команд, вдаваясь в уже видимом пользовательском интерфейсе, чтобы начать вдаваясь, или скажите слово «SELECT».</span><span class="sxs-lookup"><span data-stu-id="3faf8-131">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="3faf8-132">Пользователь должен иметь возможность:</span><span class="sxs-lookup"><span data-stu-id="3faf8-132">The user should have the ability to:</span></span> 
* <span data-ttu-id="3faf8-133">Переключение на практически без участия</span><span class="sxs-lookup"><span data-stu-id="3faf8-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="3faf8-134">Переключение на руки</span><span class="sxs-lookup"><span data-stu-id="3faf8-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="3faf8-135">Переключение на контроллер с помощью контроллера</span><span class="sxs-lookup"><span data-stu-id="3faf8-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="3faf8-136">Создание избыточных способов переключения режимов</span><span class="sxs-lookup"><span data-stu-id="3faf8-136">Create redundant ways to switch modes</span></span>
<span data-ttu-id="3faf8-137">Первый принцип — о доступе, второй — о доступности.</span><span class="sxs-lookup"><span data-stu-id="3faf8-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="3faf8-138">Не нужно только один способ перехода в режим и из него.</span><span class="sxs-lookup"><span data-stu-id="3faf8-138">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="3faf8-139">Ниже приведены некоторые примеры.</span><span class="sxs-lookup"><span data-stu-id="3faf8-139">Some examples would be:</span></span> 
* <span data-ttu-id="3faf8-140">Кнопка для начала взаимодействия с голосовыми сообщениями</span><span class="sxs-lookup"><span data-stu-id="3faf8-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="3faf8-141">Голосовая команда для перехода, с использованием Head-взгляда и вдаваясь</span><span class="sxs-lookup"><span data-stu-id="3faf8-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="3faf8-142">Добавление тире драма</span><span class="sxs-lookup"><span data-stu-id="3faf8-142">Add a dash of drama</span></span>
<span data-ttu-id="3faf8-143">Переключатель в режиме «режим» очень важен — важно, что когда эти переходы происходят в виде явного, даже значительного коммутатора, чтобы пользователь мог узнать, что произошло.</span><span class="sxs-lookup"><span data-stu-id="3faf8-143">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="3faf8-144">Контрольный список для удобства использования</span><span class="sxs-lookup"><span data-stu-id="3faf8-144">Usability checklist</span></span>

<span data-ttu-id="3faf8-145">**Может ли пользователь выполнять все и все возможности без участия пользователя?**</span><span class="sxs-lookup"><span data-stu-id="3faf8-145">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="3faf8-146">Все взаимодействующие должны быть доступными практически без участия</span><span class="sxs-lookup"><span data-stu-id="3faf8-146">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="3faf8-147">Убедитесь в наличии замены для всех пользовательских жестов, таких как изменение размера, размещение, прокрутка, касания и т. д.</span><span class="sxs-lookup"><span data-stu-id="3faf8-147">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="3faf8-148">Убедитесь, что пользователь уверенно контролирует присутствие, размещение и детализацию пользовательского интерфейса в любое время.</span><span class="sxs-lookup"><span data-stu-id="3faf8-148">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="3faf8-149">Получение пользовательского интерфейса из пути</span><span class="sxs-lookup"><span data-stu-id="3faf8-149">Getting UI out of the way</span></span>
    * <span data-ttu-id="3faf8-150">Адрес пользовательского интерфейса, который не является полем представления (фов)</span><span class="sxs-lookup"><span data-stu-id="3faf8-150">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="3faf8-151">Сколько я вижу, где, когда</span><span class="sxs-lookup"><span data-stu-id="3faf8-151">How much I see, where, when</span></span>

<span data-ttu-id="3faf8-152">**Является ли механика взаимодействия, которую вы научили и зааффорданцеси с помощью правильного объекта?**</span><span class="sxs-lookup"><span data-stu-id="3faf8-152">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="3faf8-153">Понимает ли пользователь...</span><span class="sxs-lookup"><span data-stu-id="3faf8-153">Does the user understand ...</span></span>
* <span data-ttu-id="3faf8-154">... В каком режиме они находятся?</span><span class="sxs-lookup"><span data-stu-id="3faf8-154">... What mode they are in?</span></span>
* <span data-ttu-id="3faf8-155">... Что можно сделать в этом режиме?</span><span class="sxs-lookup"><span data-stu-id="3faf8-155">... What they can do in this mode?</span></span>
* <span data-ttu-id="3faf8-156">... Что такое текущее состояние?</span><span class="sxs-lookup"><span data-stu-id="3faf8-156">... What is the current state?</span></span>
* <span data-ttu-id="3faf8-157">... Как они могут переходить?</span><span class="sxs-lookup"><span data-stu-id="3faf8-157">... How they can transition out?</span></span>
    
<span data-ttu-id="3faf8-158">**Оптимизирован ли пользовательский интерфейс для работы без участия пользователя?**</span><span class="sxs-lookup"><span data-stu-id="3faf8-158">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="3faf8-159">Пример: вдаваясь аффорданцес не встроены в стандартные 2D-шаблоны</span><span class="sxs-lookup"><span data-stu-id="3faf8-159">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="3faf8-160">Пример: нацеливание на голоса лучше с выделением объектов</span><span class="sxs-lookup"><span data-stu-id="3faf8-160">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="3faf8-161">Пример: голосовое взаимодействие лучше с субтитрами, которые необходимо включить.</span><span class="sxs-lookup"><span data-stu-id="3faf8-161">Example: Voice interactions are better with captions that need to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="3faf8-162">См. также</span><span class="sxs-lookup"><span data-stu-id="3faf8-162">See also</span></span>
* [<span data-ttu-id="3faf8-163">Отслеживание глаз в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3faf8-163">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="3faf8-164">Взгляните и зафиксируйте</span><span class="sxs-lookup"><span data-stu-id="3faf8-164">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3faf8-165">Взгляд и остановка</span><span class="sxs-lookup"><span data-stu-id="3faf8-165">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="3faf8-166">Руки — прямое управление</span><span class="sxs-lookup"><span data-stu-id="3faf8-166">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3faf8-167">Жесты руки</span><span class="sxs-lookup"><span data-stu-id="3faf8-167">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="3faf8-168">Практические указания и фиксация</span><span class="sxs-lookup"><span data-stu-id="3faf8-168">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="3faf8-169">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="3faf8-169">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="3faf8-170">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="3faf8-170">Voice input</span></span>](voice-input.md)
