---
title: Учебники по службам речи Azure — 4. Настройка намерения и естественного понимания языка
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e712fc2fd66b1add5b16b7dd8e6c37551aefe43a
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003213"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="11f7d-105">4. Настройка намерения и естественного понимания языка</span><span class="sxs-lookup"><span data-stu-id="11f7d-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="11f7d-106">На этом занятии будет рассмотрена функция службы "речь" в Azure.</span><span class="sxs-lookup"><span data-stu-id="11f7d-106">In this lesson, you will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="11f7d-107">Функция с намерением позволяет создавать свои приложения с помощью голосовых команд на основе искусственного интеллекта, где пользователи могут говорить о неспецифических голосовых командах и по-прежнему иметь смысл, понятный системе.</span><span class="sxs-lookup"><span data-stu-id="11f7d-107">The Intent feature allows you to equip our application with AI-powered voice commands, where users can say non-specific voice commands and still have their intent understood by the system.</span></span> <span data-ttu-id="11f7d-108">На этом занятии мы создадим портал Azure LUIS Portal, настроили наши намерения, сущности и фразы продолжительностью, публикуем наш ресурс, подключим приложение Unity к нашему намеренному ресурсу и сделаем наш первый вызов API.</span><span class="sxs-lookup"><span data-stu-id="11f7d-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="11f7d-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="11f7d-109">Objectives</span></span>

- <span data-ttu-id="11f7d-110">Узнайте, как настроить намерение и естественное понимание языка в нашем приложении.</span><span class="sxs-lookup"><span data-stu-id="11f7d-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="11f7d-111">Узнайте, как настроить портал LUIS для Azure.</span><span class="sxs-lookup"><span data-stu-id="11f7d-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="11f7d-112">Узнайте, как настроить намерения, сущности и фразы продолжительностью в Azure.</span><span class="sxs-lookup"><span data-stu-id="11f7d-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="11f7d-113">Инструкция</span><span class="sxs-lookup"><span data-stu-id="11f7d-113">Instructions</span></span>

1. <span data-ttu-id="11f7d-114">Разрешить компьютеру Включить диктовку.</span><span class="sxs-lookup"><span data-stu-id="11f7d-114">Allow your machine to enable Dictation.</span></span> <span data-ttu-id="11f7d-115">Для этого перейдите в раздел "Параметры Windows", выберите "Конфиденциальность", "речь", а затем "Ввод рукописного ввода &" и включите речевые службы и введите рекомендации.</span><span class="sxs-lookup"><span data-stu-id="11f7d-115">To do this, go to Windows Settings, select "privacy," then "speech," followed by "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="11f7d-119">Войдите на [портал Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="11f7d-119">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="11f7d-120">Войдя в систему, щелкните Создать ресурс, выполните поиск по запросу "Language Understanding" и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="11f7d-120">Once you are logged in, click on Create a resource, search for "Language Understanding" and click Enter.</span></span>

    ![mrlearning-Speech-CH4-1-step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="11f7d-122">Нажмите кнопку **создать** , чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="11f7d-122">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="11f7d-124">Присвойте ресурсу **имя**, например " *речь-SDK-Learning-module*".</span><span class="sxs-lookup"><span data-stu-id="11f7d-124">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="11f7d-125">В качестве **подписки**выберите вариант *Оплата по мере* использования или *бесплатный* , если у вас есть пробная учетная запись.</span><span class="sxs-lookup"><span data-stu-id="11f7d-125">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="11f7d-126">Затем создайте новую **группу ресурсов** , щелкнув ссылку **создать** , введите имя, например *HoloLens-2-Tutorial-Resource-Group*и нажмите кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="11f7d-126">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and click the **OK** button.</span></span>

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="11f7d-128">Выберите **расположение для разработки** и **расположение среды выполнения**.</span><span class="sxs-lookup"><span data-stu-id="11f7d-128">Select your **Authoring location** and **Runtime location**.</span></span> <span data-ttu-id="11f7d-129">Для целей этого учебника используйте *(US) Западная часть США*, а затем выберите *F0 (5 вызовов в секунду, 10000 вызовов в месяц)* для ценовой категории " **Разработка** " и **ценовой категории времени выполнения**.</span><span class="sxs-lookup"><span data-stu-id="11f7d-129">For the purpose of this tutorial, use *(US) West US*, then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="11f7d-130">Наконец, нажмите кнопку **создать** , чтобы создать ресурс, а также новую группу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="11f7d-130">Finally, click the **Create** button to create the resource, as well as the new resource group.</span></span>

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="11f7d-132">После нажатия кнопки Создать необходимо подождать, пока не будет создана служба, что может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="11f7d-132">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

5. <span data-ttu-id="11f7d-133">После завершения создания ресурса вы увидите сообщение о том, что **Развертывание завершено**.</span><span class="sxs-lookup"><span data-stu-id="11f7d-133">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-Speech-CH4-1-step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="11f7d-135">Используя ту же учетную запись пользователя, войдите на портал [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) , выберите свою страну и примите условия использования.</span><span class="sxs-lookup"><span data-stu-id="11f7d-135">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="11f7d-136">При достижении Language Understanding портала вам может потребоваться войти в систему, если вы еще не сделали это с теми же учетными данными, что и у портал Azure.</span><span class="sxs-lookup"><span data-stu-id="11f7d-136">Upon reaching the Language Understanding portal, you may need to log in, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="11f7d-137">Если вы впервые используете LUIS, необходимо прокрутить вниз до нижней части страницы приветствия, чтобы найти и нажать кнопку "создать LUIS" приложения.</span><span class="sxs-lookup"><span data-stu-id="11f7d-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the Welcome page to find and click the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="11f7d-138">После входа в систему щелкните Мои приложения (если вы еще не находясь в этом разделе).</span><span class="sxs-lookup"><span data-stu-id="11f7d-138">Once logged in, click My Apps (if you are not currently in that section).</span></span> <span data-ttu-id="11f7d-139">Затем можно щелкнуть создать новое приложение.</span><span class="sxs-lookup"><span data-stu-id="11f7d-139">You can then click on Create new app.</span></span> <span data-ttu-id="11f7d-140">Назовите новое приложение "модуль Learning SDK для речевых приложений".</span><span class="sxs-lookup"><span data-stu-id="11f7d-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="11f7d-141">Добавьте также "модуль обучения речевого SDK" в поле описания.</span><span class="sxs-lookup"><span data-stu-id="11f7d-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="11f7d-142">Затем нажмите кнопку "Готово".</span><span class="sxs-lookup"><span data-stu-id="11f7d-142">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="11f7d-145">Если ваше приложение должно понимать язык, отличающийся от английского, следует изменить язык и региональные параметры на соответствующий.</span><span class="sxs-lookup"><span data-stu-id="11f7d-145">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="11f7d-146">Щелкните "сборка", расположенную в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="11f7d-146">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="11f7d-147">В разделе "активы приложения" слева выберите "цели", затем щелкните "создать цель" и назовите его "Прессбуттон".</span><span class="sxs-lookup"><span data-stu-id="11f7d-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="11f7d-149">Важно использовать имена целей и сущностей, используемых в этом руководстве, так как приложение Лунарком будет ссылаться на них по имени.</span><span class="sxs-lookup"><span data-stu-id="11f7d-149">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="11f7d-150">Теперь у вас должно быть два варианта: "Прессбуттон" и "нет".</span><span class="sxs-lookup"><span data-stu-id="11f7d-150">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="11f7d-151">В разделе активы приложения слева выберите "сущности", щелкните "создать новую сущность", присвойте ей имя "Action" и укажите для типа сущности "Simple".</span><span class="sxs-lookup"><span data-stu-id="11f7d-151">Under App Assets on the left, select “Entities”, click “Create New Entity”, name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="11f7d-153">Снова нажмите кнопку "создать сущность" и назовите ее "цель".</span><span class="sxs-lookup"><span data-stu-id="11f7d-153">Click “Create New Entity” again and name it “Target”.</span></span> <span data-ttu-id="11f7d-154">Для типа сущности также следует использовать "простой".</span><span class="sxs-lookup"><span data-stu-id="11f7d-154">Keep the Entity Type as “Simple”, as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="11f7d-156">В разделе активы приложения слева выберите "цели", а затем нажмите кнопку "Прессбуттон", созданную на шаге 10.</span><span class="sxs-lookup"><span data-stu-id="11f7d-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="11f7d-158">Щелкните раскрывающийся список "Просмотр параметров" справа и выберите "Показать значения сущностей".</span><span class="sxs-lookup"><span data-stu-id="11f7d-158">Click the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="11f7d-160">Щелкните "введите пример...".</span><span class="sxs-lookup"><span data-stu-id="11f7d-160">Click the “Enter an example…”</span></span> <span data-ttu-id="11f7d-161">.</span><span class="sxs-lookup"><span data-stu-id="11f7d-161">textbox.</span></span> <span data-ttu-id="11f7d-162">Затем введите следующую фразы продолжительностью:</span><span class="sxs-lookup"><span data-stu-id="11f7d-162">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="11f7d-164">Щелкните раскрывающийся список "Просмотр параметров" справа и выберите "Показать имена сущностей".</span><span class="sxs-lookup"><span data-stu-id="11f7d-164">Click the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="11f7d-166">Убедитесь, что каждый из 10 фразы продолжительностью имеет следующие метки сущностей в следующих местах на 1.) Если щелкнуть слова, которые помечены как неподписанные, и во всплывающем окне выбрать пункт "удалить метку" и 2.) Щелкните слова, которые должны быть помечены, и во всплывающем окне выберите соответствующую метку.</span><span class="sxs-lookup"><span data-stu-id="11f7d-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="11f7d-168">Теперь, чтобы опубликовать модель, щелкните "обучение" в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="11f7d-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="11f7d-169">После завершения обработки нажмите кнопку "тест" в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="11f7d-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="11f7d-171">Введите в текстовом поле "нажмите кнопку запуска".</span><span class="sxs-lookup"><span data-stu-id="11f7d-171">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="11f7d-172">Мы не добавили "Select" в качестве действия в любой из наших фразы продолжительностью, но если щелкнуть "проверить", модель распознала "Select" как сущность действия.</span><span class="sxs-lookup"><span data-stu-id="11f7d-172">We did not add “select” as an action in any of our Utterances, but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="11f7d-174">Щелкните Publish (опубликовать) в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="11f7d-174">Click "publish" in the top right.</span></span> <span data-ttu-id="11f7d-175">Убедитесь, что в раскрывающемся списке указано «Production», и щелкните «Publish» (опубликовать) в всплывающем окне.</span><span class="sxs-lookup"><span data-stu-id="11f7d-175">Ensure the dropdown says “Production” and click "publish" on the popup, as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="11f7d-177">После публикации в верхней части страницы должен появиться зеленый отрезок.</span><span class="sxs-lookup"><span data-stu-id="11f7d-177">Once published, a green bar should appear at the top of the page.</span></span> <span data-ttu-id="11f7d-178">Щелкните зеленую панель, чтобы просмотреть страницу "Управление".</span><span class="sxs-lookup"><span data-stu-id="11f7d-178">Click the green bar to view the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="11f7d-180">Щелкните "ключи и конечные точки" в разделе "Параметры приложения" слева.</span><span class="sxs-lookup"><span data-stu-id="11f7d-180">Click "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="11f7d-181">Затем установите в раскрывающемся списке "опубликовать в" значение "Рабочая".</span><span class="sxs-lookup"><span data-stu-id="11f7d-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="11f7d-182">Укажите, что часовой пояс должен соответствовать вашим данным, и установите флажок, чтобы включить все оценки предполагаемого намерения.</span><span class="sxs-lookup"><span data-stu-id="11f7d-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="11f7d-183">Наконец, щелкните "назначить ресурс".</span><span class="sxs-lookup"><span data-stu-id="11f7d-183">Lastly, click "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="11f7d-185">Выберите клиент в первом раскрывающемся списке и в раскрывающемся списке имя подписки выберите "Оплата по мере использования".</span><span class="sxs-lookup"><span data-stu-id="11f7d-185">Select tenant from the first dropdown and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="11f7d-186">В разделе Имя ресурса LUIS выберите ресурс, созданный ранее в шагах 1-5.</span><span class="sxs-lookup"><span data-stu-id="11f7d-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="11f7d-187">Затем щелкните "назначить ресурс".</span><span class="sxs-lookup"><span data-stu-id="11f7d-187">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="11f7d-189">Обязательно скопируйте и сохраните URL-адрес конечной точки, связанный с назначенным ресурсом, чтобы он был легко доступен для следующего раздела.</span><span class="sxs-lookup"><span data-stu-id="11f7d-189">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="11f7d-190">В качестве имени клиента добавьте свою организацию или профиль, созданный для этого приложения.</span><span class="sxs-lookup"><span data-stu-id="11f7d-190">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="11f7d-191">Теперь откройте новое приложение в Unity и выберите объект Lunarcom_Base в иерархии.</span><span class="sxs-lookup"><span data-stu-id="11f7d-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="11f7d-192">Щелкните "добавить компонент" на панели инспектора и найдите и выберите "Лунаркоминтентрекогнизер".</span><span class="sxs-lookup"><span data-stu-id="11f7d-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="11f7d-194">В поле Конечная точка Luis в "Лунаркоминтентрекогнизер" на панели инспектора введите URL-адрес конечной точки, сохраненной на шаге 22.</span><span class="sxs-lookup"><span data-stu-id="11f7d-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="11f7d-196">В компоненте "Лунаркомоффлинерекогнизер" на панели инспектора убедитесь, что для "Симулатеоффлинемоде" выбрано значение "отключить", а проверка программы не будет работать.</span><span class="sxs-lookup"><span data-stu-id="11f7d-196">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="11f7d-197">Нажмите кнопку Воспроизведение в редакторе Unity и нажмите кнопку Rocket, чтобы начать распознавание намерения.</span><span class="sxs-lookup"><span data-stu-id="11f7d-197">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="11f7d-198">Полное фразу "нажмите кнопку запуска Rocket".</span><span class="sxs-lookup"><span data-stu-id="11f7d-198">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="11f7d-199">Приложение распознал нужную функцию и активировало кнопку Rocket.</span><span class="sxs-lookup"><span data-stu-id="11f7d-199">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="11f7d-201">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="11f7d-201">Congratulations</span></span>

<span data-ttu-id="11f7d-202">На этом занятии вы узнали, как добавлять голосовые команды на основе AI.</span><span class="sxs-lookup"><span data-stu-id="11f7d-202">In this lesson, you learned how to add AI-powered speech commands.</span></span> <span data-ttu-id="11f7d-203">Теперь ваша программа может распознать намерение пользователей, даже если они не полное точные команды Voice.</span><span class="sxs-lookup"><span data-stu-id="11f7d-203">Now your program can recognize users' intent, even if they do not utter precise voice commands!</span></span>
