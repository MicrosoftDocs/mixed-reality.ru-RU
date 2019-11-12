---
title: Учебники по службам речи Azure — 3. Добавление компонента перевода речи Azure Cognitive Services
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913198"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="1321a-105">3. Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="1321a-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="1321a-106">В этом учебнике мы рассмотрим компонент перевода речи Azure Cognitive Services в нашем проекте, а также на трех разных языках.</span><span class="sxs-lookup"><span data-stu-id="1321a-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="1321a-107">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1321a-107">Instructions</span></span>

1. <span data-ttu-id="1321a-108">Выберите объект Lunarcom_Base в иерархии и нажмите кнопку Добавить компонент на панели Инспектор.</span><span class="sxs-lookup"><span data-stu-id="1321a-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="1321a-109">Найдите и выберите распознаватель Лунарком Translation.</span><span class="sxs-lookup"><span data-stu-id="1321a-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="1321a-111">Отключите симулятор автономного режима.</span><span class="sxs-lookup"><span data-stu-id="1321a-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="1321a-113">Перед переходом убедитесь, что симулятор автономного режима отключен, как показано на рисунке выше, перед тестированием транслятора Speech-SDK.</span><span class="sxs-lookup"><span data-stu-id="1321a-113">Before moving on, ensure the offline mode simulator is disabled, as shown in the image above, before testing the Speech-SDK translator.</span></span> <span data-ttu-id="1321a-114">Для преобразования необходимо подключение к Интернету.</span><span class="sxs-lookup"><span data-stu-id="1321a-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="1321a-115">Щелкните раскрывающийся список раскрывающегося списка Лунарком Translation и выберите язык, на который вы хотите перевести.</span><span class="sxs-lookup"><span data-stu-id="1321a-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="1321a-117">Теперь запустите приложение и протестируйте переводчик, нажав кнопку спутника и начинайте говорить.</span><span class="sxs-lookup"><span data-stu-id="1321a-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="1321a-118">Нажмите вспомогательную кнопку еще раз, чтобы прерывать распознавание.</span><span class="sxs-lookup"><span data-stu-id="1321a-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="1321a-119">Ниже приведен пример того, как будет выглядеть сцена.</span><span class="sxs-lookup"><span data-stu-id="1321a-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="1321a-120">Вы можете изменить язык в раскрывающемся списке "целевой язык" (см. рисунок выше), чтобы просмотреть перевод на другие языки.</span><span class="sxs-lookup"><span data-stu-id="1321a-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="1321a-121">Ниже приведен пример того, как должна выглядеть сцена:</span><span class="sxs-lookup"><span data-stu-id="1321a-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="1321a-123">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1321a-123">Congratulations</span></span>

<span data-ttu-id="1321a-124">Теперь ваш проект может переводить слова на несколько разных языков.</span><span class="sxs-lookup"><span data-stu-id="1321a-124">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="1321a-125">Вы можете поэкспериментировать с языками и проверить точность перевода.</span><span class="sxs-lookup"><span data-stu-id="1321a-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="1321a-126">Следующее руководство: 4. Настройка намерения и естественного понимания языка</span><span class="sxs-lookup"><span data-stu-id="1321a-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
