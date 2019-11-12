---
title: Учебники по службам речи Azure — 2. Добавление автономного режима для локального перевода речи в текст
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 962d7d4750cf59fe56de4af9088c90e8ecd0aa16
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913212"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="a4c61-105">2. Добавление автономного режима для локального перевода речи в текст</span><span class="sxs-lookup"><span data-stu-id="a4c61-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="a4c61-106">В этом руководстве мы добавим автономный режим, который позволяет выполнять локальные преобразования речи в текст, когда не удается подключиться к службе Azure.</span><span class="sxs-lookup"><span data-stu-id="a4c61-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="a4c61-107">Кроме того, мы будем *имитировать* отключенное состояние.</span><span class="sxs-lookup"><span data-stu-id="a4c61-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="a4c61-108">Инструкция</span><span class="sxs-lookup"><span data-stu-id="a4c61-108">Instructions</span></span>

1. <span data-ttu-id="a4c61-109">Выберите объект Lunarcom_Base в иерархии.</span><span class="sxs-lookup"><span data-stu-id="a4c61-109">Select the Lunarcom_Base object in the hierarchy.</span></span>

2. <span data-ttu-id="a4c61-110">Нажмите кнопку Добавить компонент на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="a4c61-110">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="a4c61-111">Найдите и выберите автономное распознавание Лунарком.</span><span class="sxs-lookup"><span data-stu-id="a4c61-111">Search for and select the Lunarcom Offline Recognition.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. <span data-ttu-id="a4c61-113">Щелкните раскрывающийся список в Лунаркомоффлинерекогнизер и выберите включено.</span><span class="sxs-lookup"><span data-stu-id="a4c61-113">Click the drop-down in the LunarcomOfflineRecognizer and select Enabled.</span></span> <span data-ttu-id="a4c61-114">Этот проект будет работать так же, как у пользователя нет подключения.</span><span class="sxs-lookup"><span data-stu-id="a4c61-114">This programs the project to act like the user doesn't have a connection.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. <span data-ttu-id="a4c61-116">Нажмите кнопку Воспроизведение в редакторе Unity и проверьте его.</span><span class="sxs-lookup"><span data-stu-id="a4c61-116">Press Play in Unity Editor, and test it.</span></span> <span data-ttu-id="a4c61-117">Нажмите микрофон в левом нижнем углу сцены и начните говорить.</span><span class="sxs-lookup"><span data-stu-id="a4c61-117">Press the microphone in the bottom-left corner in the scene and begin speaking.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a4c61-118">Так как мы отключены от сети, функции пробуждения слова недоступны.</span><span class="sxs-lookup"><span data-stu-id="a4c61-118">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="a4c61-119">Вам нужно будет физически щелкать микрофон каждый раз, когда вы хотите, чтобы распознавание речи было признано в автономном режиме.</span><span class="sxs-lookup"><span data-stu-id="a4c61-119">You'll need to physically click the microphone every time you wish to have your speech recognized when offline.</span></span>

    <span data-ttu-id="a4c61-120">Ниже приведен пример того, как может выглядеть сцена.</span><span class="sxs-lookup"><span data-stu-id="a4c61-120">Below is an example of what your scene could look like.</span></span>

    ![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="a4c61-122">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="a4c61-122">Congratulations</span></span>

<span data-ttu-id="a4c61-123">Автономный режим включен.</span><span class="sxs-lookup"><span data-stu-id="a4c61-123">The offline mode has been enabled.</span></span> <span data-ttu-id="a4c61-124">Теперь, когда вы работаете в автономном режиме, вы по-прежнему можете работать над проектом с помощью Speech-SDK!</span><span class="sxs-lookup"><span data-stu-id="a4c61-124">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span>

[<span data-ttu-id="a4c61-125">Следующее руководство: 3. Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="a4c61-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
