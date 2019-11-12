---
title: Учебники по службам речи Azure — 4. Настройка намерения и естественного понимания языка
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 9235452d9dce38e9d849821a694a5d4c710d8e87
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913321"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="2910e-105">4. Настройка намерения и естественного понимания языка</span><span class="sxs-lookup"><span data-stu-id="2910e-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="2910e-106">На этом занятии мы рассмотрим функцию службы "речь" в Azure.</span><span class="sxs-lookup"><span data-stu-id="2910e-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="2910e-107">Функция с намерением позволяет нам составить свое приложение с помощью голосовых команд на основе искусственного интеллекта, где пользователи могут говорить о неспециальных голосовых командах и по-прежнему иметь смысл, понятный системе.</span><span class="sxs-lookup"><span data-stu-id="2910e-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="2910e-108">На этом занятии мы создадим портал Azure LUIS Portal, настроили наши намерения, сущности и фразы продолжительностью, публикуем наш ресурс, подключим приложение Unity к нашему намеренному ресурсу и сделаем наш первый вызов API.</span><span class="sxs-lookup"><span data-stu-id="2910e-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="2910e-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="2910e-109">Objectives</span></span>

- <span data-ttu-id="2910e-110">Узнайте, как настроить намерение и естественное понимание языка в нашем приложении.</span><span class="sxs-lookup"><span data-stu-id="2910e-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="2910e-111">Узнайте, как настроить портал LUIS для Azure.</span><span class="sxs-lookup"><span data-stu-id="2910e-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="2910e-112">Узнайте, как настроить намерения, сущности и фразы продолжительностью в Azure.</span><span class="sxs-lookup"><span data-stu-id="2910e-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="2910e-113">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2910e-113">Instructions</span></span>

1. <span data-ttu-id="2910e-114">Разрешить компьютеру Включить диктовку. для этого перейдите в раздел "Параметры Windows", выберите "Конфиденциальность", "речь", а затем "Ввод рукописного ввода &" и включите речевые службы и введите рекомендации.</span><span class="sxs-lookup"><span data-stu-id="2910e-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="2910e-118">Войдите на [портал Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="2910e-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="2910e-119">Войдя в систему, щелкните Создать ресурс и выполните поиск по запросу «Language Understanding» и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="2910e-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

    ![mrlearning-Speech-CH4-1-step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="2910e-121">Нажмите кнопку **создать** , чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="2910e-121">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="2910e-123">Присвойте ресурсу **имя**, например " *речь-SDK-Learning-module*".</span><span class="sxs-lookup"><span data-stu-id="2910e-123">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="2910e-124">В качестве **подписки**выберите вариант *Оплата по мере* использования или *бесплатный* , если у вас есть пробная учетная запись.</span><span class="sxs-lookup"><span data-stu-id="2910e-124">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="2910e-125">Затем создайте новую **группу ресурсов** , щелкнув ссылку **создать** , введите имя, например *HoloLens-2-Tutorial-Resource-Group*, и нажмите кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="2910e-125">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and clicking the **OK** button.</span></span>

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="2910e-127">Выберите **расположение для создания** и **расположение среды выполнения**. в рамках этого руководства используйте *(US) Западная часть США*.</span><span class="sxs-lookup"><span data-stu-id="2910e-127">Select your **Authoring location** and **Runtime location**, for the purpose of this tutorial, use *(US) West US*.</span></span> <span data-ttu-id="2910e-128">Затем выберите *F0 (5 вызовов в секунду, 10000 вызовов в месяц)* для ценовой категории " **Разработка** " и **ценовой категории времени выполнения**.</span><span class="sxs-lookup"><span data-stu-id="2910e-128">Then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="2910e-129">Наконец, нажмите кнопку " **создать** ", чтобы создать ресурс, а также новую группу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="2910e-129">Finally, click the **Create** button to create the resource as well as the new resource group.</span></span>

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="2910e-131">После нажатия кнопки Создать необходимо подождать, пока не будет создана служба. это может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="2910e-131">After you click the Create button you will have to wait for the service to be created, this might take a few minute.</span></span>

5. <span data-ttu-id="2910e-132">После завершения создания ресурса вы увидите сообщение о том, что **Развертывание завершено**.</span><span class="sxs-lookup"><span data-stu-id="2910e-132">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-Speech-CH4-1-step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="2910e-134">Используя ту же учетную запись пользователя, войдите на портал [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) , выберите свою страну и примите условия использования.</span><span class="sxs-lookup"><span data-stu-id="2910e-134">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2910e-135">При достижении Language Understanding портала вам может потребоваться выполнить вход, если вы еще не сделали этого, с теми же учетными данными, что и у портал Azure.</span><span class="sxs-lookup"><span data-stu-id="2910e-135">Upon reaching the Language Understanding portal, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="2910e-136">Если вы впервые используете LUIS, необходимо прокрутить вниз до нижней части страницы приветствия, чтобы найти и нажать кнопку "создать LUIS" приложения.</span><span class="sxs-lookup"><span data-stu-id="2910e-136">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="2910e-137">После входа в систему щелкните Мои приложения (если вы не в этом разделе сейчас).</span><span class="sxs-lookup"><span data-stu-id="2910e-137">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="2910e-138">Затем можно щелкнуть создать новое приложение.</span><span class="sxs-lookup"><span data-stu-id="2910e-138">You can then click on Create new app.</span></span> <span data-ttu-id="2910e-139">Назовите новое приложение "модуль Learning SDK для речевых приложений".</span><span class="sxs-lookup"><span data-stu-id="2910e-139">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="2910e-140">Добавьте также "модуль обучения речевого SDK" в поле описания.</span><span class="sxs-lookup"><span data-stu-id="2910e-140">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="2910e-141">Затем нажмите кнопку "Готово".</span><span class="sxs-lookup"><span data-stu-id="2910e-141">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="2910e-144">Если ваше приложение должно понимать язык, отличающийся от английского, следует изменить язык и региональные параметры на соответствующий.</span><span class="sxs-lookup"><span data-stu-id="2910e-144">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="2910e-145">Щелкните "сборка", расположенную в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="2910e-145">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="2910e-146">В разделе "активы приложения" слева выберите "цели", затем щелкните "создать цель" и назовите его "Прессбуттон".</span><span class="sxs-lookup"><span data-stu-id="2910e-146">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="2910e-148">Важно использовать имена целей и сущностей, используемых в этом руководстве, так как приложение Лунарком будет ссылаться на них по имени.</span><span class="sxs-lookup"><span data-stu-id="2910e-148">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2910e-149">Теперь у вас должно быть два варианта: "Прессбуттон" и "нет".</span><span class="sxs-lookup"><span data-stu-id="2910e-149">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="2910e-150">В разделе активы приложения слева выберите "сущности" и щелкните "создать новую сущность" и присвойте ему имя "Action", а для типа сущности — "Simple".</span><span class="sxs-lookup"><span data-stu-id="2910e-150">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="2910e-152">Снова нажмите кнопку "создать сущность" и присвойте ему имя "Target", а также укажите для типа сущности значение "Simple".</span><span class="sxs-lookup"><span data-stu-id="2910e-152">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="2910e-154">В разделе активы приложения слева выберите "цели", а затем нажмите кнопку "Прессбуттон", созданную на шаге 10.</span><span class="sxs-lookup"><span data-stu-id="2910e-154">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="2910e-156">Щелкните раскрывающийся список "Просмотр параметров" справа и выберите "Показать значения сущностей".</span><span class="sxs-lookup"><span data-stu-id="2910e-156">Click on the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="2910e-158">Щелкните "введите пример...".</span><span class="sxs-lookup"><span data-stu-id="2910e-158">Click on the “Enter an example…”</span></span> <span data-ttu-id="2910e-159">текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="2910e-159">textbox.</span></span> <span data-ttu-id="2910e-160">Затем введите следующую фразы продолжительностью:</span><span class="sxs-lookup"><span data-stu-id="2910e-160">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="2910e-162">Щелкните раскрывающийся список "Просмотр параметров" справа и выберите "Показать имена сущностей".</span><span class="sxs-lookup"><span data-stu-id="2910e-162">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="2910e-164">Убедитесь, что каждый из 10 фразы продолжительностью имеет следующие метки сущностей в следующих местах на 1.) Если щелкнуть слова, которые помечены как неподписанные, и во всплывающем окне выбрать пункт "удалить метку" и 2.) Щелкните слова, которые должны быть помечены, и во всплывающем окне выберите соответствующую метку.</span><span class="sxs-lookup"><span data-stu-id="2910e-164">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="2910e-166">Теперь, чтобы опубликовать модель, щелкните "обучение" в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="2910e-166">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="2910e-167">После завершения обработки нажмите кнопку "тест" в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="2910e-167">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="2910e-169">Введите в текстовом поле "нажмите кнопку запуска".</span><span class="sxs-lookup"><span data-stu-id="2910e-169">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2910e-170">Мы не добавили "Select" в качестве действия в какой-либо из наших фразы продолжительностью, но если щелкнуть "проверить", модель распознала "Select" как сущность действия.</span><span class="sxs-lookup"><span data-stu-id="2910e-170">We did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="2910e-172">Теперь щелкните Publish (опубликовать) в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="2910e-172">Now, click "publish" in the top right.</span></span> <span data-ttu-id="2910e-173">Убедитесь, что в раскрывающемся списке указано «Production», и щелкните «Publish» (опубликовать) на всплывающем окне.</span><span class="sxs-lookup"><span data-stu-id="2910e-173">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="2910e-175">После публикации в верхней части страницы должен появиться зеленый отрезок.</span><span class="sxs-lookup"><span data-stu-id="2910e-175">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="2910e-176">Щелкните зеленую панель, чтобы выполнить переход на страницу "Управление".</span><span class="sxs-lookup"><span data-stu-id="2910e-176">Click on the green bar to be taken to the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="2910e-178">Щелкните "ключи и конечные точки" в разделе "Параметры приложения" слева.</span><span class="sxs-lookup"><span data-stu-id="2910e-178">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="2910e-179">Затем установите в раскрывающемся списке "опубликовать в" значение "Рабочая".</span><span class="sxs-lookup"><span data-stu-id="2910e-179">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="2910e-180">Укажите, что часовой пояс должен соответствовать вашим данным, и установите флажок, чтобы включить все оценки предполагаемого намерения.</span><span class="sxs-lookup"><span data-stu-id="2910e-180">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="2910e-181">Наконец, щелкните "назначить ресурс".</span><span class="sxs-lookup"><span data-stu-id="2910e-181">Lastly, Click on "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="2910e-183">Выберите клиент в первом раскрывающемся списке и в раскрывающемся списке имя подписки выберите "Оплата по мере использования".</span><span class="sxs-lookup"><span data-stu-id="2910e-183">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="2910e-184">В разделе Имя ресурса LUIS выберите ресурс, созданный ранее в шагах 1-5.</span><span class="sxs-lookup"><span data-stu-id="2910e-184">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="2910e-185">Затем щелкните "назначить ресурс".</span><span class="sxs-lookup"><span data-stu-id="2910e-185">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="2910e-187">Обязательно скопируйте и сохраните URL-адрес конечной точки, связанный с назначенным ресурсом, чтобы он был легко доступен для следующего раздела.</span><span class="sxs-lookup"><span data-stu-id="2910e-187">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2910e-188">В качестве имени клиента добавьте свою организацию или профиль, созданный для этого приложения.</span><span class="sxs-lookup"><span data-stu-id="2910e-188">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="2910e-189">Теперь откройте новое приложение в Unity и выберите объект Lunarcom_Base в иерархии.</span><span class="sxs-lookup"><span data-stu-id="2910e-189">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="2910e-190">Щелкните "добавить компонент" на панели инспектора и найдите и выберите "Лунаркоминтентрекогнизер".</span><span class="sxs-lookup"><span data-stu-id="2910e-190">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="2910e-192">В поле Конечная точка Luis в "Лунаркоминтентрекогнизер" на панели инспектора введите URL-адрес конечной точки, сохраненной на шаге 22.</span><span class="sxs-lookup"><span data-stu-id="2910e-192">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="2910e-194">В компоненте "Лунаркомоффлинерекогнизер" на панели инспектора убедитесь, что для "Симулатеоффлинемоде" выбрано значение "отключить", а проверка программы не будет работать.</span><span class="sxs-lookup"><span data-stu-id="2910e-194">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="2910e-195">Нажмите кнопку Воспроизведение в редакторе Unity и нажмите кнопку Rocket, чтобы начать распознавание намерения.</span><span class="sxs-lookup"><span data-stu-id="2910e-195">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="2910e-196">Полное фразу "нажмите кнопку запуска Rocket".</span><span class="sxs-lookup"><span data-stu-id="2910e-196">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="2910e-197">Приложение распознал нужную функцию и активировало кнопку Rocket.</span><span class="sxs-lookup"><span data-stu-id="2910e-197">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="2910e-199">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="2910e-199">Congratulations</span></span>

<span data-ttu-id="2910e-200">На этом занятии мы узнали, как добавлять голосовые команды на основе AI!</span><span class="sxs-lookup"><span data-stu-id="2910e-200">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="2910e-201">Теперь программа может распознать намерение пользователей, даже если они не полное точные команды Voice.</span><span class="sxs-lookup"><span data-stu-id="2910e-201">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>
