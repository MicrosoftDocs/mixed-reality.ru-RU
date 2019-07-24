---
title: Голосовой ввод
description: Речевой ввод — это основной ввод для впечатляющих головных телефонов HoloLens и Windows Mixed Reality. Voice можно использовать для команд, диктовки, Кортаны и т. д.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ГГВ, Voice, Кортана, речь, вход
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829951"
---
# <a name="voice-input"></a><span data-ttu-id="30b41-105">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="30b41-105">Voice input</span></span>

<span data-ttu-id="30b41-106">Voice — одна из трех основных форм входных данных в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="30b41-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="30b41-107">Он позволяет напрямую создавать голограммы без использования [жестов](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="30b41-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="30b41-108">Просто [Взгляните](gaze.md) на голограмму и говорите о команде.</span><span class="sxs-lookup"><span data-stu-id="30b41-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="30b41-109">Речевой ввод может быть естественным способом сообщить о своем намерении.</span><span class="sxs-lookup"><span data-stu-id="30b41-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="30b41-110">Речь особенно хорошо работает при обходе сложных интерфейсов, поскольку позволяет пользователям перемещаться по вложенным меню с помощью одной команды.</span><span class="sxs-lookup"><span data-stu-id="30b41-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="30b41-111">Речевой ввод обеспечивается тем [же механизмом](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) , который поддерживает речь во всех других универсальных приложениях Windows.</span><span class="sxs-lookup"><span data-stu-id="30b41-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="30b41-112">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="30b41-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30b41-113"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="30b41-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="30b41-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="30b41-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="30b41-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="30b41-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="30b41-116"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="30b41-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30b41-117">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="30b41-117">Voice input</span></span></td>
        <td><span data-ttu-id="30b41-118">✔️</span><span class="sxs-lookup"><span data-stu-id="30b41-118">✔️</span></span></td>
        <td><span data-ttu-id="30b41-119">✔️</span><span class="sxs-lookup"><span data-stu-id="30b41-119">✔️</span></span></td>
        <td><span data-ttu-id="30b41-120">✔️ (с микрофоном)</span><span class="sxs-lookup"><span data-stu-id="30b41-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="30b41-121">Команда "Select"</span><span class="sxs-lookup"><span data-stu-id="30b41-121">The "select" command</span></span>

<span data-ttu-id="30b41-122">Даже без специального добавления поддержки голоса в приложение пользователи могут активировать голограммы, просто указав "Select".</span><span class="sxs-lookup"><span data-stu-id="30b41-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="30b41-123">Это ведет себя так же, как [воздушный](gestures.md#air-tap) вызов в hololens, нажатие кнопки выбрать на кнопке [hololens](hardware-accessories.md#hololens-clicker)или нажатие триггера на контроллере [движения Windows Mixed Reality](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="30b41-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="30b41-124">Вы услышите звук и увидите подсказку с сообщением "Select" в качестве подтверждения.</span><span class="sxs-lookup"><span data-stu-id="30b41-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="30b41-125">"Select" включается алгоритмом обнаружения низкого уровня зарезервированных слов, поэтому он всегда доступен для вас в любое время с минимальным влиянием на время работы от аккумулятора, даже при работе с вашей стороны.</span><span class="sxs-lookup"><span data-stu-id="30b41-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="30b41-126">В [ближайшее время ожидается](index.md#news-and-notes)более подробное руководство по HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="30b41-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="30b41-127">![Скажите "выбрать", чтобы использовать голосовую команду для выбора](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="30b41-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="30b41-128">*Скажите "выбрать", чтобы использовать голосовую команду для выбора*</span><span class="sxs-lookup"><span data-stu-id="30b41-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="30b41-129">"Привет, Кортана!"</span><span class="sxs-lookup"><span data-stu-id="30b41-129">Hey Cortana</span></span>

<span data-ttu-id="30b41-130">Вы также можете сказать "Привет, Кортана!", чтобы открыть Кортану в любое время.</span><span class="sxs-lookup"><span data-stu-id="30b41-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="30b41-131">Вам не нужно ждать, пока не появится вопрос о своем вопросе или дать ему инструкцию. Например, попробуйте сказать: «Привет, Кортана, что такое Погода?».</span><span class="sxs-lookup"><span data-stu-id="30b41-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="30b41-132">как одно предложение.</span><span class="sxs-lookup"><span data-stu-id="30b41-132">as a single sentence.</span></span> <span data-ttu-id="30b41-133">Чтобы получить дополнительные сведения о Кортане и о том, что вы можете сделать, просто спросите!</span><span class="sxs-lookup"><span data-stu-id="30b41-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="30b41-134">Скажите: "Привет, Кортана, что можно сказать?"</span><span class="sxs-lookup"><span data-stu-id="30b41-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="30b41-135">и она будет получать список рабочих и рекомендуемых команд.</span><span class="sxs-lookup"><span data-stu-id="30b41-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="30b41-136">Если вы уже находитесь в приложении Кортаны, вы также можете щелкнуть значок **?**</span><span class="sxs-lookup"><span data-stu-id="30b41-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="30b41-137">значок на боковой панели, чтобы извлечь это же меню.</span><span class="sxs-lookup"><span data-stu-id="30b41-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="30b41-138">**Команды, относящиеся к HoloLens**</span><span class="sxs-lookup"><span data-stu-id="30b41-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="30b41-139">"Что можно говорить?"</span><span class="sxs-lookup"><span data-stu-id="30b41-139">"What can I say?"</span></span>
* <span data-ttu-id="30b41-140">"Перейти домой" или "перейти к началу" — вместо [раскрытия](gestures.md#bloom) для перехода в [меню "Пуск](navigating-the-windows-mixed-reality-home.md#start-menu) "</span><span class="sxs-lookup"><span data-stu-id="30b41-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="30b41-141">"Запуск <app>"</span><span class="sxs-lookup"><span data-stu-id="30b41-141">"Launch <app>"</span></span>
* <span data-ttu-id="30b41-142">"Переместить <app> сюда"</span><span class="sxs-lookup"><span data-stu-id="30b41-142">"Move <app> here"</span></span>
* <span data-ttu-id="30b41-143">"Сделать фотографию"</span><span class="sxs-lookup"><span data-stu-id="30b41-143">"Take a picture"</span></span>
* <span data-ttu-id="30b41-144">"Начать запись"</span><span class="sxs-lookup"><span data-stu-id="30b41-144">"Start recording"</span></span>
* <span data-ttu-id="30b41-145">"Закончить запись"</span><span class="sxs-lookup"><span data-stu-id="30b41-145">"Stop recording"</span></span>
* <span data-ttu-id="30b41-146">"Увеличить яркость"</span><span class="sxs-lookup"><span data-stu-id="30b41-146">"Increase the brightness"</span></span>
* <span data-ttu-id="30b41-147">"Уменьшить яркость"</span><span class="sxs-lookup"><span data-stu-id="30b41-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="30b41-148">"Увеличение объема тома"</span><span class="sxs-lookup"><span data-stu-id="30b41-148">"Increase the volume"</span></span>
* <span data-ttu-id="30b41-149">"Уменьшить объем тома"</span><span class="sxs-lookup"><span data-stu-id="30b41-149">"Decrease the volume"</span></span>
* <span data-ttu-id="30b41-150">"Отключить" или "включить звук"</span><span class="sxs-lookup"><span data-stu-id="30b41-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="30b41-151">"Завершение работы устройства"</span><span class="sxs-lookup"><span data-stu-id="30b41-151">"Shut down the device"</span></span>
* <span data-ttu-id="30b41-152">"Перезапустить устройство"</span><span class="sxs-lookup"><span data-stu-id="30b41-152">"Restart the device"</span></span>
* <span data-ttu-id="30b41-153">"Переход в спящий режим"</span><span class="sxs-lookup"><span data-stu-id="30b41-153">"Go to sleep"</span></span>
* <span data-ttu-id="30b41-154">"Что такое время?"</span><span class="sxs-lookup"><span data-stu-id="30b41-154">"What time is it?"</span></span>
* <span data-ttu-id="30b41-155">«Сколько аккумулятора осталось?»</span><span class="sxs-lookup"><span data-stu-id="30b41-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="30b41-156">"Call <contact>" (требуется Skype для HoloLens)</span><span class="sxs-lookup"><span data-stu-id="30b41-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="30b41-157">«Видите, скажите»</span><span class="sxs-lookup"><span data-stu-id="30b41-157">"See It, Say It"</span></span>

<span data-ttu-id="30b41-158">HoloLens имеет модель "видите ИТ-IT" для голосового ввода, где метки на кнопках указывают пользователям, какие голосовые команды также могут говорить.</span><span class="sxs-lookup"><span data-stu-id="30b41-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="30b41-159">Например, при просмотре 2D-приложения пользователь может сказать команду "Изменить", которая отображается на панели приложений, чтобы настроить расположение приложения в мире.</span><span class="sxs-lookup"><span data-stu-id="30b41-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![При просмотре 2D-приложения или голограммы пользователь может сказать команду "настроить", которая отображается на панели приложений, чтобы настроить расположение приложения в мире](images/microphone-600px.png)

<span data-ttu-id="30b41-161">Когда приложения следуют этому правилу, пользователи могут легко понять, что следует сказать для управления системой.</span><span class="sxs-lookup"><span data-stu-id="30b41-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="30b41-162">Чтобы прикрепить это, в то время как облаками на кнопке, вы увидите всплывающую подсказку "Voice вдаваясь", которая появляется после второй, если кнопка включена с помощью голоса и отображает команду "нажать".</span><span class="sxs-lookup"><span data-stu-id="30b41-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="30b41-163">![Видите, что команды отображаются под кнопками](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="30b41-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="30b41-164">*В разделе "кнопки" отображаются следующие команды.*</span><span class="sxs-lookup"><span data-stu-id="30b41-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="30b41-165">Команды Voice для быстрой обработки с голограммами</span><span class="sxs-lookup"><span data-stu-id="30b41-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="30b41-166">Кроме того, существует ряд голосовых команд, которые можно сказать, облаками на голограммах, чтобы быстро выполнять задачи манипуляции.</span><span class="sxs-lookup"><span data-stu-id="30b41-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="30b41-167">Эти команды работают с 2D-приложениями, а также с трехмерными объектами, размещенными в мире.</span><span class="sxs-lookup"><span data-stu-id="30b41-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="30b41-168">**Команды обработки голограмм**</span><span class="sxs-lookup"><span data-stu-id="30b41-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="30b41-169">Лицом мне</span><span class="sxs-lookup"><span data-stu-id="30b41-169">Face me</span></span>
* <span data-ttu-id="30b41-170">Больше | Улучшение</span><span class="sxs-lookup"><span data-stu-id="30b41-170">Bigger | Enhance</span></span>
* <span data-ttu-id="30b41-171">Размеров</span><span class="sxs-lookup"><span data-stu-id="30b41-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="30b41-172">Диктовка</span><span class="sxs-lookup"><span data-stu-id="30b41-172">Dictation</span></span>

<span data-ttu-id="30b41-173">Вместо ввода с помощью [воздушных](gestures.md#air-tap)наработок речь может оказаться более эффективной для ввода текста в приложение.</span><span class="sxs-lookup"><span data-stu-id="30b41-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="30b41-174">Это может значительно ускорить ввод данных с меньшими усилиями для пользователя.</span><span class="sxs-lookup"><span data-stu-id="30b41-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="30b41-175">![Диктовка речи начинается с нажатия кнопки микрофона](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="30b41-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="30b41-176">*Диктовка речи начинается с нажатия кнопки микрофона на клавиатуре*</span><span class="sxs-lookup"><span data-stu-id="30b41-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="30b41-177">В любой момент, когда набиралась неактивная клавиатура, можно переключиться в режим диктовки вместо ввода.</span><span class="sxs-lookup"><span data-stu-id="30b41-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="30b41-178">Чтобы начать работу, выберите микрофон на стороне текстового поля ввода.</span><span class="sxs-lookup"><span data-stu-id="30b41-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="30b41-179">Связь</span><span class="sxs-lookup"><span data-stu-id="30b41-179">Communication</span></span>

<span data-ttu-id="30b41-180">Для приложений, которые хотят воспользоваться преимуществами настраиваемых параметров обработки ввода звука, предоставляемых HoloLens, важно понимать различные [категории звуковых потоков](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) , которые может использовать приложение.</span><span class="sxs-lookup"><span data-stu-id="30b41-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="30b41-181">Windows 10 поддерживает несколько различных категорий потоков, и HoloLens использует три из них, чтобы обеспечить настраиваемую обработку, чтобы оптимизировать качество звука микрофона, предназначенное для речи, взаимодействия и других, которые могут использоваться для звука окружающей среды. видеозаписи (например, "видеокамера").</span><span class="sxs-lookup"><span data-stu-id="30b41-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="30b41-182">Категория потока AudioCategory_Communications настраивается для сценариев качества вызова и речевого сопровождения и обеспечивает клиент с помощью 16kHz 24bit Mono Audio Voice.</span><span class="sxs-lookup"><span data-stu-id="30b41-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="30b41-183">Категория потока AudioCategory_Speech настраивается для обработчика речи HoloLens (Windows) и обеспечивает его с помощью 16kHz 24bit моно потока голоса пользователя.</span><span class="sxs-lookup"><span data-stu-id="30b41-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="30b41-184">При необходимости эту категорию могут использовать сторонние модули распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="30b41-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="30b41-185">Категория потока AudioCategory_Other настраивается для записи звука в окружающей среде и обеспечивает клиент с 48kHz 24-битным стерео аудио-потоком.</span><span class="sxs-lookup"><span data-stu-id="30b41-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="30b41-186">Вся эта обработка аудио аппаратного ускорения означает, что функции заменяют гораздо меньше энергии, чем при выполнении такой же обработки на ЦП HoloLens.</span><span class="sxs-lookup"><span data-stu-id="30b41-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="30b41-187">Избегайте выполнения других системных входных данных на ЦП, чтобы максимально увеличить время работы от аккумулятора и воспользоваться встроенной, развернутой погрузкой входной обработки.</span><span class="sxs-lookup"><span data-stu-id="30b41-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="30b41-188">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="30b41-188">Troubleshooting</span></span>

<span data-ttu-id="30b41-189">Если у вас возникли проблемы с помощью команды "выбрать" и "Привет, Кортана", попробуйте переместиться в скрытое место, отключив его от источника шума или нажимая звук.</span><span class="sxs-lookup"><span data-stu-id="30b41-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="30b41-190">В настоящее время все распознавание речи в HoloLens настраивается и оптимизируется специально для собственных докладчиков США английского.</span><span class="sxs-lookup"><span data-stu-id="30b41-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="30b41-191">В выпуске Windows Mixed Reality для выпуска 2017 логика управления конечными точками звука будет работать нормально (бессрочно) после выхода и возврата на Рабочий стол компьютера после первоначального подключения ХМД.</span><span class="sxs-lookup"><span data-stu-id="30b41-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="30b41-192">Перед первым входом в систему после выхода из ВМР OOBE пользователь может столкнуться с различными проблемами аудио, начиная с отсутствия звука, в зависимости от того, как система была настроена, прежде чем подключать ХМД в первый раз.</span><span class="sxs-lookup"><span data-stu-id="30b41-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="30b41-193">См. также</span><span class="sxs-lookup"><span data-stu-id="30b41-193">See also</span></span>
* [<span data-ttu-id="30b41-194">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="30b41-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="30b41-195">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="30b41-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="30b41-196">212. Ввод в смешанной реальности: голос</span><span class="sxs-lookup"><span data-stu-id="30b41-196">MR Input 212: Voice</span></span>](holograms-212.md)
