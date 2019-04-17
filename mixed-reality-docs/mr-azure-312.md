---
title: Г-н и 312 Azure — интеграция программ-роботов
description: Завершите этот курс, чтобы узнать, как создать и развернуть программы-робота, используя Microsoft Bot Framework версии 4 и взаимодействовать с ним в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, компьютерного зрения, hololens, создающий эффект присутствия, vr, microsoft bot framework v4, программ-роботов приложение web, bot framework, программ-роботов microsoft
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604983"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

# <a name="mr-and-azure-312-bot-integration"></a>Г-н и Azure 312: Интеграция программ-роботов

В рамках этого курса вы узнаете, как создать и развернуть программы-робота, используя Microsoft Bot Framework версии 4 и взаимодействовать с ним через приложение Windows Mixed Reality. 

![](images/AzureLabs-Lab312-00.png)

**Microsoft Bot Framework V4** — это набор API-интерфейсов, предназначенных предоставляет разработчикам средства для создания масштабируемые программ-роботов приложение. Дополнительные сведения см. в статье [страницы Microsoft Bot Framework](https://dev.botframework.com/) или [V4 репозитория](https://github.com/Microsoft/botbuilder-dotnet/wiki).

После прохождения этого курса вы сможете создать это приложение Windows Mixed Reality, которое будет осуществлять следующее:

1. Используйте **коснитесь жест** для запуска программ-роботов, прослушивание голоса пользователей.
2. Если пользователь говорилось что-то, бот будет пытаться предоставить ответ.
3. Отобразить ответ программы-роботы как текст, расположенный рядом с программ-роботов, в сцене Unity.

В приложении зависит от пользователя о том, как интегрировать результаты проектированию. Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity. Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> Г-н и Azure 312: Интеграция программ-роботов</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс основное внимание уделяется HoloLens, можно также применить полученные знания в этот курс поможет вам Windows Mixed Reality иммерсивную (VR). Поскольку иммерсивную (VR) не имеют доступных камеры, вам потребуется внешний камеры, подключенном к ПК. При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки иммерсивную (VR).

## <a name="prerequisites"></a>предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#. Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.). Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.

Рекомендуется следующее оборудование и программное обеспечение для этого курса:

- На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)
- [Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Доступ к Интернету для Azure, а также для извлечения программ-роботов Azure. Дополнительные сведения [щелкните эту ссылку](https://dev.botframework.com/).

### <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).
2.  Настроить и проверить ваш HoloLens. Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя). 

Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).

Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Глава 1 – Создание приложения программ-роботов

Первым шагом является создание бота как локальное приложение ASP.Net Core Web. После завершения и протестировали его, как опубликовать его на портал Azure.

1.  Откройте Visual Studio. Создайте новый проект, выберите **веб-приложение ASP NET Core** в качестве типа проекта (его будет найти в подразделе .NET Core) и назовите его **MyBot**. Нажмите кнопку **ОК**.

2.  В окне, которое будет отображаться выберите **пустой**. Также убедитесь, что целевой объект имеет значение **ASP NET Core 2.0** и проверки подлинности значение **без проверки подлинности**. Нажмите кнопку **ОК**.  

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-01.png)

3.  Теперь будет открыто решение. Щелкните правой кнопкой мыши на решении **Mybot** в **обозревателе решений** и щелкнуть **управление пакетами NuGet для решения**. 

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-02.png)

4.  В **Обзор** вкладке, поиск **Microsoft.Bot.Builder.Integration.AspNet.Core** (Убедитесь, что у вас есть **включения предварительного выпуска** флажок установлен). Выберите версию пакета **4.0.1-preview**и установите флажки проекта. Нажмите кнопку на **установить**. Теперь вы установили библиотеки, необходимые для **Bot Framework версии 4**. Закройте страницу NuGet.

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-03.png)

5.  Щелкните правой кнопкой мыши ваш *проекта*, **MyBot**в **обозревателе решений** и щелкнуть **добавить** **|** **Класс**.

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-04.png)

6.  Назовите класс **MyBot** и щелкнуть **добавить**.

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-05.png)

7.  Повторите предыдущие точек, чтобы создать другой класс с именем **ConversationContext**. 

8.  Щелкните правой кнопкой мыши **wwwroot** в **обозревателе решений** и щелкнуть **добавить** **|** **новый элемент**. Выберите **HTML-страницу** (вы найдете ее в разделе Web подраздела). Назовите файл **default.html**. Нажмите кнопку **Добавить**.

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-06.png)

9.  Список классов и объектов в **обозревателе решений** должен выглядеть как на следующем рисунке.

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-07.png)

10. Дважды щелкните **ConversationContext** класса. Этот класс отвечает за хранение переменные, используемые задачей бота для поддержания контекста диалога. Эти значения контекста диалога сохраняются в экземпляре этого класса, так как любой экземпляр **MyBot** класс будет обновляться каждый раз при получении действия. Добавьте следующий код к классу:

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

11. Дважды щелкните **MyBot** класса. Этот класс будет размещаться обработчиков, вызываемых любого входящего действия от клиента. В этом классе вы добавите код, используемый для создания диалога между бота-помощника и клиента. Как упоминалось ранее, экземпляр этого класса инициализируется каждый раз при получении действия. Добавьте следующий код для этого класса:

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

12. Дважды щелкните **запуска** класса. Этот класс будет инициализировать бота. Добавьте следующий код к классу:

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

13. Откройте **программы** файле класса и проверьте код, в нем зависит от того, как показано ниже:

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

14. Не забудьте сохранить изменения, чтобы сделать это, перейдите к **файл** > **сохранить все**, на панели инструментов в верхней части Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Глава 2 - Создание службы Azure Bot

Теперь, когда вы создавали код для вашего бота, вам нужно опубликовать его в экземпляр *программ-роботов приложение Web* службы на портале Azure. В этой главе показано, как создать и настроить службу программ-роботов на Azure и затем их публикация кода.

1.  Во-первых, войдите на портал Azure (https://portal.azure.com). 

    1. Если у вас еще нет учетной записи Azure, необходимо будет создать его. Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.

2.  После входа в систему щелкните **создать ресурс** в левом верхнем углу, а поиск *бот веб-приложения*и нажмите кнопку **ввод**.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  Новая страница будет предоставить описание *программ-роботов приложение Web* службы. В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать ассоциацию с данным службы.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  Когда вы перейдете на **создать**:

    1. Вставить нужный **имя** для данного экземпляра службы.
    2. Выберите **подписки**.
    3. Выберите **группы ресурсов** или создайте новую. Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure. Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, [щелкните эту ссылку](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. Определите расположение для группы ресурсов (Если вы создаете новую группу ресурсов). Расположение оптимально подойдет в регионе, в котором приложение будет работать. Некоторые ресурсы Azure доступны только в определенных регионах.
    5. Выберите **Ценовая** подходит для вас, если это первое времени на создание *программ-роботов приложение Web* службы, уровень "бесплатный" (с именем F0) должны быть доступны для вас
    6. **Имя приложения** можно просто оставить так же, как *имя бота*. 
    7. Оставьте *шаблона программ-роботов* как **основные (C#)**.
    8. *План службы приложений или расположение* должно было автоматически заполняться сведениями для вашей учетной записи.
    9. Задайте **хранилища Azure** , которые нужно использовать для размещения вашего бота. Если вы не сделали, можно создать его здесь.
    10. Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.
    11. Нажмите кнопку Создать.
 
        ![Создание службы Azure Bot](images/AzureLabs-Lab312-10.png)

5.  Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.

6.  Уведомление будет отображаться на портале, после создания экземпляра службы.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  Щелкните уведомление, чтобы изучить ваш новый экземпляр службы. 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы. Откроется в новом экземпляре службы Azure. 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  На этом этапе необходимо настроить функцию, называемую **прямую линию** чтобы разрешить клиентскому приложению взаимодействовать с этой службой программ-роботов. Щелкните **каналы**, а затем в **добавить основной канал** щелкните **настроить прямую линию канал**.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-14.png)

10. На этой странице вы найдете **секретных ключей** , обеспечивая клиентского приложения для проверки подлинности с помощью программ-роботов. Щелкните **Показать** кнопку и сделайте копию один из отображаемых ключей, так как он потребуется позже в проекте. 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Глава 3 – публикация программ-роботов, программ-роботов приложение в Azure веб-службу

Теперь, когда служба будет готов, необходимо опубликовать код программ-роботов, которое вы создали ранее, в только что созданный веб-службу программ-роботов приложение.

> [!NOTE] 
> Необходимо будет опубликовать бота в службе Azure каждый раз при внесении изменений в решение Bot / code.

1.  Вернитесь к решения Visual Studio, который вы создали ранее. 
2.  Щелкните правой кнопкой мыши вашей **MyBot** проекта **обозревателе решений**, затем щелкните **публикации**.

    ![Публикация программ-роботов, программ-роботов приложение в Azure веб-службу](images/AzureLabs-Lab312-16.png)

3.  На *выберите целевой объект публикации* щелкните **службы приложений**, затем **выбрать существующее**, наконец, щелкните на **создать профиль** (может потребоваться Щелкните стрелку раскрывающегося списка рядом с *публикации* кнопку, если это не отображается).

    ![Публикация программ-роботов, программ-роботов приложение в Azure веб-службу](images/AzureLabs-Lab312-17.png)

4. Если вы не еще вошли в учетную запись Майкрософт, что необходимо сделать его здесь.
5. На **публикации** странице вы найдете это нужно сделать же **подписки** , использованная для *программ-роботов приложение Web* создать службу. Затем установите **представление** как **группы ресурсов** и в раскрывающемся списке структуру папок, выберите **группы ресурсов** созданный ранее. Нажмите кнопку **ОК**. 

    ![Публикация программ-роботов, программ-роботов приложение в Azure веб-службу](images/AzureLabs-Lab312-18.png)

6.  Теперь щелкните **публикации** кнопку и подождите, программ-роботов для публикации (может занять несколько минут).

    ![Публикация программ-роботов, программ-роботов приложение в Azure веб-службу](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Глава 4 – Настройка проекта Unity

Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.

1.  Откройте *Unity* и нажмите кнопку **New**. 

    ![Настройка проекта Unity](images/AzureLabs-Lab312-20.png)

2.  Теперь необходимо будет указать имя проекта Unity. Вставить **Hololens программ-роботов**. Убедитесь, что шаблон проекта присваивается **3D**. Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги). Щелкните **создать проект**.

    ![Настройка проекта Unity](images/AzureLabs-Lab312-21.png)

3.  С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**. Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**. Изменение **внешнего редактора скриптов** для **Visual Studio 2017**. Закрыть **предпочтения** окна.

    ![Настройка проекта Unity](images/AzureLabs-Lab312-22.png)

4.  Перейдите к **файл > Параметры сборки** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** кнопку, чтобы применить выбранные параметры.

    ![Настройка проекта Unity](images/AzureLabs-Lab312-23.png)

5.  Оставаясь в **файл > Параметры сборки** и убедитесь, что:

    1.  **Целевое устройство** присваивается **Hololens**

        > Иммерсивную, задайте **целевое устройство** для *любого устройства*.

    2.  **Тип сборки** присваивается **D3D**

    3.  **Пакет SDK для** присваивается **самую новую установленную**

    4.  **Версия Visual Studio** присваивается **самую новую установленную**

    5.  **Сборка и запуск** присваивается **локального компьютера**

    6.  Сохраните сцены и добавить его к сборке. 

        1. Это сделать, выбрав **добавьте откройте сцены**. Сохранение окно будет отображаться.
        
            ![Настройка проекта Unity](images/AzureLabs-Lab312-24.png)

        2. Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.

             ![Настройка проекта Unity](images/AzureLabs-Lab312-25.png)

        3. Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **BotScene**, нажмите кнопку на **Сохранить**.

            ![Настройка проекта Unity](images/AzureLabs-Lab312-26.png)

    7. Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.

6. В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится. 

    ![Настройка проекта Unity](images/AzureLabs-Lab312-27.png)

7. В этой панели необходимо проверить некоторые настройки:

    1. В **другие параметры** вкладке:

        1. **Версия среды выполнения сценариев** должно быть **экспериментальная (эквивалент 4.6 NET)**; это изменение потребует перезапуска редактора.
        2. **Создание сценариев серверной части** должно быть **.NET**
        3. **Уровень совместимости API** должно быть **.NET 4.6**

            ![Настройка проекта Unity](images/AzureLabs-Lab312-28.png)
      
    2. В рамках **параметров публикации** в списке **возможности**, проверьте:

        - **internetClient**
        - **"Микрофон"**

            ![Настройка проекта Unity](images/AzureLabs-Lab312-29.png)

    3. Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.

        ![Настройка проекта Unity](images/AzureLabs-Lab312-30.png)

8.  Вернитесь в *параметры построения* _Unity C#_  проектов больше не отображается серым, установите флажок рядом с это. 
9.  Закройте окно Параметры построения.
10. Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).


## <a name="chapter-5--camera-setup"></a>Глава 5 – Настройка камеры

> [!IMPORTANT]
> Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [Azure MR-312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 7](#chapter-7-–-create-the-botobjects-class).

1.  В *панели иерархии*выберите **Main Camera**. 
2.  После выбора можно видеть все компоненты **Main Camera** в *панели Инспектора*.

    1. **Объекта Camera** должен иметь имя **Main Camera** (Обратите внимание, правильность написания)
    2. Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания)
    3. Убедитесь, что **преобразование положения** присваивается **0, 0, 0**
    4. Задайте **очистить флаги** для **Одноцветная**.
    5. Задайте **фона** цвет компонента камеры для **черная, альфа-значение 0 (шестнадцатеричный код: #00000000)**

    ![Настройка камеры](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Глава 6 – импорт библиотеки Newtonsoft

Для десериализации и сериализации объектов получаемых и отправляемых в службу программ-роботов необходимо скачать **Newtonsoft** библиотеки. Вы найдете [совместимой версии, уже упорядочены с правильного Unity структуре папок здесь](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage). 

Чтобы импортировать библиотеки Newtonsoft в проект, используйте пакет Unity, который прилагается этот курс.

1.  Добавить *.unitypackage* к Unity с помощью **активы** > **Импорт пакета** > **пользовательского пакета** пункт меню.

    ![Импортировать библиотеку Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  В **Импорт пакета Unity** который появится убедитесь, что все, что в разделе (вплоть до) **подключаемые модули** выбран.

    ![Импортировать библиотеку Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.

4.  Перейдите к **Newtonsoft** папке **подключаемые модули** в представлении проекта и выберите подключаемый модуль Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  С помощью подключаемого модуля Newtonsoft выбран, убедитесь, что **Any платформы** — **unchecked**, убедитесь, что флажок **WSAPlayer** также **unchecked**, Нажмите кнопку **применить**. Это, чтобы убедиться, что файлы настроены правильно.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Пометка этих подключаемых модулей позволяет настроить их только для использования в редакторе Unity. Существует другой набор их в папке WSA, которая будет использоваться после проект будет экспортирован из Unity.

6.  Затем необходимо открыть **WSA** папку, в пределах **Newtonsoft** папки. Вы увидите копию тот же файл, который вы только что настроили. Выберите файл и затем в инспекторе, убедитесь, что
    -   **Любой платформе** является **unchecked** 
    -   **только** **WSAPlayer** является **проверки**
    -   **Не обрабатывать** является **проверки**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Глава 7 – создание BotTag

1.  Создайте новый **тега** объект под названием **BotTag**. Выберите Main Camera в сцене. Щелкните тег раскрывающегося меню на панели инспектора. Щелкните **добавьте тег**.

    ![Настройка камеры](images/AzureLabs-Lab312-32.png)
 
2.  Щелкните **+** символов. Имя нового **тега** как **BotTag**, *Сохранить*.

    ![Настройка камеры](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **Не** применить **BotTag** к камере Main. Если вы случайно сделали это, не забудьте заменить Main Camera, тег обратно в *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Глава 8 – создать класс BotObjects

Первый скрипт, чтобы создать **BotObjects** класс, который является пустым классом создан таким образом, чтобы ряд других объектов класса, которые могут храниться в тот же сценарий и доступны для других сценариев в сцене.

Создание этого класса является чисто архитектуры выбором, эти объекты могут быть размещены вместо этого в скрипт программ-роботов, который вы создадите далее в этом курсе.

Для создания этого класса: 

1.  Щелкните правой кнопкой мыши в *панель проекта*, затем **Создать > Папка**. Назовите папку **сценариев**. 

    ![Создайте папку scripts.](images/AzureLabs-Lab312-36.png)

2.  Дважды щелкните **сценариев** папку, чтобы открыть его. Затем в этой папке, щелкните правой кнопкой мыши и выберите **Создать > C# сценарий**. Назовите сценарий **BotObjects**. 

3.  Дважды щелкните новый **BotObjects** скрипт, чтобы открыть его с **Visual Studio**.

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

6.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-9--create-the-gazeinput-class"></a>Глава 9 – создать класс GazeInput

Далее нужно создать класс является **GazeInput** класса. Этот класс отвечает за:

- Создается курсор, который будет представлять *помощи* проигрывателя.
- Обнаружение объектов попадания по взглядом проигрывателя и содержит ссылку на обнаруженных объектов.

Для создания этого класса: 

1.  Перейдите к **сценариев** папку, созданную ранее. 
2.  Щелкните правой кнопкой мыши внутри папки **Создать > C# сценарий**. Вызовите сценарий **GazeInput**. 
3.  Дважды щелкните новый **GazeInput** скрипт, чтобы открыть его с **Visual Studio**.
4.  Вставьте следующую строку прямо на вверху имя класса:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Затем добавьте следующие переменные внутри **GazeInput** класса выше **Start()** метод:

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

6.  Код для **Start()** метода должны быть добавлены. Вызывается при инициализации класса:

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

7.  Реализуйте метод, который будет создать и настроить курсор взглядом: 

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

8.  Реализуйте методы, которые позволят настроить Raycast из Main Camera и будет отслеживать фокус текущего объекта.

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
 
9.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-10--create-the-bot-class"></a>Глава 10 – создать класс программ-роботов

Этот сценарий, который вы собираетесь создать теперь называется **программ-роботов**. Это основной класс приложения, он сохраняет: 

- Учетные данные программ-роботов приложение Web
- Метод, который собирает голосовые команды пользователя
- Метод, необходимо инициировать диалог с Ботом Web App 
- Метод, необходимые для отправки сообщений в веб приложение бота 

Для отправки сообщений в службу программ-роботов, **SendMessageToBot()** сопрограммы построит действие, которое является объектом, Bot Framework распознает как данные, отправляемые пользователем. 
 
Для создания этого класса: 

1. Дважды щелкните **сценариев** папки, чтобы открыть его. 
2. Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**. Назовите сценарий **программ-роботов**. 
3. Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.
4. Обновите пространства имен должны совпадать, как показано ниже, в верхней части **программ-роботов** класса:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Внутри **программ-роботов** класса добавьте следующие переменные:

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
    > Убедитесь, что вы вставляете вашей **программ-роботов секретный ключ** в **botSecret** переменной. Будет записанными вашей **программ-роботов секретный ключ** в начале этого курса в  **[Глава 2](#chapter-2---create-the-azure-bot-service), шаг 10**.

7. Код для **Awake()** и **Start()** теперь должен быть добавлен. 

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

8. Добавление двух обработчиков, которые называются библиотеками речи, когда записи голоса начинается и заканчивается. *DictationRecognizer* автоматически останавливаются записи голоса пользователя, когда пользователь останавливает кстати.

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

1. Следующий обработчик собирает результат голосовой ввод пользователя и вызывает сопрограммы, отвечающего за отправку сообщения программ-роботов приложение веб-службы.

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

10. Следующие сопрограммы называется мог начать диалог с Ботом. Обратите внимание, что после завершения вызова диалога, вызовет **SendMessageToCoroutine()** путем передачи ряда параметров, которые будут задавать действия для отправки в службу программ-роботов, как пустое сообщение. Это позволяет запрашивать службу программ-роботов, инициировать диалог.

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

11. Следующие сопрограммы вызывается для создания действий, отправляемых в службу программ-роботов. 

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

12. Следующие сопрограммы вызывается для запроса ответа после отправки действие службу программ-роботов. 

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

13. Последний метод для добавления в этот класс необходим для отображения сообщения в сцене:

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
    > Может появиться ошибка консоли редактора Unity, об отсутствующих **SceneOrganiser** класса. Игнорируйте это сообщение, так как позже в этом руководстве вы создадите этот класс.

14.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Глава 11 — создать класс взаимодействия

Вы собираетесь создать класс теперь называется **взаимодействия**. Этот класс используется для обнаружения HoloLens коснитесь входные данные пользователя. 

Если пользователь касается просматривая *программ-роботов* объект в сцене и бота готов для прослушивания речевой ввод, меняет цвет для объекта программ-роботов **red** и начать прослушивание речевой ввод. 

Этот класс наследует от **GazeInput** класса и поэтому является возможность создания ссылок на **Start()** метод и переменные из этого класса, обозначенное с помощью **базового**. 
 
Для создания этого класса:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его. 
2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**. Назовите сценарий **взаимодействия**. 
3.  Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.
4.  Обновление пространства имен и наследование классов должны совпадать, как показано ниже, в верхней части **взаимодействия** класса:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Внутри **взаимодействия** класса добавьте следующую переменную:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Затем добавьте **Start()** метод:

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

7.  Добавьте обработчик, который будет применяться при выполнении пользователем жеста касания HoloLens камеры

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

8. Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Глава 12 — создать класс SceneOrganiser

В этом лабораторном занятии требуется последний класс называется **SceneOrganiser**. Этот класс настроит сцены программно, путем добавления компонентов и сценариев Main Camera и создания соответствующих объектов в сцене.
 
Для создания этого класса:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его. 
2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**. Назовите сценарий **SceneOrganiser**. 
3.  Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.
4.  Внутри **SceneOrganiser** класса добавьте следующие переменные:

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

6.  Затем добавьте **Awake()** и **Start()** методы:

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

7.  Добавьте следующий метод, отвечает за создание программ-роботов объект в сцене и настройка параметров и компонентов:

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

7.  Добавьте следующий метод, отвечает за создание объект пользовательского интерфейса в сцене, представляющий ответы от программ-роботов:

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

8.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.
9.  В редакторе Unity перетащите **SceneOrganiser** сценарий из папки скриптов Main Camera. Компонент Organiser сцены должен появиться в объекте Main Camera, как показано на рисунке ниже.

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Глава 13 – перед сборкой

Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш HoloLens.
Прежде чем сделать, убедитесь, что:

-   Все параметры, упомянутые в [ **Глава 4** ](#Chapter-4-–-Set-up-the-unity-project) заданы правильно. 
-   Сценарий **SceneOrganiser** присоединяется к **Main Camera** объекта. 
-   В **программ-роботов** класса, убедитесь, что вы вставили вашей **программ-роботов секретный ключ** в **botSecret** переменной.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Глава 14 — сборки и передайте в HoloLens

Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.

1.  Перейдите к **параметры сборки**, **файл > Параметры сборки...** .
2.  Из **параметры построения** окно, нажмите кнопку **построения**.

    ![Создание приложения из Unity](images/AzureLabs-Lab312-38.png)

3.  Если не сделали, установите **Unity C# проекты**.
4.  Щелкните **Сборка**. Unity приведет к запуску **проводнике** окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в. Создайте эту папку и назовите его **приложения**. Затем с помощью **приложения** щелкните папку, **Выбор папки**. 
5.  Unity начнется построение проекта для **приложения** папки. 
6.  Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).

## <a name="chapter-15--deploy-to-hololens"></a>Глава 15 – развертывание в HoloLens

Для развертывания на HoloLens:

1.  Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика**. Выполните указанные ниже действия.

    1. Хотя носить вашей HoloLens, откройте **параметры**.
    2. Перейдите к **сеть и Интернет > Wi-Fi > Дополнительные параметры**
    3. Примечание **IPv4** адрес.
    4. Затем перейдите к **параметры**, а затем в **обновление и безопасность > для разработчиков** 
    5. Включен режим разработчика.

2.  Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.
3.  В **конфигурации решения** выберите **Отладка**.
4.  В **платформа решения**выберите **x86**, **удаленный компьютер**. 

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Перейдите к **меню "сборка"** и щелкнуть **развернуть решение**, чтобы загрузить неопубликованное приложение для вашего HoloLens.
6.  Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!

    > [!NOTE]
    > Чтобы развернуть иммерсивных гарнитура, переключите **платформа решения** для *локального компьютера*и задайте **конфигурации** для *Отладка*, с *x86* как **платформы**. Затем развернуть на локальный компьютер, с помощью **меню "сборка"**, выбрав *развернуть решение*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Глава 16 – с помощью приложения на HoloLens

- Сразу после запуска приложения, вы увидите бота как синий сферы перед глазами.

- Используйте **коснитесь жест** хотя gazing в сферу, чтобы начать диалог. 
 
- Ожидания для диалога для запуска (пользовательского интерфейса будет выведено сообщение, когда это случается). После получения вводное сообщение от программ-роботов, снова коснитесь на бота, он будет красным цветом и начать прослушивание ваш голос. 

- После остановки разговор, приложение будет отправлять сообщения боту, и вы своевременно получите ответ, который будет отображаться в пользовательском Интерфейсе. 

- Повторите процедуру, чтобы отправлять дополнительные сообщения бота (необходимо коснитесь каждый раз, когда вы хотите отправить сообщение).

Этот диалог показано, как Bot можно сохранить сведения (имя), пока также обеспечение известные данные (например, элементы на складе).

#### <a name="some-questions-to-ask-the-bot"></a>Некоторые вопросы, которые можете попросить бота:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Готового приложения Web App программ-роботов (версия 4)

Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Azure Web App, программ-роботов, Microsoft Bot Framework версии 4.

![Конечный продукт](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Упражнения премии

### <a name="exercise-1"></a>Упражнение 1

Структура диалога в этой лабораторной работе является очень простым. Используйте Microsoft LUIS для Наделите своего бота возможности распознавания естественного языка.

### <a name="exercise-2"></a>Упражнение 2

В этом примере не поддерживает завершение диалога и его перезапуск. Чтобы сделать программ-роботов, функцию завершения, попробуйте реализовать закрытия для диалога.
