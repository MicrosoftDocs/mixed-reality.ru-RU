---
title: Учебники по службам речи Azure — 3. Добавление компонента перевода речи Azure Cognitive Services
description: В этом курсе вы узнаете, как реализовать пакет SDK для распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143235"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="dbce1-105">3. Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="dbce1-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="dbce1-106">В этом руководстве вы узнаете о компоненте перевода речи Azure Cognitive Services в проекте, а также о том, как выполнить перевод на три разных языка.</span><span class="sxs-lookup"><span data-stu-id="dbce1-106">In this tutorial, you'll learn about the Azure Cognitive Services Speech Translation component of your project, as well as how to translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="dbce1-107">Инструкция</span><span class="sxs-lookup"><span data-stu-id="dbce1-107">Instructions</span></span>

1. <span data-ttu-id="dbce1-108">Выберите объект Lunarcom_Base в иерархии и нажмите кнопку Добавить компонент на панели Инспектор.</span><span class="sxs-lookup"><span data-stu-id="dbce1-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="dbce1-109">Найдите и выберите распознаватель Лунарком Translation.</span><span class="sxs-lookup"><span data-stu-id="dbce1-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="dbce1-111">Отключите симулятор автономного режима.</span><span class="sxs-lookup"><span data-stu-id="dbce1-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="dbce1-113">Перед переходом убедитесь, что симулятор автономного режима отключен (как показано на рисунке выше) перед тестированием транслятора Speech-SDK.</span><span class="sxs-lookup"><span data-stu-id="dbce1-113">Before moving on, ensure that the offline mode simulator is disabled (as shown in the image above) before testing the Speech-SDK translator.</span></span> <span data-ttu-id="dbce1-114">Для преобразования необходимо подключение к Интернету.</span><span class="sxs-lookup"><span data-stu-id="dbce1-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="dbce1-115">Щелкните раскрывающийся список раскрывающегося списка Лунарком Translation и выберите язык, на который вы хотите перевести.</span><span class="sxs-lookup"><span data-stu-id="dbce1-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="dbce1-117">Запустите приложение и протестируйте переводчик, нажав кнопку вспомогательная кнопка, и начните говорить.</span><span class="sxs-lookup"><span data-stu-id="dbce1-117">Run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="dbce1-118">Нажмите вспомогательную кнопку еще раз, чтобы прерывать распознавание.</span><span class="sxs-lookup"><span data-stu-id="dbce1-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="dbce1-119">Ниже приведен пример того, как будет выглядеть сцена.</span><span class="sxs-lookup"><span data-stu-id="dbce1-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="dbce1-120">Вы можете изменить язык в раскрывающемся списке "целевой язык" (см. рисунок выше), чтобы просмотреть перевод на другие языки.</span><span class="sxs-lookup"><span data-stu-id="dbce1-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="dbce1-121">Ниже приведен пример того, как должна выглядеть сцена:</span><span class="sxs-lookup"><span data-stu-id="dbce1-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="dbce1-123">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="dbce1-123">Congratulations</span></span>

<span data-ttu-id="dbce1-124">Теперь ваш проект может успешно переводить слова на несколько разных языков.</span><span class="sxs-lookup"><span data-stu-id="dbce1-124">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="dbce1-125">Вы можете поэкспериментировать с языками и проверить точность перевода.</span><span class="sxs-lookup"><span data-stu-id="dbce1-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="dbce1-126">Следующее руководство: 4. Настройка намерения и естественного понимания языка</span><span class="sxs-lookup"><span data-stu-id="dbce1-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
