---
title: Учебники по службам речи Azure — 2. Добавление автономного режима для локального перевода речи в текст
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 1dd6c01768ddf5dda954f50e0f7507022bd59c3b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701861"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="a8ad1-105">2. Добавление автономного режима для локального перевода речи в текст</span><span class="sxs-lookup"><span data-stu-id="a8ad1-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="a8ad1-106">В этом руководстве мы добавим автономный режим, который позволяет выполнять локальные преобразования речи в текст, когда не удается подключиться к службе Azure.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="a8ad1-107">Кроме того, мы будем *имитировать* отключенное состояние.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="a8ad1-108">Инструкция</span><span class="sxs-lookup"><span data-stu-id="a8ad1-108">Instructions</span></span>

1. <span data-ttu-id="a8ad1-109">Выберите объект Lunarcom_Base в иерархии и нажмите кнопку Добавить компонент на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-109">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="a8ad1-110">Найдите и выберите автономное распознавание Лунарком.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-110">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="a8ad1-112">Щелкните раскрывающийся список в Лунаркомоффлинерекогнизер и выберите включено.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-112">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="a8ad1-113">Этот проект будет работать так же, как у пользователя нет подключения.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-113">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="a8ad1-115">Теперь нажмите кнопку Воспроизведение в редакторе Unity и проверьте его.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-115">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="a8ad1-116">Нажмите микрофон в левом нижнем углу сцены и начните говорить.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-116">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="a8ad1-117">Так как мы отключены от сети, функции пробуждения слова недоступны.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-117">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="a8ad1-118">Вам придется физически щелкать микрофон каждый раз, когда вы хотите, чтобы распознавание речи было признано в автономном режиме.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-118">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="a8ad1-119">Ниже приведен пример того, как может выглядеть сцена.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-119">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="a8ad1-121">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="a8ad1-121">Congratulations</span></span>

<span data-ttu-id="a8ad1-122">Автономный режим включен.</span><span class="sxs-lookup"><span data-stu-id="a8ad1-122">The offline mode has been enabled.</span></span> <span data-ttu-id="a8ad1-123">Теперь, когда вы работаете в автономном режиме, вы по-прежнему можете работать над проектом с помощью Speech-SDK!</span><span class="sxs-lookup"><span data-stu-id="a8ad1-123">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="a8ad1-124">Следующий учебник: 3.  Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="a8ad1-124">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

