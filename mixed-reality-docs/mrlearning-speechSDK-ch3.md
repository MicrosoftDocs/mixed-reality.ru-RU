---
title: Модуль Спичсдк с MR Learning — распознавание речи и транскрипция
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 7fe3c96cf7b888a4a91960147270be81a0973980
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485757"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="b5f2a-104">3.    Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="b5f2a-104">3.    Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="b5f2a-105">В этом учебнике мы рассмотрим аабаут в нашем проекте компонент перевода речи Azure Cognitive Services, а также на трех разных языках.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-105">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

## <a name="instructions"></a><span data-ttu-id="b5f2a-106">Инструкция</span><span class="sxs-lookup"><span data-stu-id="b5f2a-106">Instructions</span></span>

1. <span data-ttu-id="b5f2a-107">Выберите объект Lunarcom_Base в иерархии и нажмите кнопку Добавить компонент на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-107">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="b5f2a-108">Найдите и выберите Лунаркомтранслатионрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-108">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="b5f2a-110">Примечание. Перед тестированием транслятора речи-SDK убедитесь, что симулятор автономного режима отключен.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-110">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="b5f2a-111">Для преобразования необходимо подключение к Интернету.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-111">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="b5f2a-112">Чтобы найти этот параметр, см. изображение ниже.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-112">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="b5f2a-114">Щелкните раскрывающийся список в Лунаркомтранслатионрекогнизер и выберите язык, на который вы хотите перевести.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-114">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="b5f2a-116">Теперь запустите приложение и протестируйте переводчик, нажав кнопку спутника и начинайте говорить.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-116">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="b5f2a-117">Нажмите вспомогательную кнопку еще раз, чтобы прерывать распознавание.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-117">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="b5f2a-118">Ниже приведен пример того, как будет выглядеть сцена.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-118">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="b5f2a-119">Вы можете изменить язык в раскрывающемся списке "целевой язык" (см. рисунок выше), чтобы просмотреть перевод на другие языки.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-119">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="b5f2a-120">Примечание. Перед тестированием убедитесь, что автономный симулятор отключен, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-120">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="b5f2a-122">Ниже приведен пример того, как должна выглядеть сцена:</span><span class="sxs-lookup"><span data-stu-id="b5f2a-122">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="b5f2a-124">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="b5f2a-124">Congratulations</span></span>

<span data-ttu-id="b5f2a-125">Теперь ваш проект может переводить слова на несколько разных языков.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-125">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="b5f2a-126">Вы можете поэкспериментировать с языками и проверить точность перевода.</span><span class="sxs-lookup"><span data-stu-id="b5f2a-126">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="b5f2a-127">Следующий учебник: 4.  Настройка намерения и распознавание естественного языка</span><span class="sxs-lookup"><span data-stu-id="b5f2a-127">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

