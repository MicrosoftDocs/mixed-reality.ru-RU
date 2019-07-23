---
title: Г-н и Azure 311 - Microsoft Graph
description: Выполните этот курс поможет вам научиться использовать Microsoft Graph и подключения к данным, влияющим на производительность приложения смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, microsoft graph, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694528"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

# <a name="mr-and-azure-311---microsoft-graph"></a>Г-н и Azure 311 - Microsoft Graph

В рамках этого курса вы узнаете, как использовать *Microsoft Graph* для входа в учетную запись Майкрософт, с помощью безопасной проверки подлинности в приложении смешанной реальности. Затем извлечения и отображения запланированных собраниях в интерфейсе приложения.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* — это набор API-интерфейсы, обеспечивающие доступ к множеству служб корпорации Майкрософт. Майкрософт описывает Microsoft Graph как матрицу, соединенным отношениями, это означает, что он позволяет приложению получить доступ к все виды данных подключенного пользователя. Дополнительные сведения см. в статье [страницы Microsoft Graph](https://developer.microsoft.com/graph).

Разработки будет включать создание приложения, где пользователю будет рекомендовано для помощи в, а затем нажмите сфера, который предложит пользователю безопасно входить в систему с учетной записью Майкрософт. После входа в систему с учетной записью, пользователь будет иметь возможность просмотреть список встреч, запланированных на день.

После выполнения этого курса, у вас будет смешанной реальности HoloLens приложения, который будет осуществлять следующее:

1.  С помощью жеста касания, коснитесь кнопки на объект, который предложит пользователю выполнять вход в учетную запись Майкрософт (перемещение из приложения для входа и затем обратно в приложение).
2.  Просмотрите список встреч, запланированных на день. 

В приложении зависит от пользователя о том, как интегрировать результаты проектированию. Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity. Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> Г-н и Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#. Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.). Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.

Рекомендуется следующее оборудование и программное обеспечение для этого курса:

- Компьютере разработки
- [Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Объект [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Доступ к Интернету для настройки Azure и получения данных Microsoft Graph
- Является допустимым **учетной записи Майкрософт** (личные или рабочие или учебные учетные записи)
- Несколько собраний, запланировано на текущий день, с использованием одной и той же учетной записи Майкрософт

### <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).
2.  Настроить и проверить ваш HoloLens. Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя). 

Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).

Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Глава 1 - Создание приложения на портале регистрации приложений

Начнем с того, необходимо будет создать и зарегистрировать приложение в **портал регистрации приложений**.

В этой главе вы также найдете ключ службы, который позволит вам выполнять вызовы к *Microsoft Graph* для доступа к содержимому вашей учетной записи.

1.  Перейдите к [портале регистрации приложений Майкрософт](https://apps.dev.microsoft.com) и войдите в систему с учетной записью Майкрософт. После входа, вы будете перенаправлены к **портал регистрации приложений**.

2.  В **моих приложений** щелкните кнопку **Добавление веб-приложения**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **Портал регистрации приложений** может выглядеть иначе, в зависимости от того, является ли вы ранее работали с *Microsoft Graph*. Ниже снимках экрана отображают эти разные версии.

3.  Добавьте имя для приложения и выберите **создать**.

    ![](images/AzureLabs-Lab311-03.png)

4.  После создания приложения, вы будете перенаправлены на главную страницу приложения. Копировать **идентификатор приложения** и обязательно запишите это значение в безопасном месте, он будет использоваться только в коде.

    ![](images/AzureLabs-Lab311-04.png)

5.  В **платформ** разделе, убедитесь, что **собственное приложение** отображается. Если *не* щелкните **Добавление платформы** и выберите **собственное приложение**.

    ![](images/AzureLabs-Lab311-05.png)

6.  Прокрутите вниз, в той же странице и в разделе **разрешения Microsoft Graph** необходимо будет добавить дополнительные разрешения для приложения. Щелкните **добавить** рядом с полем **делегированные разрешения**.

    ![](images/AzureLabs-Lab311-06.png)

7.  Так как требуется приложению доступ к календарю пользователя, установите флажок называется **Calendars.Read** и нажмите кнопку **ОК**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Прокрутите вниз и нажмите кнопку **Сохранить** кнопки.

    ![](images/AzureLabs-Lab311-08.png)

9.  Сохранения будет подтвержден и вы можете выйти из **портал регистрации приложений**.

## <a name="chapter-2---set-up-the-unity-project"></a>Глава 2 - Настройка проекта Unity

Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.

1.  Откройте *Unity* и нажмите кнопку **New**.

    ![](images/AzureLabs-Lab311-09.png)

2.  Необходимо указать имя проекта Unity. Вставить **MSGraphMR**. Убедитесь, что шаблон проекта присваивается **3D**. Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги). Щелкните **создать проект**.

    ![](images/AzureLabs-Lab311-10.png)

3.  С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**. Перейдите к **изменить** > **предпочтения** и затем в окне «Новый» перейдите к **внешние средства**. Изменение **внешнего редактора скриптов** для **Visual Studio 2017**. Закрыть **предпочтения** окна.

    ![](images/AzureLabs-Lab311-11.png)

4.  Перейдите к **файл** > **параметры построения** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** Чтобы применить выбранные параметры.

    ![](images/AzureLabs-Lab311-12.png)

5.  Оставаясь в **файл** > **параметры построения**, убедитесь, что:

    1. **Целевое устройство** присваивается **HoloLens**
    2. **Тип сборки** присваивается **D3D**
    3. **Пакет SDK для** присваивается **самую новую установленную**
    4. **Версия Visual Studio** присваивается **самую новую установленную**
    5. **Сборка и запуск** присваивается **локального компьютера**
    6. Сохраните сцены и добавить его к сборке.

        1. Это сделать, выбрав **добавьте откройте сцены**. Сохранение окно будет отображаться.

            ![](images/AzureLabs-Lab311-13.png)

        2. Создайте новую папку и все будущие, сцены. Выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **MR_ComputerVisionScene**, нажмите кнопку **Сохранить** .

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Следует помнить, что необходимо сохранить в Unity кадром *активы* папку, так как они должны быть связаны с проектом Unity. Создание папки сцены (и другие аналогичные папки) — это типичный способ структурирования проекта Unity.

    7.  Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.

6.  В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится. 

    ![](images/AzureLabs-Lab311-16.png)

7. В этой панели необходимо проверить некоторые настройки:

    1. В **другие параметры** вкладке:

        1.  **Scripting** **версии среды выполнения** должно быть **экспериментальные** (.NET 4.6 эквивалент), что вызовет необходимость перезапуска редактора.

        2. **Создание сценариев серверной части** должно быть **.NET**

        3. **Уровень совместимости API** должно быть **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  В рамках **параметров публикации** в списке **возможности**, проверьте:

        - **internetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Далее панели в **параметры XR** (под **параметры публикации**), проверьте **поддерживается виртуальной реальности**, убедитесь, что **Windows Mixed Reality Пакет SDK** добавляется.

        ![](images/AzureLabs-Lab311-19.png)

8.  Вернитесь в *параметры построения*, *Unity C# проекты* больше не отображается серым, установите флажок возле это.

9.  Закрыть *параметры построения* окна.

10.  Сохраните сцену и проекта (**ФАЙЛ** > **сохранить СЦЕНЫ / FILE** > **сохранить ПРОЕКТ**).

## <a name="chapter-3---import-libraries-in-unity"></a>Глава 3 - библиотеки импорта в Unity

> [!IMPORTANT]
> Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 5](#chapter-5---create-meetingsui-class).

Для использования *Microsoft Graph* в Unity, необходимо использовать **Microsoft.Identity.Client** библиотеки DLL. Можно использовать пакет SDK для Microsoft Graph, однако потребуется Добавление пакета NuGet после построения проекта Unity (то есть редактирования после построения проекта). Он считается проще импортировать необходимые библиотеки DLL непосредственно в Unity.

> [!NOTE]
> В Unity, который требует подключаемых модулей, чтобы повторно настроить после импорта в настоящее время имеется известная проблема. Эти шаги (4 – 7 в этом разделе), не будет обязательным после устранения ошибки.

Чтобы импортировать *Microsoft Graph* в проект, [Загрузите файл MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Этот пакет был создан с версиями библиотек, которые были протестированы.

Если вы хотите узнать больше о том, как добавить особые DLL-файлы в проект Unity [перейдите по этой ссылке](https://docs.unity3d.com/Manual/UsingDLL.html).

Чтобы импортировать пакет:

1.  Добавьте пакет Unity Unity с помощью **активы** > **Импорт пакета** > **пользовательского пакета** пункт меню. Выберите пакет, который вы только что загрузили.

2.  В **Импорт пакета Unity** который появится убедитесь, что все, что в разделе (вплоть до) **подключаемые модули** выбран.

    ![](images/AzureLabs-Lab311-20.png)

3.  Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.

4.  Перейдите к **MSGraph** папке **подключаемые модули** в *панель проекта* и выберите подключаемый модуль **Microsoft.Identity.Client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  С помощью *подключаемый модуль* выбран, убедитесь, что **Any платформы** не установлен, а затем убедитесь, что **WSAPlayer** также не установлен, а затем щелкните **применить**. Это, чтобы убедиться, что файлы настроены правильно.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Пометка этих подключаемых модулей позволяет настроить их только для использования в редакторе Unity. Существует другой набор библиотек DLL в папке WSA, которая будет использоваться после проект будет экспортирован из Unity как универсальное приложение Windows.

6.  Затем необходимо открыть **WSA** папку, в пределах **MSGraph** папки. Вы увидите копию тот же файл, который вы только что настроили. Выберите файл, а затем в окне инспектора:

    -   Убедитесь, что **Any платформы** — **unchecked**и что **только** **WSAPlayer** — **проверяется**.

    -   Убедитесь, **SDK** имеет значение **UWP**, и **сценариев серверной части** присваивается **точка Net**

    -   Убедитесь, что **не обрабатывать** — **проверяется**.

        ![](images/AzureLabs-Lab311-23.png)

7.  Щелкните **Применить**.

## <a name="chapter-4---camera-setup"></a>Глава 4 – Настройка камеры

Во время этой главе вы настроите Main Camera часть сцены:

1.  В *панели иерархии*выберите **Main Camera**.

2.  После выбора можно видеть все компоненты **Main Camera** в *инспектор* панели.

    1.  **Объекта Camera** должен иметь имя **Main Camera** (Обратите внимание, правильность написания!)

    2.  Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания!)

    3.  Убедитесь, что **преобразование положения** присваивается **0, 0, 0**

    4.  Задайте **очистить флаги** для **сплошным цветом**

    5.  Задайте **цвет фона** компонента камеры для **черная, альфа-канал 0** **(шестнадцатеричный код: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  Структура результирующий объект в *панели иерархии* должно быть, как показано на рисунке ниже:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Глава 5 - создание класса MeetingsUI

Первый скрипт, чтобы создать **MeetingsUI**, который отвечает за размещение и заполнения UI приложения (приветственное сообщение, инструкции и сведения собрания).

Для создания этого класса:

1.  Щелкните правой кнопкой мыши **активы** папку в *панель проекта*, а затем выберите **создать** > **папку**. Назовите папку **сценариев**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Откройте **сценарии** папки затем, внутри этой папки, щелкните правой кнопкой мыши, **создать**  >   **C# сценарий**. Назовите сценарий **MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Дважды щелкните новый **MeetingsUI** скрипт, чтобы открыть его с *Visual Studio*.

4.  Вставьте следующие пространства имен:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  Внутри класса вставьте следующие переменные:

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  Затем замените **Start()** метод и добавьте **Awake()** метод. Это будет вызываться при инициализации класса.

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  Добавьте методы, ответственный за создание *пользовательского интерфейса собрания* и заполняет ее текущего собраниях по запросу:

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Удалить** **Update()** метод, и **сохранить изменения** в Visual Studio перед возвратом к Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Глава 6 - создание класса Graph

Далее сценарий для создания **Graph** скрипта. Этот сценарий отвечает за обеспечение вызовов для проверки подлинности пользователя и получения запланированных собраний за текущий день из календаря пользователя.

Для создания этого класса:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его.

2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**. Назовите сценарий **Graph**.

3.  Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.

4.  Вставьте следующие пространства имен:

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > Обратите внимание, что фрагменты кода в этом сценарии являются оболочкой [директивы предварительной компиляции](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), это позволяет избежать проблем с библиотеками, при построении решения Visual Studio.

5.  Удалить **Start()** и **Update()** методы, так как они не будут использоваться.

6.  За пределами **Graph** класса, вставьте следующие объекты, которые являются необходимыми для десериализации объекта JSON, представляющего ежедневных запланированных собраний:

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  Внутри **Graph** добавьте следующие переменные:

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > Изменение **appId** значение должно быть **идентификатор приложения** , записанными в  **[главе 1](#chapter-1---create-your-app-in-the-application-registration-portal), шаг 4**. Это значение должно быть такой же, как в **портал регистрации приложений,** на странице регистрации приложения.

8.  В рамках **Graph** добавьте методы **SignInAsync()** и **AquireTokenAsync()** , который предложит пользователю вставлять учетные данные входа.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  Добавьте следующие два метода:

    1.  **BuildTodayCalendarEndpoint()** , который строит URI, указав день и интервал времени, в которой извлекаются запланированных собраниях.

    2.  **ListMeetingsAsync()** , которая запрашивает запланированных встреч из *Microsoft Graph*.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. Вы завершили **Graph** скрипта. **Сохраните внесенные** в Visual Studio перед возвратом к Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Глава 7 - создание скрипта GazeInput

Теперь вы создадите **GazeInput**. Этот класс обрабатывает и отслеживает взглядом пользователя, с помощью **Raycast** из **Main Camera**, проецирование вперед.

Для создания скрипта:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его.

2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**. Назовите сценарий **GazeInput**.

3.  Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.

4.  Изменить код пространства имен, чтобы соответствовать приведенному ниже, а также добавление " **\[System.Serializable\]** " тег выше вашей **GazeInput** класса, чтобы его можно было сериализовать:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  Внутри **GazeInput** добавьте следующие переменные:

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

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

6.  Добавить **CreateCursor()** метод для создания курсора HoloLens в сцене и вызовите метод из **Start()** метод:

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  Следующие методы включить взглядом Raycast и отслеживать фокус объекты.

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
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
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
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **Сохраните внесенные** в Visual Studio перед возвратом к Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Глава 8 - создать класс взаимодействия

Теперь необходимо будет создать **взаимодействия** сценарий, который отвечает за:

-   Обработка **коснитесь** взаимодействия и **помощи камеры**, который позволяет пользователю взаимодействовать с журналом в «кнопка» в сцене.

-   Создание журнала в объект «кнопка» в сцене для взаимодействия с пользователем.

Для создания скрипта:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его.

2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**. Назовите сценарий **взаимодействия**.

3.  Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.

4.  Вставьте следующие пространства имен:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Изменение порядка наследования класса **взаимодействия** класса из *MonoBehaviour* для **GazeInput**.

    ~~открытый класс взаимодействия: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  Внутри **взаимодействия** класс вставить следующую переменную:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Замените **запустить** метод; Обратите внимание, что он является методом переопределения, который вызывает метод класса «base» взглядом. **Start()** будет вызываться при инициализации класса, регистрацию для ввода распознавания и Создание входа *кнопку* в сцене:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  Добавить **CreateSignInButton()** метод, который будет создавать входа *кнопку* в сцене и задать его свойства:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  Добавить **GestureRecognizer_Tapped()** метод, который будет отвечать на запросы *коснитесь* событием пользователя.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Удалить** **Update()** метод, а затем **сохранить изменения** в Visual Studio перед возвратом к Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Глава 9 - Настройка ссылки на скрипты

В этой главе, вам потребуется разместить **взаимодействия** скрипт на **Main Camera**. Затем этот скрипт обрабатывающий размещение другие сценарии, где они должны быть.

-  Из **сценарии** папку в *панель проекта*, перетащить сценарий **взаимодействия** для **Main Camera** объекта, как на рисунке ниже.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Глава 10 - Настройка тега

Код, обрабатывающий взглядом будут работать с тега **SignInButton** для идентификации объекта, который пользователь будет взаимодействовать с для входа в *Microsoft Graph*.

Создание тега:

1.  Щелкните в редакторе Unity **Main Camera** в *панели иерархии*.

2.  В *панели Инспектора* щелкните **MainCamera** *тега* для открытия раскрывающегося списка. Щелкните **добавьте тег...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Щелкните **+** кнопки.

    ![](images/AzureLabs-Lab311-31.png)

4.  Имя тега, как написать **SignInButton** и щелкните "Сохранить".

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Глава 11 - сборки проекта Unity для универсальной платформы Windows

Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.

1.  Перейдите к *параметры сборки* (**файл*>*построения параметры**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Если не сделали, установите **Unity C\# проекты**.

3.  Щелкните **Сборка**. Unity приведет к запуску **проводнике** окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в. Создайте эту папку и назовите его **приложения**. Затем с помощью **приложения** щелкните папку, **Выбор папки**.

4.  Unity начнется построение проекта для **приложения** папки.

5.  Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).

## <a name="chapter-12---deploy-to-hololens"></a>Глава 12 - развертывание в HoloLens

Для развертывания на HoloLens:

1.  Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика.** Выполните указанные ниже действия.

    1.  Хотя носить вашей HoloLens, откройте **параметры**.

    2.  Перейдите к **сеть и Интернет** > **Wi-Fi** > **Дополнительные параметры**

    3.  Примечание **IPv4** адрес.

    4.  Затем перейдите к **параметры**, а затем в **обновление и безопасность** > **для разработчиков**

    5.  Задайте **режим разработчика на**.

2.  Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.

3.  В **конфигурации решения** выберите **Отладка**.

4.  В **платформа решения**выберите **x86, удаленный компьютер**. Вам будет предложено вставить **IP-адрес** удаленного устройства (HoloLens, таким образом, который вы записали).

    ![](images/AzureLabs-Lab311-34.png)

5.  Перейдите к **построения** меню и щелкните **развернуть решение** для загрузки неопубликованных приложений для вашей HoloLens.

6.  Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!

## <a name="your-microsoft-graph-hololens-application"></a>Приложение Microsoft Graph HoloLens

Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Microsoft Graph, для чтения и отображения данных календаря пользователя.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Упражнения премии

### <a name="exercise-1"></a>Упражнение 1

Использовать Microsoft Graph для отображения других сведений о пользователе

-   Адрес электронной почты пользователя, номер телефона, изображение профиля

### <a name="exercise-1"></a>Упражнение 1

Реализуйте управление голосовой связью для перехода в пользовательский Интерфейс Microsoft Graph.
