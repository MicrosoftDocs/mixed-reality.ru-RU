---
title: Ввод голоса в DirectX
description: В этой статье объясняется, как реализовать голосовые команды и небольшие фразы и распознавание предложений в приложении DirectX для Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Пошаговое руководство, голосовая команда, фраза, распознавание, речь, DirectX, платформа, Кортана, Windows Mixed Reality
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548664"
---
# <a name="voice-input-in-directx"></a>Ввод голоса в DirectX

В этом разделе объясняется, как реализовать [голосовые команды](voice-input.md)и небольшие фразы и распознавание предложений в приложении DirectX для Windows Mixed Reality.

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>Использование Спичрекогнизер для непрерывного распознавания голосовых команд

В этом разделе описано, как использовать непрерывное распознавание речи для включения голосовых команд в приложение. В этом пошаговом руководстве используется код из примера [холографиквоицеинпут](http://go.microsoft.com/fwlink/p/?LinkId=844964) . При запуске образца говорите с именем одной из команд зарегистрированного цвета, чтобы изменить цвет вращающегося куба.

Сначала создайте новый экземпляр **Windows:: Media:: спичрекогнитион:: спичрекогнизер** .

Из *холографиквоицеинпутсамплемаин:: креатеспичконстраинтсфоркуррентстате*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Для прослушивания распознавателя необходимо создать список речевых команд. Здесь мы создаем набор команд для изменения цвета голограммы. Для удобства мы также создадим данные, которые будут использоваться для команд далее.

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

Команды можно указать с помощью фонетических слов, которые могут отсутствовать в словаре:

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Список команд загружается в список ограничений для распознавателя речи. Это делается с помощью объекта [спичрекогнитионлистконстраинт](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

Подпишитесь на событие [ресултженератед](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) в [спичконтинуаусрекогнитионсессион](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)распознавателя речи. Это событие уведомляет ваше приложение о том, что одна из команд распознана.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Обработчик событий **онресултженератед** получает данные события в экземпляре [спичконтинуаусрекогнитионресултженератедевентаргс](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) . Если достоверность превышает установленное пороговое значение, приложение должно отметить, что событие произошло. Сохраните данные события, чтобы их можно было использовать в последующем цикле обновления.

Из *холографиквоицеинпутсамплемаин. cpp*:

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

Используйте данные, но применимы к сценарию приложения. В нашем примере кода мы изменим цвет для кубика с голограммой в соответствии с пользовательской командой.

Из *холографиквоицеинпутсамплемаин:: Update*:

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>Использование диктовки для одноразового распознавания речевых фраз и предложений

Вы можете настроить распознаватель речи для прослушивания фраз или предложений, произнесенных пользователем. В этом случае мы применяем Спичрекогнитионтопикконстраинт, который сообщает распознавателю распознавания речи, какой тип входных данных следует рассчитывать. Ниже приведен рабочий процесс приложения для этого типа сценария.
1. Приложение создает Спичрекогнизер, предоставляет запросы пользовательского интерфейса и начинает прослушивание команды для немедленной речи.
2. Пользователь говорит о фразе или предложении.
3. Выполняется распознавание речи пользователя, и результат возвращается в приложение. На этом этапе приложение должно предоставить запрос пользовательского интерфейса, указывающий на то, что произошло распознавание.
4. В зависимости от уровня достоверности, на который вы хотите ответить, и уровня достоверности результатов распознавания речи, приложение может обработать результат и ответить соответствующим образом.

В этом разделе описывается создание Спичрекогнизер, компиляция ограничения и прослушивание речевого ввода.

Следующий код компилирует ограничение раздела, которое в этом случае оптимизировано для поиска в Интернете.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Если компиляция выполнена, можно продолжить распознавание речи.

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

Затем результат возвращается приложению. Если у нас достаточно уверенности в результате, мы можем обработать команду. Этот пример кода обрабатывает результаты по крайней мере средней достоверности.

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

При использовании распознавания речи следует следить за исключениями, которые могут означать, что пользователь отключил микрофон в настройках конфиденциальности системы. Это может произойти во время инициализации или во время распознавания.

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

**ПРИМЕЧАНИЕ.** Существует несколько предопределенных [спичрекогнитионсценариос](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) , доступных для оптимизации распознавания речи.
* Если вы хотите оптимизировать для диктовки, используйте сценарий диктовки:

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* При использовании речи для поиска в Интернете можно использовать ограничение для веб-сценариев следующим образом.

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* Используйте ограничение формы для заполнения форм. В этом случае лучше применить собственную грамматику, оптимизированную для заполнения формы.

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* Вы можете предоставить собственную грамматику, используя формат SRGS.

## <a name="use-continuous-freeform-speech-dictation"></a>Использование непрерывной диктовки в произвольных рукописных сообщениях

См. пример кода речи Windows 10 UWP для сценария непрерывной диктовки [.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>Ухудшение качества

Иногда условия в среде могут препятствовать работе распознавания речи. Например, комната может оказаться слишком шумным или пользователь мог говорить на слишком высоком томе. API распознавания речи предоставляет сведения, где это возможно, о условиях, которые привели к ухудшению качества.

Эти сведения помещаются в приложение с помощью события WinRT. Ниже приведен пример подписки на это событие.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

В нашем примере кода мы решили записать сведения об условиях в консоль отладки. Приложение может захотеть предоставить отзыв пользователю через пользовательский интерфейс, синтез речи и т. д. или, если речь прерывается за счет временного снижения качества.

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

Если вы не используете классы ссылок для создания приложения DirectX, необходимо отказаться от подписки на событие перед освобождением или повторным созданием распознавателя речи. В Холографикспичпромптсампле есть подпрограммы для прекращения распознавания и отмены подписки на события следующим образом:

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>Использование синтеза речи для ввода голосовых запросов

В пошаговых примерах holographic речь используется синтез речи для предоставления пользователю инструкций. В этом разделе рассматривается процесс создания примера синтезированного голоса и его воспроизведения с помощью API аудио ХРТФ.

При запросе ввода фразы необходимо указать собственные голосовые запросы. Это также может быть полезным для того, чтобы указать, когда можно говорить о голосовых командах, для сценария непрерывного распознавания. Ниже приведен пример того, как это сделать с помощью синтезатора речи. Обратите внимание, что можно также использовать предварительно записанный голосовый ролик, визуальный пользовательский интерфейс или другой индикатор того, что следует сказать, например в сценариях, где запрос не является динамическим.

Сначала создайте объект Спичсинсесизер:

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Кроме того, требуется строка с текстом для синтезирования:

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Речь засинтезирована асинхронно с помощью Синсесизетексттостреамасинк. Здесь мы начнем асинхронную задачу для синтезирования речи.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

Синтез речи отправляется в виде потока байтов. Мы можем инициализировать XAudio2 голоса, используя этот поток байтов. для наших примеров кода мы воспроизводим его как ХРТФ Audio.

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

Как и при распознавании речи, синтез речи создает исключение, если что-то пойдет не так.

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a>См. также
* [Разработка речевых приложений](https://msdn.microsoft.com/library/dn596121.aspx)
* [Пространственный звук в DirectX](spatial-sound-in-directx.md)
* [Пример Спичрекогнитионандсинсесис](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
