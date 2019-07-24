---
title: MR и Azure 312 — интеграция с Bot
description: Пройдите этот курс, чтобы научиться создавать и развертывать роботы, использовать Microsoft Bot Framework v4 и взаимодействовать с ней в приложении для смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, компьютерное зрение, hololens, иммерсивное, VR, Microsoft Bot Framework V4, Bot веб-приложения, Bot Framework, Microsoft Bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63542466"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

# <a name="mr-and-azure-312-bot-integration"></a>MR и Azure 312: Интеграция с Bot

В этом курсе вы узнаете, как создать и развернуть робот с помощью Microsoft Bot Framework v4 и взаимодействовать с ним через приложение Windows Mixed Reality. 

![](images/AzureLabs-Lab312-00.png)

**Microsoft Bot Framework v4** — это набор интерфейсов API, предназначенных для предоставления разработчикам средств для создания расширяемого и масштабируемого приложения-робота. Дополнительные сведения см. на [странице Microsoft Bot Framework](https://dev.botframework.com/) или в [репозитории Git v4](https://github.com/Microsoft/botbuilder-dotnet/wiki).

После завершения этого курса вы получите приложение Windows Mixed Reality, которое сможет сделать следующее:

1. Используйте **жест касания** для запуска программы-робота, ожидающей голоса пользователя.
2. Когда пользователь сказал что-то, программа Bot попытается предоставить ответ.
3. Отображение ответа программы-роботы в виде текста, расположенного рядом с Bot, в сцене Unity.

В приложении вы будете выполнять интеграцию результатов с вашей структурой. Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity. Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> MR и Azure 312: Интеграция с Bot</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс в основном ориентирован на HoloLens, вы можете также применить сведения, которые вы узнаете в этом курсе, к головным телефонам Windows Mixed Reality (VR). Так как у головных гарнитур нет доступных камер, вам потребуется внешняя камера, подключенная к компьютеру. При работе с курсом вы увидите заметки о любых изменениях, которые могут потребоваться для поддержки головных телефонов (VR).

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#. Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018). Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.

Для этого курса рекомендуется следующее оборудование и программное обеспечение:

- ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)
- [Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK для Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Доступ к Интернету для Azure и получение Azure Bot. Для получения дополнительных сведений [перейдите по этой ссылке](https://dev.botframework.com/).

### <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).
2.  Настройка и тестирование HoloLens. Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя). 

Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens).

Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Глава 1. Создание приложения-робота

Первым шагом является создание программы Bot в качестве локального веб-приложения ASP.Net Core. После завершения и тестирования вы сможете опубликовать его на портале Azure.

1.  Откройте Visual Studio. Создайте новый проект, выберите в качестве типа проекта **веб-приложение ASP NET Core** (его можно найти в подразделе .NET Core) и вызовите его **мибот**. Нажмите кнопку **ОК**.

2.  В окне, которое будет отображаться, выберите пустое. Также убедитесь, что для целевого объекта задано значение **ASP NET Core 2,0** , а для параметра Проверка подлинности — значение **без проверки**подлинности. Нажмите кнопку **ОК**.  

    ![Создание приложения-робота](images/AzureLabs-Lab312-01.png)

3.  Теперь решение откроется. Щелкните правой кнопкой мыши решение **мибот** в **Обозреватель решений** и выберите пункт **Управление пакетами NuGet для решения**. 

    ![Создание приложения-робота](images/AzureLabs-Lab312-02.png)

4.  На вкладке **Обзор** выполните поиск **Microsoft. Bot. Builder. Integration. AspNet. Core** (убедитесь, что установлен флажок **Предварительная версия включена** ). Выберите версию пакета **4.0.1-Preview**и установите флажки в полях проекта. Затем нажмите кнопку **установить**. Теперь вы установили библиотеки, необходимые для **Bot Framework v4**. Закройте страницу NuGet.

    ![Создание приложения-робота](images/AzureLabs-Lab312-03.png)

5.  Щелкните правой кнопкой мыши *проект* **мибот**в **Обозреватель решений** и выберите **Добавить** **|** **класс**.

    ![Создание приложения-робота](images/AzureLabs-Lab312-04.png)

6.  Назовите класс **мибот** и нажмите кнопку **Добавить**.

    ![Создание приложения-робота](images/AzureLabs-Lab312-05.png)

7.  Повторите предыдущую точку, чтобы создать другой класс с именем **конверсатионконтекст**. 

8.  Щелкните правой кнопкой мыши узел **wwwroot** в **Обозреватель решений** и выберите команду **добавить** **|** **новый элемент**. Выберите **HTML-страница** (она будет находиться в подразделе веб). Назовите файл **Default. HTML**. Нажмите кнопку **Добавить**.

    ![Создание приложения-робота](images/AzureLabs-Lab312-06.png)

9.  Список классов и объектов в **Обозреватель решений** должен выглядеть, как показано на рисунке ниже.

    ![Создание приложения-робота](images/AzureLabs-Lab312-07.png)

10. Дважды щелкните класс **конверсатионконтекст** . Этот класс отвечает за хранение переменных, используемых программой Bot для поддержания контекста диалога. Эти значения контекста диалога сохраняются в экземпляре этого класса, так как любой экземпляр класса **мибот** будет обновляться при каждом получении действия. Добавьте в класс следующий код:

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Дважды щелкните класс **мибот** . Этот класс будет размещать обработчики, вызываемые любыми входящими действиями от клиента. В этом классе будет добавлен код, используемый для создания диалога между Bot и клиентом. Как упоминалось ранее, экземпляр этого класса инициализируется каждый раз при получении действия. Добавьте в этот класс следующий код:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Дважды щелкните класс **Startup** . Этот класс инициализирует робот. Добавьте в класс следующий код:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Откройте файл класса **Program** и проверьте, что код в нем совпадает со следующим:

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. Не забудьте сохранить изменения. чтобы сделать это, выберите **файл** > **сохранить все**на панели инструментов в верхней части Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Глава 2. Создание службы Azure Bot

Теперь, когда вы создали код для программы Bot, необходимо опубликовать его в экземпляре службы *веб-приложения Bot* на портале Azure. В этой главе мы покажем, как создать и настроить службу Bot в Azure, а затем опубликовать в ней свой код.

1.  Сначала войдите на портал Azure (https://portal.azure.com). 

    1. Если у вас еще нет учетной записи Azure, необходимо создать ее. Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.

2.  После входа в систему щелкните **создать ресурс** в левом верхнем углу, а затем выполните поиск по запросу *Bot веб-приложения*и нажмите клавишу **Ввод**.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  На новой странице будет представлено описание службы *веб-приложения Bot* . В нижнем левом углу этой страницы нажмите кнопку **создать** , чтобы создать связь с этой службой.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  После нажатия кнопки **создать**:

    1. Вставьте нужное **имя** для этого экземпляра службы.
    2. Выберите **подписку**.
    3. Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure. Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.

        > Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, [перейдите по этой ссылке.](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. Определите расположение группы ресурсов (при создании новой группы ресурсов). В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение. Некоторые ресурсы Azure доступны только в определенных регионах.
    5. Выберите **ценовую категорию** , подходящую для вас. Если вы впервые создаете службу *веб-приложения Bot* , для вас должен быть доступен бесплатный уровень (с именем F0).
    6. **Имя приложения** может быть просто оставлено *именем Bot*. 
    7. Оставьте *шаблон Bot* **Basic (C#)** .
    8. *План службы приложений или расположение* должны быть заполнены автоматически для вашей учетной записи.
    9. Укажите службу **хранилища Azure** , которую вы хотите использовать для размещения программы-робота. Если у вас его еще нет, его можно создать здесь.
    10. Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.
    11. Нажмите кнопку Создать.
 
        ![Создание службы Azure Bot](images/AzureLabs-Lab312-10.png)

5.  После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.

6.  После создания экземпляра службы на портале отобразится уведомление.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  Щелкните уведомление, чтобы просмотреть новый экземпляр службы. 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы. Вы будете перенаправлены на новый экземпляр службы Azure. 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  На этом этапе необходимо настроить функцию **прямой командной строки** , которая позволит клиентскому приложению взаимодействовать с этой службой Bot. Щелкните **каналы**, а затем в разделе **Добавление избранного канала** щелкните **настроить прямой канал линии**.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-14.png)

10. На этой странице находятся **секретные ключи** , которые позволяют клиентскому приложению проходить проверку подлинности с помощью программы-робота. Нажмите кнопку **Показать** и получите копию одного из отображаемых ключей, так как это потребуется позже в проекте. 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Глава 3. Публикация программы-робота в службе Azure Web App Bot

Теперь, когда служба готова, необходимо опубликовать созданный ранее код Bot в созданной службе веб-приложения Bot.

> [!NOTE] 
> Каждый раз при внесении изменений в решение или код для программы-робота потребуется опубликовать программу Bot в службе Azure.

1.  Вернитесь к созданному ранее решению Visual Studio. 
2.  Щелкните правой кнопкой мыши проект **мибот** в **Обозреватель решений**, а затем щелкните **Publish (опубликовать**).

    ![Публикация программы Bot в службе веб-приложения Azure Bot](images/AzureLabs-Lab312-16.png)

3.  На странице *Выбор целевого объекта публикации* щелкните **служба приложений**, а затем **выберите существующий**, в последний раз щелкните **создать профиль** (если это не отображается, может потребоваться щелкнуть стрелку раскрывающегося списка рядом с кнопкой *опубликовать* .)

    ![Публикация программы Bot в службе веб-приложения Azure Bot](images/AzureLabs-Lab312-17.png)

4. Если вы еще не вошли в учетную запись Майкрософт, это можно сделать здесь.
5. На странице **Публикация** вам нужно будет задать ту же подписку, которая  использовалась для создания службы *веб-приложения Bot* . Затем задайте **представление** в качестве **группы ресурсов** и в раскрывающейся структуре папок выберите **группу ресурсов** , созданную ранее. Нажмите кнопку **ОК**. 

    ![Публикация программы Bot в службе веб-приложения Azure Bot](images/AzureLabs-Lab312-18.png)

6.  Теперь нажмите кнопку " **опубликовать** " и дождитесь публикации программы-робота (это может занять несколько минут).

    ![Публикация программы Bot в службе веб-приложения Azure Bot](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Глава 4 — Настройка проекта Unity

Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.

1.  Откройте *Unity* и нажмите кнопку **создать**. 

    ![Настройка проекта Unity](images/AzureLabs-Lab312-20.png)

2.  Теперь необходимо указать имя проекта Unity. Вставьте **Hololens Bot**. Убедитесь, что для шаблона проекта задано значение **3D**. Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше). Затем нажмите кнопку **создать проект**.

    ![Настройка проекта Unity](images/AzureLabs-Lab312-21.png)

3.  При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**. Перейдите к разделу **изменение параметров >** , а затем в новом окне перейдите к разделу **Внешние инструменты**. Измените **Редактор внешних скриптов** на **Visual Studio 2017**. Закройте окно **настройки** .

    ![Настройка проекта Unity](images/AzureLabs-Lab312-22.png)

4.  Затем перейдите в раздел **файл > параметры сборки** и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.

    ![Настройка проекта Unity](images/AzureLabs-Lab312-23.png)

5.  Несмотря на то что в **файле > параметры сборки** , убедитесь в том, что:

    1.  **Целевое устройство** имеет значение **Hololens**

        > Для впечатляющих головных телефонов задайте для параметра **целевое устройство** *любое устройство*.

    2.  Для **типа сборки** задано значение **D3D**

    3.  **Пакет SDK** установлен в значение " **Последняя установка** "

    4.  Для **версии Visual Studio** установлено значение " **Последняя установка** "

    5.  **Сборка и запуск** настроены на **локальный компьютер**

    6.  Сохраните сцену и добавьте ее в сборку. 

        1. Для этого выберите **Добавить открытые сцены**. Появится окно сохранения.
        
            ![Настройка проекта Unity](images/AzureLabs-Lab312-24.png)

        2. Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».

             ![Настройка проекта Unity](images/AzureLabs-Lab312-25.png)

        3. Откройте созданную папку **сцены** , а затем в текстовом поле *имя файла*введите **Ботсцене**, а затем щелкните **Save (сохранить**).

            ![Настройка проекта Unity](images/AzureLabs-Lab312-26.png)

    7. Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.

6. В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* . 

    ![Настройка проекта Unity](images/AzureLabs-Lab312-27.png)

7. На этой панели необходимо проверить несколько параметров:

    1. На вкладке **другие параметры** выполните следующие действия.

        1. **Версия среды выполнения сценариев** должна быть **экспериментальной (.NET 4,6 эквивалент)** ; чтобы изменить это, потребуется перезапустить редактор.
        2. **Серверная часть сценариев** должна быть **.NET**
        3. **Уровень совместимости API** должен быть **.NET 4,6**

            ![Настройка проекта Unity](images/AzureLabs-Lab312-28.png)
      
    2. На вкладке **Параметры публикации** в разделе **возможности**установите флажок:

        - **InternetClient**
        - **Звук**

            ![Настройка проекта Unity](images/AzureLabs-Lab312-29.png)

    3. На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .

        ![Настройка проекта Unity](images/AzureLabs-Lab312-30.png)

8.  Назад в *параметрах сборки* проект _Unity C#_  больше не является серым. Установите флажок рядом с этим. 
9.  Закройте окно параметры сборки.
10. Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).


## <a name="chapter-5--camera-setup"></a>Глава 5 — Настройка камеры

> [!IMPORTANT]
> Если вы хотите пропустить компонент *установки Unity* , установленный в этом курсе, и продолжить работу с кодом, скачайте этот пакет [Azure-MR-312-Package. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте [ Глава 7](#chapter-7-–-create-the-botobjects-class).

1.  На *панели Иерархия*выберите **основную камеру**. 
2.  После выбора вы сможете увидеть все компоненты **основной камеры** на *панели инспектора*.

    1. **Объект Camera** должен называться **основной камерой** (Обратите внимание на орфографию)
    2. Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на орфографию)
    3. Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .
    4. Установите для параметра **сбросить флаги** **сплошной цвет**.
    5. Установить черный цвет **фона** для компонента камеры **, альфа 0 (шестнадцатеричный код: #00000000)**

    ![Настройка камеры](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Глава 6 — Импорт библиотеки Newtonsoft

Чтобы упростить десериализацию и сериализацию объектов, полученных и отправленных службе Bot, необходимо загрузить библиотеку **Newtonsoft** . [Совместимая версия уже организована с правильной структурой папок Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage). 

Чтобы импортировать библиотеку Newtonsoft в проект, используйте пакет Unity, прилагаемый к этому курсу.

1.  Добавьте *. пакет unitypackage* в Unity с помощью команды меню**настраиваемый пакет** **Импорт** >  **активов** > .

    ![Импорт библиотеки Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  В появившемся окне **Импорт пакета Unity** убедитесь, что выбраны все компоненты **подключаемых модулей** (включая).

    ![Импорт библиотеки Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.

4.  Перейдите в папку **Newtonsoft** в разделе **подключаемые модули** в представлении проекта и выберите подключаемый модуль Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Выбрав подключаемый модуль Newtonsoft, убедитесь, что не **установлен флажок**для **любой платформы** , а затем убедитесь, что **всаплайер** также не **установлен**, а затем нажмите кнопку **Применить**. Это необходимо только для того, чтобы убедиться, что файлы настроены правильно.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Пометка этих подключаемых модулей настраивает их для использования только в редакторе Unity. В папке WSA имеется другой набор, который будет использоваться после экспорта проекта из Unity.

6.  Далее необходимо открыть папку **WSA** в папке **Newtonsoft** Вы увидите копию того же файла, который вы только что настроили. Выберите файл, а затем в инспекторе убедитесь, что
    -   **Все платформы** не **отмечены** 
    -   **только** **Всаплайер** **установлен**
    -   **Установлен** **процесс не**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Глава 7 — создание Боттаг

1.  Создайте новый объект **Tag** с именем **боттаг**. Выберите основную камеру в сцене. Щелкните раскрывающееся меню тега на панели инспектора. Щелкните **Добавить тег**.

    ![Настройка камеры](images/AzureLabs-Lab312-32.png)
 
2.  **+** Щелкните символ. Присвойте новому **тегу** имя **боттаг**, *Сохраните*.

    ![Настройка камеры](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **Не** применяйте **Боттаг** к основной камере. Если вы случайно сделали это, обязательно замените основной тег камеры обратно на *маинкамера*.

## <a name="chapter-8--create-the-botobjects-class"></a>Глава 8 — Создание класса Ботобжектс

Первым скриптом, который необходимо создать, является класс **ботобжектс** , который представляет собой пустой класс, так что ряд других объектов класса может храниться в пределах одного скрипта и обращаться к ним из других скриптов в сцене.

Создание этого класса является исключительно архитектурным выбором, поэтому эти объекты можно разместить в скрипте Bot, который будет создан далее в этом курсе.

Чтобы создать этот класс, сделайте следующее: 

1.  Щелкните правой кнопкой мыши на *панели проект*, а затем **Создайте > папку**. Назовите папку **Scripts**. 

    ![Создайте папку Scripts.](images/AzureLabs-Lab312-36.png)

2.  Дважды щелкните папку Scripts  , чтобы открыть ее. Затем в этой папке щелкните правой кнопкой мыши и выберите **создать > C# скрипт**. Назовите сценарий **ботобжектс**. 

3.  Дважды щелкните новый скрипт **ботобжектс** , чтобы открыть его в **Visual Studio**.

4.  Удалите содержимое скрипта и замените его следующим кодом:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-9--create-the-gazeinput-class"></a>Глава 9 — Создание класса Газеинпут

Следующий класс, который предстоит создать, — это класс **газеинпут** . Этот класс отвечает за:

- Создание курсора, который будет представлять *взгляд* на игрока.
- Обнаружение объектов, которые попадают на взгляд игроку, и хранение ссылок на обнаруженные объекты.

Чтобы создать этот класс, сделайте следующее: 

1.  Перейдите к созданной ранее папке **Scripts** . 
2.  Щелкните правой кнопкой мыши внутри папки, **Создайте скрипт C# >** . Вызовите скрипт **газеинпут**. 
3.  Дважды щелкните новый скрипт **газеинпут** , чтобы открыть его в **Visual Studio**.
4.  Вставьте следующую строку непосредственно в начале имени класса:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Затем добавьте следующие переменные в класс **газеинпут** над методом **Start ()** :

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Необходимо добавить код для метода **Start ()** . Он будет вызываться при инициализации класса:

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Реализуйте метод, который будет создавать и настраивать курсор взгляда: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Реализуйте методы, которые будут настраивать Райкаст из основной камеры и отслеживают текущий объект, на который осуществляется запись.

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-10--create-the-bot-class"></a>Глава 10 — Создание класса Bot

Скрипт, который предстоит создать, называется **Bot**. Это основной класс вашего приложения, который хранит: 

- Учетные данные для роботов веб-приложения
- Метод, собирающий пользовательские команды
- Метод, необходимый для инициации диалогов с помощью робота веб-приложения 
- Метод, необходимый для отправки сообщений в робот веб-приложения 

Чтобы отправлять сообщения в службу Bot, соподпрограмма **сендмессажетобот ()** создает действие, которое представляет собой объект, распознаваемый программой Bot в качестве данных, отправленных пользователем. 
 
Чтобы создать этот класс, сделайте следующее: 

1. Дважды щелкните папку Scripts  , чтобы открыть ее. 
2. Щелкните правой кнопкой мыши в  папке Scripts и выберите **создать C# > скрипт**. Присвойте сценарию имя **Bot**. 
3. Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.
4. Обновите пространства имен, как показано ниже, в верхней части класса **Bot** :

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Внутри класса **Bot** добавьте следующие переменные:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Обязательно вставьте **секретный ключ Bot** в переменную **ботсекрет** . В начале этого курса вы заметили **секретный ключ** программы-робота, в  **[главе 2](#chapter-2---create-the-azure-bot-service), шаг 10**.

7. Необходимо добавить код для спящего режима **()** и **запуска ()** . 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Добавьте два обработчика, которые вызываются библиотеками распознавания речи при начале и окончании захвата голоса. *Диктатионрекогнизер* автоматически прекратит запись голоса пользователя, когда пользователь прекратит говорить.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. Следующий обработчик собирает результат входного голоса пользователя и вызывает соподпрограмму, ответственную за отправку сообщения в службу веб-приложения Bot.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. Для начала диалога с роботом вызывается следующая соподпрограмма. Вы заметите, что после завершения вызова диалога он вызовет **сендмессажетокораутине ()** путем передачи ряда параметров, которые задают действие, которое будет отправлено в службу Bot, в виде пустого сообщения. Это делается для запроса службы Bot на инициацию диалога.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. Для создания действия, которое будет отправлено в службу Bot, вызывается следующая соподпрограмма. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. Для запроса ответа после отправки действия в службу Bot вызывается следующая соподпрограмма. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. Последний метод, который необходимо добавить в этот класс, необходим для вывода сообщения в сцене:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > В консоли редактора Unity может появиться сообщение об ошибке, в котором отсутствует класс **сценеорганисер** . Пропустите это сообщение, так как вы создадите этот класс позже в этом руководстве.

14.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Глава 11 — Создание класса взаимодействий

Класс, который будет создан, теперь называется взаимодействием. Этот класс используется для обнаружения входных данных касания HoloLens от пользователя. 

Если пользователь перейдет на объект *Bot* в сцене, и Bot готов к прослушиванию речевых входов, объект Bot изменит цвет на **красный** и начнет прослушивание входных данных голоса. 

Этот класс наследует от класса **газеинпут** , поэтому он может ссылаться на метод **Start ()** и переменные из этого класса, обозначенные с помощью **base**. 
 
Чтобы создать этот класс, сделайте следующее:

1.  Дважды щелкните папку Scripts  , чтобы открыть ее. 
2.  Щелкните правой кнопкой мыши в  папке Scripts и выберите **создать C# > скрипт**. Назовите скрипт **взаимодействия**. 
3.  Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.
4.  Обновите пространства имен и наследование класса, как показано ниже, в верхней части класса **Interactions** :

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Внутри класса **Interactions** добавьте следующую переменную:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Затем добавьте метод **Start ()** :

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  Добавьте обработчик, который будет срабатывать, когда пользователь выполняет жест касания перед камерой HoloLens.

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Глава 12 — создание класса Сценеорганисер

Последний класс, необходимый в этом лабораторном занятии, называется **сценеорганисер**. Этот класс настраивает сцену программным способом, добавляя компоненты и скрипты в основную камеру и создавая соответствующие объекты в сцене.
 
Чтобы создать этот класс, сделайте следующее:

1.  Дважды щелкните папку Scripts  , чтобы открыть ее. 
2.  Щелкните правой кнопкой мыши в  папке Scripts и выберите **создать C# > скрипт**. Назовите сценарий **сценеорганисер**. 
3.  Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.
4.  Внутри класса **сценеорганисер** добавьте следующие переменные:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  Затем добавьте методы **спящего режима ()** и **Start ()** :

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Добавьте следующий метод, отвечающий за создание объекта Bot в сцене и настройку параметров и компонентов:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Добавьте следующий метод, отвечающий за создание объекта пользовательского интерфейса в сцене, представляющий ответы от программы-робота:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.
9.  В редакторе Unity перетащите сценарий **сценеорганисер** из папки Scripts на главную камеру. Теперь компонент сцены Органисер должен отображаться на объекте основной камеры, как показано на рисунке ниже.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Глава 13 – перед сборкой

Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на HoloLens.
Перед этим убедитесь в том, что:

-   Все параметры, упомянутые в [**главе 4**](#Chapter-4-–-Set-up-the-unity-project) , заданы правильно. 
-   **Сценеорганисер** скрипта прикреплен к главному объекту **Camera** . 
-   В классе **Bot** убедитесь, что вы вставили секретный **ключ Bot** в переменную **ботсекрет** .

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Глава 14 — сборка и загружать неопубликованные в HoloLens

Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.

1.  Перейдите к разделу **параметры сборки**, **Файл > параметры сборки..** .
2.  В окне " **параметры сборки** " щелкните **Сборка**.

    ![Создание приложения из Unity](images/AzureLabs-Lab312-38.png)

3.  Если это еще не так, то проекты Ticks **Unity C#** .
4.  Щелкните **Сборка**. Unity запустит окно **проводника** , в котором необходимо создать, а затем выбрать папку для сборки приложения. Создайте эту папку сейчас и назовите ее **app**Name. Затем выберите папку **приложения** и щелкните **выбрать папку**. 
5.  Unity начнет сборку проекта в папку **приложения** . 
6.  После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).

## <a name="chapter-15--deploy-to-hololens"></a>Глава 15 — развертывание в HoloLens

Для развертывания на HoloLens выполните следующие действия.

1.  Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика**. Выполните указанные ниже действия.

    1. Людьми HoloLens, откройте **Параметры**.
    2. Последовательно выберите пункты **сеть & интернет > Wi-Fi > дополнительные параметры**
    3. Запишите **IPv4** -адрес.
    4. Затем вернитесь к параметрам и **обновите & > безопасности для разработчиков** . 
    5. Задайте режим разработчика на.

2.  Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.
3.  В **конфигурации решения** выберите **Отладка**.
4.  На **платформе решения**выберите **x86**, **Удаленный компьютер**. 

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Перейдите в **меню "сборка** " и щелкните " **Развернуть решение**", чтобы загружать неопубликованные приложение в HoloLens.
6.  Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.

    > [!NOTE]
    > Чтобы выполнить развертывание в иммерсивное виртуальную гарнитуру, задайте для **платформы решения** значение *локальный компьютер*и задайте для параметра **Конфигурация** значение *Отладка*( *x86* в качестве **платформы**). Затем выполните развертывание на локальном компьютере с помощью **меню "сборка**" и выберите пункт " *Развернуть решение*". 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Глава 16 — использование приложения в HoloLens

- После запуска приложения вы увидите робота в качестве синей сферы перед вами.

- Используйте **жест касания** , когда вы облакамие в сфере, чтобы начать беседу. 
 
- Ожидание запуска диалога (в пользовательском интерфейсе будет отображаться сообщение, когда оно произойдет). Получив вводное сообщение от программы-робота, снова коснитесь программы-робота, чтобы он превратится в красный, и начнется прослушивание голоса. 

- После того как вы перестанете разговор, ваше приложение отправит сообщение в Bot, и Вы незамедлительно получите ответ, который будет отображаться в пользовательском интерфейсе. 

- Повторите эту процедуру, чтобы отправить больше сообщений в программу-робот (нужно коснуться каждый раз, когда нужно нда сообщение).

В этом диалоговом окне показано, как Bot может хранить информацию (ваше имя), а также предоставлять известную информацию (например, товары, которые хранятся в запасах).

#### <a name="some-questions-to-ask-the-bot"></a>Вот некоторые вопросы, которые необходимо задать для программы-робота:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Готовое приложение Bot веб-приложения (v4)

Поздравляем! вы создали приложение смешанной реальности, которое использует робот веб-приложения Azure, Microsoft Bot Framework v4.

![Окончательный продукт](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Премиальные упражнения

### <a name="exercise-1"></a>Упражнение 1

Структура диалога в этом лабораторном занятии является очень простой. Используйте Microsoft LUIS, чтобы дать вашему естественному языку возможность понимания возможностей.

### <a name="exercise-2"></a>Упражнение 2

Этот пример не включает в себя завершение диалога и перезапуск нового. Чтобы сделать компонент Bot завершенным, попробуйте реализовать замыкание диалога.
