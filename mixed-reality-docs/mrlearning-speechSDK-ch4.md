## <a name="lesson-4"></a><span data-ttu-id="35be7-101">Занятие 4</span><span class="sxs-lookup"><span data-stu-id="35be7-101">Lesson 4</span></span>

<span data-ttu-id="35be7-102">В главе 4 мы рассмотрим функцию намерений службы распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="35be7-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="35be7-103">Мы будет Настройка нашего LUIS портала Azure, Настройка наши намерения и сущности/фразы, публикация нашего намерения ресурса, соединиться нашего ресурса намерением наше приложение Unity и сделать наш первый вызов API намерение.</span><span class="sxs-lookup"><span data-stu-id="35be7-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="35be7-104">Разрешение компьютер включить режим диктовки сделать это, перейдите к параметрам Windows, выберите «конфиденциальность», а затем «речь» и наконец «рукописный ввод & введя» и включите службы распознавания речи и ввода предложения.</span><span class="sxs-lookup"><span data-stu-id="35be7-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="35be7-108">Примечание: сведения о том, как это сделать на Mac/Macbook [здесь](linkgoeshere).</span><span class="sxs-lookup"><span data-stu-id="35be7-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="35be7-109">Войдите в [портала Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="35be7-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="35be7-110">После входа в систему щелкните Создать ресурс и выполните поиск «Language Understanding» и нажмите ВВОД.</span><span class="sxs-lookup"><span data-stu-id="35be7-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="35be7-112">Нажмите кнопку "Создать", чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="35be7-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="35be7-113">Назовите проект «Speech_SDK_Learning_Module» и выберите пункт «Оплата по мере использования.»</span><span class="sxs-lookup"><span data-stu-id="35be7-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="35be7-116">Выберите свой регион.</span><span class="sxs-lookup"><span data-stu-id="35be7-116">Select your Region.</span></span>  <span data-ttu-id="35be7-117">В рамках этого руководства выберите «(США) Западная часть США.»</span><span class="sxs-lookup"><span data-stu-id="35be7-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="35be7-118">Затем выберите «F0» для ценовой категории.</span><span class="sxs-lookup"><span data-stu-id="35be7-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="35be7-119">Теперь щелкните «Создать» (находится в левом нижнем углу), чтобы создать ресурс.</span><span class="sxs-lookup"><span data-stu-id="35be7-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="35be7-120">Обратите внимание: когда вы перейдете на «создать», вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="35be7-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="35be7-121">Уведомление будет отображаться на портале, после создания ресурса.</span><span class="sxs-lookup"><span data-stu-id="35be7-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="35be7-122">Щелкните это уведомление и выберите команду «Перейти к ресурсу».</span><span class="sxs-lookup"><span data-stu-id="35be7-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="35be7-123">На странице «Быстрый запуск» службы «API LUIS» перейдите к первому шагу, получите «ключи» и щелкните «ключи» (это можно также сделать, щелкнув синий hyperlink «ключи», показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="35be7-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="35be7-124">Это покажет вашей службы, «Ключи».</span><span class="sxs-lookup"><span data-stu-id="35be7-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="35be7-125">Сохраните копию одного из ключей, чтобы можно было использовать позже в приложении.</span><span class="sxs-lookup"><span data-stu-id="35be7-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="35be7-127">Обратно на страницы «Быстрый запуск» в разделе 2b щелкните «Портал Language Understanding» (показано на приведенном выше рисунке) перенаправление на веб-страницу, который будет использоваться для создания новой службы, приложения LUIS.</span><span class="sxs-lookup"><span data-stu-id="35be7-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="35be7-128">Примечание. При достижении «портал Language Understanding», может потребоваться войти в систему, если вы еще не сделали, с теми же учетными данными, как портал Azure.</span><span class="sxs-lookup"><span data-stu-id="35be7-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="35be7-129">Если вы впервые используете LUIS, необходимо будет прокрутите вниз страницу приветствия, для поиска и нажмите кнопку «Создать LUIS» приложения.</span><span class="sxs-lookup"><span data-stu-id="35be7-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="35be7-130">После входа в систему, щелкните Мои приложения (Если вы не в этом разделе в данный момент).</span><span class="sxs-lookup"><span data-stu-id="35be7-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="35be7-131">Затем можно выбрать Создание нового приложения.</span><span class="sxs-lookup"><span data-stu-id="35be7-131">You can then click on Create new app.</span></span> <span data-ttu-id="35be7-132">Назовите новое приложение «Модуля обучения пакета SDK для распознавания речи».</span><span class="sxs-lookup"><span data-stu-id="35be7-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="35be7-133">Модуль «Speech SDK обучения» в поле описания, а также.</span><span class="sxs-lookup"><span data-stu-id="35be7-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="35be7-134">Нажмите кнопку «Готово».</span><span class="sxs-lookup"><span data-stu-id="35be7-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="35be7-137">Примечание. Если приложения должны понимать языке, отличном от английского, следует изменить «Culture» для соответствующего языка.</span><span class="sxs-lookup"><span data-stu-id="35be7-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="35be7-138">Нажмите кнопку «Build», расположенный в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="35be7-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="35be7-139">В разделе ресурсов приложения в левой части выберите «Целей» а затем нажмите кнопку «Создать назначение» и назовите его «PressButton.»</span><span class="sxs-lookup"><span data-stu-id="35be7-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="35be7-141">Примечание: необходимо использовать имена намерения и сущности, используемые в этом руководстве, так как приложение Lunarcom будет ссылаться на них по имени.</span><span class="sxs-lookup"><span data-stu-id="35be7-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="35be7-142">Для других проектов соглашения об именовании может быть любым показателям.</span><span class="sxs-lookup"><span data-stu-id="35be7-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="35be7-143">Примечание: теперь у вас 2 намерения - «PressButton» и «None».</span><span class="sxs-lookup"><span data-stu-id="35be7-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="35be7-144">В разделе ресурсов приложения в левой части выберите «Сущности» и нажмите кнопку «Создать новую сущность» и назовите его «Действие» и сохранить тип сущности как «Простой».</span><span class="sxs-lookup"><span data-stu-id="35be7-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="35be7-146">Снова нажмите кнопку «Создать новую сущность» и назовите его «Цель» и также сохранить тип сущности, как «Простой».</span><span class="sxs-lookup"><span data-stu-id="35be7-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="35be7-148">В разделе ресурсов приложения в левой части выберите «Целей» щелкните «PressButton» намерения, созданный на шаге 10.</span><span class="sxs-lookup"><span data-stu-id="35be7-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="35be7-150">Щелкните раскрывающийся список «Просмотреть параметры» в правом углу и выберите пункт «Показать значения сущности».</span><span class="sxs-lookup"><span data-stu-id="35be7-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="35be7-152">Щелкните «введите пример...»</span><span class="sxs-lookup"><span data-stu-id="35be7-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="35be7-153">текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="35be7-153">textbox.</span></span> <span data-ttu-id="35be7-154">Затем введите следующие фразы:</span><span class="sxs-lookup"><span data-stu-id="35be7-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="35be7-156">Щелкните раскрывающийся список «Просмотреть параметры» в правом углу и выберите пункт «Показать имена сущностей».</span><span class="sxs-lookup"><span data-stu-id="35be7-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="35be7-158">Убедитесь, что каждый из 10 фразы имеют следующие метки сущности в следующих местах на 1.) Если щелкнуть на слова, которые являются неправильными метками и во всплывающем окне выберите «Удалить метку» и 2.) Если щелкнуть по словам, которые должны быть помечены и во всплывающем окне выберите соответствующую метку.</span><span class="sxs-lookup"><span data-stu-id="35be7-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="35be7-160">Теперь чтобы опубликовать эту модель, нажмите кнопку «Обучение» в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="35be7-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="35be7-161">После завершения обработки, щелкните «Test» в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="35be7-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="35be7-163">Введите в сообщение об ошибке «выберите "запустить"» в текстовом поле.</span><span class="sxs-lookup"><span data-stu-id="35be7-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="35be7-164">Примечание: мы не добавляли «select» как действие в одном из наших фразы -, но если щелкнуть «Инспектировать» модели признана «выберите» сущности действия.</span><span class="sxs-lookup"><span data-stu-id="35be7-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="35be7-166">Теперь нажмите кнопку «Опубликовать» в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="35be7-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="35be7-167">Убедитесь, что в раскрывающемся списке выбран «Production» и нажмите кнопку «Опубликовать», а также контекстного меню.</span><span class="sxs-lookup"><span data-stu-id="35be7-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="35be7-169">После публикации зеленой полосой должны отображаться в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="35be7-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="35be7-170">Щелкните зеленый панели, чтобы перейти к странице «Управление».</span><span class="sxs-lookup"><span data-stu-id="35be7-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="35be7-172">Щелкните «Ключи и конечные точки» в разделе «Параметры приложения» слева.</span><span class="sxs-lookup"><span data-stu-id="35be7-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="35be7-173">Затем задайте раскрывающийся список «Публиковать в» как «Production».</span><span class="sxs-lookup"><span data-stu-id="35be7-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="35be7-174">Задайте часовой пояс вашими и установите флажок для включения всех прогнозируемых оценок намерений.</span><span class="sxs-lookup"><span data-stu-id="35be7-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="35be7-175">Наконец щелкните «Назначить ресурс».</span><span class="sxs-lookup"><span data-stu-id="35be7-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="35be7-177">Выберите клиент в первом раскрывающемся списке и выберите «Оплата по мере использования» в раскрывающемся списке имя подписки.</span><span class="sxs-lookup"><span data-stu-id="35be7-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="35be7-178">В разделе LUIS имя ресурса выберите ресурс, который мы создали выше в шагах 1 – 5.</span><span class="sxs-lookup"><span data-stu-id="35be7-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="35be7-179">Затем щелкните «Назначить ресурс».</span><span class="sxs-lookup"><span data-stu-id="35be7-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="35be7-181">Примечание: Убедитесь, что скопируйте и сохраните URL-адрес конечной точки, связанный с ресурсом, мы просто назначили, чтобы он был легко доступен в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="35be7-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="35be7-182">Обратите внимание: имя клиента, можно поместить в корпорации или профиль, созданный для этого приложения.</span><span class="sxs-lookup"><span data-stu-id="35be7-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="35be7-183">Теперь откройте новое приложение в Unity и выберите объект Lunarcom_Base в иерархии.</span><span class="sxs-lookup"><span data-stu-id="35be7-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="35be7-184">Нажмите кнопку «Добавить компонент» на панели инспектора и найдите и выберите «LunarcomIntentRecognizer.»</span><span class="sxs-lookup"><span data-stu-id="35be7-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="35be7-186">В поле конечной точке Luis «LunarcomIntentRecognizer» на панели Инспектора введите URL-адрес конечной точки, созданный на шаге 22.</span><span class="sxs-lookup"><span data-stu-id="35be7-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="35be7-188">Примечание. В компоненте «LunarcomOfflineRecognizer» на панели Инспектора убедитесь, что «отключить» для «SimulateOfflineMode» в противном случае выбирается, тестирование программы не будет работать.</span><span class="sxs-lookup"><span data-stu-id="35be7-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="35be7-189">Нажмите кнопку воспроизведения в редакторе Unity и щелкните «rocket», чтобы запустить распознавание сути высказывания.</span><span class="sxs-lookup"><span data-stu-id="35be7-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="35be7-190">Тещи фразу «"выберите" запустить rocket».</span><span class="sxs-lookup"><span data-stu-id="35be7-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="35be7-191">Примечание. Приложение распознает нужной функции и активирована кнопка rocket.</span><span class="sxs-lookup"><span data-stu-id="35be7-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="35be7-193">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="35be7-193">Congratulations</span></span>

<span data-ttu-id="35be7-194">Официально вы узнали, как добавить голосовые команды из программы speech SDK!</span><span class="sxs-lookup"><span data-stu-id="35be7-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="35be7-195">Теперь программа могла распознать голосовые команды всех типов объектов типа Variant.</span><span class="sxs-lookup"><span data-stu-id="35be7-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="35be7-196">Протестировать его и создали немного поэкспериментируем с ней.</span><span class="sxs-lookup"><span data-stu-id="35be7-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="35be7-197">Следующий урок. Пакет SDK для распознавания речи — занятие 5</span><span class="sxs-lookup"><span data-stu-id="35be7-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)

