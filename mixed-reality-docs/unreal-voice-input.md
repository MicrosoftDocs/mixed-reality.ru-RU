---
title: Речевой ввод
description: Руководство по настройке и использованию речевого ввода в HoloLens 2 и нереальном подсистеме
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, нереалное, нереальное ядро 4, UE4, HoloLens 2, голосовая передача, голосовая передача, распознавание речи, Смешанная реальность, разработка, функции, документация, руководства, голограммы, Разработка игр
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330636"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="f01e0-104">Ввод голоса в нереальном режиме</span><span class="sxs-lookup"><span data-stu-id="f01e0-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="f01e0-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="f01e0-105">Overview</span></span>
<span data-ttu-id="f01e0-106">Речевой ввод позволяет взаимодействовать с голограммами без использования жестов руки и поддерживается в HoloLens (1-й Gen) и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f01e0-106">Voice input allows you to interact with a hologram without having to use hand gestures and is supported on HoloLens (1st Gen) and HoloLens 2.</span></span> <span data-ttu-id="f01e0-107">Он работает на основе того же механизма, который поддерживает речь во всех других универсальных приложениях Windows и может добавить естественное ощущение к способу взаимодействия в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f01e0-107">It's powered by the same engine that supports speech in all other Universal Windows Apps and can add a natural feeling to the way you interact in mixed reality.</span></span> 

<span data-ttu-id="f01e0-108">Поддерживаемые функции голоса включают:</span><span class="sxs-lookup"><span data-stu-id="f01e0-108">Supported voice features include:</span></span>
- <span data-ttu-id="f01e0-109">[Команда SELECT](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span><span class="sxs-lookup"><span data-stu-id="f01e0-109">The [Select command](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span></span>
- [<span data-ttu-id="f01e0-110">Эй, Кортана</span><span class="sxs-lookup"><span data-stu-id="f01e0-110">Hey, Cortana</span></span>](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- <span data-ttu-id="f01e0-111">См. раздел "для взаимодействия кнопок и меток</span><span class="sxs-lookup"><span data-stu-id="f01e0-111">"See it, say it" for button and label interaction</span></span>
- <span data-ttu-id="f01e0-112">Диктовка</span><span class="sxs-lookup"><span data-stu-id="f01e0-112">Dictation</span></span>

<span data-ttu-id="f01e0-113">Дополнительные сведения см. в основной документации по [голосовым входным данным](voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="f01e0-113">For more information, check out the main [Voice Input](voice-input.md) documentation.</span></span>

## <a name="enabling-speech-recognition"></a><span data-ttu-id="f01e0-114">Включение распознавания речи</span><span class="sxs-lookup"><span data-stu-id="f01e0-114">Enabling Speech Recognition</span></span>

<span data-ttu-id="f01e0-115">Включение распознавания речи в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="f01e0-115">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="f01e0-116">Выберите **Параметры проекта > платформа > HoloLens >ные возможности** и включите **микрофон**.</span><span class="sxs-lookup"><span data-stu-id="f01e0-116">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="f01e0-117">Включено распознавание речи рекогнизтион в **параметрах > конфиденциальность > речи** и выберите **Английский**.</span><span class="sxs-lookup"><span data-stu-id="f01e0-117">Enabled speech recogniztion in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="f01e0-118">Функция распознавания речи всегда работает на языке интерфейса Windows, настроенном в приложении " **Параметры** ".</span><span class="sxs-lookup"><span data-stu-id="f01e0-118">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="f01e0-119">Рекомендуется также включить **Распознавание речи в Интернете** , чтобы обеспечить лучшее качество обслуживания.</span><span class="sxs-lookup"><span data-stu-id="f01e0-119">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Параметры распознавания речи Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="f01e0-121">При первом запуске приложения отобразится диалоговое окно с запросом на включение микрофона.</span><span class="sxs-lookup"><span data-stu-id="f01e0-121">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="f01e0-122">Выбор параметра **Да** запускает голосовое входное значение в приложении.</span><span class="sxs-lookup"><span data-stu-id="f01e0-122">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="f01e0-123">Речевой ввод не требует специальных интерфейсов API Windows Mixed Reality; Он основан на существующем API-интерфейсе сопоставления [входных данных](https://docs.unrealengine.com/Gameplay/Input/index.html) в нереального модуля 4.</span><span class="sxs-lookup"><span data-stu-id="f01e0-123">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="f01e0-124">Добавление сопоставлений речи</span><span class="sxs-lookup"><span data-stu-id="f01e0-124">Adding Speech Mappings</span></span>
<span data-ttu-id="f01e0-125">Подключение речи к действию является важным шагом при использовании голосового ввода.</span><span class="sxs-lookup"><span data-stu-id="f01e0-125">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="f01e0-126">Эти сопоставления отслеживают ключевые слова приложения для речи, которые пользователь может сказать, а затем запускают связанное действие.</span><span class="sxs-lookup"><span data-stu-id="f01e0-126">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="f01e0-127">Сопоставления речи можно найти, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="f01e0-127">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="f01e0-128">Выберите **изменить > параметры проекта**, прокрутите до раздела **подсистема** и выберите **входные данные**.</span><span class="sxs-lookup"><span data-stu-id="f01e0-128">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="f01e0-129">Чтобы добавить новое сопоставление речи для команды перехода, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="f01e0-129">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="f01e0-130">Щелкните **+** значок рядом с **элементом массив** и заполните следующие значения:</span><span class="sxs-lookup"><span data-stu-id="f01e0-130">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="f01e0-131">**жумпворд** для **имени действия**</span><span class="sxs-lookup"><span data-stu-id="f01e0-131">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="f01e0-132">**Перейти** к **ключевому слову речи**</span><span class="sxs-lookup"><span data-stu-id="f01e0-132">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="f01e0-133">В качестве ключевого слова можно использовать любые английские слова или короткие предложения.</span><span class="sxs-lookup"><span data-stu-id="f01e0-133">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Входное настройки UE4 Engine](images/unreal/engine-input.png)

<span data-ttu-id="f01e0-135">Сопоставления речи можно использовать в качестве входных компонентов, таких как сопоставление действий или осей, или как узлы схемы в графе событий.</span><span class="sxs-lookup"><span data-stu-id="f01e0-135">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="f01e0-136">Например, можно связать команду перехода, чтобы напечатать два разных журнала в зависимости от того, когда речь идет об слове:</span><span class="sxs-lookup"><span data-stu-id="f01e0-136">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="f01e0-137">Дважды щелкните проект, чтобы открыть его в **графе событий**.</span><span class="sxs-lookup"><span data-stu-id="f01e0-137">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="f01e0-138">Щелкните **правой кнопкой мыши** и найдите **имя действия** для сопоставления речи (в данном случае это **жумпворд**), а затем нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="f01e0-138">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="f01e0-139">При этом на граф добавляется узел **входного действия** .</span><span class="sxs-lookup"><span data-stu-id="f01e0-139">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="f01e0-140">Перетащите выделенный ПИН **-** код для **печати строкового** узла, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="f01e0-140">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="f01e0-141">**Освобожденный** ПИН-код можно оставить пустым, он не будет выполнять никаких действий для сопоставления речи.</span><span class="sxs-lookup"><span data-stu-id="f01e0-141">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Простое действие для голоса](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="f01e0-143">Воспроизводите приложение, скажем, **Переход** на слово и Просмотр консоли выводят журналы.</span><span class="sxs-lookup"><span data-stu-id="f01e0-143">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="f01e0-144">Это все, что необходимо для того, чтобы добавить речевой ввод в приложения HoloLens в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="f01e0-144">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="f01e0-145">Дополнительные сведения о речевых операциях и интерактивных действиях можно найти по ссылкам ниже, и не забудьте подумать о том, что вы создаете для пользователей.</span><span class="sxs-lookup"><span data-stu-id="f01e0-145">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="see-also"></a><span data-ttu-id="f01e0-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f01e0-146">See also</span></span>
* [<span data-ttu-id="f01e0-147">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="f01e0-147">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="f01e0-148">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="f01e0-148">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f01e0-149">212. Ввод в смешанной реальности: голос</span><span class="sxs-lookup"><span data-stu-id="f01e0-149">MR Input 212: Voice</span></span>](holograms-212.md)
