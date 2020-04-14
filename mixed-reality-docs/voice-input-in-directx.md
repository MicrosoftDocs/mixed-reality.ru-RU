---
title: Ввод голоса в DirectX
description: В этой статье объясняется, как реализовать голосовые команды и небольшие фразы и распознавание предложений в приложении DirectX для Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Пошаговое руководство, голосовая команда, фраза, распознавание, речь, DirectX, платформа, Кортана, Windows Mixed Reality
ms.openlocfilehash: 2837a0fc42e8fdebb2e1facee118d20b5668cd43
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277972"
---
# <a name="voice-input-in-directx"></a>Ввод голоса в DirectX

В этой статье объясняется, как реализовать [голосовые команды](voice-input.md) , а также распознавание строчных фраз и предложений в приложении DirectX для Windows Mixed Reality.

>[!NOTE]
>В фрагментах кода в этой статье используется C++код/CX, а не совместимый C++с C + +17/WinRT, который используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, но код необходимо преобразовать.

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>Использование Спичрекогнизер для непрерывного распознавания речи

В этом разделе описывается использование непрерывного распознавания речи для включения голосовых команд в приложении. В этом пошаговом руководстве используется код из примера [холографиквоицеинпут](https://go.microsoft.com/fwlink/p/?LinkId=844964) . При запуске образца говорите с именем одной из команд зарегистрированного цвета, чтобы изменить цвет вращающегося куба.

Сначала создайте новый экземпляр *Windows:: Media:: спичрекогнитион:: спичрекогнизер* .

Из *холографиквоицеинпутсамплемаин:: креатеспичконстраинтсфоркуррентстате*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Создайте список речевых команд для распознавателя для прослушивания. Здесь мы создаем набор команд для изменения цвета голограммы. Для удобства мы также создадим данные, которые будут использоваться для команд позже.

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

Для указания команд можно использовать фонетические слова, которые могут отсутствовать в словаре.

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Чтобы загрузить список команд в список ограничений для распознавателя речи, используйте объект [спичрекогнитионлистконстраинт](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .

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

Обработчик событий *онресултженератед* получает данные события в экземпляре [спичконтинуаусрекогнитионресултженератедевентаргс](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) . Если достоверность превышает заданное пороговое значение, приложение должно отметить, что событие произошло. Сохраните данные события, чтобы их можно было использовать в последующем цикле обновления.

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

В нашем примере кода мы изменим цвет для кубика с голограммой в соответствии с пользовательской командой.

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

## <a name="use-one-shot-recognition"></a>Использовать распознавание "один раз"

Можно настроить распознавание речи для прослушивания фраз или предложений, которые говорит пользователь. В этом случае мы применяем *спичрекогнитионтопикконстраинт* , который сообщает распознавателю распознавания речи, какой тип входных данных следует рассчитывать. Ниже приведен рабочий процесс приложения для этого сценария.
1. Приложение создает Спичрекогнизер, предоставляет запросы пользовательского интерфейса и начинает прослушивание произнесенной команды.
2. Пользователь говорит о фразе или предложении.
3. Выполняется распознавание речи пользователя, и результат возвращается в приложение. На этом этапе приложение должно предоставить запрос пользовательского интерфейса, чтобы указать, что произошло распознавание.
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

Затем результат возвращается приложению. Если у нас есть достаточная уверенность в результатах, мы можем обработать команду. Этот пример кода обрабатывает результаты по крайней мере средней достоверности.

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

При использовании распознавания речи Следите за исключениями, которые могут означать, что пользователь отключил микрофон в настройках конфиденциальности системы. Это может произойти во время инициализации или распознавания.

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

> [!NOTE]
> Существует несколько предопределенных [спичрекогнитионсценариос](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) , которые можно использовать для оптимизации распознавания речи.

* Чтобы оптимизировать для диктовки, используйте сценарий диктовки.<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* Для поиска в Интернете через речь используйте следующее ограничение для конкретного веб-сценария.

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
* Вы можете предоставить собственную грамматику в формате SRGS.

## <a name="use-continuous-recognition"></a>Использовать непрерывное распознавание

Сведения о сценарии непрерывной диктовки см. в [примере кода речи Windows 10 UWP](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).

## <a name="handle-quality-degradation"></a>Обработано снижение качества

Условия среды иногда мешают распознаванию речи. Например, комната может быть слишком шумным, или пользователь может говорить слишком громко. Когда это возможно, API распознавания речи предоставляет сведения об условиях снижения качества. Эти сведения передаются в приложение с помощью события WinRT. В следующем примере показано, как подписываться на это событие.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

В нашем примере кода данные условий записываются в консоль отладки. Приложение может захотеть предоставить отзыв пользователю с помощью пользовательского интерфейса, синтеза речи и другого метода. Или может потребоваться поведение по-разному, если речь прерывается за счет временного снижения качества.

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

Если вы не используете классы ссылок для создания приложения DirectX, необходимо отказаться от подписки на событие до выпуска или повторного создания распознавателя речи. В Холографикспичпромптсампле есть подпрограммы для прекращения распознавания и отмены подписки на события.

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>Использование синтеза речи для ввода звуковых запросов

В пошаговых примерах holographic речь используется синтез речи для предоставления пользователю инструкций. В этом разделе показано, как создать пример синтезированного голоса, а затем воспроизвести его с помощью API аудио ХРТФ.

При запросе ввода фраз необходимо указать собственные голосовые запросы. Кроме того, в запросах можно указать, когда голосовые команды могут быть полезны для сценария непрерывного распознавания. В следующем примере показано, как использовать синтезатор речи для этого. Можно также использовать предварительно записанный голосовый ролик, визуальный пользовательский интерфейс или другой индикатор того, что следует сказать, например в сценариях, где запрос не является динамическим.

Сначала создайте объект Спичсинсесизер.

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Кроме того, требуется строка, содержащая текст для синтезирования.

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Речь создается асинхронно через Синсесизетексттостреамасинк. Здесь мы начнем асинхронную задачу для синтезирования речи.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

Синтез речи отправляется в виде потока байтов. Мы можем использовать этот поток байтов для инициализации голоса XAudio2. Для наших примеров кода мы воспроизводим его как ХРТФ Audio.

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

## <a name="see-also"></a>См. также:
* [Разработка речевых приложений](https://msdn.microsoft.com/library/dn596121.aspx)
* [Пример Спичрекогнитионандсинсесис](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
