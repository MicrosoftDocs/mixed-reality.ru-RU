---
title: Ввод голоса в DirectX
description: В этой статье объясняется, как реализовать голосовые команды и небольшие фразы и распознавание предложений в приложении DirectX для Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Пошаговое руководство, голосовая команда, фраза, распознавание, речь, DirectX, платформа, Кортана, Windows Mixed Reality
ms.openlocfilehash: 0dcfaae13f763c9b8a06910f11558d2fd8e00276
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641078"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="8f411-104">Ввод голоса в DirectX</span><span class="sxs-lookup"><span data-stu-id="8f411-104">Voice input in DirectX</span></span>

<span data-ttu-id="8f411-105">В этом разделе объясняется, как реализовать [голосовые команды](voice-input.md)и небольшие фразы и распознавание предложений в приложении DirectX для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="8f411-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="8f411-106">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="8f411-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="8f411-107">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="8f411-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="8f411-108">Использование Спичрекогнизер для непрерывного распознавания голосовых команд</span><span class="sxs-lookup"><span data-stu-id="8f411-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="8f411-109">В этом разделе описано, как использовать непрерывное распознавание речи для включения голосовых команд в приложение.</span><span class="sxs-lookup"><span data-stu-id="8f411-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="8f411-110">В этом пошаговом руководстве используется код из примера [холографиквоицеинпут](https://go.microsoft.com/fwlink/p/?LinkId=844964) .</span><span class="sxs-lookup"><span data-stu-id="8f411-110">This walkthrough uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="8f411-111">При запуске образца говорите с именем одной из команд зарегистрированного цвета, чтобы изменить цвет вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="8f411-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="8f411-112">Сначала создайте новый экземпляр **Windows:: Media:: спичрекогнитион:: спичрекогнизер** .</span><span class="sxs-lookup"><span data-stu-id="8f411-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="8f411-113">Из *холографиквоицеинпутсамплемаин:: креатеспичконстраинтсфоркуррентстате*:</span><span class="sxs-lookup"><span data-stu-id="8f411-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="8f411-114">Для прослушивания распознавателя необходимо создать список речевых команд.</span><span class="sxs-lookup"><span data-stu-id="8f411-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="8f411-115">Здесь мы создаем набор команд для изменения цвета голограммы.</span><span class="sxs-lookup"><span data-stu-id="8f411-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="8f411-116">Для удобства мы также создадим данные, которые будут использоваться для команд далее.</span><span class="sxs-lookup"><span data-stu-id="8f411-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="8f411-117">Команды можно указать с помощью фонетических слов, которые могут отсутствовать в словаре:</span><span class="sxs-lookup"><span data-stu-id="8f411-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="8f411-118">Список команд загружается в список ограничений для распознавателя речи.</span><span class="sxs-lookup"><span data-stu-id="8f411-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="8f411-119">Это делается с помощью объекта [спичрекогнитионлистконстраинт](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8f411-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="8f411-120">Подпишитесь на событие [ресултженератед](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) в [спичконтинуаусрекогнитионсессион](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)распознавателя речи.</span><span class="sxs-lookup"><span data-stu-id="8f411-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="8f411-121">Это событие уведомляет ваше приложение о том, что одна из команд распознана.</span><span class="sxs-lookup"><span data-stu-id="8f411-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="8f411-122">Обработчик событий **онресултженератед** получает данные события в экземпляре [спичконтинуаусрекогнитионресултженератедевентаргс](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8f411-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="8f411-123">Если достоверность превышает установленное пороговое значение, приложение должно отметить, что событие произошло.</span><span class="sxs-lookup"><span data-stu-id="8f411-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="8f411-124">Сохраните данные события, чтобы их можно было использовать в последующем цикле обновления.</span><span class="sxs-lookup"><span data-stu-id="8f411-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="8f411-125">Из *холографиквоицеинпутсамплемаин. cpp*:</span><span class="sxs-lookup"><span data-stu-id="8f411-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="8f411-126">Используйте данные, но применимы к сценарию приложения.</span><span class="sxs-lookup"><span data-stu-id="8f411-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="8f411-127">В нашем примере кода мы изменим цвет для кубика с голограммой в соответствии с пользовательской командой.</span><span class="sxs-lookup"><span data-stu-id="8f411-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="8f411-128">Из *холографиквоицеинпутсамплемаин:: Update*:</span><span class="sxs-lookup"><span data-stu-id="8f411-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="8f411-129">Использование диктовки для одноразового распознавания речевых фраз и предложений</span><span class="sxs-lookup"><span data-stu-id="8f411-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="8f411-130">Вы можете настроить распознаватель речи для прослушивания фраз или предложений, произнесенных пользователем.</span><span class="sxs-lookup"><span data-stu-id="8f411-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="8f411-131">В этом случае мы применяем Спичрекогнитионтопикконстраинт, который сообщает распознавателю распознавания речи, какой тип входных данных следует рассчитывать.</span><span class="sxs-lookup"><span data-stu-id="8f411-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="8f411-132">Ниже приведен рабочий процесс приложения для этого типа сценария.</span><span class="sxs-lookup"><span data-stu-id="8f411-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="8f411-133">Приложение создает Спичрекогнизер, предоставляет запросы пользовательского интерфейса и начинает прослушивание команды для немедленной речи.</span><span class="sxs-lookup"><span data-stu-id="8f411-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="8f411-134">Пользователь говорит о фразе или предложении.</span><span class="sxs-lookup"><span data-stu-id="8f411-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="8f411-135">Выполняется распознавание речи пользователя, и результат возвращается в приложение.</span><span class="sxs-lookup"><span data-stu-id="8f411-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="8f411-136">На этом этапе приложение должно предоставить запрос пользовательского интерфейса, указывающий на то, что произошло распознавание.</span><span class="sxs-lookup"><span data-stu-id="8f411-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="8f411-137">В зависимости от уровня достоверности, на который вы хотите ответить, и уровня достоверности результатов распознавания речи, приложение может обработать результат и ответить соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="8f411-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="8f411-138">В этом разделе описывается создание Спичрекогнизер, компиляция ограничения и прослушивание речевого ввода.</span><span class="sxs-lookup"><span data-stu-id="8f411-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="8f411-139">Следующий код компилирует ограничение раздела, которое в этом случае оптимизировано для поиска в Интернете.</span><span class="sxs-lookup"><span data-stu-id="8f411-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="8f411-140">Если компиляция выполнена, можно продолжить распознавание речи.</span><span class="sxs-lookup"><span data-stu-id="8f411-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="8f411-141">Затем результат возвращается приложению.</span><span class="sxs-lookup"><span data-stu-id="8f411-141">The result is then returned to the app.</span></span> <span data-ttu-id="8f411-142">Если у нас достаточно уверенности в результате, мы можем обработать команду.</span><span class="sxs-lookup"><span data-stu-id="8f411-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="8f411-143">Этот пример кода обрабатывает результаты по крайней мере средней достоверности.</span><span class="sxs-lookup"><span data-stu-id="8f411-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="8f411-144">При использовании распознавания речи следует следить за исключениями, которые могут означать, что пользователь отключил микрофон в настройках конфиденциальности системы.</span><span class="sxs-lookup"><span data-stu-id="8f411-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="8f411-145">Это может произойти во время инициализации или во время распознавания.</span><span class="sxs-lookup"><span data-stu-id="8f411-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="8f411-146">**Примечание.** Существует несколько предопределенных [спичрекогнитионсценариос](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) , доступных для оптимизации распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="8f411-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="8f411-147">Если вы хотите оптимизировать для диктовки, используйте сценарий диктовки:</span><span class="sxs-lookup"><span data-stu-id="8f411-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="8f411-148">При использовании речи для поиска в Интернете можно использовать ограничение для веб-сценариев следующим образом.</span><span class="sxs-lookup"><span data-stu-id="8f411-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="8f411-149">Используйте ограничение формы для заполнения форм.</span><span class="sxs-lookup"><span data-stu-id="8f411-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="8f411-150">В этом случае лучше применить собственную грамматику, оптимизированную для заполнения формы.</span><span class="sxs-lookup"><span data-stu-id="8f411-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="8f411-151">Вы можете предоставить собственную грамматику, используя формат SRGS.</span><span class="sxs-lookup"><span data-stu-id="8f411-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="8f411-152">Использование непрерывной диктовки в произвольных рукописных сообщениях</span><span class="sxs-lookup"><span data-stu-id="8f411-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="8f411-153">См. пример кода речи Windows 10 UWP для сценария непрерывной диктовки [.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="8f411-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="8f411-154">Ухудшение качества</span><span class="sxs-lookup"><span data-stu-id="8f411-154">Handle degradation in quality</span></span>

<span data-ttu-id="8f411-155">Иногда условия в среде могут препятствовать работе распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="8f411-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="8f411-156">Например, комната может оказаться слишком шумным или пользователь мог говорить на слишком высоком томе.</span><span class="sxs-lookup"><span data-stu-id="8f411-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="8f411-157">API распознавания речи предоставляет сведения, где это возможно, о условиях, которые привели к ухудшению качества.</span><span class="sxs-lookup"><span data-stu-id="8f411-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="8f411-158">Эти сведения помещаются в приложение с помощью события WinRT.</span><span class="sxs-lookup"><span data-stu-id="8f411-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="8f411-159">Ниже приведен пример подписки на это событие.</span><span class="sxs-lookup"><span data-stu-id="8f411-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="8f411-160">В нашем примере кода мы решили записать сведения об условиях в консоль отладки.</span><span class="sxs-lookup"><span data-stu-id="8f411-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="8f411-161">Приложение может захотеть предоставить отзыв пользователю через пользовательский интерфейс, синтез речи и т. д. или, если речь прерывается за счет временного снижения качества.</span><span class="sxs-lookup"><span data-stu-id="8f411-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="8f411-162">Если вы не используете классы ссылок для создания приложения DirectX, необходимо отказаться от подписки на событие перед освобождением или повторным созданием распознавателя речи.</span><span class="sxs-lookup"><span data-stu-id="8f411-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="8f411-163">В Холографикспичпромптсампле есть подпрограммы для прекращения распознавания и отмены подписки на события следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8f411-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="8f411-164">Использование синтеза речи для ввода голосовых запросов</span><span class="sxs-lookup"><span data-stu-id="8f411-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="8f411-165">В пошаговых примерах holographic речь используется синтез речи для предоставления пользователю инструкций.</span><span class="sxs-lookup"><span data-stu-id="8f411-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="8f411-166">В этом разделе рассматривается процесс создания примера синтезированного голоса и его воспроизведения с помощью API аудио ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="8f411-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="8f411-167">При запросе ввода фразы необходимо указать собственные голосовые запросы.</span><span class="sxs-lookup"><span data-stu-id="8f411-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="8f411-168">Это также может быть полезным для того, чтобы указать, когда можно говорить о голосовых командах, для сценария непрерывного распознавания.</span><span class="sxs-lookup"><span data-stu-id="8f411-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="8f411-169">Ниже приведен пример того, как это сделать с помощью синтезатора речи. Обратите внимание, что можно также использовать предварительно записанный голосовый ролик, визуальный пользовательский интерфейс или другой индикатор того, что следует сказать, например в сценариях, где запрос не является динамическим.</span><span class="sxs-lookup"><span data-stu-id="8f411-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="8f411-170">Сначала создайте объект Спичсинсесизер:</span><span class="sxs-lookup"><span data-stu-id="8f411-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="8f411-171">Кроме того, требуется строка с текстом для синтезирования:</span><span class="sxs-lookup"><span data-stu-id="8f411-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="8f411-172">Речь засинтезирована асинхронно с помощью Синсесизетексттостреамасинк.</span><span class="sxs-lookup"><span data-stu-id="8f411-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="8f411-173">Здесь мы начнем асинхронную задачу для синтезирования речи.</span><span class="sxs-lookup"><span data-stu-id="8f411-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="8f411-174">Синтез речи отправляется в виде потока байтов.</span><span class="sxs-lookup"><span data-stu-id="8f411-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="8f411-175">Мы можем инициализировать XAudio2 голоса, используя этот поток байтов. для наших примеров кода мы воспроизводим его как ХРТФ Audio.</span><span class="sxs-lookup"><span data-stu-id="8f411-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="8f411-176">Как и при распознавании речи, синтез речи создает исключение, если что-то пойдет не так.</span><span class="sxs-lookup"><span data-stu-id="8f411-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8f411-177">См. также</span><span class="sxs-lookup"><span data-stu-id="8f411-177">See also</span></span>
* [<span data-ttu-id="8f411-178">Разработка речевых приложений</span><span class="sxs-lookup"><span data-stu-id="8f411-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="8f411-179">Пример Спичрекогнитионандсинсесис</span><span class="sxs-lookup"><span data-stu-id="8f411-179">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
