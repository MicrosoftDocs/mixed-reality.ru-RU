## <a name="lesson-4"></a>Занятие 4

В главе 4 мы рассмотрим функцию намерений службы распознавания речи. Мы будет Настройка нашего LUIS портала Azure, Настройка наши намерения и сущности/фразы, публикация нашего намерения ресурса, соединиться нашего ресурса намерением наше приложение Unity и сделать наш первый вызов API намерение.

1. Разрешение компьютер включить режим диктовки сделать это, перейдите к параметрам Windows, выберите «конфиденциальность», а затем «речь» и наконец «рукописный ввод & введя» и включите службы распознавания речи и ввода предложения.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> Примечание: сведения о том, как это сделать на Mac/Macbook [здесь](linkgoeshere).

2. Войдите в [портала Azure](https://portal.azure.com/). После входа в систему щелкните Создать ресурс и выполните поиск «Language Understanding» и нажмите ВВОД.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Нажмите кнопку "Создать", чтобы создать экземпляр этой службы. Назовите проект «Speech_SDK_Learning_Module» и выберите пункт «Оплата по мере использования.»

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Выберите свой регион.  В рамках этого руководства выберите «(США) Западная часть США.» Затем выберите «F0» для ценовой категории. Теперь щелкните «Создать» (находится в левом нижнем углу), чтобы создать ресурс.

   >  Обратите внимание: когда вы перейдете на «создать», вы получите ожидания службы должен быть создан, это может занять около минуты.

5. Уведомление будет отображаться на портале, после создания ресурса. Щелкните это уведомление и выберите команду «Перейти к ресурсу».

6. На странице «Быстрый запуск» службы «API LUIS» перейдите к первому шагу, получите «ключи» и щелкните «ключи» (это можно также сделать, щелкнув синий hyperlink «ключи», показано на рисунке ниже). Это покажет вашей службы, «Ключи». Сохраните копию одного из ключей, чтобы можно было использовать позже в приложении.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. Обратно на страницы «Быстрый запуск» в разделе 2b щелкните «Портал Language Understanding» (показано на приведенном выше рисунке) перенаправление на веб-страницу, который будет использоваться для создания новой службы, приложения LUIS.

> Примечание. При достижении «портал Language Understanding», может потребоваться войти в систему, если вы еще не сделали, с теми же учетными данными, как портал Azure. Если вы впервые используете LUIS, необходимо будет прокрутите вниз страницу приветствия, для поиска и нажмите кнопку «Создать LUIS» приложения.

8. После входа в систему, щелкните Мои приложения (Если вы не в этом разделе в данный момент). Затем можно выбрать Создание нового приложения. Назовите новое приложение «Модуля обучения пакета SDK для распознавания речи». Модуль «Speech SDK обучения» в поле описания, а также. Нажмите кнопку «Готово».

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> Примечание. Если приложения должны понимать языке, отличном от английского, следует изменить «Culture» для соответствующего языка.

9. Нажмите кнопку «Build», расположенный в правом верхнем углу.

10. В разделе ресурсов приложения в левой части выберите «Целей» а затем нажмите кнопку «Создать назначение» и назовите его «PressButton.» 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Примечание: необходимо использовать имена намерения и сущности, используемые в этом руководстве, так как приложение Lunarcom будет ссылаться на них по имени.  Для других проектов соглашения об именовании может быть любым показателям. 
>
> Примечание: теперь у вас 2 намерения - «PressButton» и «None».

11. В разделе ресурсов приложения в левой части выберите «Сущности» и нажмите кнопку «Создать новую сущность» и назовите его «Действие» и сохранить тип сущности как «Простой».

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Снова нажмите кнопку «Создать новую сущность» и назовите его «Цель» и также сохранить тип сущности, как «Простой».

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. В разделе ресурсов приложения в левой части выберите «Целей» щелкните «PressButton» намерения, созданный на шаге 10.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Щелкните раскрывающийся список «Просмотреть параметры» в правом углу и выберите пункт «Показать значения сущности». 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Щелкните «введите пример...» текстовое поле. Затем введите следующие фразы: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Щелкните раскрывающийся список «Просмотреть параметры» в правом углу и выберите пункт «Показать имена сущностей».

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Убедитесь, что каждый из 10 фразы имеют следующие метки сущности в следующих местах на 1.) Если щелкнуть на слова, которые являются неправильными метками и во всплывающем окне выберите «Удалить метку» и 2.) Если щелкнуть по словам, которые должны быть помечены и во всплывающем окне выберите соответствующую метку.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. Теперь чтобы опубликовать эту модель, нажмите кнопку «Обучение» в правом верхнем углу. После завершения обработки, щелкните «Test» в правом верхнем углу.

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Введите в сообщение об ошибке «выберите "запустить"» в текстовом поле.

> Примечание: мы не добавляли «select» как действие в одном из наших фразы -, но если щелкнуть «Инспектировать» модели признана «выберите» сущности действия.
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. Теперь нажмите кнопку «Опубликовать» в правом верхнем углу. Убедитесь, что в раскрывающемся списке выбран «Production» и нажмите кнопку «Опубликовать», а также контекстного меню. 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. После публикации зеленой полосой должны отображаться в верхней части страницы.  Щелкните зеленый панели, чтобы перейти к странице «Управление». 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. Щелкните «Ключи и конечные точки» в разделе «Параметры приложения» слева. Затем задайте раскрывающийся список «Публиковать в» как «Production». Задайте часовой пояс вашими и установите флажок для включения всех прогнозируемых оценок намерений. Наконец щелкните «Назначить ресурс».

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Выберите клиент в первом раскрывающемся списке и выберите «Оплата по мере использования» в раскрывающемся списке имя подписки. В разделе LUIS имя ресурса выберите ресурс, который мы создали выше в шагах 1 – 5. Затем щелкните «Назначить ресурс». 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Примечание: Убедитесь, что скопируйте и сохраните URL-адрес конечной точки, связанный с ресурсом, мы просто назначили, чтобы он был легко доступен в следующем разделе.
>
> Обратите внимание: имя клиента, можно поместить в корпорации или профиль, созданный для этого приложения.

23. Теперь откройте новое приложение в Unity и выберите объект Lunarcom_Base в иерархии. Нажмите кнопку «Добавить компонент» на панели инспектора и найдите и выберите «LunarcomIntentRecognizer.»

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. В поле конечной точке Luis «LunarcomIntentRecognizer» на панели Инспектора введите URL-адрес конечной точки, созданный на шаге 22. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Примечание. В компоненте «LunarcomOfflineRecognizer» на панели Инспектора убедитесь, что «отключить» для «SimulateOfflineMode» в противном случае выбирается, тестирование программы не будет работать. 

25. Нажмите кнопку воспроизведения в редакторе Unity и щелкните «rocket», чтобы запустить распознавание сути высказывания. Тещи фразу «"выберите" запустить rocket».

>  Примечание. Приложение распознает нужной функции и активирована кнопка rocket.
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Поздравляем!

Официально вы узнали, как добавить голосовые команды из программы speech SDK! Теперь программа могла распознать голосовые команды всех типов объектов типа Variant. Протестировать его и создали немного поэкспериментируем с ней.

[Следующий урок. Пакет SDK для распознавания речи — занятие 5](placeholderlink)
