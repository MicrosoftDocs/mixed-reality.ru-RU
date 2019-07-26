---
title: Модуль Спичсдк с MR Learning — распознавание речи и транскрипция
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485780"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="ee8d7-104">4. Настройка намерения и естественного понимания языка</span><span class="sxs-lookup"><span data-stu-id="ee8d7-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="ee8d7-105">На этом занятии мы рассмотрим функцию службы "речь" в Azure.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-105">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="ee8d7-106">Функция с намерением позволяет нам составить свое приложение с помощью голосовых команд на основе искусственного интеллекта, где пользователи могут говорить о неспециальных голосовых командах и по-прежнему иметь смысл, понятный системе.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-106">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="ee8d7-107">На этом занятии мы создадим портал Azure LUIS Portal, настроили наши намерения, сущности и фразы продолжительностью, публикуем наш ресурс, подключим приложение Unity к нашему намеренному ресурсу и сделаем наш первый вызов API.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-107">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="ee8d7-108">Цели</span><span class="sxs-lookup"><span data-stu-id="ee8d7-108">Objectives</span></span>

- <span data-ttu-id="ee8d7-109">Узнайте, как настроить намерение и естественное понимание языка в нашем приложении.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-109">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="ee8d7-110">Узнайте, как настроить портал LUIS для Azure.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-110">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="ee8d7-111">Узнайте, как настроить намерения, сущности и фразы продолжительностью в Azure.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-111">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="ee8d7-112">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ee8d7-112">Instructions</span></span>
1. <span data-ttu-id="ee8d7-113">Разрешить компьютеру Включить диктовку. для этого перейдите в раздел "Параметры Windows", выберите "Конфиденциальность", "речь", а затем "Ввод рукописного ввода &" и включите речевые службы и введите рекомендации.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-113">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="ee8d7-117">Войдите на [портал Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="ee8d7-117">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="ee8d7-118">Войдя в систему, щелкните Создать ресурс и выполните поиск по запросу «Language Understanding» и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-118">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="ee8d7-120">Нажмите кнопку Создать, чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-120">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="ee8d7-121">Присвойте проекту имя "Speech_SDK_Learning_Module" и выберите "Оплата по мере использования".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-121">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="ee8d7-124">Выберите свой регион.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-124">Select your Region.</span></span>  <span data-ttu-id="ee8d7-125">Для целей данного учебника выберите "(US) Западная часть США".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-125">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="ee8d7-126">Затем выберите "F0" для ценовой категории.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-126">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="ee8d7-127">Теперь щелкните "создать" (находится в левом нижнем углу), чтобы создать ресурс.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-127">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="ee8d7-128">Примечание. После того, как вы щелкнули "создать", вам придется подождать, пока будет создана служба, что может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-128">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="ee8d7-129">После создания ресурса на портале появится уведомление.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-129">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="ee8d7-130">Щелкните это уведомление и выберите "переход к ресурсу".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-130">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="ee8d7-131">На странице "Быстрое начало" службы "API LUIS" перейдите к первому шагу, возьмите "ключи" и щелкните "ключи" (это можно также сделать, щелкнув синюю ссылку "ключи", показанную на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="ee8d7-131">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="ee8d7-132">Будет отображена служба "ключи".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-132">This will reveal your service, "Keys."</span></span> <span data-ttu-id="ee8d7-133">Сохраните копию одного из ключей, чтобы ее можно было использовать позже в приложении.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-133">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="ee8d7-135">Вернитесь на страницу "Быстрое начало" в разделе 2b, щелкните "Language Understanding портал" (показанный на рисунке выше), чтобы перенаправить на веб-страницу, которая будет использоваться для создания новой службы в приложении LUIS.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-135">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="ee8d7-136">Примечание. При обращении к «Language Understanding порталу» может потребоваться выполнить вход, если вы еще не сделали этого, с теми же учетными данными, что и у портал Azure.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-136">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="ee8d7-137">Если вы впервые используете LUIS, необходимо прокрутить вниз до нижней части страницы приветствия, чтобы найти и нажать кнопку "создать LUIS" приложения.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="ee8d7-138">После входа в систему щелкните Мои приложения (если вы не в этом разделе сейчас).</span><span class="sxs-lookup"><span data-stu-id="ee8d7-138">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="ee8d7-139">Затем можно щелкнуть создать новое приложение.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-139">You can then click on Create new app.</span></span> <span data-ttu-id="ee8d7-140">Назовите новое приложение "модуль Learning SDK для речевых приложений".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="ee8d7-141">Добавьте также "модуль обучения речевого SDK" в поле описания.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="ee8d7-142">Затем нажмите кнопку "Готово".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-142">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="ee8d7-145">метим Если ваше приложение должно понимать язык, отличающийся от английского, следует изменить язык и региональные параметры на соответствующий.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-145">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="ee8d7-146">Щелкните "сборка", расположенную в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-146">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="ee8d7-147">В разделе "активы приложения" слева выберите "цели", затем щелкните "создать цель" и назовите его "Прессбуттон".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="ee8d7-149">Примечание. Важно использовать имена целей и сущностей, используемых в этом руководстве, так как приложение Лунарком будет ссылаться на них по имени.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-149">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="ee8d7-150">Примечание. Теперь у вас должно быть два варианта: "Прессбуттон" и "нет".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-150">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="ee8d7-151">В разделе активы приложения слева выберите "сущности" и щелкните "создать новую сущность" и присвойте ему имя "Action", а для типа сущности — "Simple".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-151">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="ee8d7-153">Снова нажмите кнопку "создать сущность" и присвойте ему имя "Target", а также укажите для типа сущности значение "Simple".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-153">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="ee8d7-155">В разделе активы приложения слева выберите "цели", а затем нажмите кнопку "Прессбуттон", созданную на шаге 10.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-155">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="ee8d7-157">Щелкните раскрывающийся список "Просмотр параметров" справа и выберите "Показать значения сущностей".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-157">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="ee8d7-159">Щелкните "введите пример...".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-159">Click on the “Enter an example…”</span></span> <span data-ttu-id="ee8d7-160">текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-160">textbox.</span></span> <span data-ttu-id="ee8d7-161">Затем введите следующую фразы продолжительностью:</span><span class="sxs-lookup"><span data-stu-id="ee8d7-161">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="ee8d7-163">Щелкните раскрывающийся список "Просмотр параметров" справа и выберите "Показать имена сущностей".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-163">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="ee8d7-165">Убедитесь, что каждый из 10 фразы продолжительностью имеет следующие метки сущностей в следующих местах на 1.) Если щелкнуть слова, которые помечены как неподписанные, и во всплывающем окне выбрать пункт "удалить метку" и 2.) Щелкните слова, которые должны быть помечены, и во всплывающем окне выберите соответствующую метку.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-165">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="ee8d7-167">Теперь, чтобы опубликовать модель, щелкните "обучение" в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-167">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="ee8d7-168">После завершения обработки нажмите кнопку "тест" в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-168">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="ee8d7-170">Введите в текстовом поле "нажмите кнопку запуска".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-170">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="ee8d7-171">Примечание. Мы не добавили "Select" в качестве действия в какой-либо из наших фразы продолжительностью, но если щелкнуть "проверить", модель распознала "Select" как сущность действия.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-171">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="ee8d7-173">Теперь щелкните Publish (опубликовать) в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-173">Now, click "publish" in the top right.</span></span> <span data-ttu-id="ee8d7-174">Убедитесь, что в раскрывающемся списке указано «Production», и щелкните «Publish» (опубликовать) на всплывающем окне.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-174">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="ee8d7-176">После публикации в верхней части страницы должен появиться зеленый отрезок.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-176">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="ee8d7-177">Щелкните зеленую панель, чтобы выполнить переход на страницу "Управление".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-177">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="ee8d7-179">Щелкните "ключи и конечные точки" в разделе "Параметры приложения" слева.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-179">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="ee8d7-180">Затем установите в раскрывающемся списке "опубликовать в" значение "Рабочая".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-180">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="ee8d7-181">Укажите, что часовой пояс должен соответствовать вашим данным, и установите флажок, чтобы включить все оценки предполагаемого намерения.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-181">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="ee8d7-182">Наконец, щелкните "назначить ресурс".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-182">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="ee8d7-184">Выберите клиент в первом раскрывающемся списке и в раскрывающемся списке имя подписки выберите "Оплата по мере использования".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-184">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="ee8d7-185">В разделе Имя ресурса LUIS выберите ресурс, созданный ранее в шагах 1-5.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-185">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="ee8d7-186">Затем щелкните "назначить ресурс".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-186">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="ee8d7-188">Примечание. Обязательно скопируйте и сохраните URL-адрес конечной точки, связанный с назначенным ресурсом, чтобы он был легко доступен для следующего раздела.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-188">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="ee8d7-189">Примечание. В качестве имени клиента добавьте свою организацию или профиль, созданный для этого приложения.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-189">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="ee8d7-190">Теперь откройте новое приложение в Unity и выберите объект Lunarcom_Base в иерархии.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-190">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="ee8d7-191">Щелкните "добавить компонент" на панели инспектора и найдите и выберите "Лунаркоминтентрекогнизер".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-191">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="ee8d7-193">В поле Конечная точка Luis в "Лунаркоминтентрекогнизер" на панели инспектора введите URL-адрес конечной точки, сохраненной на шаге 22.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-193">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="ee8d7-195">Примечание. В компоненте "Лунаркомоффлинерекогнизер" на панели инспектора убедитесь, что для "Симулатеоффлинемоде" выбрано значение "отключить", а проверка программы не будет работать.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-195">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="ee8d7-196">Нажмите кнопку Воспроизведение в редакторе Unity и нажмите кнопку Rocket, чтобы начать распознавание намерения.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-196">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="ee8d7-197">Полное фразу "нажмите кнопку запуска Rocket".</span><span class="sxs-lookup"><span data-stu-id="ee8d7-197">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="ee8d7-198">Примечание. Приложение распознал нужную функцию и активировало кнопку Rocket.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-198">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="ee8d7-200">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="ee8d7-200">Congratulations</span></span>

<span data-ttu-id="ee8d7-201">На этом занятии мы узнали, как добавлять голосовые команды на основе AI!</span><span class="sxs-lookup"><span data-stu-id="ee8d7-201">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="ee8d7-202">Теперь программа может распознать намерение пользователей, даже если они не полное точные команды Voice.</span><span class="sxs-lookup"><span data-stu-id="ee8d7-202">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

