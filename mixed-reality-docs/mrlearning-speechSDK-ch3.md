---
title: Учебники по службам речи Azure — 3. Добавление компонента перевода речи Azure Cognitive Services
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 27742702f7a274b3212cdf12c77d8acfa0a29834
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701828"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="cb946-105">3. Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="cb946-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="cb946-106">В этом учебнике мы рассмотрим аабаут в нашем проекте компонент перевода речи Azure Cognitive Services, а также на трех разных языках.</span><span class="sxs-lookup"><span data-stu-id="cb946-106">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

## <a name="instructions"></a><span data-ttu-id="cb946-107">Инструкция</span><span class="sxs-lookup"><span data-stu-id="cb946-107">Instructions</span></span>

1. <span data-ttu-id="cb946-108">Выберите объект Lunarcom_Base в иерархии и нажмите кнопку Добавить компонент на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="cb946-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="cb946-109">Найдите и выберите Лунаркомтранслатионрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="cb946-109">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="cb946-111">Примечание. Перед тестированием транслятора речи-SDK убедитесь, что симулятор автономного режима отключен.</span><span class="sxs-lookup"><span data-stu-id="cb946-111">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="cb946-112">Для преобразования необходимо подключение к Интернету.</span><span class="sxs-lookup"><span data-stu-id="cb946-112">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="cb946-113">Чтобы найти этот параметр, см. изображение ниже.</span><span class="sxs-lookup"><span data-stu-id="cb946-113">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="cb946-115">Щелкните раскрывающийся список в Лунаркомтранслатионрекогнизер и выберите язык, на который вы хотите перевести.</span><span class="sxs-lookup"><span data-stu-id="cb946-115">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="cb946-117">Теперь запустите приложение и протестируйте переводчик, нажав кнопку спутника и начинайте говорить.</span><span class="sxs-lookup"><span data-stu-id="cb946-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="cb946-118">Нажмите вспомогательную кнопку еще раз, чтобы прерывать распознавание.</span><span class="sxs-lookup"><span data-stu-id="cb946-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="cb946-119">Ниже приведен пример того, как будет выглядеть сцена.</span><span class="sxs-lookup"><span data-stu-id="cb946-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="cb946-120">Вы можете изменить язык в раскрывающемся списке "целевой язык" (см. рисунок выше), чтобы просмотреть перевод на другие языки.</span><span class="sxs-lookup"><span data-stu-id="cb946-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="cb946-121">Примечание. Перед тестированием убедитесь, что автономный симулятор отключен, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="cb946-121">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="cb946-123">Ниже приведен пример того, как должна выглядеть сцена:</span><span class="sxs-lookup"><span data-stu-id="cb946-123">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="cb946-125">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="cb946-125">Congratulations</span></span>

<span data-ttu-id="cb946-126">Теперь ваш проект может переводить слова на несколько разных языков.</span><span class="sxs-lookup"><span data-stu-id="cb946-126">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="cb946-127">Вы можете поэкспериментировать с языками и проверить точность перевода.</span><span class="sxs-lookup"><span data-stu-id="cb946-127">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="cb946-128">Следующий учебник: 4.  Настройка намерения и распознавание естественного языка</span><span class="sxs-lookup"><span data-stu-id="cb946-128">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

