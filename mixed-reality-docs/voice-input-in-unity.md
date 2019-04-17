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
# <a name="voice-input-in-unity"></a>Голосовой ввод в Unity

Unity предоставляет три способа добавления [голоса](voice-input.md) приложение Unity.

С KeywordRecognizer, (по одному из двух типов PhraseRecognizers) приложения могут получить массив строки команд для прослушивания. С помощью GrammarRecognizer (другие тип PhraseRecognizer) приложения могут получить файла SRGS, определение грамматики для прослушивания. С DictationRecognizer ваше приложение может прослушивать любое слово и предоставить пользователю примечания или других отображается их речи.

>[!NOTE]
>Только диктовки или распознаваний могут обрабатываться одновременно. Это означает, что если GrammarRecognizer или KeywordRecognizer активен, DictationRecognizer не может быть активным и наоборот.

## <a name="enabling-the-capability-for-voice"></a>Включение возможности голосовой связи

**"Микрофон"** возможность должны объявляться для приложения использовать голосовой ввод.
1. В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»
2. Перейдите на вкладку «Windows Store»
3. В разделе «Возможности публикации > Параметры» установите флажок **"микрофон"** возможностей

## <a name="phrase-recognition"></a>Функция распознавания

Чтобы включить приложения для прослушивания определенного фразам пользователем затем выполнить определенное действие, вам потребуется:
1. Укажите, какие фраз для прослушивания с помощью KeywordRecognizer или GrammarRecognizer
2. Обработать событие OnPhraseRecognized и предпринять действия, соответствующего распознанной фразы

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Пространство имен:** *UnityEngine.Windows.Speech*<br>
**Типы:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Нам потребуется некоторые операторы using, чтобы сохранить некоторые нажатий клавиш:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Затем давайте добавим несколько полей для класса для хранения распознавателю и ключевое слово "->" словарь действия:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Теперь добавьте ключевое слово в словарь (например, внутри метода Start()). В этом примере мы добавляем слово «активировать»:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Создайте распознаватель ключевое слово и сообщаете о том, что мы хотим распознавания:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Теперь Зарегистрируйте событие OnPhraseRecognized

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Обработчик пример —:

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

Наконец запустите распознавание!

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Пространство имен:** *UnityEngine.Windows.Speech*<br>
**Типы**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

GrammarRecognizer используется в том случае, если вы указываете вашей грамматики распознавания, с помощью SRGS. Это полезно в том случае, если приложение имеет более чем несколько ключевых слов, чтобы распознать более сложные фраз, или если вы хотите легко включать и отключать наборов команд. Пример [Создание с помощью XML SRGS грамматики](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) файл сведения о форматировании.

Если ваш грамматику SRGS, и он находится в проекте в [StreamingAssets папку](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Создайте GrammarRecognizer и передать ей путь к файлу SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Теперь Зарегистрируйте событие OnPhraseRecognized

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Вы получите обратного вызова, содержащий сведения, указанные в вашей грамматику SRGS, который может обрабатывать соответствующим образом. Большая часть важной информации будет предоставляться в массиве semanticMeanings.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Наконец запустите распознавание!

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Диктовка

**Пространство имен:** *UnityEngine.Windows.Speech*<br>
**Типы**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Используйте DictationRecognizer для преобразования пользователя речи в текст. Предоставляет DictationRecognizer [диктовки](voice-input.md#dictation) завершения события, поэтому вы можете отправить отзыв пользователю оба хотя они говорят функциональные возможности и поддерживает регистрацию и прослушивание гипотезы и фразы, а затем. Методы Start() и Stop() соответственно Включение и отключение режима диктовки распознавания. После этого с помощью распознавателя, он должен быть удален с помощью метода Dispose() необходимо освободить ресурсы, используемые в нем. Он будет освободить эти ресурсы автоматически во время сбора мусора за плату дополнительную производительность — Если не освобождаются до этого.

Существует лишь несколько шагов, необходимых для начала работы с диктовки.
1. Создание нового DictationRecognizer
2. Обработка событий диктовки
3. Запустить DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Включение возможности для диктовки

Возможность «Интернет-клиент», помимо возможностей «Микрофон» было сказано выше, должны объявляться для приложения для использования режима диктовки.
1. В редакторе Unity, перейдите к параметрам проигрывателя, перейдя на страницу «Изменить > проекта Параметры > Player»
2. Перейдите на вкладку «Windows Store»
3. В разделе «Возможности публикации > Параметры» установите флажок **InternetClient** возможностей

### <a name="dictationrecognizer"></a>DictationRecognizer

Создание DictationRecognizer следующим образом:

```
dictationRecognizer = new DictationRecognizer();
```

Существует четыре режима диктовки событий, которые можно подписаться и обработать для реализации поведения диктовки.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

Это событие возникает, когда пользователь приостанавливает, обычно в конце предложения. Полный распознал, что здесь возвращается строка.

Во-первых подписаться на событие DictationResult:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Затем обработки DictationResult обратного вызова:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Это событие возникает постоянно, пока пользователь. Как распознаватель ожидает передачи данных, он предоставляет текст о том, до сих слышали.

Во-первых подписаться на событие DictationHypothesis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Затем обработки DictationHypothesis обратного вызова:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Это событие возникает при остановке распознаватель, как и в случае с Stop(), вызываемого, происходящих истечения времени ожидания или другой ошибки.

Во-первых подписаться на событие DictationComplete:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Затем обработки DictationComplete обратного вызова:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Это событие вызывается при возникновении ошибки.

Во-первых подписаться на событие DictationError:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Затем обработки DictationError обратного вызова:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

После подписаны и обработанные события диктовки, которые вас интересуют, запустите распознаватель диктовки, чтобы начать получать события.

```
dictationRecognizer.Start();
```

Если вы больше не хотите сохранить DictationRecognizer вокруг, необходимо отменить подписку на события и Dispose DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Советы**
* Методы Start() и Stop() соответственно Включение и отключение режима диктовки распознавания.
* После этого с помощью распознавателя, он должен быть удален с помощью метода Dispose() необходимо освободить ресурсы, используемые в нем. Он будет освободить эти ресурсы автоматически во время сбора мусора за плату дополнительную производительность — Если не освобождаются до этого.
* Истекает время ожидания после заданного периода времени. Можно проверить это время ожидания в событии DictationComplete. Существует два времени ожидания, которые следует учитывать:
   1. Если распознаватель запускается не слышит аудио для первых пяти секунд, истечет.
   2. Если распознаватель дала результат, но затем слышит бездействия в течение 20 секунд, время ожидания истекает.

## <a name="using-both-phrase-recognition-and-dictation"></a>С помощью распознавания фразы и режимом диктовки

Если вы хотите использовать распознаваний и режимом диктовки в приложении, необходимо полностью выключить один перед запуском другой. Если у вас есть несколько KeywordRecognizers работает, можно выключить их все за один раз с:

```
PhraseRecognitionSystem.Shutdown();
```

Чтобы восстановить все распознавателей к предыдущим значениям после остановки DictationRecognizer, можно вызвать:

```
PhraseRecognitionSystem.Restart();
```

Можно также просто начать KeywordRecognizer, что приведет к перезапуску PhraseRecognitionSystem также.

## <a name="using-the-microphone-helper"></a>Использование вспомогательного метода "микрофон"

Смешанной реальности Toolkit на GitHub содержит вспомогательный класс "микрофон", указание конференции для разработчиков, если в системе можно использовать "микрофон". Для него применяется где следовало бы проверьте, есть "микрофон" в системе перед отображением подсказки для взаимодействия с любой речи в приложении.

Вспомогательный сценарий "микрофон" можно найти в [папки входных данных и сценарии или служебные программы](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). Репозиторий GitHub также содержит [небольшую выборку](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) демонстрируется использование вспомогательного объекта.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Голосовой ввод в смешанной реальности Toolkit
В этой сценой, можно найти примеры голосовой ввод.

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
