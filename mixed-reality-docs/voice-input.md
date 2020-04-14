---
title: Речевой ввод
description: Речевой ввод — это основной ввод для впечатляющих головных телефонов HoloLens и Windows Mixed Reality. Voice можно использовать для команд, диктовки, Кортаны и т. д.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ГГВ, Voice, Кортана, речь, вход
ms.openlocfilehash: 6cf94e6bc828c6f07ee81cb121cb64601df41c4e
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277982"
---
# <a name="voice-input"></a><span data-ttu-id="c3aa8-105">Речевой ввод</span><span class="sxs-lookup"><span data-stu-id="c3aa8-105">Voice input</span></span>

![Речевой ввод](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="c3aa8-107">Голос — один из основных типов ввода в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="c3aa8-108">Он позволяет напрямую создавать голограммы без использования [жестов руки](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="c3aa8-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="c3aa8-109">Голосовой ввод позволяет естественным способом сообщить о своих намерениях.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="c3aa8-110">Речь особенно хорошо работает при обходе сложных интерфейсов, поскольку позволяет пользователям перемещаться по вложенным меню с помощью одной команды.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="c3aa8-111">Речевой ввод обеспечивается тем [же механизмом](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) , который поддерживает речь во всех других _универсальных приложениях Windows_.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="c3aa8-112">В HoloLens распознавание речи всегда будет работать на языке интерфейса Windows, настроенном в параметрах.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="c3aa8-113">Речь и взгляд</span><span class="sxs-lookup"><span data-stu-id="c3aa8-113">Voice and gaze</span></span>

<span data-ttu-id="c3aa8-114">При использовании речевых команд указатель мыши обычно используется в качестве механизма нацеливания, независимо от наличия курсора ("Select") или неявного канала команды к приложению, которое вы ищете.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="c3aa8-115">Для этого может даже не потребоваться отображение курсора-взгляда _(см. статью «как»)_ .</span><span class="sxs-lookup"><span data-stu-id="c3aa8-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="c3aa8-116">Разумеется, некоторым голосовым командам не требуется цель, например "перейти на начало" или "Привет, Кортана!".</span><span class="sxs-lookup"><span data-stu-id="c3aa8-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="c3aa8-117">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="c3aa8-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c3aa8-118"><strong>Функциями</strong></span><span class="sxs-lookup"><span data-stu-id="c3aa8-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c3aa8-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c3aa8-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c3aa8-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c3aa8-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c3aa8-121"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="c3aa8-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c3aa8-122">Речевой ввод</span><span class="sxs-lookup"><span data-stu-id="c3aa8-122">Voice input</span></span></td>
        <td><span data-ttu-id="c3aa8-123">✔️</span><span class="sxs-lookup"><span data-stu-id="c3aa8-123">✔️</span></span></td>
        <td><span data-ttu-id="c3aa8-124">✔️</span><span class="sxs-lookup"><span data-stu-id="c3aa8-124">✔️</span></span></td>
        <td><span data-ttu-id="c3aa8-125">✔️ (с микрофоном)</span><span class="sxs-lookup"><span data-stu-id="c3aa8-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="c3aa8-126">Команда "Select"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-126">The "select" command</span></span>

<span data-ttu-id="c3aa8-127">**HoloLens (1-го поколения)**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="c3aa8-128">Даже без специального добавления поддержки голоса в приложение пользователи могут активировать голограммы, просто выполнив команду "Select".</span><span class="sxs-lookup"><span data-stu-id="c3aa8-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="c3aa8-129">Это ведет себя так же, как [воздушный](gaze-and-commit.md#composite-gestures) вызов в hololens, нажатие кнопки выбрать на кнопке [hololens](hardware-accessories.md#hololens-clicker)или нажатие триггера на [контроллере движения Windows Mixed Reality](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="c3aa8-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="c3aa8-130">Вы услышите звук и увидите подсказку с сообщением "Select" в качестве подтверждения.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="c3aa8-131">"Select" включается алгоритмом обнаружения низкого уровня зарезервированных слов, поэтому он всегда доступен для вас в любое время с минимальным влиянием на время работы от аккумулятора, даже при работе с вашей стороны.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="c3aa8-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="c3aa8-133">Чтобы использовать команду "Select" в HoloLens 2, сначала необходимо открыть курсор взгляда для использования в качестве указателя.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="c3aa8-134">Команду для ее упрощения можно запомнить — просто скажите «SELECT».</span><span class="sxs-lookup"><span data-stu-id="c3aa8-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="c3aa8-135">Чтобы выйти из режима, просто используйте руки, коснувшись касания, приближение к кнопке пальцами или с помощью жеста системы.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="c3aa8-136">*Изображение: Скажите "выбрать", чтобы использовать голосовую команду для выбора*</span><span class="sxs-lookup"><span data-stu-id="c3aa8-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Пользователь может сказать "выбрать", чтобы использовать голосовую команду для выбора.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="c3aa8-138">"Привет, Кортана!"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-138">Hey Cortana</span></span>

<span data-ttu-id="c3aa8-139">Вы также можете сказать "Привет, Кортана!", чтобы открыть Кортану в любое время.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="c3aa8-140">Вам не нужно ждать, пока не появится вопрос о своем вопросе или дать ему инструкцию. Например, попробуйте сказать "Привет, Кортана, что такое Погода?".</span><span class="sxs-lookup"><span data-stu-id="c3aa8-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="c3aa8-141">как одно предложение.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-141">as a single sentence.</span></span> <span data-ttu-id="c3aa8-142">Чтобы получить дополнительные сведения о Кортане и о том, что вы можете сделать, просто спросите!</span><span class="sxs-lookup"><span data-stu-id="c3aa8-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="c3aa8-143">Скажите: "Привет, Кортана, что можно сказать?"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="c3aa8-144">и она будет получать список рабочих и рекомендуемых команд.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="c3aa8-145">Если вы уже находитесь в приложении Кортаны, вы также можете щелкнуть значок **?**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="c3aa8-146">значок на боковой панели, чтобы извлечь это же меню.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="c3aa8-147">**Команды, относящиеся к HoloLens**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="c3aa8-148">"Что можно говорить?"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-148">"What can I say?"</span></span>
* <span data-ttu-id="c3aa8-149">"Перейти на запуск"-вместо [раскрытия](system-gesture.md#bloom) для перехода в [меню "Пуск](navigating-the-windows-mixed-reality-home.md#start-menu) "</span><span class="sxs-lookup"><span data-stu-id="c3aa8-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="c3aa8-150">"Запуск <app>"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-150">"Launch <app>"</span></span>
* <span data-ttu-id="c3aa8-151">"Переместить <app> здесь"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-151">"Move <app> here"</span></span>
* <span data-ttu-id="c3aa8-152">"Сделать фотографию"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-152">"Take a picture"</span></span>
* <span data-ttu-id="c3aa8-153">"Начать запись"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-153">"Start recording"</span></span>
* <span data-ttu-id="c3aa8-154">"Закончить запись"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-154">"Stop recording"</span></span>
* <span data-ttu-id="c3aa8-155">"Увеличить яркость"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-155">"Increase the brightness"</span></span>
* <span data-ttu-id="c3aa8-156">"Уменьшить яркость"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-156">"Decrease the brightness"</span></span>
* <span data-ttu-id="c3aa8-157">"Увеличение объема тома"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-157">"Increase the volume"</span></span>
* <span data-ttu-id="c3aa8-158">"Уменьшить объем тома"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-158">"Decrease the volume"</span></span>
* <span data-ttu-id="c3aa8-159">"Отключить" или "включить звук"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-159">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="c3aa8-160">"Завершение работы устройства"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-160">"Shut down the device"</span></span>
* <span data-ttu-id="c3aa8-161">"Перезапустить устройство"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-161">"Restart the device"</span></span>
* <span data-ttu-id="c3aa8-162">"Переход в спящий режим"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-162">"Go to sleep"</span></span>
* <span data-ttu-id="c3aa8-163">"Что такое время?"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-163">"What time is it?"</span></span>
* <span data-ttu-id="c3aa8-164">«Сколько аккумулятора осталось?»</span><span class="sxs-lookup"><span data-stu-id="c3aa8-164">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="c3aa8-165">«Видите, скажите»</span><span class="sxs-lookup"><span data-stu-id="c3aa8-165">"See It, Say It"</span></span><br>
        <span data-ttu-id="c3aa8-166">HoloLens имеет модель "видите ИТ-IT" для голосового ввода, где метки на кнопках указывают пользователям, какие голосовые команды также могут говорить.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-166">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="c3aa8-167">Например, при просмотре окна приложения в HoloLens (1-й номер) пользователь может сказать команду "настроить", которая отображается на панели приложений, чтобы настроить расположение приложения в мире.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-167">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="c3aa8-168">*Изображение: пользователь может сказать команду "настроить", которая отображается на панели приложений, чтобы настроить расположение приложения.*</span><span class="sxs-lookup"><span data-stu-id="c3aa8-168">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="c3aa8-169">![пространство](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="c3aa8-169">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="c3aa8-170">![при просмотре окна приложения или голограммы пользователь может сказать команду "настроить", которая отображается на панели приложений, чтобы скорректировать расположение приложения в мире](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="c3aa8-170">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="c3aa8-171">Когда приложения следуют этому правилу, пользователи могут легко понять, что следует сказать для управления системой.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-171">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="c3aa8-172">Чтобы прикрепить это, в то время как облаками на кнопке в HoloLens (1-й общий), вы увидите подсказку "Voice вдаваясь", которая появляется после второй, если кнопка включена с помощью голоса и отображает команду "нажать".</span><span class="sxs-lookup"><span data-stu-id="c3aa8-172">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="c3aa8-173">Чтобы показать голосовые подсказки в HoloLens 2, отобразите голосовый курсор, указав "Select" или "что можно сказать" (см. изображение).</span><span class="sxs-lookup"><span data-stu-id="c3aa8-173">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="c3aa8-174">*Изображение: команды отображаются под кнопками.*</span><span class="sxs-lookup"><span data-stu-id="c3aa8-174">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Видите, что команды отображаются под кнопками](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="c3aa8-176">Команды Voice для быстрой обработки с голограммами</span><span class="sxs-lookup"><span data-stu-id="c3aa8-176">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="c3aa8-177">Существует ряд голосовых команд, которые можно сказать, облаками на голограммах, чтобы быстро выполнять задачи манипуляции.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-177">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="c3aa8-178">Эти команды работают с окнами приложений, а также с трехмерными объектами, помещенными в мир.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-178">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="c3aa8-179">**Команды обработки голограмм**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-179">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="c3aa8-180">Лицом мне</span><span class="sxs-lookup"><span data-stu-id="c3aa8-180">Face me</span></span>
* <span data-ttu-id="c3aa8-181">Больше | Улучшение</span><span class="sxs-lookup"><span data-stu-id="c3aa8-181">Bigger | Enhance</span></span>
* <span data-ttu-id="c3aa8-182">Размеров</span><span class="sxs-lookup"><span data-stu-id="c3aa8-182">Smaller</span></span>

<span data-ttu-id="c3aa8-183">В HoloLens 2 можно также создавать более естественные взаимодействия в сочетании с глазом глаза, который неявно предоставляет контекстные сведения о том, на что вы ссылаетесь.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-183">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="c3aa8-184">Например, можно просто взгляните на голограмму и сказать, где вы хотите разместить _это_сообщение, а затем сказать, где его нужно поместить. _here_</span><span class="sxs-lookup"><span data-stu-id="c3aa8-184">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="c3aa8-185">Вы также можете взглянуть на сложную часть на сложной машине и сказать: "получить дополнительные сведения об _этом_".</span><span class="sxs-lookup"><span data-stu-id="c3aa8-185">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="c3aa8-186">Обнаружение команд Voice</span><span class="sxs-lookup"><span data-stu-id="c3aa8-186">Discovering voice commands</span></span>

<span data-ttu-id="c3aa8-187">Некоторые команды, например команды для быстрой обработки выше, могут быть скрыты.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-187">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="c3aa8-188">Чтобы узнать, какие команды можно использовать, Взгляните на объект и скажите «что можно сказать?».</span><span class="sxs-lookup"><span data-stu-id="c3aa8-188">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="c3aa8-189">Откроется список возможных команд.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-189">A list of possible commands pops up.</span></span> <span data-ttu-id="c3aa8-190">Можно также использовать курсор Head, чтобы найти и раскрывать подсказки голоса для каждой кнопки перед вами.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-190">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="c3aa8-191">Если вам нужен полный список, просто скажите «показывать все команды» в любое время.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-191">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="c3aa8-192">Диктовка</span><span class="sxs-lookup"><span data-stu-id="c3aa8-192">Dictation</span></span>

<span data-ttu-id="c3aa8-193">Вместо ввода с помощью [воздушных](gaze-and-commit.md#composite-gestures)наработок речь может оказаться более эффективной для ввода текста в приложение.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-193">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="c3aa8-194">Это может значительно ускорить ввод данных с меньшими усилиями для пользователя.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-194">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="c3aa8-195">![Диктовка речи начинается с нажатия кнопки микрофона](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="c3aa8-195">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="c3aa8-196">*Диктовка речи начинается с нажатия кнопки микрофона на клавиатуре*</span><span class="sxs-lookup"><span data-stu-id="c3aa8-196">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="c3aa8-197">В любой момент, когда набиралась неактивная клавиатура, можно переключиться в режим диктовки вместо ввода.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-197">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="c3aa8-198">Чтобы начать работу, выберите микрофон на стороне текстового поля ввода.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-198">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="c3aa8-199">Добавление в приложение голосовых команд</span><span class="sxs-lookup"><span data-stu-id="c3aa8-199">Adding voice commands to your app</span></span>

<span data-ttu-id="c3aa8-200">Рассмотрите возможность добавления голосовых команд при создании любого взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-200">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="c3aa8-201">Голосовая связь — это эффективный и удобный способ управления системой и приложениями.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-201">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="c3aa8-202">Так как пользователи говорят на различных диалектах и с разными акцентами, правильный выбор ключевых слов речи обеспечит однозначную интерпретацию команд пользователей.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-202">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="c3aa8-203">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="c3aa8-203">Best practices</span></span>

<span data-ttu-id="c3aa8-204">Ниже приведены некоторые рекомендации, которые помогут облегчить распознавание речи.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-204">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="c3aa8-205">**Используйте краткие команды**. По возможности выбирайте ключевые слова из двух или более слогов.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-205">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="c3aa8-206">В односложных словах лица с разными акцентами обычно используют разные гласные.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-206">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="c3aa8-207">Пример: "воспроизведение видео" лучше, чем "Воспроизвести текущее выбранное видео"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-207">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="c3aa8-208">**Используйте простой словарь** — пример: "показывать Примечание" лучше, чем "Показывать панель"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-208">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="c3aa8-209">**Убедитесь, что команды не являются разрушающими.** Убедитесь, что любое действие, которое может быть выполнено голосовой командой, не является разрушающим и его можно легко отменить, если другое лицо, которое говорит рядом с пользователем, случайно запустит команду.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-209">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="c3aa8-210">**Избегайте аналогично звучащих команд.** Исключите регистрацию нескольких голосовых команд, которые звучат очень похоже.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-210">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="c3aa8-211">Например, "показывать больше" и "показывать магазин" может быть очень похожим звуковым сигналом.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-211">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="c3aa8-212">**Отмените регистрацию приложения, когда оно не используется.** Если приложение не находится в состоянии, в котором действует определенная голосовая команда, рассмотрите возможность отмены регистрации, чтобы другие команды не были спутаны с ней.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-212">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="c3aa8-213">**Протестируйте с разными акцентами.** Протестируйте приложение с пользователями с разными акцентами.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-213">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="c3aa8-214">**Обеспечьте согласованность голосовых команд.** Если команда "Назад" переводит на предыдущую страницу, поддерживайте это поведение в своих приложениях.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-214">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="c3aa8-215">**Избегайте использования системных команд.** Приведенные ниже голосовые команды зарезервированы для системы.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-215">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="c3aa8-216">Они не должны использоваться приложениями.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-216">These should not be used by applications.</span></span>
   * <span data-ttu-id="c3aa8-217">"Привет, Кортана!".</span><span class="sxs-lookup"><span data-stu-id="c3aa8-217">"Hey Cortana"</span></span>
   * <span data-ttu-id="c3aa8-218">"Выбрать".</span><span class="sxs-lookup"><span data-stu-id="c3aa8-218">"Select"</span></span>
   * <span data-ttu-id="c3aa8-219">"Перейти к запуску"</span><span class="sxs-lookup"><span data-stu-id="c3aa8-219">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="c3aa8-220">Преимущества речевого ввода</span><span class="sxs-lookup"><span data-stu-id="c3aa8-220">Advantages of voice input</span></span>

<span data-ttu-id="c3aa8-221">Голосовой ввод — это естественный способ сообщить о наших намерениях.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-221">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="c3aa8-222">Голосовая передача особенно хороша при обучении интерфейсов, так как она может помочь пользователям в устранении нескольких этапов работы **с интерфейсом** (пользователь может сказать "вернуться назад" при просмотре веб-страницы, вместо того чтобы приступать к нажатию кнопки "назад" в приложении).</span><span class="sxs-lookup"><span data-stu-id="c3aa8-222">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="c3aa8-223">Это небольшое время сохранения имеет мощный **эмоциональномный результат** на восприятии пользователя и дает им небольшой объем суперсовременные.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-223">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="c3aa8-224">Использование голосовой связи — это также удобный метод ввода, когда наши руки заняты или когда нам предстоит выполнить **несколько заданий**.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-224">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="c3aa8-225">На устройствах, где ввод с клавиатуры является сложной возможностью, **Диктовка голоса** может быть эффективным альтернативным способом ввода текста.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-225">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="c3aa8-226">Наконец, в некоторых случаях, когда **диапазон точности** для взгляда и жеста ограничен, Voice может помочь в неоднозначности намерений пользователя.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-226">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="c3aa8-227">**Преимущества использования голоса для пользователя**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-227">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="c3aa8-228">Экономия времени — конечная цель достигается намного эффективнее.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-228">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="c3aa8-229">Сокращение усилий — задания выполняются намного быстрее и не требуют значительных усилий.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-229">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="c3aa8-230">Облегчение восприятия информации — это интуитивно понятно, легко выучить и запомнить.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-230">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="c3aa8-231">Это социально адаптированно — это должно вписываться в социальные нормы в плане поведения.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-231">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="c3aa8-232">Это установившаяся практика — использование голосовой связи легко может стать привычным поведением.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-232">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="c3aa8-233">Проблемы с голосовым вводом</span><span class="sxs-lookup"><span data-stu-id="c3aa8-233">Challenges for voice input</span></span>

<span data-ttu-id="c3aa8-234">Хотя речевой ввод отлично подходит для множества различных приложений, он также сталкивается с несколькими проблемами.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-234">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="c3aa8-235">Понимание преимуществ и трудностей, связанных с голосовыми вводами, позволяет разработчикам приложений более разумно выбирать способ и время использования речевого ввода и создавать превосходные возможности для пользователей.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-235">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="c3aa8-236">**Речевой ввод для непрерывного элемента управления вводом** Один из них является детализированным элементом управления.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-236">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="c3aa8-237">Например, пользователю может потребоваться изменить свой том в своем музыкальном приложении.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-237">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="c3aa8-238">Она может просто сказать «громче», но не ясно, сколько громкости система должна сделать тому.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-238">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="c3aa8-239">Пользователь может сказать: «сделайте его немного громче», но «немного» — трудность.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-239">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="c3aa8-240">Перемещение и масштабирование голограмм с помощью голоса также усложняется.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-240">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="c3aa8-241">**Надежность распознавания речевого ввода** Хотя системы ввода голоса становятся лучше и эффективнее, иногда они могут неправильно слышать и интерпретировать голосовую команду.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-241">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="c3aa8-242">Ключ заключается в решении этой проблемы в приложении, предоставляя пользователю отзыв о прослушиваемой системе и о том, что система понимается для того, чтобы понять потенциальные проблемы в правильном понимании пользователя.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-242">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="c3aa8-243">**Ввод голоса в общих пространствах** Возможно, голоса не основе социотехники в сферах, к которым вы предоставляете доступ другим пользователям.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-243">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="c3aa8-244">Вот несколько примеров.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-244">Here are a few examples:</span></span>
* <span data-ttu-id="c3aa8-245">Пользователь может не захотеть беспокоить других пользователей (например, в тихой библиотеке или в общем офисе).</span><span class="sxs-lookup"><span data-stu-id="c3aa8-245">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="c3aa8-246">Пользователи могут видеть, что речь идет о себе в общедоступной,</span><span class="sxs-lookup"><span data-stu-id="c3aa8-246">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="c3aa8-247">Пользователь может неудобно диктовать личное или конфиденциальное сообщение (включая пароли), пока другие прослушивают</span><span class="sxs-lookup"><span data-stu-id="c3aa8-247">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="c3aa8-248">**Голосовое ввод уникальных или неизвестных слов** Проблемы, возникающие при вводе голоса, также поступают, когда пользователи определяют слова, которые могут быть неизвестны для системы, например псевдонимы, определенные сленговых выражений слова или сокращения.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-248">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="c3aa8-249">**Обучение голосовым командам** Хотя конечная цель заключается в естественном противоречии системе, часто приложения по-прежнему используют определенные предварительно определенные команды.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-249">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="c3aa8-250">Задача, связанная с большим набором голосовых команд, заключается в том, как обучить их без перегрузки пользователя и как помочь пользователю их хранить.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-250">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="c3aa8-251">Состояния обратной связи голосовых команд</span><span class="sxs-lookup"><span data-stu-id="c3aa8-251">Voice feedback states</span></span>

<span data-ttu-id="c3aa8-252">При правильном применении голосовых команд пользователь понимает, **что он может сказать, и получает обратную связь о том,** что система **услышала его правильно**.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-252">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="c3aa8-253">Эти два сигнала придают пользователю уверенность в правильности выбора голосовых команд в качестве основного метода ввода.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-253">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="c3aa8-254">Ниже приведена схема, показывающая, что происходит с курсором после распознавания голосовой команды и как он сообщает это пользователю.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-254">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="c3aa8-255">![1.](images/voicefeedbackstates-regular.jpg) состояния обычного курсора</span><span class="sxs-lookup"><span data-stu-id="c3aa8-255">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="c3aa8-256">**1. состояние обычного курсора**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-256">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c3aa8-257">![2. Сообщает о голосовом отзыве, а затем исчезает](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="c3aa8-257">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="c3aa8-258">**2. сообщает о голосовом отзыве, а затем исчезает**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-258">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c3aa8-259">![\* 3.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-259">![\*3.</span></span> <span data-ttu-id="c3aa8-260">](images/voicefeedbackstates-regular.jpg) состояния обычного курсора</span><span class="sxs-lookup"><span data-stu-id="c3aa8-260">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="c3aa8-261">**3. возвращается к обычному состоянию курсора**</span><span class="sxs-lookup"><span data-stu-id="c3aa8-261">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="c3aa8-262">Главное, что пользователю следует знать о "речи" в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="c3aa8-262">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="c3aa8-263">Скажите **Выбрать** при нацеливании на кнопку (можно использовать это в любом месте для нажатия кнопки).</span><span class="sxs-lookup"><span data-stu-id="c3aa8-263">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="c3aa8-264">Вы можете произнести **имя метки кнопки панели приложения** в некоторых приложениях, чтобы выполнить действие.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-264">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="c3aa8-265">Например, глядя на приложение, пользователь может произнести команду "Удалить", чтобы удалить приложение (это экономит время, так как не нужно делать это вручную).</span><span class="sxs-lookup"><span data-stu-id="c3aa8-265">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="c3aa8-266">Чтобы Кортана начала слушать, скажите **Привет, Кортана!** .</span><span class="sxs-lookup"><span data-stu-id="c3aa8-266">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="c3aa8-267">Вы можете задавать ей вопросы ("Привет, Кортана, какая высота Эйфелевой башни"), попросить ее открыть приложение ("Привет, Кортана, открой Netflix") или попросить ее открыть меню "Пуск" ("Привет, Кортана, открой домашнюю страницу") и многое другое.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-267">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="c3aa8-268">Распространенные вопросы пользователей о голосовых командах</span><span class="sxs-lookup"><span data-stu-id="c3aa8-268">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="c3aa8-269">Что можно сказать?</span><span class="sxs-lookup"><span data-stu-id="c3aa8-269">What can I say?</span></span>
* <span data-ttu-id="c3aa8-270">Как узнать, что система услышала меня правильно?</span><span class="sxs-lookup"><span data-stu-id="c3aa8-270">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="c3aa8-271">Система продолжает неправильно интерпретировать мои голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-271">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="c3aa8-272">Она не реагирует, когда я даю ей голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-272">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="c3aa8-273">Она неправильно реагирует, когда я даю ей голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-273">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="c3aa8-274">Как нацеливать голос на конкретное приложение или команду приложения?</span><span class="sxs-lookup"><span data-stu-id="c3aa8-274">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="c3aa8-275">Можно ли использовать голос для различных команд в голографическом кадре в HoloLens?</span><span class="sxs-lookup"><span data-stu-id="c3aa8-275">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="c3aa8-276">Связь</span><span class="sxs-lookup"><span data-stu-id="c3aa8-276">Communication</span></span>

<span data-ttu-id="c3aa8-277">Для приложений, которые хотят воспользоваться преимуществами настраиваемых параметров обработки ввода звука, предоставляемых HoloLens, важно понимать различные [категории звуковых потоков](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) , которые может использовать приложение.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-277">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="c3aa8-278">Windows 10 поддерживает несколько различных категорий потоков, и HoloLens использует три из них, чтобы обеспечить настраиваемую обработку, чтобы оптимизировать качество звука микрофона, предназначенное для речи, общения и других, которые могут использоваться для воспроизведения звука в окружающей среде (например, "видеокамера").</span><span class="sxs-lookup"><span data-stu-id="c3aa8-278">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="c3aa8-279">Категория AudioCategory_Communicationsного потока настраивается для сценариев качества вызова и речевого сопровождения и обеспечивает клиент с помощью 16kHz 24bit Mono Audio Voice.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-279">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="c3aa8-280">Категория AudioCategory_Speech Stream настроена для обработчика речи HoloLens (Windows) и обеспечивает его с помощью потока 16kHz 24bit Mono голоса пользователя.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-280">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="c3aa8-281">При необходимости эту категорию могут использовать сторонние модули распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-281">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="c3aa8-282">Категория AudioCategory_Otherного потока настраивается для записи звука в окружающей среде и предоставляет клиенту 48kHz 24-битного стерео аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-282">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="c3aa8-283">Вся эта обработка аудио аппаратного ускорения означает, что функции заменяют гораздо меньше энергии, чем при выполнении такой же обработки на ЦП HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-283">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="c3aa8-284">Избегайте выполнения других системных входных данных на ЦП, чтобы максимально увеличить время работы от аккумулятора и воспользоваться встроенной, развернутой погрузкой входной обработки.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-284">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="c3aa8-285">Языки</span><span class="sxs-lookup"><span data-stu-id="c3aa8-285">Languages</span></span>

<span data-ttu-id="c3aa8-286">HoloLens 2 также поддерживает дополнительные языки.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-286">HoloLens 2 also supports additional languages.</span></span> <span data-ttu-id="c3aa8-287">Помните, что речевые команды всегда будут выполняться в языке интерфейса системы, даже если установлено несколько клавиатур или если приложения пытаются создать распознаватель речи на другом языке.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-287">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c3aa8-288">Диагностика</span><span class="sxs-lookup"><span data-stu-id="c3aa8-288">Troubleshooting</span></span>

<span data-ttu-id="c3aa8-289">Если у вас возникли проблемы с помощью команды "выбрать" и "Привет, Кортана", попробуйте переместиться в скрытое место, отключив его от источника шума или нажимая звук.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-289">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="c3aa8-290">В настоящее время все распознавание речи в HoloLens настраивается и оптимизируется специально для собственных докладчиков США английского.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-290">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="c3aa8-291">В выпуске Windows Mixed Reality для выпуска 2017 логика управления конечными точками звука будет работать нормально (бессрочно) после выхода и возврата на Рабочий стол компьютера после первоначального подключения ХМД.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-291">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="c3aa8-292">Перед первым входом в систему после выхода из ВМР OOBE пользователь может столкнуться с различными проблемами аудио, начиная с отсутствия звука, в зависимости от того, как система была настроена, прежде чем подключать ХМД в первый раз.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-292">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c3aa8-293">Ввод голоса в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="c3aa8-293">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="c3aa8-294">С помощью **[мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** можно легко назначить голосовые команды для любых объектов.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-294">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="c3aa8-295">Используйте **профиль ввода речи** мртк для определения ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-295">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="c3aa8-296">Назначая сценарий **спичинпусандлер** , можно сделать так, чтобы любой объект отвечал на ключевые слова, определенные в профиле речевого ввода.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-296">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="c3aa8-297">Спичинпусандлер также предоставляет метку подтверждения речи для улучшения достоверности пользователя.</span><span class="sxs-lookup"><span data-stu-id="c3aa8-297">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="c3aa8-298">Команда МРТК-Voice</span><span class="sxs-lookup"><span data-stu-id="c3aa8-298">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="c3aa8-299">См. также:</span><span class="sxs-lookup"><span data-stu-id="c3aa8-299">See also</span></span>
* [<span data-ttu-id="c3aa8-300">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="c3aa8-300">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="c3aa8-301">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="c3aa8-301">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="c3aa8-302">Ввод MR 212: Voice</span><span class="sxs-lookup"><span data-stu-id="c3aa8-302">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="c3aa8-303">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="c3aa8-303">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="c3aa8-304">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="c3aa8-304">Voice input in Unity</span></span>](voice-input-in-unity.md)
