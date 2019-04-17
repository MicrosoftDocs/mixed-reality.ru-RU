---
title: Голосовой ввод в DirectX
description: Объясняется, как реализовать голосовые команды и небольших распознавания фразы и предложения в приложение DirectX для Windows смешанной реальности.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Пошаговое руководство, голосовых команд, фразы, распознавания, речи, directx, платформа, cortana, смешанной реальности windows
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605103"
---
# <a name="voice-input-in-directx"></a>Голосовой ввод в DirectX

В этом разделе приведены сведения о реализации [голосовые команды](voice-input.md)и небольшой распознавания фразы и предложения в приложении DirectX для Windows смешанной реальности.

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>Использовать SpeechRecognizer для непрерывного распознавание голосовых команд

В этом разделе описано, как пользоваться распознаванием речи непрерывной, чтобы включить голосовые команды в приложении. В этом пошаговом руководстве используется код из [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) образца. При запуске образца произнести имя одного из зарегистрированных цвет команд, чтобы изменить цвет вращающегося куба.

Во-первых, создайте новый **Windows::Media::SpeechRecognition::SpeechRecognizer** экземпляра.

Из *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Вам потребуется для создания списка команд речи для распознавателя для прослушивания. Здесь мы формируют набор команд для изменения цвета голограмма. Для большего удобства мы также создадим данные, мы будем использовать позже для команд.

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

Можно указать команды, используя фонетическое слова, которые не могут быть в словаре:

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Список команд, загружаются в список ограничений для распознавателя речи. Это делается с помощью [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) объекта.

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

Подпишитесь на [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) событий в распознаватель речи [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx). Это событие уведомляет приложение, если один из ваших команд был распознан.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Ваш **OnResultGenerated** обработчик событий получает данные события в [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) экземпляра. Если достоверности выше порогового значения, которые вы определили, приложения следует отметить, что произошло событие. Сохраните данные о событии, таким образом, чтобы использовать его в цикле последующие обновления.

Из *HolographicVoiceInputSampleMain.cpp*:

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

Сделать использования данных, тем не менее подходящий для вашего сценария приложения. В нашем примере кода мы изменить цвет голограмма вращающегося куба в соответствии с команды пользователя.

Из *HolographicVoiceInputSampleMain::Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>Использовать режим диктовки для одноразовой распознавания речи фразы и предложения

Вы можете настроить распознаватель речи для прослушивания фраз или предложений, произносятся пользователем. В этом случае мы применяем SpeechRecognitionTopicConstraint, который сообщает в распознаватель речи, какой тип входных данных следует ожидать. Рабочий процесс приложения выглядит следующим образом, для такого варианта использования:
1. Ваше приложение создает SpeechRecognizer, предоставляет приглашений пользовательского интерфейса и начинает прослушивание команд для произнесения немедленно.
2. Пользователь произносит фразу или предложение.
3. Распознавание речи пользователя выполняется и возвращает результат в приложение. На этом этапе приложение должно предоставлять запросы пользовательского интерфейса, показывающее, что произошло распознавания.
4. В зависимости от уровня надежности, как нужно реагировать на них и уровень достоверности результата распознавания речи ваше приложение может обрабатывать результат и реагировать соответствующим образом.

В этом разделе описывается создание SpeechRecognizer, компиляции ограничение и прослушивать речевого ввода.

Следующий код компилирует ограничения раздела, которое в данном случае оптимизирован для поиска в Интернете.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Если компиляция выполнена успешно, можно продолжить распознавания речи.

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

Затем результат возвращается в приложение. Если мы приобрела достаточно уверенности в результат, мы сможем обработать команду. Данный пример кода обрабатывает результаты с уверенностью по крайней мере среднего размера.

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

Каждый раз при использовании распознавания речи, необходимо следить за исключений, которые могут указывать, что пользователь отключил эту "микрофон" в параметрах конфиденциальности системы. Это может произойти во время инициализации или во время распознавания.

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

**ПРИМЕЧАНИЕ.** Несколько предопределенных [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) для оптимизации распознавания речи.
* Если вы хотите оптимизировать для диктовки, используйте сценарий диктовки:

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* При использовании распознавания речи для выполнения поиска в Интернете, ограничение сценария веб задачи можно использовать следующим образом:

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* Используйте ограничение формы для заполнения форм. В этом случае лучше применить собственные грамматики, которая оптимизирована для заполнения формы.

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* Вы можете предоставить собственные грамматики в формате SRGS.

## <a name="use-continuous-freeform-speech-dictation"></a>Использовать диктовки непрерывной, произвольные речи

См. в образце кода речи Windows 10 UWP для сценария непрерывной диктовки [здесь.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>Дескриптор снижение качества

Условия в среде иногда мешает работе распознавания речи. Например возможно, комнате слишком часто срабатывает, или пользователь может произнести слишком большого объема. API распознавания речи предоставляет сведения, где это возможно, об условиях, которые привели к снижению качества.

Эта информация помещается в приложение с помощью события WinRT. Вот пример того, как подписаться на это событие.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

В нашем примере мы выбираем для записи сведений условия в консоли отладки. Приложение может пожелать предоставить отзывы пользователю с помощью пользовательского интерфейса, синтеза речи и т. д., или может потребоваться работать по-разному, при прерывании речи временный снижение качества.

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

Если вы не используете классы ссылок для создания приложения DirectX, необходимо отменить подписку на событие перед освобождением или повторном создании вашей распознаватель речи. HolographicSpeechPromptSample имеет процедуру для остановки распознавания и Отмена подписки на события следующим образом:

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>Используйте синтеза речи для предоставления звуковые голосовые инструкции

В примерах holographic речи используются синтеза речи в качестве звуковой инструкции для пользователя. В этом разделе рассматривается процесс создания образца синтезированного голоса и воспроизведение с помощью API-интерфейсы аудио HRTF.

Необходимо предоставить свои собственные речи запросов при запросе ввода фразы. Это можно также полезно, указывающие при можно произношении голосовые команды для непрерывного распознавания сценария. Вот пример того, как сделать это с помощью синтезаторов речи; Обратите внимание на то, что можно также использовать предварительно записанные голосовое сообщение, пользовательский Интерфейс visual или другой индикатор того, что сказать, например в сценариях, где строки не является динамическим.

Во-первых создайте объект SpeechSynthesizer:

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Необходимо также строка с текстом для синтезирования:

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Речь синтезировать асинхронно с помощью SynthesizeTextToStreamAsync. Здесь мы начнем асинхронной задачи для синтезирования речи.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

Синтеза речи отправляется в виде байтового потока. Мы можете инициализировать XAudio2 голоса с помощью этого потока байтов; наши примеры holographic кода мы воспроизводить его с аудио HRTF эффекта.

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

Как с помощью распознавания речи, синтеза речи будет создания исключения, если что-то пойдет не так.

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
* [Проектирование приложений для распознавания речи](https://msdn.microsoft.com/library/dn596121.aspx)
* [Пространственные звук в DirectX](spatial-sound-in-directx.md)
* [Пример SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
