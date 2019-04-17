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
# <a name="voice-input-in-directx"></a><span data-ttu-id="e86dd-104">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="e86dd-104">Voice input in DirectX</span></span>

<span data-ttu-id="e86dd-105">В этом разделе приведены сведения о реализации [голосовые команды](voice-input.md)и небольшой распознавания фразы и предложения в приложении DirectX для Windows смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e86dd-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="e86dd-106">Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="e86dd-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="e86dd-107">Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.</span><span class="sxs-lookup"><span data-stu-id="e86dd-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="e86dd-108">Использовать SpeechRecognizer для непрерывного распознавание голосовых команд</span><span class="sxs-lookup"><span data-stu-id="e86dd-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="e86dd-109">В этом разделе описано, как пользоваться распознаванием речи непрерывной, чтобы включить голосовые команды в приложении.</span><span class="sxs-lookup"><span data-stu-id="e86dd-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="e86dd-110">В этом пошаговом руководстве используется код из [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) образца.</span><span class="sxs-lookup"><span data-stu-id="e86dd-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="e86dd-111">При запуске образца произнести имя одного из зарегистрированных цвет команд, чтобы изменить цвет вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="e86dd-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="e86dd-112">Во-первых, создайте новый **Windows::Media::SpeechRecognition::SpeechRecognizer** экземпляра.</span><span class="sxs-lookup"><span data-stu-id="e86dd-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="e86dd-113">Из *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="e86dd-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="e86dd-114">Вам потребуется для создания списка команд речи для распознавателя для прослушивания.</span><span class="sxs-lookup"><span data-stu-id="e86dd-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="e86dd-115">Здесь мы формируют набор команд для изменения цвета голограмма.</span><span class="sxs-lookup"><span data-stu-id="e86dd-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="e86dd-116">Для большего удобства мы также создадим данные, мы будем использовать позже для команд.</span><span class="sxs-lookup"><span data-stu-id="e86dd-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="e86dd-117">Можно указать команды, используя фонетическое слова, которые не могут быть в словаре:</span><span class="sxs-lookup"><span data-stu-id="e86dd-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="e86dd-118">Список команд, загружаются в список ограничений для распознавателя речи.</span><span class="sxs-lookup"><span data-stu-id="e86dd-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="e86dd-119">Это делается с помощью [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) объекта.</span><span class="sxs-lookup"><span data-stu-id="e86dd-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="e86dd-120">Подпишитесь на [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) событий в распознаватель речи [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span><span class="sxs-lookup"><span data-stu-id="e86dd-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="e86dd-121">Это событие уведомляет приложение, если один из ваших команд был распознан.</span><span class="sxs-lookup"><span data-stu-id="e86dd-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="e86dd-122">Ваш **OnResultGenerated** обработчик событий получает данные события в [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="e86dd-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="e86dd-123">Если достоверности выше порогового значения, которые вы определили, приложения следует отметить, что произошло событие.</span><span class="sxs-lookup"><span data-stu-id="e86dd-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="e86dd-124">Сохраните данные о событии, таким образом, чтобы использовать его в цикле последующие обновления.</span><span class="sxs-lookup"><span data-stu-id="e86dd-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="e86dd-125">Из *HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="e86dd-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="e86dd-126">Сделать использования данных, тем не менее подходящий для вашего сценария приложения.</span><span class="sxs-lookup"><span data-stu-id="e86dd-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="e86dd-127">В нашем примере кода мы изменить цвет голограмма вращающегося куба в соответствии с команды пользователя.</span><span class="sxs-lookup"><span data-stu-id="e86dd-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="e86dd-128">Из *HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="e86dd-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="e86dd-129">Использовать режим диктовки для одноразовой распознавания речи фразы и предложения</span><span class="sxs-lookup"><span data-stu-id="e86dd-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="e86dd-130">Вы можете настроить распознаватель речи для прослушивания фраз или предложений, произносятся пользователем.</span><span class="sxs-lookup"><span data-stu-id="e86dd-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="e86dd-131">В этом случае мы применяем SpeechRecognitionTopicConstraint, который сообщает в распознаватель речи, какой тип входных данных следует ожидать.</span><span class="sxs-lookup"><span data-stu-id="e86dd-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="e86dd-132">Рабочий процесс приложения выглядит следующим образом, для такого варианта использования:</span><span class="sxs-lookup"><span data-stu-id="e86dd-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="e86dd-133">Ваше приложение создает SpeechRecognizer, предоставляет приглашений пользовательского интерфейса и начинает прослушивание команд для произнесения немедленно.</span><span class="sxs-lookup"><span data-stu-id="e86dd-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="e86dd-134">Пользователь произносит фразу или предложение.</span><span class="sxs-lookup"><span data-stu-id="e86dd-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="e86dd-135">Распознавание речи пользователя выполняется и возвращает результат в приложение.</span><span class="sxs-lookup"><span data-stu-id="e86dd-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="e86dd-136">На этом этапе приложение должно предоставлять запросы пользовательского интерфейса, показывающее, что произошло распознавания.</span><span class="sxs-lookup"><span data-stu-id="e86dd-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="e86dd-137">В зависимости от уровня надежности, как нужно реагировать на них и уровень достоверности результата распознавания речи ваше приложение может обрабатывать результат и реагировать соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="e86dd-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="e86dd-138">В этом разделе описывается создание SpeechRecognizer, компиляции ограничение и прослушивать речевого ввода.</span><span class="sxs-lookup"><span data-stu-id="e86dd-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="e86dd-139">Следующий код компилирует ограничения раздела, которое в данном случае оптимизирован для поиска в Интернете.</span><span class="sxs-lookup"><span data-stu-id="e86dd-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="e86dd-140">Если компиляция выполнена успешно, можно продолжить распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="e86dd-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="e86dd-141">Затем результат возвращается в приложение.</span><span class="sxs-lookup"><span data-stu-id="e86dd-141">The result is then returned to the app.</span></span> <span data-ttu-id="e86dd-142">Если мы приобрела достаточно уверенности в результат, мы сможем обработать команду.</span><span class="sxs-lookup"><span data-stu-id="e86dd-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="e86dd-143">Данный пример кода обрабатывает результаты с уверенностью по крайней мере среднего размера.</span><span class="sxs-lookup"><span data-stu-id="e86dd-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="e86dd-144">Каждый раз при использовании распознавания речи, необходимо следить за исключений, которые могут указывать, что пользователь отключил эту "микрофон" в параметрах конфиденциальности системы.</span><span class="sxs-lookup"><span data-stu-id="e86dd-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="e86dd-145">Это может произойти во время инициализации или во время распознавания.</span><span class="sxs-lookup"><span data-stu-id="e86dd-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="e86dd-146">**ПРИМЕЧАНИЕ.** Несколько предопределенных [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) для оптимизации распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="e86dd-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="e86dd-147">Если вы хотите оптимизировать для диктовки, используйте сценарий диктовки:</span><span class="sxs-lookup"><span data-stu-id="e86dd-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="e86dd-148">При использовании распознавания речи для выполнения поиска в Интернете, ограничение сценария веб задачи можно использовать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e86dd-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="e86dd-149">Используйте ограничение формы для заполнения форм.</span><span class="sxs-lookup"><span data-stu-id="e86dd-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="e86dd-150">В этом случае лучше применить собственные грамматики, которая оптимизирована для заполнения формы.</span><span class="sxs-lookup"><span data-stu-id="e86dd-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="e86dd-151">Вы можете предоставить собственные грамматики в формате SRGS.</span><span class="sxs-lookup"><span data-stu-id="e86dd-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="e86dd-152">Использовать диктовки непрерывной, произвольные речи</span><span class="sxs-lookup"><span data-stu-id="e86dd-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="e86dd-153">См. в образце кода речи Windows 10 UWP для сценария непрерывной диктовки [здесь.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="e86dd-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="e86dd-154">Дескриптор снижение качества</span><span class="sxs-lookup"><span data-stu-id="e86dd-154">Handle degradation in quality</span></span>

<span data-ttu-id="e86dd-155">Условия в среде иногда мешает работе распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="e86dd-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="e86dd-156">Например возможно, комнате слишком часто срабатывает, или пользователь может произнести слишком большого объема.</span><span class="sxs-lookup"><span data-stu-id="e86dd-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="e86dd-157">API распознавания речи предоставляет сведения, где это возможно, об условиях, которые привели к снижению качества.</span><span class="sxs-lookup"><span data-stu-id="e86dd-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="e86dd-158">Эта информация помещается в приложение с помощью события WinRT.</span><span class="sxs-lookup"><span data-stu-id="e86dd-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="e86dd-159">Вот пример того, как подписаться на это событие.</span><span class="sxs-lookup"><span data-stu-id="e86dd-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="e86dd-160">В нашем примере мы выбираем для записи сведений условия в консоли отладки.</span><span class="sxs-lookup"><span data-stu-id="e86dd-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="e86dd-161">Приложение может пожелать предоставить отзывы пользователю с помощью пользовательского интерфейса, синтеза речи и т. д., или может потребоваться работать по-разному, при прерывании речи временный снижение качества.</span><span class="sxs-lookup"><span data-stu-id="e86dd-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="e86dd-162">Если вы не используете классы ссылок для создания приложения DirectX, необходимо отменить подписку на событие перед освобождением или повторном создании вашей распознаватель речи.</span><span class="sxs-lookup"><span data-stu-id="e86dd-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="e86dd-163">HolographicSpeechPromptSample имеет процедуру для остановки распознавания и Отмена подписки на события следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e86dd-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="e86dd-164">Используйте синтеза речи для предоставления звуковые голосовые инструкции</span><span class="sxs-lookup"><span data-stu-id="e86dd-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="e86dd-165">В примерах holographic речи используются синтеза речи в качестве звуковой инструкции для пользователя.</span><span class="sxs-lookup"><span data-stu-id="e86dd-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="e86dd-166">В этом разделе рассматривается процесс создания образца синтезированного голоса и воспроизведение с помощью API-интерфейсы аудио HRTF.</span><span class="sxs-lookup"><span data-stu-id="e86dd-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="e86dd-167">Необходимо предоставить свои собственные речи запросов при запросе ввода фразы.</span><span class="sxs-lookup"><span data-stu-id="e86dd-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="e86dd-168">Это можно также полезно, указывающие при можно произношении голосовые команды для непрерывного распознавания сценария.</span><span class="sxs-lookup"><span data-stu-id="e86dd-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="e86dd-169">Вот пример того, как сделать это с помощью синтезаторов речи; Обратите внимание на то, что можно также использовать предварительно записанные голосовое сообщение, пользовательский Интерфейс visual или другой индикатор того, что сказать, например в сценариях, где строки не является динамическим.</span><span class="sxs-lookup"><span data-stu-id="e86dd-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="e86dd-170">Во-первых создайте объект SpeechSynthesizer:</span><span class="sxs-lookup"><span data-stu-id="e86dd-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="e86dd-171">Необходимо также строка с текстом для синтезирования:</span><span class="sxs-lookup"><span data-stu-id="e86dd-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="e86dd-172">Речь синтезировать асинхронно с помощью SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="e86dd-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="e86dd-173">Здесь мы начнем асинхронной задачи для синтезирования речи.</span><span class="sxs-lookup"><span data-stu-id="e86dd-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="e86dd-174">Синтеза речи отправляется в виде байтового потока.</span><span class="sxs-lookup"><span data-stu-id="e86dd-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="e86dd-175">Мы можете инициализировать XAudio2 голоса с помощью этого потока байтов; наши примеры holographic кода мы воспроизводить его с аудио HRTF эффекта.</span><span class="sxs-lookup"><span data-stu-id="e86dd-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="e86dd-176">Как с помощью распознавания речи, синтеза речи будет создания исключения, если что-то пойдет не так.</span><span class="sxs-lookup"><span data-stu-id="e86dd-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e86dd-177">См. также</span><span class="sxs-lookup"><span data-stu-id="e86dd-177">See also</span></span>
* [<span data-ttu-id="e86dd-178">Проектирование приложений для распознавания речи</span><span class="sxs-lookup"><span data-stu-id="e86dd-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="e86dd-179">Пространственные звук в DirectX</span><span class="sxs-lookup"><span data-stu-id="e86dd-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="e86dd-180">Пример SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="e86dd-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
