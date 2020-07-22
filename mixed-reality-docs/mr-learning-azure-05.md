---
title: Учебники по облачным службам Azure, часть 5. Интеграция Службы Azure Bot c помощью LUIS
description: Пройдите этот курс, чтобы узнать, как реализовать Службу Azure Bot и возможность распознавания естественного языка в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: смешанная реальность, unity, учебник, hololens, hololens 2, служба azure bot, luis, естественный язык, чат-бот
ms.localizationpriority: high
ms.openlocfilehash: e3a64488b1d6d22ac52f798fe90356ce8e995e26
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306514"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="2a52e-105">5. Интеграция Службы Azure Bot</span><span class="sxs-lookup"><span data-stu-id="2a52e-105">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="2a52e-106">Из этого учебника вы узнаете, как использовать **Службу Azure Bot** в демонстрационном приложении **HoloLens 2**, чтобы добавить возможность распознавания речи (LUIS) и разрешить боту помогать пользователю во время поиска **отслеживаемых объектов**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-106">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="2a52e-107">Этот учебник состоит из двух частей. В первой части вы создадите бота с помощью приложения [Bot Composer](https://docs.microsoft.com/composer/introduction) в качестве решения без кода и выполните краткий обзор Функции Azure, которая предоставляет боту необходимые данные.</span><span class="sxs-lookup"><span data-stu-id="2a52e-107">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="2a52e-108">Во второй части вы будете использовать компонент **BotManager (script)** (Диспетчер ботов — скрипт) в проекте Unity для использования размещенной Службы Bot.</span><span class="sxs-lookup"><span data-stu-id="2a52e-108">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="2a52e-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="2a52e-109">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="2a52e-110">Часть 1</span><span class="sxs-lookup"><span data-stu-id="2a52e-110">Part 1</span></span>

* <span data-ttu-id="2a52e-111">Получите основные сведения о Службе Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="2a52e-111">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="2a52e-112">Узнайте, как создать бота с помощью приложения Bot Composer.</span><span class="sxs-lookup"><span data-stu-id="2a52e-112">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="2a52e-113">Узнайте, как использовать функцию Azure для предоставления данных из службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="2a52e-113">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="2a52e-114">Часть 2</span><span class="sxs-lookup"><span data-stu-id="2a52e-114">Part 2</span></span>

* <span data-ttu-id="2a52e-115">Узнайте, как настроить сцену для использования Службы Azure Bot в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="2a52e-115">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="2a52e-116">Узнайте, как настроить и найти объекты с помощью бота.</span><span class="sxs-lookup"><span data-stu-id="2a52e-116">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="2a52e-117">Общие сведения о Службе Azure Bot</span><span class="sxs-lookup"><span data-stu-id="2a52e-117">Understanding Azure Bot Service</span></span>

<span data-ttu-id="2a52e-118">**Служба Azure Bot** позволяет разработчикам создавать интеллектуальных ботов, которые могут поддерживать естественное общение с пользователями благодаря **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-118">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="2a52e-119">Чат-бот — это отличный способ расширить возможности взаимодействия пользователя с приложением.</span><span class="sxs-lookup"><span data-stu-id="2a52e-119">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="2a52e-120">Бот можно использовать в качестве базы знаний с помощью [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs) для поддержания сложного разговора с использованием службы [распознавания речи (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="2a52e-120">A Bot can act as a knowledge base with a [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp).</span></span>

<span data-ttu-id="2a52e-121">Дополнительные сведения о [Службе Azure Bot](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0)</span><span class="sxs-lookup"><span data-stu-id="2a52e-121">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="2a52e-122">Часть 1. Создание бота</span><span class="sxs-lookup"><span data-stu-id="2a52e-122">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="2a52e-123">Прежде чем использовать бота в приложении Unity, его необходимо разработать, предоставить ему данные и разместить в **Azure**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-123">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="2a52e-124">Цель бота — оценить количество *отслеживаемых объектов*, хранимых в базе данных, найти *отслеживаемый объект* по его имени и сообщить пользователю базовую информацию о нем.</span><span class="sxs-lookup"><span data-stu-id="2a52e-124">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="2a52e-125">Краткий обзор функции отслеживаемых объектов в Azure</span><span class="sxs-lookup"><span data-stu-id="2a52e-125">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="2a52e-126">Вы собираетесь приступить к созданию бота, но чтобы сделать его полезным, необходимо предоставить ресурс, из которого он может извлекать данные.</span><span class="sxs-lookup"><span data-stu-id="2a52e-126">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="2a52e-127">Так как *бот* сможет подсчитать количество **отслеживаемых объектов**, найти конкретные объекты по имени и сообщить подробности, вы будете использовать простую Функцию Azure с доступом к **хранилищу таблиц Azure**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-127">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="2a52e-128">Скачайте проект Функции Azure: [Функция отслеживаемых объектов в Azure](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)</span><span class="sxs-lookup"><span data-stu-id="2a52e-128">Download the Azure Function Project: [Tracked Objects Azure Function](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)</span></span>

<span data-ttu-id="2a52e-129">Эта функция Azure может выполнять действия **подсчета** и **поиска**, которые можно вызвать с помощью базовых вызовов *HTTP* *GET*.</span><span class="sxs-lookup"><span data-stu-id="2a52e-129">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="2a52e-130">Код можно проверить в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-130">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="2a52e-131">Дополнительные сведения о [функциях Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="2a52e-131">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="2a52e-132">Функция **Count** запрашивает из **хранилища таблиц** все **отслеживаемые объекты**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-132">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="2a52e-133">С другой стороны, функция **Find** принимает параметр запроса *имени* из запроса *GET* и запрашивает **хранилище таблиц** для сопоставления **отслеживаемых объектов** и возвращает DTO в виде JSON.</span><span class="sxs-lookup"><span data-stu-id="2a52e-133">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="2a52e-134">Вы можете развернуть эту **Функцию Azure** непосредственно из **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-134">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="2a52e-135">Здесь вы найдете все сведения о [развертывании Функции Azure](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml).</span><span class="sxs-lookup"><span data-stu-id="2a52e-135">Find here all information regarding [Azure Function deployment](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml).</span></span>

<span data-ttu-id="2a52e-136">После завершения развертывания на **портале Azure** откройте соответствующий ресурс и выберите вкладку **Конфигурация** в разделе *Параметры*.</span><span class="sxs-lookup"><span data-stu-id="2a52e-136">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="2a52e-137">На вкладке **Параметры приложения** необходимо предоставить *строку подключения* для **хранилища Azure**, где хранятся **отслеживаемые объекты**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-137">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="2a52e-138">Щелкните элемент **Новый параметр приложения** и в качестве имени введите: **AzureStorageConnectionString**, а в качестве значения предоставьте правильную *строку подключения*.</span><span class="sxs-lookup"><span data-stu-id="2a52e-138">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="2a52e-139">После этого нажмите на кнопку **Сохранить**, и **Функция Azure** будет готова к размещению *бота* на сервере, который вы создадите далее.</span><span class="sxs-lookup"><span data-stu-id="2a52e-139">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="2a52e-140">Создание чат-бота</span><span class="sxs-lookup"><span data-stu-id="2a52e-140">Creating a conversation Bot</span></span>

<span data-ttu-id="2a52e-141">Существует несколько способов разработки чат-бота на основе платформы Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="2a52e-141">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="2a52e-142">На этом уроке вы будете использовать классическое приложение [Bot Framework Composer](https://docs.microsoft.com/composer/), которое является визуальным конструктором и идеально подходит для быстрой разработки.</span><span class="sxs-lookup"><span data-stu-id="2a52e-142">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="2a52e-143">Последние выпуски можно скачать из [репозитория GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="2a52e-143">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="2a52e-144">Он доступен для Windows, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="2a52e-144">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="2a52e-145">После установки **Bot Framework Composer** запустите приложение, и вы увидите этот интерфейс:</span><span class="sxs-lookup"><span data-stu-id="2a52e-145">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="2a52e-147">Вы подготовили проект Bot Composer, который предоставляет необходимые диалоги и триггеры для этого учебника.</span><span class="sxs-lookup"><span data-stu-id="2a52e-147">You have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span>
<span data-ttu-id="2a52e-148">Скачайте проект: [Проект Bot Framework Composer](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)</span><span class="sxs-lookup"><span data-stu-id="2a52e-148">Download the project: [Bot Framework Composer project](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)</span></span>

<span data-ttu-id="2a52e-149">На верхней панели нажмите кнопку **Open** (Открыть) и выберите скачанный проект Bot Framework с именем **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-149">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="2a52e-150">После полной загрузки проекта вы увидите, что проект готов.</span><span class="sxs-lookup"><span data-stu-id="2a52e-150">After the project is fully loaded, you should see the project ready.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="2a52e-152">Обратите внимание на **панель диалогов** в левой части страницы.</span><span class="sxs-lookup"><span data-stu-id="2a52e-152">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="2a52e-153">Здесь расположено диалоговое окно **TrackedObjectsBot**, в котором можно увидеть несколько **триггеров**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-153">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="2a52e-154">Дополнительные сведения об [основных понятиях Bot Framework](https://docs.microsoft.com/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="2a52e-154">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="2a52e-155">Эти триггеры выполняют следующие действия:</span><span class="sxs-lookup"><span data-stu-id="2a52e-155">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="2a52e-156">Приветствие</span><span class="sxs-lookup"><span data-stu-id="2a52e-156">Greeting</span></span>

<span data-ttu-id="2a52e-157">Это точка входа *чат-бота*, когда какой-либо *пользователь* инициирует диалог.</span><span class="sxs-lookup"><span data-stu-id="2a52e-157">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="2a52e-159">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="2a52e-159">AskingForCount</span></span>

<span data-ttu-id="2a52e-160">Это диалоговое окно активируется, когда *пользователь* запрашивает подсчет всех **отслеживаемых объектов**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-160">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="2a52e-161">Ниже приведены триггерные фразы:</span><span class="sxs-lookup"><span data-stu-id="2a52e-161">These are the trigger phrases:</span></span>

>* <span data-ttu-id="2a52e-162">count me all (подсчитать все);</span><span class="sxs-lookup"><span data-stu-id="2a52e-162">count me all</span></span>
>* <span data-ttu-id="2a52e-163">how many are stored (количество хранимых).</span><span class="sxs-lookup"><span data-stu-id="2a52e-163">how many are stored</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="2a52e-165">Благодаря [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) *пользователю* не нужно запрашивать фразы естественным для *пользователя* способом.</span><span class="sxs-lookup"><span data-stu-id="2a52e-165">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="2a52e-166">В этом диалоговом окне *бот* также будет обращаться к Функции Azure **Count**. Дополнительные сведения об этом см. ниже.</span><span class="sxs-lookup"><span data-stu-id="2a52e-166">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="2a52e-167">Неизвестная цель</span><span class="sxs-lookup"><span data-stu-id="2a52e-167">Unknown Intent</span></span>

<span data-ttu-id="2a52e-168">Это диалоговое окно запускается, если входные данные *пользователя* не соответствуют никаким другим условиям триггера, и просит пользователя повторно задать свой вопрос.</span><span class="sxs-lookup"><span data-stu-id="2a52e-168">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="2a52e-170">FindEntity</span><span class="sxs-lookup"><span data-stu-id="2a52e-170">FindEntity</span></span>

<span data-ttu-id="2a52e-171">Последнее диалоговое окно более сложное. Здесь приведены функции ветвления и хранения данных в памяти *ботов*.</span><span class="sxs-lookup"><span data-stu-id="2a52e-171">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="2a52e-172">Оно запрашивает у пользователя *имя* **отслеживаемого объекта**, о котором необходимо узнать больше информации, выполняет запрос Функции Azure **Find** и использует ответ для продолжения разговора.</span><span class="sxs-lookup"><span data-stu-id="2a52e-172">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="2a52e-174">Если **отслеживаемый объект** не найден, пользователь получает уведомление, а разговор завершается.</span><span class="sxs-lookup"><span data-stu-id="2a52e-174">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="2a52e-175">Когда рассматриваемый **отслеживаемый объект** будет найден, загрузчик проверит, какие свойства доступны, и сообщит о них.</span><span class="sxs-lookup"><span data-stu-id="2a52e-175">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="2a52e-176">Адаптация бота</span><span class="sxs-lookup"><span data-stu-id="2a52e-176">Adapting the Bot</span></span>

<span data-ttu-id="2a52e-177">Триггерам **AskingForCount** и **FindEntity** необходимо взаимодействовать с серверной частью. Это означает, что необходимо добавить правильный URL-адрес **Функции Azure**, развернутой ранее.</span><span class="sxs-lookup"><span data-stu-id="2a52e-177">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="2a52e-178">На панели диалоговых окон щелкните **AskingForCount** и выберите действие *Send an HTTP request* (Отправить HTTP-запрос). Здесь можно увидеть поле **URL**, в которое необходимо ввести правильный URL-адрес конечной точки функции **Count**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-178">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="2a52e-180">Наконец, найдите триггер **FindEntity** и действие *Send an HTTP request* (Отправить HTTP-запрос). В поле **URL** замените URL-адрес конечной точкой функции **Count**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-180">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="2a52e-182">Теперь все готово к развертыванию бота.</span><span class="sxs-lookup"><span data-stu-id="2a52e-182">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="2a52e-183">Так как у вас установлена программа Bot Framework Composer, его можно опубликовать непосредственно из нее.</span><span class="sxs-lookup"><span data-stu-id="2a52e-183">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="2a52e-184">Дополнительные сведения о [публикации бота с помощью программы Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="2a52e-184">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="2a52e-185">Вы можете поэкспериментировать с ботом, добавив дополнительные триггерные фразы, новые ответы или ветвление диалога.</span><span class="sxs-lookup"><span data-stu-id="2a52e-185">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="2a52e-186">Часть 2. Размещение всех элементов в Unity</span><span class="sxs-lookup"><span data-stu-id="2a52e-186">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="2a52e-187">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="2a52e-187">Preparing the scene</span></span>

<span data-ttu-id="2a52e-188">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-188">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="2a52e-190">После этого переместите заготовку **ChatBotManager** в иерархию сцены.</span><span class="sxs-lookup"><span data-stu-id="2a52e-190">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="2a52e-191">Добавив ChatBotManager в сцену, щелкните компонент **Chat Bot Manager** (Диспетчер чат-ботов).</span><span class="sxs-lookup"><span data-stu-id="2a52e-191">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="2a52e-192">В окне Inspector (Инспектор) вы увидите, что имеется пустое поле **Direct Line Secret Key** (Секретный ключ прямой линии), которое необходимо заполнить.</span><span class="sxs-lookup"><span data-stu-id="2a52e-192">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="2a52e-193">Вы можете получить *секретный ключ* на портале Azure, выполнив поиск ресурса типа **регистрации каналов ботов**, созданного в первой части этого учебника.</span><span class="sxs-lookup"><span data-stu-id="2a52e-193">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="2a52e-195">Теперь вы подключите объект **ChatBotManager** с компонентом **ChatBotController**, присоединенным к объекту **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="2a52e-195">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="2a52e-196">В окне Hierarchy (Иерархия) выберите **ChatBotPanel**, и вы увидите пустое поле **Chat Bot Manager** (Диспетчер чат-ботов). Перетащите объект **ChatBotManager** в пустое поле **Chat Bot Manager** (Диспетчер чат-ботов).</span><span class="sxs-lookup"><span data-stu-id="2a52e-196">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="2a52e-198">Далее необходимо открыть объект **ChatBotPanel**, чтобы пользователь мог взаимодействовать с ним.</span><span class="sxs-lookup"><span data-stu-id="2a52e-198">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="2a52e-199">В окне Scene (Сцена) вы могли заметить, что в объекте **MainMenu** есть кнопка *Chat Bot* (Чат-бот), которая будет использоваться для решения этой проблемы.</span><span class="sxs-lookup"><span data-stu-id="2a52e-199">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="2a52e-200">В окне Hierarchy (Иерархия) откройте папку **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** и найдите в окне Inspector (Инспектор) скрипт *ButtonConfigHelper*.</span><span class="sxs-lookup"><span data-stu-id="2a52e-200">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="2a52e-201">Там вы увидите пустой слот в функции обратного вызова события **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="2a52e-201">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="2a52e-202">Перетащите **ChatBotPanel** в область событий, из раскрывающегося списка выберите *GameObject*, а затем в подменю выберите *SetActive (bool)* (SetActive (логическое)) и установите флажок.</span><span class="sxs-lookup"><span data-stu-id="2a52e-202">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="2a52e-204">Теперь чат-бот можно запустить из главного меню, а сцена готова к использованию.</span><span class="sxs-lookup"><span data-stu-id="2a52e-204">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="2a52e-205">Тестирование чат-бота</span><span class="sxs-lookup"><span data-stu-id="2a52e-205">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="2a52e-206">Запрос количества отслеживаемых объектов</span><span class="sxs-lookup"><span data-stu-id="2a52e-206">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="2a52e-207">Сначала вы проверите, сколько **отслеживаемых объектов** хранится в базе данных.</span><span class="sxs-lookup"><span data-stu-id="2a52e-207">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="2a52e-208">На этот раз необходимо запустить приложение из HoloLens 2, так как такие службы, как *преобразование текста в речь*, могут быть недоступны в вашей системе.</span><span class="sxs-lookup"><span data-stu-id="2a52e-208">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="2a52e-209">Запустите приложение в HoloLens 2 и нажмите кнопку *Chat Bot* (Чат-бот) рядом с главным меню.</span><span class="sxs-lookup"><span data-stu-id="2a52e-209">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="2a52e-210">Чат-бот поприветствует вас. Спросите, **сколько имеется объектов?**</span><span class="sxs-lookup"><span data-stu-id="2a52e-210">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="2a52e-211">Он должен сообщить их количество и завершить диалог.</span><span class="sxs-lookup"><span data-stu-id="2a52e-211">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="2a52e-212">Запрос отслеживаемого объекта</span><span class="sxs-lookup"><span data-stu-id="2a52e-212">Asking about a tracked object</span></span>

<span data-ttu-id="2a52e-213">Теперь запустите приложение еще раз и попросите **найти отслеживаемый объект**. Чат-бот запросит название, на которое следует ответить, например введите "автомобиль", или имя другого *отслеживаемого объекта*, который есть в базе данных.</span><span class="sxs-lookup"><span data-stu-id="2a52e-213">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="2a52e-214">Бот отобразит его описание и сведения о наличии пространственной привязки.</span><span class="sxs-lookup"><span data-stu-id="2a52e-214">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="2a52e-215">Попробуйте запросить **отслеживаемые объекты**, которые не существуют в базе, и посмотрите на ответ бота.</span><span class="sxs-lookup"><span data-stu-id="2a52e-215">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2a52e-216">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="2a52e-216">Congratulations</span></span>

<span data-ttu-id="2a52e-217">Из этого учебника вы узнали, как можно использовать платформу Azure Bot Framework для взаимодействия с приложением с помощью естественного языка.</span><span class="sxs-lookup"><span data-stu-id="2a52e-217">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="2a52e-218">Вы узнали, как разрабатывать собственные боты и как все они работают.</span><span class="sxs-lookup"><span data-stu-id="2a52e-218">You learned how to develope your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="2a52e-219">Заключение</span><span class="sxs-lookup"><span data-stu-id="2a52e-219">Conclusion</span></span>

<span data-ttu-id="2a52e-220">В рамках этой серии учебников вы узнали, как **облачные службы Azure** применяют новые интересные функции к вашему приложению.</span><span class="sxs-lookup"><span data-stu-id="2a52e-220">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="2a52e-221">Теперь вы можете хранить данные и изображения в облаке **хранилища Azure**, использовать **Пользовательское визуальное распознавание Azure** для связывания изображений и обучения модели, передавать объекты в локальный контекст с помощью **Пространственных привязок Azure** и реализовать **Azure Bot Framework на платформе LUIS**, чтобы добавить чат-бота в новый и естественный шаблон взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2a52e-221">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
