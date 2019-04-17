---
title: Голосовой ввод в Unity
description: Unity предоставляет три способа добавления голосовой ввод на приложения Windows смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Голосового ввода, KeywordRecognizer, GrammarRecognizer, "микрофон", режима диктовки, голоса
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604816"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="89c67-104">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="89c67-104">Voice input in Unity</span></span>

<span data-ttu-id="89c67-105">Unity предоставляет три способа добавления [голоса](voice-input.md) приложение Unity.</span><span class="sxs-lookup"><span data-stu-id="89c67-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="89c67-106">С KeywordRecognizer, (по одному из двух типов PhraseRecognizers) приложения могут получить массив строки команд для прослушивания.</span><span class="sxs-lookup"><span data-stu-id="89c67-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="89c67-107">С помощью GrammarRecognizer (другие тип PhraseRecognizer) приложения могут получить файла SRGS, определение грамматики для прослушивания.</span><span class="sxs-lookup"><span data-stu-id="89c67-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="89c67-108">С DictationRecognizer ваше приложение может прослушивать любое слово и предоставить пользователю примечания или других отображается их речи.</span><span class="sxs-lookup"><span data-stu-id="89c67-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="89c67-109">Только диктовки или распознаваний могут обрабатываться одновременно.</span><span class="sxs-lookup"><span data-stu-id="89c67-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="89c67-110">Это означает, что если GrammarRecognizer или KeywordRecognizer активен, DictationRecognizer не может быть активным и наоборот.</span><span class="sxs-lookup"><span data-stu-id="89c67-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="89c67-111">Включение возможности голосовой связи</span><span class="sxs-lookup"><span data-stu-id="89c67-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="89c67-112">**"Микрофон"** возможность должны объявляться для приложения использовать голосовой ввод.</span><span class="sxs-lookup"><span data-stu-id="89c67-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="89c67-113">В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»</span><span class="sxs-lookup"><span data-stu-id="89c67-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="89c67-114">Перейдите на вкладку «Windows Store»</span><span class="sxs-lookup"><span data-stu-id="89c67-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="89c67-115">В разделе «Возможности публикации > Параметры» установите флажок **"микрофон"** возможностей</span><span class="sxs-lookup"><span data-stu-id="89c67-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="89c67-116">Функция распознавания</span><span class="sxs-lookup"><span data-stu-id="89c67-116">Phrase Recognition</span></span>

<span data-ttu-id="89c67-117">Чтобы включить приложения для прослушивания определенного фразам пользователем затем выполнить определенное действие, вам потребуется:</span><span class="sxs-lookup"><span data-stu-id="89c67-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="89c67-118">Укажите, какие фраз для прослушивания с помощью KeywordRecognizer или GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="89c67-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="89c67-119">Обработать событие OnPhraseRecognized и предпринять действия, соответствующего распознанной фразы</span><span class="sxs-lookup"><span data-stu-id="89c67-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="89c67-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="89c67-120">KeywordRecognizer</span></span>

<span data-ttu-id="89c67-121">**Пространство имен:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="89c67-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="89c67-122">**Типы:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="89c67-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="89c67-123">Нам потребуется некоторые операторы using, чтобы сохранить некоторые нажатий клавиш:</span><span class="sxs-lookup"><span data-stu-id="89c67-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="89c67-124">Затем давайте добавим несколько полей для класса для хранения распознавателю и ключевое слово "->" словарь действия:</span><span class="sxs-lookup"><span data-stu-id="89c67-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="89c67-125">Теперь добавьте ключевое слово в словарь (например, внутри метода Start()).</span><span class="sxs-lookup"><span data-stu-id="89c67-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="89c67-126">В этом примере мы добавляем слово «активировать»:</span><span class="sxs-lookup"><span data-stu-id="89c67-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="89c67-127">Создайте распознаватель ключевое слово и сообщаете о том, что мы хотим распознавания:</span><span class="sxs-lookup"><span data-stu-id="89c67-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="89c67-128">Теперь Зарегистрируйте событие OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="89c67-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="89c67-129">Обработчик пример —:</span><span class="sxs-lookup"><span data-stu-id="89c67-129">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="89c67-130">Наконец запустите распознавание!</span><span class="sxs-lookup"><span data-stu-id="89c67-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="89c67-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="89c67-131">GrammarRecognizer</span></span>

<span data-ttu-id="89c67-132">**Пространство имен:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="89c67-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="89c67-133">**Типы**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="89c67-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="89c67-134">GrammarRecognizer используется в том случае, если вы указываете вашей грамматики распознавания, с помощью SRGS.</span><span class="sxs-lookup"><span data-stu-id="89c67-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="89c67-135">Это полезно в том случае, если приложение имеет более чем несколько ключевых слов, чтобы распознать более сложные фраз, или если вы хотите легко включать и отключать наборов команд.</span><span class="sxs-lookup"><span data-stu-id="89c67-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="89c67-136">Пример [Создание с помощью XML SRGS грамматики](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) файл сведения о форматировании.</span><span class="sxs-lookup"><span data-stu-id="89c67-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="89c67-137">Если ваш грамматику SRGS, и он находится в проекте в [StreamingAssets папку](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="89c67-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="89c67-138">Создайте GrammarRecognizer и передать ей путь к файлу SRGS:</span><span class="sxs-lookup"><span data-stu-id="89c67-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="89c67-139">Теперь Зарегистрируйте событие OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="89c67-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="89c67-140">Вы получите обратного вызова, содержащий сведения, указанные в вашей грамматику SRGS, который может обрабатывать соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="89c67-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="89c67-141">Большая часть важной информации будет предоставляться в массиве semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="89c67-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="89c67-142">Наконец запустите распознавание!</span><span class="sxs-lookup"><span data-stu-id="89c67-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="89c67-143">Диктовка</span><span class="sxs-lookup"><span data-stu-id="89c67-143">Dictation</span></span>

<span data-ttu-id="89c67-144">**Пространство имен:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="89c67-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="89c67-145">**Типы**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="89c67-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="89c67-146">Используйте DictationRecognizer для преобразования пользователя речи в текст.</span><span class="sxs-lookup"><span data-stu-id="89c67-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="89c67-147">Предоставляет DictationRecognizer [диктовки](voice-input.md#dictation) завершения события, поэтому вы можете отправить отзыв пользователю оба хотя они говорят функциональные возможности и поддерживает регистрацию и прослушивание гипотезы и фразы, а затем.</span><span class="sxs-lookup"><span data-stu-id="89c67-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="89c67-148">Методы Start() и Stop() соответственно Включение и отключение режима диктовки распознавания.</span><span class="sxs-lookup"><span data-stu-id="89c67-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="89c67-149">После этого с помощью распознавателя, он должен быть удален с помощью метода Dispose() необходимо освободить ресурсы, используемые в нем.</span><span class="sxs-lookup"><span data-stu-id="89c67-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="89c67-150">Он будет освободить эти ресурсы автоматически во время сбора мусора за плату дополнительную производительность — Если не освобождаются до этого.</span><span class="sxs-lookup"><span data-stu-id="89c67-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="89c67-151">Существует лишь несколько шагов, необходимых для начала работы с диктовки.</span><span class="sxs-lookup"><span data-stu-id="89c67-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="89c67-152">Создание нового DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="89c67-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="89c67-153">Обработка событий диктовки</span><span class="sxs-lookup"><span data-stu-id="89c67-153">Handle Dictation events</span></span>
3. <span data-ttu-id="89c67-154">Запустить DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="89c67-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="89c67-155">Включение возможности для диктовки</span><span class="sxs-lookup"><span data-stu-id="89c67-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="89c67-156">Возможность «Интернет-клиент», помимо возможностей «Микрофон» было сказано выше, должны объявляться для приложения для использования режима диктовки.</span><span class="sxs-lookup"><span data-stu-id="89c67-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="89c67-157">В редакторе Unity, перейдите к параметрам проигрывателя, перейдя на страницу «Изменить > проекта Параметры > Player»</span><span class="sxs-lookup"><span data-stu-id="89c67-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="89c67-158">Перейдите на вкладку «Windows Store»</span><span class="sxs-lookup"><span data-stu-id="89c67-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="89c67-159">В разделе «Возможности публикации > Параметры» установите флажок **InternetClient** возможностей</span><span class="sxs-lookup"><span data-stu-id="89c67-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="89c67-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="89c67-160">DictationRecognizer</span></span>

<span data-ttu-id="89c67-161">Создание DictationRecognizer следующим образом:</span><span class="sxs-lookup"><span data-stu-id="89c67-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="89c67-162">Существует четыре режима диктовки событий, которые можно подписаться и обработать для реализации поведения диктовки.</span><span class="sxs-lookup"><span data-stu-id="89c67-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="89c67-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="89c67-163">DictationResult</span></span>
2. <span data-ttu-id="89c67-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="89c67-164">DictationComplete</span></span>
3. <span data-ttu-id="89c67-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="89c67-165">DictationHypothesis</span></span>
4. <span data-ttu-id="89c67-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="89c67-166">DictationError</span></span>

<span data-ttu-id="89c67-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="89c67-167">**DictationResult**</span></span>

<span data-ttu-id="89c67-168">Это событие возникает, когда пользователь приостанавливает, обычно в конце предложения.</span><span class="sxs-lookup"><span data-stu-id="89c67-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="89c67-169">Полный распознал, что здесь возвращается строка.</span><span class="sxs-lookup"><span data-stu-id="89c67-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="89c67-170">Во-первых подписаться на событие DictationResult:</span><span class="sxs-lookup"><span data-stu-id="89c67-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="89c67-171">Затем обработки DictationResult обратного вызова:</span><span class="sxs-lookup"><span data-stu-id="89c67-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="89c67-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="89c67-172">**DictationHypothesis**</span></span>

<span data-ttu-id="89c67-173">Это событие возникает постоянно, пока пользователь.</span><span class="sxs-lookup"><span data-stu-id="89c67-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="89c67-174">Как распознаватель ожидает передачи данных, он предоставляет текст о том, до сих слышали.</span><span class="sxs-lookup"><span data-stu-id="89c67-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="89c67-175">Во-первых подписаться на событие DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="89c67-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="89c67-176">Затем обработки DictationHypothesis обратного вызова:</span><span class="sxs-lookup"><span data-stu-id="89c67-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="89c67-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="89c67-177">**DictationComplete**</span></span>

<span data-ttu-id="89c67-178">Это событие возникает при остановке распознаватель, как и в случае с Stop(), вызываемого, происходящих истечения времени ожидания или другой ошибки.</span><span class="sxs-lookup"><span data-stu-id="89c67-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="89c67-179">Во-первых подписаться на событие DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="89c67-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="89c67-180">Затем обработки DictationComplete обратного вызова:</span><span class="sxs-lookup"><span data-stu-id="89c67-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="89c67-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="89c67-181">**DictationError**</span></span>

<span data-ttu-id="89c67-182">Это событие вызывается при возникновении ошибки.</span><span class="sxs-lookup"><span data-stu-id="89c67-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="89c67-183">Во-первых подписаться на событие DictationError:</span><span class="sxs-lookup"><span data-stu-id="89c67-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="89c67-184">Затем обработки DictationError обратного вызова:</span><span class="sxs-lookup"><span data-stu-id="89c67-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="89c67-185">После подписаны и обработанные события диктовки, которые вас интересуют, запустите распознаватель диктовки, чтобы начать получать события.</span><span class="sxs-lookup"><span data-stu-id="89c67-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="89c67-186">Если вы больше не хотите сохранить DictationRecognizer вокруг, необходимо отменить подписку на события и Dispose DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="89c67-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="89c67-187">**Советы**</span><span class="sxs-lookup"><span data-stu-id="89c67-187">**Tips**</span></span>
* <span data-ttu-id="89c67-188">Методы Start() и Stop() соответственно Включение и отключение режима диктовки распознавания.</span><span class="sxs-lookup"><span data-stu-id="89c67-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="89c67-189">После этого с помощью распознавателя, он должен быть удален с помощью метода Dispose() необходимо освободить ресурсы, используемые в нем.</span><span class="sxs-lookup"><span data-stu-id="89c67-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="89c67-190">Он будет освободить эти ресурсы автоматически во время сбора мусора за плату дополнительную производительность — Если не освобождаются до этого.</span><span class="sxs-lookup"><span data-stu-id="89c67-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="89c67-191">Истекает время ожидания после заданного периода времени.</span><span class="sxs-lookup"><span data-stu-id="89c67-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="89c67-192">Можно проверить это время ожидания в событии DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="89c67-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="89c67-193">Существует два времени ожидания, которые следует учитывать:</span><span class="sxs-lookup"><span data-stu-id="89c67-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="89c67-194">Если распознаватель запускается не слышит аудио для первых пяти секунд, истечет.</span><span class="sxs-lookup"><span data-stu-id="89c67-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="89c67-195">Если распознаватель дала результат, но затем слышит бездействия в течение 20 секунд, время ожидания истекает.</span><span class="sxs-lookup"><span data-stu-id="89c67-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="89c67-196">С помощью распознавания фразы и режимом диктовки</span><span class="sxs-lookup"><span data-stu-id="89c67-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="89c67-197">Если вы хотите использовать распознаваний и режимом диктовки в приложении, необходимо полностью выключить один перед запуском другой.</span><span class="sxs-lookup"><span data-stu-id="89c67-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="89c67-198">Если у вас есть несколько KeywordRecognizers работает, можно выключить их все за один раз с:</span><span class="sxs-lookup"><span data-stu-id="89c67-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="89c67-199">Чтобы восстановить все распознавателей к предыдущим значениям после остановки DictationRecognizer, можно вызвать:</span><span class="sxs-lookup"><span data-stu-id="89c67-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="89c67-200">Можно также просто начать KeywordRecognizer, что приведет к перезапуску PhraseRecognitionSystem также.</span><span class="sxs-lookup"><span data-stu-id="89c67-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="89c67-201">Использование вспомогательного метода "микрофон"</span><span class="sxs-lookup"><span data-stu-id="89c67-201">Using the microphone helper</span></span>

<span data-ttu-id="89c67-202">Смешанной реальности Toolkit на GitHub содержит вспомогательный класс "микрофон", указание конференции для разработчиков, если в системе можно использовать "микрофон".</span><span class="sxs-lookup"><span data-stu-id="89c67-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="89c67-203">Для него применяется где следовало бы проверьте, есть "микрофон" в системе перед отображением подсказки для взаимодействия с любой речи в приложении.</span><span class="sxs-lookup"><span data-stu-id="89c67-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="89c67-204">Вспомогательный сценарий "микрофон" можно найти в [папки входных данных и сценарии или служебные программы](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="89c67-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="89c67-205">Репозиторий GitHub также содержит [небольшую выборку](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) демонстрируется использование вспомогательного объекта.</span><span class="sxs-lookup"><span data-stu-id="89c67-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="89c67-206">Голосовой ввод в смешанной реальности Toolkit</span><span class="sxs-lookup"><span data-stu-id="89c67-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="89c67-207">В этой сценой, можно найти примеры голосовой ввод.</span><span class="sxs-lookup"><span data-stu-id="89c67-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="89c67-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span><span class="sxs-lookup"><span data-stu-id="89c67-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
