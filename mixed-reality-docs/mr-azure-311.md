---
title: MR и Azure 311 — Microsoft Graph
description: Пройдите этот курс, чтобы узнать, как использовать Microsoft Graph и подключиться к данным, которые повышают производительность, в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, Microsoft Graph, hololens, иммерсивное, VR
ms.openlocfilehash: 775971c4e4289d2dc963dfa2bf033192d9f3489e
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047206"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

# <a name="mr-and-azure-311---microsoft-graph"></a>MR и Azure 311 — Microsoft Graph

В этом курсе вы узнаете, как использовать *Microsoft Graph* для входа в учетная запись Майкрософт с помощью безопасной проверки подлинности в приложении смешанной реальности. Затем вы получите и отобразите запланированные собрания в интерфейсе приложения.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* — это набор интерфейсов API, предназначенных для обеспечения доступа ко многим службам Майкрософт. Корпорация Майкрософт описывает Microsoft Graph как матрица ресурсов, Соединенных связями, то есть позволяет приложению получать доступ ко всем данным о подключенных пользователях. Дополнительные сведения см. на [странице Microsoft Graph](https://developer.microsoft.com/graph).

Разработка будет включать в себя создание приложения, в котором пользователю будет предложено Взгляните на сферу, а затем коснуться сферы, которая предложит пользователю безопасно войти в учетная запись Майкрософт. После входа в учетную запись пользователь увидит список собраний, запланированных на данный день.

Прополнив этот курс, вы получите приложение HoloLens для смешанной реальности, которое сможет сделать следующее:

1.  С помощью жеста TAP Коснитесь объекта, который предложит пользователю войти в учетную запись Майкрософт (выход из приложения для входа в систему, а затем снова вернуться в приложение).
2.  Просмотр списка собраний, запланированных на данный день. 

В приложении вы будете выполнять интеграцию результатов с вашей структурой. Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity. Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> MR и Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#. Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018). Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.

Для этого курса рекомендуется следующее оборудование и программное обеспечение:

- ПК для разработки
- [Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK для Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Доступ к Интернету для установки Azure и Microsoft Graph получение данных
- Допустимая **учетная запись Майкрософт** (личная или рабочая или учебная)
- Несколько собраний, запланированных на текущий день, с использованием той же учетной записи Майкрософт

### <a name="before-you-start"></a>Перед началом

1.  Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).
2.  Настройка и тестирование HoloLens. Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя). 

Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).

Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Глава 1. Создание приложения на портале регистрации приложений

Для начала вам потребуется создать и зарегистрировать приложение на **портале регистрации приложений**.

В этой главе вы также найдете ключ службы, который позволит выполнять вызовы *Microsoft Graph* для доступа к содержимому вашей учетной записи.

1.  Перейдите на [портал регистрации приложений Майкрософт](https://apps.dev.microsoft.com) и войдите с помощью учетной записи Майкрософт. После входа вы будете перенаправлены на **портал регистрации приложений**.

2.  В разделе **Мои приложения** нажмите кнопку **Добавить приложение**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **Портал регистрации приложений** может выглядеть по-разному в зависимости от того, работал ли ранее *Microsoft Graph*. На следующих снимках экрана показаны эти различные версии.

3.  Добавьте имя приложения и нажмите кнопку **создать**.

    ![](images/AzureLabs-Lab311-03.png)

4.  После создания приложения вы будете перенаправлены на главную страницу приложения. Скопируйте **идентификатор приложения** и запишите это значение в безопасном месте, вы будете использовать его вскоре в своем коде.

    ![](images/AzureLabs-Lab311-04.png)

5.  В разделе **платформы** убедитесь, что отображается **собственное приложение** . Если *не* щелкнуть **Добавить платформу** и выбрать **собственное приложение**.

    ![](images/AzureLabs-Lab311-05.png)

6.  Прокрутите вниз на той же странице и в разделе, который называется **Microsoft Graph** разрешениями, необходимо добавить дополнительные разрешения для приложения. Щелкните **Добавить** рядом с **делегированными**разрешениями.

    ![](images/AzureLabs-Lab311-06.png)

7.  Так как вы хотите, чтобы приложение поменяло доступ к календарю пользователя, установите флажок **календари. чтение** и нажмите кнопку **ОК**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Прокрутите вниз и нажмите кнопку **сохранить** .

    ![](images/AzureLabs-Lab311-08.png)

9.  Сохранение будет подтверждено, и вы можете выйти из **портала регистрации приложений**.

## <a name="chapter-2---set-up-the-unity-project"></a>Глава 2. Настройка проекта Unity

Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.

1.  Откройте *Unity* и нажмите кнопку **создать**.

    ![](images/AzureLabs-Lab311-09.png)

2.  Необходимо указать имя проекта Unity. Вставьте **мсграфмр**. Убедитесь, что для шаблона проекта задано значение **3D**. Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше). Затем нажмите кнопку **создать проект**.

    ![](images/AzureLabs-Lab311-10.png)

3.  При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**. Перейдите к разделу **изменение** > **настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**. Измените **Редактор внешних скриптов** на **Visual Studio 2017**. Закройте окно **настройки** .

    ![](images/AzureLabs-Lab311-11.png)

4.  Перейдите в раздел**параметры сборки** **файлов** > и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.

    ![](images/AzureLabs-Lab311-12.png)

5.  Несмотря на то, что все еще находятся в**параметрах сборки** **файлов** > , убедитесь, что:

    1. **Целевое устройство** имеет значение **HoloLens**
    2. Для **типа сборки** задано значение **D3D**
    3. **Пакет SDK** установлен в значение " **Последняя установка** "
    4. Для **версии Visual Studio** установлено значение " **Последняя установка** "
    5. **Сборка и запуск** настроены на **локальный компьютер**
    6. Сохраните сцену и добавьте ее в сборку.

        1. Для этого выберите **Добавить открытые сцены**. Появится окно сохранения.

            ![](images/AzureLabs-Lab311-13.png)

        2. Создайте новую папку для этой и любой будущей сцены. Нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».

            ![](images/AzureLabs-Lab311-14.png)

        3. Откройте только что созданную папку **сцены** , а затем в поле *имя файла*: введите **MR_ComputerVisionScene**, а затем нажмите кнопку **сохранить**.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Помните, что сцены Unity необходимо сохранять в папке Assets , так как они должны быть связаны с проектом Unity. Создание папки «сцены» (и других аналогичных папок) — типичный способ структуризации проекта Unity.

    7.  Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.

6.  В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* . 

    ![](images/AzureLabs-Lab311-16.png)

7. На этой панели необходимо проверить несколько параметров:

    1. На вкладке **другие параметры** выполните следующие действия.

        1.  **Создание сценариев** **Версия среды выполнения** должна быть экспериментальной (эквивалент .NET 4,6), что вызовет необходимость перезапуска редактора.

        2. **Серверная часть сценариев** должна быть **.NET**

        3. **Уровень совместимости API** должен быть **.NET 4,6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  На вкладке **Параметры публикации** в разделе **возможности**установите флажок:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**) Проверьте, **поддерживается**ли **пакет SDK для Windows Mixed Reality** .

        ![](images/AzureLabs-Lab311-19.png)

8.  Вернувшись в *параметры сборки*, *проекты C# Unity* больше не заключаются. Установите флажок рядом с этим.

9.  Закройте окно *параметры сборки* .

10.  Сохраните сцену и проект (**файл** > **сохранить сцены/файл** > **сохранить проект**).

## <a name="chapter-3---import-libraries-in-unity"></a>Глава 3. импорт библиотек в Unity

> [!IMPORTANT]
> Если вы хотите пропустить компонент *установки Unity* , установленный в этом курсе, и продолжить работу с кодом, скачайте этот [Azure-MR-311. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в [главе 5 ](#chapter-5---create-meetingsui-class).

Чтобы использовать *Microsoft Graph* в Unity, необходимо использовать библиотеку DLL **Microsoft. Identity. Client** . Можно использовать пакет SDK для Microsoft Graph, однако после сборки проекта Unity потребуется добавить пакет NuGet (то есть редактирует проект после сборки). Проще импортировать необходимые библиотеки DLL непосредственно в Unity.

> [!NOTE]
> В Unity существует известная ошибка, которая требует перенастройки подключаемых модулей после импорта. Эти действия (4-7 в этом разделе) больше не понадобятся после устранения ошибки.

Чтобы импортировать *Microsoft Graph* в собственный проект, [скачайте файл MSGraph_LabPlugins. zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Этот пакет был создан с использованием версий библиотек, которые были проверены.

Если вы хотите узнать больше о том, как добавить пользовательские библиотеки DLL в проект Unity, [перейдите по этой ссылке](https://docs.unity3d.com/Manual/UsingDLL.html).

Чтобы импортировать пакет, выполните следующие действия.

1.  Добавьте пакет Unity в Unity с помощью команды меню**настраиваемый пакет** **Импорт** >  **активов** > . Выберите только что скачанный пакет.

2.  В появившемся окне **Импорт пакета Unity** убедитесь, что выбраны все компоненты **подключаемых модулей** (включая).

    ![](images/AzureLabs-Lab311-20.png)

3.  Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.

4.  Перейдите в папку **мсграф** в разделе **подключаемые модули** на *панели проект* и выберите подключаемый модуль **Microsoft. Identity. Client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  Выбрав *подключаемый модуль* , убедитесь, что **все платформы** не установлены, убедитесь, что флажок **всаплайер** также не установлен, а затем нажмите кнопку **Применить**. Это необходимо только для того, чтобы убедиться, что файлы настроены правильно.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Пометка этих подключаемых модулей настраивает их для использования только в редакторе Unity. В папке WSA имеется другой набор библиотек DLL, который будет использоваться после экспорта проекта из Unity в качестве универсального приложения Windows.

6.  Далее необходимо открыть папку **WSA** в папке **мсграф** Вы увидите копию того же файла, который вы только что настроили. Выберите файл, а затем в инспекторе:

    -   Убедитесь, что **все платформы** не **установлены и установлен** **флажок** **только** **всаплайер** .

    -   Убедитесь, что **пакет SDK** имеет значение **UWP**, а для **серверной части скрипта** задано значение **net** .

    -   Убедитесь, что флажок **не обрабатывать** **установлен**.

        ![](images/AzureLabs-Lab311-23.png)

7.  Щелкните **Применить**.

## <a name="chapter-4---camera-setup"></a>Глава 4. Настройка камеры

В этой главе вы настроите основную камеру для сцены:

1.  На *панели Иерархия*выберите **основную камеру**.

2.  После выбора вы сможете увидеть все компоненты **основной камеры** на панели *инспектора* .

    1.  **Объект Camera** должен называться **основной камерой** (Обратите внимание на орфографию!)

    2.  Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на правописание).

    3.  Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .

    4.  Установить для чистых флагов **сплошной цвет**

    5.  Установить черный **цвет фона** для компонента камеры **, альфа 0** **(шестнадцатеричный код: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  Итоговая структура объектов на *панели Иерархия* должна выглядеть так, как показано на рисунке ниже:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Глава 5. Создание класса Митингсуи

Первый сценарий, который необходимо создать, — это **митингсуи**, который отвечает за размещение и заполнение пользовательского интерфейса приложения (приветственное сообщение, инструкции и сведения о собраниях).

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши папку **Assets** на *панели проект*, а затем выберите **создать** > **папку**. Назовите папку **Scripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Откройте папку **Scripts** , а затем в этой папке щелкните правой кнопкой мыши, **Создайте**  >   **C# скрипт**. Назовите сценарий **митингсуи.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Дважды щелкните новый скрипт **митингсуи** , чтобы открыть его в *Visual Studio*.

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

6.  Затем замените метод **Start ()** и добавьте метод спящего режима **()** . Они будут вызываться при инициализации класса:

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

7.  Добавьте методы, отвечающие за создание *пользовательского интерфейса совещаний* , и заполните его текущими собраниями по запросу:

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

8. **Удалите** метод **Update ()** и **Сохраните изменения** в Visual Studio перед возвратом в Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Глава 6. Создание класса Graph

Следующий скрипт для создания — это сценарий **графа** . Этот сценарий отвечает за выполнение вызовов для проверки подлинности пользователя и получение запланированных собраний за текущий день из календаря пользователя.

Чтобы создать этот класс, сделайте следующее:

1.  Дважды щелкните папку Scripts , чтобы открыть ее.

2.  Щелкните правой кнопкой мыши внутри папки Scripts и выберите команду **создать**  >   **C# скрипт**. Присвойте имя **графу**скрипта.

3.  Дважды щелкните скрипт, чтобы открыть его в Visual Studio.

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
    > Обратите внимание, что части кода в этом скрипте заключены в оболочку для [директив предварительной компиляции](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html). Это позволяет избежать проблем с библиотеками при построении решения Visual Studio.

5.  Удалите методы **Start ()** и **Update ()** , так как они не будут использоваться.

6.  За пределами класса **Graph** вставьте следующие объекты, которые необходимы для десериализации объекта JSON, представляющего ежедневные запланированные собрания:

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

7.  В классе **Graph** добавьте следующие переменные:

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
    > Измените значение **AppID** , чтобы оно было **идентификатором приложения** , записанным в  **[главе 1](#chapter-1---create-your-app-in-the-application-registration-portal), шаг 4**. Это значение должно совпадать со значением, отображаемым на **портале регистрации приложений** на странице регистрации приложения.

8.  В классе **Graph** добавьте методы **сигнинасинк ()** и **акуиретокенасинк ()** , которые предложит пользователю вставить учетные данные для входа.

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

    1.  **Буилдтодайкалендарендпоинт ()** , который создает URI, указывающий день, и интервал времени, в который извлекаются запланированные собрания.

    2.  **Листмитингсасинк ()** , которая запрашивает запланированные собрания *Microsoft Graph*.

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

10. Вы завершили выполнение скрипта **Graph** . **Сохраните изменения** в Visual Studio перед возвратом в Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Глава 7. Создание скрипта Газеинпут

Теперь создадим **газеинпут**. Этот класс обрабатывает и отслеживает взгляд пользователя, используя **райкаст** , поступающий от **основной камеры**, проецирование вперед.

Чтобы создать скрипт, выполните следующие действия.

1.  Дважды щелкните папку Scripts , чтобы открыть ее.

2.  Щелкните правой кнопкой мыши внутри папки Scripts и выберите команду **создать**  >   **C# скрипт**. Назовите сценарий **газеинпут**.

3.  Дважды щелкните скрипт, чтобы открыть его в Visual Studio.

4.  Измените код пространства имен, чтобы он соответствовал приведенному ниже, вместе с добавлением **\[тега System.\]Serializable**над классом **газеинпут** , чтобы его можно было сериализовать:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  В классе **газеинпут** добавьте следующие переменные:

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

6.  Добавьте метод **креатекурсор ()** , чтобы создать курсор HoloLens в сцене, и вызовите метод из метода **Start ()** :

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

7.  Следующие методы позволяют Райкасту взгляда и отслеживание объектов с сортировкой.

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

8.  **Сохраните изменения** в Visual Studio перед возвратом в Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Глава 8. Создание класса взаимодействий

Теперь потребуется создать скрипт **взаимодействия** , который отвечает за:

-   Обработка взаимодействия **касания** и **обзора камеры**, которая позволяет пользователю взаимодействовать с журналом "Кнопка" в сцене.

-   Создание входного объекта "Кнопка" в сцене для пользователя, с которым будет взаимодействовать.

Чтобы создать скрипт, выполните следующие действия.

1.  Дважды щелкните папку Scripts , чтобы открыть ее.

2.  Щелкните правой кнопкой мыши внутри папки Scripts и выберите команду **создать**  >   **C# скрипт**. Назовите скрипт **взаимодействия**.

3.  Дважды щелкните скрипт, чтобы открыть его в Visual Studio.

4.  Вставьте следующие пространства имен:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Измените наследование класса **взаимодействия** , используя неизменное *поведение* , на **газеинпут**.

    ~~Взаимодействие с открытым классом: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  Внутри класса **взаимодействия** вставьте следующую переменную:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Замените метод **Start** ; Обратите внимание, что это метод переопределения, который вызывает метод класса взгляда Base. **Start ()** будет вызываться при инициализации класса, регистрации для распознавания ввода и создании *кнопки* входа в сцене:

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

8.  Добавьте метод **креатесигнинбуттон ()** , который создаст экземпляр *кнопки* входа в сцене и установит его свойства:

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

9.  Добавьте метод **GestureRecognizer_Tapped ()** , отвечающий на событие *TAP* User.

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

10. **Удалите** метод **Update ()** , а затем **Сохраните изменения** в Visual Studio перед возвратом в Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Глава 9. Настройка ссылок на скрипты

В этой главе необходимо разместить сценарий **взаимодействия** на **основной камере**. Затем этот скрипт будет обрабатывать размещение других сценариев, где они должны быть.

-  В папке **скрипты** на *панели проект*перетащите диалоговые окна **взаимодействия** сценария в **основной объект Camera** , как показано на рисунке ниже.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Глава 10. Настройка тега

Код, обрабатывающий взгляд, будет использовать тег **сигнинбуттон** для указания объекта, с которым пользователь будет взаимодействовать для входа в *Microsoft Graph*.

Чтобы создать тег, выполните следующие действия.

1.  В редакторе Unity щелкните **главную камеру** на *панели Иерархия*.

2.  На *панели инспектора* щелкните *тег* **маинкамера** , чтобы открыть раскрывающийся список. Щелкните **Добавить тег...**

    ![](images/AzureLabs-Lab311-30.png)

3.  **+** Нажмите кнопку.

    ![](images/AzureLabs-Lab311-31.png)

4.  Запишите имя тега как **сигнинбуттон** и нажмите кнопку Сохранить.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Глава 11. Создание проекта Unity для UWP

Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.

1.  Перейдите к *параметры сборки* (**файл*>*построения параметры**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Если это еще не так, то тактовые **проекты Unity на C\#** .

3.  Щелкните **Сборка**. Unity запустит окно **проводника** , в котором необходимо создать, а затем выбрать папку для сборки приложения. Создайте эту папку сейчас и назовите ее **app**Name. Затем выберите папку **приложения** и щелкните **выбрать папку**.

4.  Unity начнет сборку проекта в папку **приложения** .

5.  После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).

## <a name="chapter-12---deploy-to-hololens"></a>Глава 12. Развертывание в HoloLens

Для развертывания на HoloLens выполните следующие действия.

1.  Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика.** Выполните указанные ниже действия.

    1.  Людьми HoloLens, откройте **Параметры**.

    2.  Выберите сетевые &**Дополнительные параметры** **сети Интернет** > **Wi-Fi** > 

    3.  Запишите **IPv4** -адрес.

    4.  Затем вернитесь к параметрами **Обновите & безопасности** > **для разработчиков** .

    5.  Задайте **режим разработчика на**.

2.  Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.

3.  В **конфигурации решения** выберите **Отладка**.

4.  На **платформе решения**выберите **x86, удаленный компьютер**. Вам будет предложено вставить **IP-адрес** удаленного устройства (в данном случае это HoloLens).

    ![](images/AzureLabs-Lab311-34.png)

5.  Перейдите в меню **Сборка** и щелкните **Развернуть решение** , чтобы загружать неопубликованные приложение в HoloLens.

6.  Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.

## <a name="your-microsoft-graph-hololens-application"></a>Приложение Microsoft Graph HoloLens

Поздравляем, вы создали приложение смешанной реальности, которое использует Microsoft Graph для чтения и просмотра данных календаря пользователя.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Премиальные упражнения

### <a name="exercise-1"></a>Упражнение 1

Использование Microsoft Graph для просмотра других сведений о пользователе

-   Адрес электронной почты пользователя, номер телефона или изображение профиля

### <a name="exercise-1"></a>Упражнение 1

Реализуйте голосовое управление для навигации по Microsoft Graph пользовательскому интерфейсу.
