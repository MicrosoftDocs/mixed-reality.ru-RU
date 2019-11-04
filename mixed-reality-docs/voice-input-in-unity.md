---
title: Ввод голоса в Unity
description: Unity предоставляет три способа добавления речевого ввода в приложение Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Ввод голоса, Кэйвордрекогнизер, Граммаррекогнизер, микрофон, Диктовка, речь
ms.openlocfilehash: d1cd2a2b954a195bc3f2688d915965f89aa30f98
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438199"
---
# <a name="voice-input-in-unity"></a>Ввод голоса в Unity

>[!NOTE]
>Вместо приведенной ниже информации рассмотрите возможность использования подключаемого модуля Unity для пакета SDK служб распознавания речи, который обеспечивает гораздо более высокую точность результатов распознавания речи и предоставляет удобный доступ к декодированию речи в текст и расширенным функциям речи, таким как диалоговое окно, на основе намерения взаимодействие, перевод, синтез текста в речь и распознавание речи в естественном языке. Найдите пример и документация: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity   

Unity предоставляет три способа добавления [речевого ввода](voice-input.md) в приложение Unity.

При использовании Кэйвордрекогнизер (одного из двух типов Фрасерекогнизерс) приложению можно предоставить массив строк команд для прослушивания. В Граммаррекогнизер (другой тип Фрасерекогнизер) приложению можно предоставить файл SRGS, определяющий конкретную грамматику для прослушивания. С помощью Диктатионрекогнизер приложение может прослушивать любое слово и предоставить пользователю заметку или другое отображение речи.

>[!NOTE]
>Одновременно можно обрабатывать только диктовку или распознавание фразы. Это означает, что Граммаррекогнизер или Кэйвордрекогнизер активен, Диктатионрекогнизер не может быть активным и наоборот.

## <a name="enabling-the-capability-for-voice"></a>Включение возможности для голоса

Чтобы использовать речевой ввод, для приложения необходимо объявить возможность использования **микрофона** .
1. В редакторе Unity перейдите к параметрам проигрывателя, перейдя к разделу "изменение параметров проекта > > Player".
2. Перейдите на вкладку "Магазин Windows".
3. В разделе "Параметры публикации > возможности" проверьте возможность использования **микрофона** .

## <a name="phrase-recognition"></a>Распознавание фраз

Чтобы разрешить приложению прослушивать определенные фразы, произносимые пользователем, выполните некоторые действия:
1. Укажите, какие фразы следует прослушивать с помощью Кэйвордрекогнизер или Граммаррекогнизер
2. Обрабатывает событие Онфрасерекогнизед и принимает действие, соответствующее распознанной фразе

### <a name="keywordrecognizer"></a>кэйвордрекогнизер

**Пространство имен:** *UnityEngine. Windows. Speech*<br>
**Типы:** *кэйвордрекогнизер*, *фрасерекогнизедевентаргс*, *спичеррор*, *спичсистемстатус*

Чтобы сохранить несколько нажатий клавиш, потребуется несколько операторов using:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Затем добавим несколько полей в класс для хранения словаря распознавателя и ключевого слова >.

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Теперь добавьте в словарь ключевое слово (например, внутри метода Start ()). В этом примере мы добавляем ключевое слово "Activate":

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Создайте распознаватель ключевых слов и сообщите ему, что мы хотим узнать:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Теперь Зарегистрируйтесь для события Онфрасерекогнизед

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Пример обработчика:

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

Наконец, начните распознать!

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>граммаррекогнизер

**Пространство имен:** *UnityEngine. Windows. Speech*<br>
**Типы**: *граммаррекогнизер*, *фрасерекогнизедевентаргс*, *спичеррор*, *спичсистемстатус*

Граммаррекогнизер используется, если вы указываете грамматику для распознавания с помощью SRGS. Это может быть полезно, если приложение содержит несколько ключевых слов, если вы хотите распознавать более сложные фразы или хотите легко включать и выключать наборы команд. Сведения о формате файла см. [в статье Создание грамматик с помощью XML-кода SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) .

После того как грамматика SRGS будет доступна в проекте в [папке стреамингассетс](https://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Создайте Граммаррекогнизер и передайте ему путь к файлу SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Теперь Зарегистрируйтесь для события Онфрасерекогнизед

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Вы получите обратный вызов, содержащий сведения, указанные в грамматике SRGS, которую можно будет правильно обойти. Большая часть важной информации будет предоставлена в массиве Семантикмеанингс.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Наконец, начните распознать!

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Диктовка

**Пространство имен:** *UnityEngine. Windows. Speech*<br>
**Типы**: *диктатионрекогнизер*, *спичеррор*, *спичсистемстатус*

Используйте Диктатионрекогнизер для преобразования речи пользователя в текст. Диктатионрекогнизер предоставляет функции [диктовки](voice-input.md#dictation) и поддерживает регистрацию и прослушивание событий завершения и фразы, поэтому вы можете отправить отзыв пользователю, когда они говорят и затем. Методы Start () и останавливают () соответственно включают и отключают распознавание диктовки. После завершения с распознавателем его следует удалить с помощью метода Dispose (), чтобы освободить используемые ресурсы. Эти ресурсы будут автоматически освобождены во время сборки мусора при дополнительных затратах на производительность, если они не выводятся до этого.

Чтобы начать работу с диктовкой, необходимо выполнить несколько шагов.
1. Создание нового Диктатионрекогнизер
2. Обработку событий диктовки
3. Запуск Диктатионрекогнизер

### <a name="enabling-the-capability-for-dictation"></a>Включение функции для диктовки

В дополнение к возможности "микрофона", упомянутой выше, необходимо объявить клиентский Интернет, чтобы использовать диктовку в приложении.
1. В редакторе Unity перейдите к параметрам проигрывателя, перейдя на страницу "Изменение > параметров проекта > Player".
2. Перейдите на вкладку "Магазин Windows".
3. В разделе "Параметры публикации > возможности" проверьте возможность **InternetClient**

### <a name="dictationrecognizer"></a>диктатионрекогнизер

Создайте Диктатионрекогнизер следующим образом:

```
dictationRecognizer = new DictationRecognizer();
```

Существует четыре события диктовки, которые можно подписывать и обрабатывать для реализации поведения диктовки.
1. диктатионресулт
2. диктатионкомплете
3. диктатионхипосесис
4. диктатионеррор

**диктатионресулт**

Это событие возникает после приостановки пользователем, как правило, в конце предложения. Здесь возвращается полная распознанная строка.

Сначала Подпишитесь на событие Диктатионресулт:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Затем обработайте обратный вызов Диктатионресулт:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**диктатионхипосесис**

Это событие возникает постоянно во время разговора пользователя. Как распознаватель прослушивает этот момент, он предоставляет текст о том, что он слышал.

Сначала Подпишитесь на событие Диктатионхипосесис:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Затем обработайте обратный вызов Диктатионхипосесис:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**диктатионкомплете**

Это событие возникает при остановке распознавателя, при вызове из метода Stop (), истечения времени ожидания или при возникновении какой-либо другой ошибки.

Сначала Подпишитесь на событие Диктатионкомплете:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Затем обработайте обратный вызов Диктатионкомплете:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**диктатионеррор**

Это событие возникает при возникновении ошибки.

Сначала Подпишитесь на событие Диктатионеррор:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Затем обработайте обратный вызов Диктатионеррор:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

После подписки и обработки событий диктовки запустите распознаватель диктовки, чтобы начать получать события.

```
dictationRecognizer.Start();
```

Если вы больше не хотите поддерживать Диктатионрекогнизер, необходимо отменить подписывание событий и ликвидировать Диктатионрекогнизер.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Предпринять**
* Методы Start () и останавливают () соответственно включают и отключают распознавание диктовки.
* После завершения с распознавателем его необходимо удалить с помощью метода Dispose (), чтобы освободить используемые ресурсы. Эти ресурсы будут автоматически освобождены во время сборки мусора при дополнительных затратах на производительность, если они не выводятся до этого.
* Время ожидания происходит по истечении заданного периода времени. Эти времена ожидания можно проверить в событии Диктатионкомплете. Существует два времени ожидания, которые следует учитывать:
   1. Если распознаватель запускается и не слышит звук в течение первых пяти секунд, время ожидания истечет.
   2. Если распознаватель предоставил результат, а затем слышит бездействия в течение двадцати секунд, время ожидания истечет.

## <a name="using-both-phrase-recognition-and-dictation"></a>Использование распознавания и диктовки фраз

Если вы хотите использовать как распознавание, так и диктовку в приложении, необходимо полностью закрыть один из них, прежде чем можно будет начать другой. Если вы используете несколько Кэйвордрекогнизерс, вы можете завершить их все одновременно с помощью:

```
PhraseRecognitionSystem.Shutdown();
```

Чтобы восстановить все распознаватели до их предыдущего состояния, после остановки Диктатионрекогнизер можно вызвать:

```
PhraseRecognitionSystem.Restart();
```

Кроме того, можно просто запустить Кэйвордрекогнизер, который также перезапустит Фрасерекогнитионсистем.

## <a name="using-the-microphone-helper"></a>Использование вспомогательного метода микрофона

Набор средств Mixed Reality в GitHub содержит вспомогательный класс микрофона для указания разработчикам, если в системе есть пригодный для использования микрофон. Одним из них является необходимость проверки наличия микрофона в системе перед отображением любых подсказок речевого взаимодействия в приложении.

Вспомогательный сценарий микрофона можно найти в [папке input/Scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). Репозиторий GitHub также содержит [небольшой пример](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) , демонстрирующий использование вспомогательного метода.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Речевой ввод в наборе средств Mixed Reality
Примеры речевого ввода можно найти в этой сцене.

- [Холотулкит-ексамплес/input/сцены/Спичинпутсаурце. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
