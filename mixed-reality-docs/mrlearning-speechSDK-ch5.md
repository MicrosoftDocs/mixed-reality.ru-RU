---
title: Модуль Спичсдк с MR Learning — распознавание речи и транскрипция
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: fc65dccfcbc181af0c0b321374c721797e120e5d
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460335"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="87b60-104">Модуль Learning SDK для распознавания речи — управление средством запуска Rocket с помощью голосовых команд</span><span class="sxs-lookup"><span data-stu-id="87b60-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="87b60-105">На этом занятии мы будем использовать функцию службы распознавания речи Azure, чтобы понять назначение речи.</span><span class="sxs-lookup"><span data-stu-id="87b60-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="87b60-106">Мы будем использовать обнаруженную цель распознавания речи в качестве голосовых команд для управления средством запуска Rocket.</span><span class="sxs-lookup"><span data-stu-id="87b60-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="87b60-107">На этом занятии будет импортирован ресурс средства запуска Rocket, и мы будем использовать команды, обнаруженные с помощью командного голоса, к стандартным кнопкам управления для управления Rocket.</span><span class="sxs-lookup"><span data-stu-id="87b60-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span> 

## <a name="objectives"></a><span data-ttu-id="87b60-108">Цели</span><span class="sxs-lookup"><span data-stu-id="87b60-108">Objectives</span></span>

- <span data-ttu-id="87b60-109">Узнайте, как связать голосовые команды с намерением речи.</span><span class="sxs-lookup"><span data-stu-id="87b60-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="87b60-110">Узнайте, как использовать голосовые команды с намерением речи в качестве входных команд для управления Rocket.</span><span class="sxs-lookup"><span data-stu-id="87b60-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="87b60-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="87b60-111">Instructions</span></span>
1. <span data-ttu-id="87b60-112">В этом руководстве мы будем использовать ресурс-контейнер "Басемодуле" для интеграции средства запуска Rocket с командами распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="87b60-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="87b60-113">Для этого необходимо импортировать ресурс в наш проект.</span><span class="sxs-lookup"><span data-stu-id="87b60-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="87b60-114">Вы можете скачать ресурс Rocket Launcher с помощью этой ссылки (присоедините ссылку).</span><span class="sxs-lookup"><span data-stu-id="87b60-114">You can download the "Rocket Launcher" asset using this link (Attach the link).</span></span> 

2. <span data-ttu-id="87b60-115">Чтобы импортировать ресурс, перейдите в раздел "активы"-> "Импорт пакета" > "пользовательский пакет" > перейдите к скачанному файлу и нажмите кнопку "Импорт".</span><span class="sxs-lookup"><span data-stu-id="87b60-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="87b60-117">После импорта ресурса "средство запуска Rocket" перейдите в папку "Rocket Launcher" — > Prefabs-> выберите "Rocket Launcher_Complete", а затем перетащите ее в существующую иерархию сцены.</span><span class="sxs-lookup"><span data-stu-id="87b60-117">After importing the "Rocket Launcher" asset, navigate inside the "Rocket Launcher" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="87b60-119">Теперь нам нужно интегрировать «Rocket Launcher» с нашим проектом LUIS, который мы работали на предыдущем занятии (ссылка для lesson4).</span><span class="sxs-lookup"><span data-stu-id="87b60-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson (link for lesson4).</span></span> <span data-ttu-id="87b60-120">Для этого разверните prefab "Rocket Launcher_Complete" в иерархии и найдите кнопки "Лаунчраундбуттон", "Ресетраундбуттон" и "подсказки размещения".</span><span class="sxs-lookup"><span data-stu-id="87b60-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="87b60-122">Выберите "Лаунчраундбуттон" и на панели инспектора перейдите в раздел "взаимодействие" и в разделе "события" OnClick () "перетащите" Лунармодуле "prefab.</span><span class="sxs-lookup"><span data-stu-id="87b60-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="87b60-123">Затем выберите раскрывающийся список функций и выберите "Лунармодуле", а затем перейдите к функции "Стартсрустер ()" и выберите ее.</span><span class="sxs-lookup"><span data-stu-id="87b60-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="87b60-126">Выберите "Ресетраундбуттон" и на панели инспектора перейдите в раздел "взаимодействие" и в разделе "события" OnClick () "перетащите" Лунармодуле "prefab.</span><span class="sxs-lookup"><span data-stu-id="87b60-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="87b60-127">Затем выберите раскрывающийся список функций и выберите "Лунармодуле", а затем перейдите к функции "Ресетмодуле ()" и выберите ее.</span><span class="sxs-lookup"><span data-stu-id="87b60-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="87b60-129">Выберите "подсказки размещения" и на панели инспектора перейдите в раздел "взаимодействие" и в разделе "события" OnClick () "перетащите" Лунармодуле "prefab.</span><span class="sxs-lookup"><span data-stu-id="87b60-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="87b60-130">Затем выберите раскрывающийся список функций и выберите "Лунармодуле", а затем перейдите к функции "Тогглеплацеменсинтс" и выберите Тогглегамеобжектс ().</span><span class="sxs-lookup"><span data-stu-id="87b60-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  <span data-ttu-id="87b60-132">Затем выберите Lunarcom_Completed prefab в иерархии, а затем в инспекторе перейдите к скрипту распознавания намерений Лунарком, а затем перетащите кнопки Лаунчраундбуттон, "Ресетраундбуттон" и "подсказки размещения" в соответствующие места.</span><span class="sxs-lookup"><span data-stu-id="87b60-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="87b60-134">Нажмите кнопку Воспроизведение в редакторе Unity и нажмите кнопку "Rocket" и полное такие фразы, как "Push Rocket Launch Button", "Показать подсказку о размещении", "нажмите кнопку" Отправить "или любые другие фразы, относящиеся к запуску, сбросу или запросу подсказки для средства запуска Rocket.</span><span class="sxs-lookup"><span data-stu-id="87b60-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="87b60-138">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="87b60-138">Congratulations</span></span>

<span data-ttu-id="87b60-139">На этом занятии мы узнали, как подключить команды речи на основе AI к голосовым командам, чтобы использовать их в качестве метода ввода.</span><span class="sxs-lookup"><span data-stu-id="87b60-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="87b60-140">Теперь наша программа может использовать эти динамики в качестве речевых команд для предоставления входных данных для средства запуска Rocket.</span><span class="sxs-lookup"><span data-stu-id="87b60-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>

