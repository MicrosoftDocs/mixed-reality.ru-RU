---
title: Направление головы и остановка
description: Общие сведения о модели направления головы и остановки
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Смешанная реальность, взгляд, остановка, взаимодействие , конструктор
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439315"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="5d98c-104">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="5d98c-104">Head-gaze and dwell</span></span>

<span data-ttu-id="5d98c-105">Когда руки заняты инструментами и деталями, жестикулировать может быть сложно или невозможно.</span><span class="sxs-lookup"><span data-stu-id="5d98c-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="5d98c-106">При определенных обстоятельствах, например в чрезмерно шумных условиях, на голосовые команды, такие как жесты, нельзя положиться.</span><span class="sxs-lookup"><span data-stu-id="5d98c-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="5d98c-107">Кроме того, использование голоса для управления компьютерами не всегда доступно, но оно, безусловно, становится более популярным!</span><span class="sxs-lookup"><span data-stu-id="5d98c-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="5d98c-108">"Направление головы и остановка" предлагает наиболее знакомый и простой в освоении механизм для работы в режиме "внимание" и "громкая связь" на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5d98c-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="5d98c-109">Кроме того, опция "Направление головы и остановка" на 100 % надежна, независимо от шумовых помех и проблем с тишиной в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="5d98c-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="5d98c-110">Сценарии</span><span class="sxs-lookup"><span data-stu-id="5d98c-110">Scenarios</span></span>

<span data-ttu-id="5d98c-111">Руководитель-взгляд и вдаваясь предназначен в сценариях, где руки человека заняты другими задачами, а речь не 100% надежна или недоступна из-за ограничений среды или социальных сетей.</span><span class="sxs-lookup"><span data-stu-id="5d98c-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="5d98c-112">Хорошим примером является пользователь, носящий HoloLens для получения справочной информации при ремонте двигателя автомобиля.</span><span class="sxs-lookup"><span data-stu-id="5d98c-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="5d98c-113">Их руки заняты инструментами или поддержкой своего тела, когда они нагибаются в моторный отсек.</span><span class="sxs-lookup"><span data-stu-id="5d98c-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="5d98c-114">Гараж — шумный, с постоянным грохотом и гудением инструментов, что создает помехи голосовым командам.</span><span class="sxs-lookup"><span data-stu-id="5d98c-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="5d98c-115">Head-взгляд и вдаваясь позволяют пользователю, использующему HoloLens, уверенно перемещаться по справочным материалам, не прерывая рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="5d98c-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="5d98c-116">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="5d98c-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5d98c-117"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="5d98c-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="5d98c-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5d98c-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="5d98c-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="5d98c-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="5d98c-120"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="5d98c-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5d98c-121">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="5d98c-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="5d98c-122">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="5d98c-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="5d98c-123">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="5d98c-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="5d98c-124">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="5d98c-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="5d98c-125">Принципы проектирования</span><span class="sxs-lookup"><span data-stu-id="5d98c-125">Design principles</span></span>

<span data-ttu-id="5d98c-126">**Избегайте "Взгляните как оружия"**</span><span class="sxs-lookup"><span data-stu-id="5d98c-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="5d98c-127">"Направление головы и остановка" требует, чтобы визуальный отзыв был понятным, но слишком перенасыщенный отзыв может вызвать беспокойство.</span><span class="sxs-lookup"><span data-stu-id="5d98c-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="5d98c-128">Отзыв должен помочь пользователю узнать, на что он нацелен, но не выбирать цель автоматически по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="5d98c-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="5d98c-129">Чтение текста, значков и меток требует дополнительного внимания, чтобы предоставить человеку возможность усвоить информацию перед выбором.</span><span class="sxs-lookup"><span data-stu-id="5d98c-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="5d98c-130">**Поиск скорости сказку**</span><span class="sxs-lookup"><span data-stu-id="5d98c-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="5d98c-131">Взаимодействия с остановкой могут иметь разные таймеры, основанные на влиянии навигации. Более часто используемые функции обычно выигрывают от более короткого времени заполнения, в то время как более последовательные функции могут выиграть от более длительного времени заполнения.</span><span class="sxs-lookup"><span data-stu-id="5d98c-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="5d98c-132">При использовании способа заполнения для отображения этих таймеров анимационные кривые цвета заполнения могут положительно влиять на ощущение более короткого времени заполнения.</span><span class="sxs-lookup"><span data-stu-id="5d98c-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="5d98c-133">Необходимо принять во внимание возможность принятия пользователем решения по переопределению скорости заполнения в пользу быстрой, средней или медленной.</span><span class="sxs-lookup"><span data-stu-id="5d98c-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="5d98c-134">**Скажите «нет», чтобы сказать-yo**</span><span class="sxs-lookup"><span data-stu-id="5d98c-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="5d98c-135">Эффект йо-йо — это неудобный шаблон движения головы, который может возникнуть, когда размещение содержимого, контроль за направлением головы и остановкой заставляет людей постоянно смотреть вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="5d98c-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="5d98c-136">Например, в списке на панели навигации с кнопкой Head-взгляд и вдаваясь в нижней части вызывается цикл-Поиск в вдаваясь, поиск в результатах, поиск в вдаваясь и т. д. Такой шаблон некомфортен, поэтому его следует избегать, размещая элементы управления навигацией в централизованном расположении, для которого требуется меньшее количество резервных копий.</span><span class="sxs-lookup"><span data-stu-id="5d98c-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="5d98c-137">Расположение кнопок остановки относительно их воздействия становится важным для комфорта.</span><span class="sxs-lookup"><span data-stu-id="5d98c-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="5d98c-138">Руководства и рекомендации по взаимодействию с пользователем</span><span class="sxs-lookup"><span data-stu-id="5d98c-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="5d98c-139">Размеры цели</span><span class="sxs-lookup"><span data-stu-id="5d98c-139">Target sizes</span></span>
  <span data-ttu-id="5d98c-140">Чтобы иметь возможность легко получить доступ, целевые объекты Head-взгляд и вдаваясь должны быть достаточно большими, чтобы иметь возможность взглянуть на них и вместить один из них в целевое время.</span><span class="sxs-lookup"><span data-stu-id="5d98c-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="5d98c-141">Для достижения наиболее удобного интерфейса рекомендуется использовать минимальный целевой размер в 2 градусах.</span><span class="sxs-lookup"><span data-stu-id="5d98c-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="5d98c-142">Визуальная обратная связь</span><span class="sxs-lookup"><span data-stu-id="5d98c-142">Visual feedback</span></span>

<span data-ttu-id="5d98c-143">При использовании радиальной заливки для представления таймера остановки начинайте с центра кнопки.</span><span class="sxs-lookup"><span data-stu-id="5d98c-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="5d98c-144">Последовательный ответ меньше сбивает с толку, чем все разные направления на разных кнопках.</span><span class="sxs-lookup"><span data-stu-id="5d98c-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="5d98c-145">Это правило может быть нарушено для направленных взаимодействий (например, навигация вверх/вниз/влево/вправо и т. д.).</span><span class="sxs-lookup"><span data-stu-id="5d98c-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="5d98c-146">Например, "Руководство по Microsoft Dynamics 365" делает исключение для ДАЛЕЕ/НАЗАД при заливке слева направо.</span><span class="sxs-lookup"><span data-stu-id="5d98c-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="5d98c-147">Подумайте о перевертывании радиальной заливки снаружи при выключении кнопки.</span><span class="sxs-lookup"><span data-stu-id="5d98c-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="5d98c-148">Ощущение инверсии после нажатия кнопки — хороший визуальный шаблон, который следует поддерживать.</span><span class="sxs-lookup"><span data-stu-id="5d98c-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="5d98c-149">Поэтапное представление информации</span><span class="sxs-lookup"><span data-stu-id="5d98c-149">Progressive disclosure</span></span>

<span data-ttu-id="5d98c-150">Поэтапное представление информации означает только представление того количества деталей, которое уместно на каждом этапе взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="5d98c-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="5d98c-151">Для остановки это означает, что целевые объекты остановки обнаруживаются при выделении (например, в элементе управления "Список").</span><span class="sxs-lookup"><span data-stu-id="5d98c-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="5d98c-152">Целевые объекты слишком большого размера</span><span class="sxs-lookup"><span data-stu-id="5d98c-152">Oversized targets</span></span>
<span data-ttu-id="5d98c-153">Область остановки может быть больше, чем неактивный значок, чтобы проще было использовать, например, кнопку "Назад" в Руководстве по Microsoft Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5d98c-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="5d98c-154">Предотвращение мерцания с помощью задержки ответа</span><span class="sxs-lookup"><span data-stu-id="5d98c-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="5d98c-155">Используйте короткую задержку перед началом визуального ответа, чтобы избежать мерцания, когда кто-то не заметит целевой объект остановки.</span><span class="sxs-lookup"><span data-stu-id="5d98c-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="5d98c-156">Для кнопок, часто взаимодействующих с, следует держать задержку очень коротким, чтобы приложение оставалось активным.</span><span class="sxs-lookup"><span data-stu-id="5d98c-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="5d98c-157">Для кнопок, которые взаимодействуют с нечасто, может быть целесообразно более длительная задержка, чтобы избежать недостаточного твитчи.</span><span class="sxs-lookup"><span data-stu-id="5d98c-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="5d98c-158">Шаблоны пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="5d98c-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="5d98c-159">Высокая частота кнопок</span><span class="sxs-lookup"><span data-stu-id="5d98c-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5d98c-160">Кнопки с высокой частотой — это кнопки, которые обычно используются во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="5d98c-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="5d98c-161">Наглядным примером являются кнопки "Далее" и "Назад" в Руководстве по Microsoft Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5d98c-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="5d98c-162">**Проектирован**</span><span class="sxs-lookup"><span data-stu-id="5d98c-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="5d98c-163">Кнопки с высокой частотой должны быть большими, проще в попадании с помощью головного взгляда</span><span class="sxs-lookup"><span data-stu-id="5d98c-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="5d98c-164">Оставайтесь рядом с высотой глаз, чтобы избежать эффекта эргономичного ограничения.</span><span class="sxs-lookup"><span data-stu-id="5d98c-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="5d98c-165">*Изображение: кнопка "Далее" руководства по Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="5d98c-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Кнопка "Далее" руководства по Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="5d98c-167">Редко использующиеся кнопки</span><span class="sxs-lookup"><span data-stu-id="5d98c-167">Low frequency buttons</span></span>
<span data-ttu-id="5d98c-168">Редко использующиеся кнопки — это кнопки, не взаимодействующие в приложении регулярно.</span><span class="sxs-lookup"><span data-stu-id="5d98c-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="5d98c-169">Наглядным примером может быть кнопка для доступа к меню параметров или кнопка для очистки всей работы.</span><span class="sxs-lookup"><span data-stu-id="5d98c-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="5d98c-170">Попытайтесь, чтобы на эти кнопки не влияла частая смена направления головы, чтобы избежать случайной активации.</span><span class="sxs-lookup"><span data-stu-id="5d98c-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="5d98c-171">Подтверждения</span><span class="sxs-lookup"><span data-stu-id="5d98c-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5d98c-172">Когда какое-либо действие оказывает существенное влияние, такое как снятие денег, удаление работы или запуск длинного процесса, полезно подтвердить, что пользователь хотел выбрать кнопку.</span><span class="sxs-lookup"><span data-stu-id="5d98c-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="5d98c-173">**Проектирован**</span><span class="sxs-lookup"><span data-stu-id="5d98c-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="5d98c-174">Показать выбранные выделения на главной кнопке.</span><span class="sxs-lookup"><span data-stu-id="5d98c-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="5d98c-175">Обнаружить целевой объект остановки одновременно с выбранным выделением.</span><span class="sxs-lookup"><span data-stu-id="5d98c-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="5d98c-176">Для дополнительной кнопки показать целевой объект остановки в направлении головы.</span><span class="sxs-lookup"><span data-stu-id="5d98c-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="5d98c-177">*Изображение: диалоговое окно подтверждения руководств по Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="5d98c-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Диалоговое окно для подтверждения руководств по Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="5d98c-179">Выключатели</span><span class="sxs-lookup"><span data-stu-id="5d98c-179">Toggle buttons</span></span>
<span data-ttu-id="5d98c-180">Выключатели требуют некоторой детализированной логики для правильной работы.</span><span class="sxs-lookup"><span data-stu-id="5d98c-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="5d98c-181">Когда пользователь останавливается на выключателе и активирует его, ему необходимо выйти из кнопки и затем вернуться, чтобы перезапустить логику остановки.</span><span class="sxs-lookup"><span data-stu-id="5d98c-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="5d98c-182">Важно, чтобы переключаемые кнопки имели четкое активное или неактивное состояние.</span><span class="sxs-lookup"><span data-stu-id="5d98c-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="5d98c-183">Представления списка</span><span class="sxs-lookup"><span data-stu-id="5d98c-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5d98c-184">Представления списка представляют собой определенную задачу для вдаваясь и ввода в голову.</span><span class="sxs-lookup"><span data-stu-id="5d98c-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="5d98c-185">Люди должны иметь возможность просматривать содержимое, не чувствуя, что должны быть осторожными с целевыми объектами остановки.</span><span class="sxs-lookup"><span data-stu-id="5d98c-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="5d98c-186">**Проектирован**</span><span class="sxs-lookup"><span data-stu-id="5d98c-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="5d98c-187">Выделяйте весь строкой, когда Head-газед, но не начинайте вдаваясь, если только Headed-взгляд находится на определенном целевом объекте вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="5d98c-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="5d98c-188">Отображать целевой объект вдаваясь только в том случае, если строка выделена для вырезания визуального шума.</span><span class="sxs-lookup"><span data-stu-id="5d98c-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="5d98c-189">Будьте понятны и соответствуют положению целевых объектов вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="5d98c-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="5d98c-190">Не показывать все целевые объекты вдаваясь одновременно, чтобы избежать повторения пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="5d98c-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="5d98c-191">Повторно используйте тот же шаблон, как можно чаще, чтобы обеспечить знание UX.</span><span class="sxs-lookup"><span data-stu-id="5d98c-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="5d98c-192">*Изображение: список руководств по Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="5d98c-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Список руководств по Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="5d98c-194">См. также</span><span class="sxs-lookup"><span data-stu-id="5d98c-194">See also</span></span>
* [<span data-ttu-id="5d98c-195">Взгляните и зафиксируйте</span><span class="sxs-lookup"><span data-stu-id="5d98c-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5d98c-196">Руки — прямое управление</span><span class="sxs-lookup"><span data-stu-id="5d98c-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5d98c-197">Жесты руки</span><span class="sxs-lookup"><span data-stu-id="5d98c-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="5d98c-198">Практические указания и фиксация</span><span class="sxs-lookup"><span data-stu-id="5d98c-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="5d98c-199">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="5d98c-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="5d98c-200">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="5d98c-200">Voice input</span></span>](voice-input.md)
