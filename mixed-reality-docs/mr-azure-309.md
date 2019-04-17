---
title: Г-н и 309 Azure - Application insights
description: Выполните этот курс, чтобы узнать, как для сбора аналитики в отношении поведения пользователей приложения смешанной реальности, с помощью службы Azure Application Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, application insights, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 838dbe38724d29f4c5987e2f6ac7a07231015c82
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604773"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>Г-н и Azure 309: Application insights

![конечный продукт-запуск](images/AzureLabs-Lab309-00.png)

В рамках этого курса вы узнаете, как для добавления возможностей Application Insights с приложением смешанной реальности, с помощью Azure Application Insights API для сбора аналитики о поведении пользователей.

Application Insights — службе Майкрософт, позволяя разработчикам сбора аналитики из своих приложений и управлять им с помощью портала к использованию. Аналитики может быть что угодно — от производительности для пользовательских сведений, которые вы хотите собирать. Дополнительные сведения см. в статье [страница Application Insights](https://azure.microsoft.com/services/application-insights/).

После выполнения этого курса, у вас будет приложение иммерсивных гарнитуры смешанной реальности, которое сможет выполнить следующие:

1.  Разрешает пользователю помощи и перемещать сцены.
2.  Инициировать отправку analytics для *служба Application Insights*, за счет использования взглядом и близости от объектов сцены.
3.  Приложение также будет вызывать службу, получение сведений о том, что о какой объект был к наиболее пользователем, за последние 24 часа. Этот объект будет изменить его цвет зеленый цвет.

Этот курс ознакомят вас для получения результатов из службы Application Insights в приложение на базе Unity образец. Это будет необходимо применение этих понятий в пользовательское приложение, возможно, вы разрабатываете.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> Г-н и Azure 309: Application insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens. При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens. При использовании HoloLens, вы можете заметить некоторые echo во время записи голоса.

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#. Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.). Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.

Рекомендуется следующее оборудование и программное обеспечение для этого курса:

- На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)
- [Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Наушники с помощью встроенного микрофона (если гарнитура не имеет встроенных mic, а также докладчиков)
- Доступ к Интернету для настройки Azure и получения данных Application Insights

## <a name="before-you-start"></a>Прежде чем начать

Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).

> [!WARNING] 
> Имейте в виду, данные, передаваемые *Application Insights* занимает некоторое время, поэтому будьте пациента. Если вы хотите проверить, если служба получила данные, см. статью [Глава 14](#chapter-14---the-application-insights-service-portal), где будет показано как перейти на портал.

## <a name="chapter-1---the-azure-portal"></a>Глава 1 - портала Azure

Чтобы использовать *Application Insights*, вам потребуется создать и настроить *служба Application Insights* на портале Azure.

1.  Войдите в [портала Azure](https://portal.azure.com).

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо будет создать его. Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.

2.  После входа в систему щелкните **New** в левом верхнем углу, а поиск *Application Insights*и нажмите кнопку **ввод**.

    > [!NOTE]
    > Слово **New** может были заменены **создать ресурс**, в новых порталов.

    ![Портал Azure](images/AzureLabs-Lab309-01.png)

3.  Новая страница справа будет предоставить описание *Azure Application Insights* службы. В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать ассоциацию с данным службы.

    ![Портал Azure](images/AzureLabs-Lab309-02.png)

4.  Когда вы перейдете на **создать**:

    1.  Вставить нужный **имя** для данного экземпляра службы.

    2.  Как **тип приложения**выберите **Общие**.

    3.  Выберите соответствующее **подписки**.

    4.  Выберите **группы ресурсов** или создайте новую. Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure. Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Выберите **расположение**.

    6.  Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.

    7.  Щелкните **Создать**.

        ![Портал Azure](images/AzureLabs-Lab309-03.png)

5.  Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.

6.  Уведомление будет отображаться на портале, после создания экземпляра службы.

    ![Портал Azure](images/AzureLabs-Lab309-04.png)

7.  Щелкните уведомлений для просмотра в новом экземпляре службы.

    ![Портал Azure](images/AzureLabs-Lab309-05.png)

8.  Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы. Вы перейдете на новый *служба Application Insights* экземпляра.

    ![Портал Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Не закрывайте эту веб-страницу и удобный доступ, вам будет вернитесь сюда часто, чтобы просмотреть собранные данные.

    > [!IMPORTANT]
    > Чтобы реализовать Application Insights, необходимо будет использовать конкретные значения трех (3): **Ключ инструментирования**, **идентификатор приложения**, и **ключ API**. Ниже показано, как получить эти значения из вашей службы. Обязательно запишите эти значения на пустое *Блокнот* странице, поскольку будет использовать их только в коде.

9.  Чтобы найти **ключ инструментирования**, вам потребуется прокрутите вниз список функций службы и щелкните **свойства**, показывают отображается вкладка **ключ службы**.

    ![Портал Azure](images/AzureLabs-Lab309-07.png)

10. Немного ниже **свойства**, вы найдете **доступ через API**, который нужно щелкнуть. Панель справа предоставит **идентификатор приложения** вашего приложения.

    ![Портал Azure](images/AzureLabs-Lab309-08.png)

11. С помощью **идентификатор приложения** панели все еще открыт, выберите **Создание ключа API**, при этом открывается *Создание ключа API* панели.

    ![Портал Azure](images/AzureLabs-Lab309-09.png)

12. В рамках открытым теперь *Создание ключа API* панели, введите описание, и **деления три поля**.

13. Нажмите кнопку **создания ключа**. Ваш **ключ API** будет необходимо создать и отобразить. 

    ![Портал Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Это единственный случай, когда ваш **ключ службы** будет отображаться, поэтому убедитесь, вы теперь сделать его копию.

## <a name="chapter-2---set-up-the-unity-project"></a>Глава 2 - Настройка проекта Unity

Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.

1.  Откройте *Unity* и нажмите кнопку **New**.

    ![Настройка проекта Unity](images/AzureLabs-Lab309-11.png)

2.  Введите имя проекта Unity, теперь нужно вставить **MR\_Azure\_приложения\_Insights**. Убедитесь, что *шаблона* присваивается **3D**. Задайте *расположение* в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги). Щелкните **создать проект**.

    ![Настройка проекта Unity](images/AzureLabs-Lab309-12.png)

3.  С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**. Перейдите к **изменить \> предпочтения** и затем в окне «Новый» перейдите к **внешние средства**. Изменение **внешнего редактора скриптов** для **Visual Studio 2017**. Закрыть **предпочтения** окна.

    ![Настройка проекта Unity](images/AzureLabs-Lab309-13.png)

4.  Перейдите к **файл \> параметры построения** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.

    ![Настройка проекта Unity](images/AzureLabs-Lab309-14.png)

5.  Перейдите к **файл \> параметры построения** и убедитесь, что:

    1.  **Целевое устройство** присваивается **любого устройства**

        > Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.

    2.  **Тип сборки** присваивается **D3D**

    3.  **Пакет SDK для** присваивается **самую новую установленную**

    4.  **Сборка и запуск** присваивается **локального компьютера**

    5.  Сохраните сцены и добавить его к сборке.

        1.  Это сделать, выбрав **добавьте откройте сцены**. Сохранение окно будет отображаться.

            ![Настройка проекта Unity](images/AzureLabs-Lab309-15.png)

        2. Создайте новую папку для этого и все будущие сцены, а затем щелкните **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.

            ![Настройка проекта Unity](images/AzureLabs-Lab309-16.png)

        3. Откройте только что созданный **сцены** папку, а затем в *имя файла:* текстовое поле, тип **ApplicationInsightsScene**, нажмите кнопку **Сохранить**.

            ![Настройка проекта Unity](images/AzureLabs-Lab309-17.png)

6.  Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.

7.  В **параметры построения** щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где **инспектор** находится.

    ![Настройка проекта Unity](images/AzureLabs-Lab309-18.png)

8. В этой панели необходимо проверить некоторые настройки:

    1.  В **другие параметры** вкладке:

        1.  **Scripting** **версии среды выполнения** должно быть **экспериментальные (.NET 4.6 эквивалент)**, что вызовет необходимость перезапуска редактора.

        2.  **Создание сценариев серверной части** должно быть **.NET**

        3.  **Уровень совместимости API** должно быть **.NET 4.6**

        ![Настройка проекта Unity](images/AzureLabs-Lab309-19.png)

    2.  В рамках **параметров публикации** в списке **возможности**, проверьте:

        - **internetClient**     

            ![Настройка проекта Unity](images/AzureLabs-Lab309-20.png)

    3.  Далее панели в **XR параметры** (под **параметров публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **Windows Mixed Reality Пакет SDK** добавляется.

        ![Настройка проекта Unity](images/AzureLabs-Lab309-21.png)

9.  Вернитесь в **параметры построения**, **Unity C\# проекты** больше не отображается серым, установите флажок рядом с это.

10.  Закройте окно Параметры построения.

11.  Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).


## <a name="chapter-3---import-the-unity-package"></a>Глава 3 - Импорт пакета Unity

> [!IMPORTANT]
> Если вы хотите пропустить *Настройка Unity* компоненты этого курса и по-прежнему непосредственно в код, вы можете загрузить [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html). Оно также будет содержать библиотеки DLL из следующей главе. После импорта, по-прежнему из [ **Глава 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Чтобы использовать Application Insights в Unity, необходимо импортировать библиотеку DLL для него, вместе с Newtonsoft DLL. В Unity, который требует подключаемых модулей, чтобы повторно настроить после импорта в настоящее время имеется известная проблема. Эти шаги (4 – 7 в этом разделе), не будет обязательным после устранения ошибки.

Чтобы импортировать Application Insights в свой проект, убедитесь, что у вас есть [загружен «.unitypackage», содержащий подключаемые модули](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). Затем сделайте следующее:

1.  Добавить **.unitypackage** к Unity с помощью **активы \> Импорт пакета \> пользовательского пакета** пункт меню.

2.  В **Импорт пакета Unity** который появится убедитесь, что все, что в разделе (вплоть до) **подключаемые модули** выбран.

    ![Импорт пакета Unity](images/AzureLabs-Lab309-22.png)

3.  Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.

4.  Перейдите к **Insights** папке **подключаемые модули** в проекте можно просматривать и выбирать следующие подключаемые модули *только*:

    -   Microsoft.ApplicationInsights

    ![Импорт пакета Unity](images/AzureLabs-Lab309-23.png)

5.  С этим *подключаемый модуль* выбран, убедитесь, что **Any платформы** — **unchecked**, убедитесь, что флажок **WSAPlayer** также  **unchecked**, затем нажмите кнопку **применить**. Это — просто убедитесь, что файлы настроены правильно.

    ![Импорт пакета Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Пометки подключаемых модулей, например это, настраивает их можно использовать только в редакторе Unity. Существует другой набор библиотек DLL в папке WSA, которая будет использоваться после проект будет экспортирован из Unity.

6.  Затем необходимо открыть **WSA** папку, в пределах **Insights** папки. Вы увидите копию тот же файл, который вы только что настроили. Выберите этот файл и затем в инспекторе, убедитесь, что **Any платформы** — **unchecked**, убедитесь, что флажок **только** **WSAPlayer** является **проверяется**. Щелкните **Применить**.

    ![Импорт пакета Unity](images/AzureLabs-Lab309-25.png)

7. Теперь необходимо будет выполнить **шаги 4 – 6**, но для *Newtonsoft* подключаемые модули вместо этого. См. в разделе ниже снимок экрана для результат должен выглядеть так.

    ![Импорт пакета Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Глава 4 – Настройка камеры и пользователем элементы управления

В этой главе вы настроите камеры и элементов управления позволяет пользователю см. в разделе и переместите в сцене.

1.  Щелкните правой кнопкой мыши пустую область на панели «иерархии», затем на **Создать > пустой**.

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-26.png)

2.  Переименуйте новый пустой объект GameObject для **камеры родительского**.

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-27.png)

3.  Щелкните правой кнопкой мыши пустую область на панели «иерархии», затем на **трехмерный объект**, то на **Sphere**.

4.  Переименовать сферой **правом**.

5.  Задайте **преобразование масштабирования** стрелки вправо к **0.1, 0.1, 0,1**

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-28.png)

6.  Удалить **Sphere Collider** с правой стороны, щелкнув **шестеренки** в *Sphere Collider* компонента, а затем **удалить компонент** .

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-29.png)

7.  В панели иерархии перетащите **Main Camera** и **правом** перетаскивание объектов **камеры родительского** объекта.

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-30.png)

8.  Задайте **преобразование положения** обоих **Main Camera** и **правом** объект **0, 0, 0**.

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-31.png)

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Глава 5 - Настройка объектов в сцене Unity

Теперь вы создадите некоторые основные фигуры для сцены, с помощью которого пользователь может взаимодействовать.

1.  Щелкните правой кнопкой мыши пустую область в *панели иерархии*, то на **трехмерный объект**, а затем выберите **плоскости**.

2.  Задайте плоскость **преобразование положения** для **0, -1, 0**.

3.  Задайте плоскость **преобразование масштабирования** для **5, 1, 5**.

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-33.png)

4.  Создать базовый материал для использования с вашей **плоскости** объекта, таким образом, проще видеть другие фигуры. Перейдите к вашей *панель проекта*, щелкните правой кнопкой мыши, затем **создать**, за которым следует **папку**, чтобы создать новую папку. Назовите его **материалы**.

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-34.png) ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-35.png)

5.  Откройте **материалы** папку, а затем щелкните правой кнопкой мыши щелкните **создать**, затем **материал**, чтобы создать новый материал. Назовите его **синий**.

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-36.png) ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-37.png)

6.  С новым **синий** выбран, взгляните на материал *инспектор*и нажмите кнопку прямоугольное окно вместе с **Albedo**. Выберите голубой цвет (один ниже изображен **Hex цвет: \#3592FFFF**). После выбора нажмите кнопку "Закрыть".

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-38.png)

7.  Перетащите новый материал из **материалы** папки, в только что созданный **плоскости**, в сценах (или поместите его на **плоскости** объекта в пределах  *Иерархия*).

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-39.png)

8.  Щелкните правой кнопкой мыши пустую область в *панели иерархии*, то на **трехмерного объекта, Capsule**.

    -  С помощью **Capsule** , измените его **преобразования** *позиции* для: **-10 "," 1 "," 0**.

9.  Щелкните правой кнопкой мыши пустую область в *панели иерархии*, то на **трехмерного объекта, куб**.

    -  С помощью **куба** , измените его **преобразования** *позиции* для: **0, 0, 10**.

10. Щелкните правой кнопкой мыши пустую область в *панели иерархии*, то на **трехмерного объекта, Sphere**.

    -  С помощью **Sphere** , измените его **преобразования** *позиции* для: **10, 0, 0**.

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Эти *позиции* значения: *предложения*. Вы свободны в задается расположение объектов в любое другое, то, что это удобнее для пользователя приложения, если объекты на расстоянии не слишком далеко от камеры.

11. Когда приложение запущено, необходимо иметь возможность идентифицировать объекты на сцене, чтобы добиться этого, их необходимо отметить тегами. Выберите один из объектов, а также в *инспектор* панели, щелкните **добавить тег...** , который поменяет *инспектор* с **теги & слои** панели.

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. Нажмите кнопку **+ (плюс)** символов, а затем введите имя тега, как **ObjectInScene**.

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Если вы используете другое имя для тега, необходимо гарантировать это изменение также *DataFromAnalytics*, *ObjectTrigger*, и *помощи*, более поздней версии, сценарии, чтобы ваши объекты найден и обнаружено, в сценах.

13. Тег создан необходимо применить его для всех трех объектов. Из *иерархии*, удерживайте **Shift** ключа, а затем щелкните **Capsule**, **куба**, и **Sphere**, объекты, а затем в *инспектор*, щелкните раскрывающееся меню рядом с **тега**, нажмите кнопку *ObjectInScene* тег был создан.

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Глава 6 - создание класса ApplicationInsightsTracker

Первый скрипт, чтобы создать **ApplicationInsightsTracker**, который отвечает за:

1.  Создание событий, в зависимости от действий пользователя для отправки в Azure Application Insights.

2. Создание соответствующие имена событий, в зависимости от взаимодействия с пользователем.

3. Отправка событий в экземпляре службы Application Insights.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши в *проекта панели*, затем **Создать > Папка**. Назовите папку **сценариев**.

    ![Создание класса ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Создание класса ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  С помощью **сценариев** папка создана, дважды щелкните его, чтобы открыть. Затем, внутри этой папки, щелкните правой кнопкой мыши **Создать > C\# скрипт**. Назовите сценарий **ApplicationInsightsTracker**.

3.  Дважды щелкните новый **ApplicationInsightsTracker** скрипт, чтобы открыть его с **Visual Studio**.

4.  Обновление пространства имен в верхней части скрипта как показано ниже:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  Внутри класса вставьте следующие переменные:

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > Задайте **instrumentationKey, идентификатор приложения и ключа API** значения соответствующим образом, с помощью *ключи службы* на портале Azure, как упоминалось в [главе 1](#chapter-1---the-azure-portal), шаг 9 и более поздних версий.

6.  Затем добавьте **Start()** и **Awake()** методы, которые будут вызываться при инициализации класса:

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  Добавьте методы, отвечающий за отправку событий и метрик, зарегистрированные для приложения.

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-7---create-the-gaze-script"></a>Глава 7 - создание скрипта взглядом

Далее сценарий для создания **помощи** скрипта. Этот сценарий отвечает за создание *Raycast* , будет проецироваться вперед от *Main Camera*, для обнаружения какой объект, который просматривает пользователь. В этом случае *Raycast* будет необходимо определить, если пользователь просматривает объект с **ObjectInScene** тег, а затем подсчитать как долго пользователь *gazes* на этот объект.

1.  Дважды щелкните **сценариев** папки, чтобы открыть его.

2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Назовите сценарий **помощи**.

3.  Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.

4.  Замените существующий код следующим:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  Код для **Awake()** и **Start()** методы теперь должен быть добавлен.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  Внутри **помощи** добавьте следующий код в **Update()** метод проект *Raycast* и обнаруживать попадание целевой объект:

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  Добавить **ResetFocusedObject()** метод для отправки данных **Application Insights** когда пользователь открывал объекта.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  Вы завершили **помощи** скрипта. Сохраните изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Глава 8 - создать класс ObjectTrigger

Далее необходимо создать сценарий **ObjectTrigger**, который отвечает за:

- Добавление компонентов, необходимых для конфликта в Main Camera.
- Обнаружение, если камера находится рядом с объектом, помеченным как **ObjectInScene**.

Для создания скрипта:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его.

2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** **C\# > скрипт**. Назовите сценарий **ObjectTrigger**.

3.  Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio. Замените существующий код следующим:

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Глава 9 — создать класс DataFromAnalytics

Теперь необходимо будет создать **DataFromAnalytics** сценарий, который отвечает за:

- Выборка данных аналитики, о том, какие объекта были достиг камеры больше всего.
- С помощью *ключи службы*, разрешить связь с экземпляром службы Azure Application Insights.
- Упорядочивание объектов в сцене, в соответствии с которым имеет наибольшее количество событий.
- Изменение цветом материала, наиболее approached объекта, к *зеленый*.

Для создания скрипта:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его.

2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** **C\# > скрипт**. Назовите сценарий **DataFromAnalytics**.

3.  Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.

4.  Вставьте следующие пространства имен:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Внутри скрипта вставьте следующее:

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  В рамках **DataFromAnalytics** класса, сразу после **Start()** метод, добавьте следующий метод с именем **FetchAnalytics()**. Этот метод отвечает за заполнение списка пар ключ-значение с *GameObject* и номером число событий заполнителя. Затем он инициализирует **GetWebRequest()** соподпрограмме. Структура запроса вызова *Application Insights* можно найти в этот метод также, как *URL-адрес запроса* конечной точки.

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  Прямо под **FetchAnalytics()** метод, добавьте метод с именем **GetWebRequest()**, который возвращает *IEnumerator*. Этот метод отвечает за запрос, сколько раз событие, соответствующее конкретному *GameObject*, был вызван в *Application Insights*. Если все отправленные запросы вернули, **DetermineWinner()** вызывается метод.

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  Далее метод **DetermineWinner()**, который сортирует список из *GameObject* и *Int* пары, в соответствии с наибольшее количество событий. Затем он изменяет цвет материала, *GameObject* для *зеленый* (в виде обратной связи для оно имеет наибольшие число). Откроется сообщение с результатами анализа.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  Добавьте структуру класса, который будет использоваться для десериализации объекта JSON, полученных от *Application Insights*. Добавьте эти классы в самом низу окна вашего **DataFromAnalytics** файл класса **за пределами** определения класса.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-10---create-the-movement-class"></a>Глава 10 — создать класс перемещения

**Перемещения** скрипт представляет следующий скрипт, необходимо будет создать. Он отвечает за:

- Перемещение камеры Main в соответствии с направление камеры смотрит сторону.
- Добавление всех других скриптов объектов сцены.

Для создания скрипта:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его.

2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Назовите сценарий **перемещения**.

3.  Дважды щелкните сценарий, чтобы открыть его с *Visual Studio*.

4.  Замените существующий код следующим:

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  В рамках **перемещения** класс, *ниже* пустой **Update()** метод, вставьте следующие методы, позволяющие пользователю с помощью контроллера вручную перемещать в виртуальном пространстве:

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  Наконец, добавьте вызов метода в **Update()** метод.

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Глава 11 - Настройка ссылки на скрипты

В этой главе, вам потребуется разместить **перемещения** скрипт на **камеры родительского** и задайте его ссылку целевых объектов. Затем этот скрипт обрабатывающий размещение другие сценарии, где они должны быть.

1.  Из **сценарии** папку в *панель проекта*, перетащите **перемещения** сценария **камеры родительского** объект, расположенный в  *Панель иерархии*.

    ![Настройка ссылок сценариев в сцене Unity](images/AzureLabs-Lab309-48.png)

2.  Щелкните **камеры родительского**. В *панели иерархии*, перетащите **правом** объекта из *панели иерархии* для ссылочной целевой **контроллера**в *Панели Инспектора*. Задайте **скорость пользователя** для **5**, как показано на рисунке ниже.

    ![Настройка ссылок сценариев в сцене Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Глава 12 - сборки проекта Unity

Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.

1.  Перейдите к **параметры сборки**, **(Файл > Параметры сборки...)** .

2.  Из **параметры построения** окно, нажмите кнопку **построения**.

    ![Построение проекта Unity, чтобы решение универсальной платформы Windows](images/AzureLabs-Lab309-50.png)

3.  Объект **проводнике** всплывающее окно будет окно, для расположения для сборки. Создайте новую папку (щелкнув **новую папку** в левом верхнем углу) и назовите его **ПОСТРОЕНИЯ**.

    ![Построение проекта Unity, чтобы решение универсальной платформы Windows](images/AzureLabs-Lab309-51.png)

    1.  Откройте новый **ПОСТРОЕНИЯ** папки и создайте другую папку (с помощью **новую папку** еще раз) и назовите его **MR\_Azure\_приложения\_ Insights**.

        ![Построение проекта Unity, чтобы решение универсальной платформы Windows](images/AzureLabs-Lab309-52.png)

    2.  С помощью **MR\_Azure\_приложения\_Insights** щелкните папку, **Выбор папки**. Проекта займет около минуты для построения.

4.  Следуя *построения*, **проводнике** появится расположение нового проекта.

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>Глава 13 - развертывание приложения MR_Azure_Application_Insights на компьютер

Чтобы развернуть **MR\_Azure\_приложения\_Insights** приложения на локальном компьютере:

1.  Откройте файл решения вашей **MR\_Azure\_приложения\_Insights** приложения в **Visual Studio**.

2.  В **платформа решения**выберите **x86, локальный компьютер**.

3.  В **конфигурации решения** выберите **Отладка**.

    ![Построение проекта Unity, чтобы решение универсальной платформы Windows](images/AzureLabs-Lab309-53.png)

4.  Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на компьютер.

5.  Приложения появятся в списке установленных приложений, Готово к запуску.

6. Запустите приложение смешанной реальности.

7. Перемещение сцены, приближается к объектам и просмотрев их, когда *служба Azure Insight* собрал достаточно данных событий она будет задана объект, который достиг максимально на зеленый.

> [!IMPORTANT] 
> Хотя среднего времени ожидания *событий и метрик* собираемых службой занимает около 15 минут, в некоторых случаях может занять до 1 часа.

## <a name="chapter-14---the-application-insights-service-portal"></a>Глава 14 - портале службы Application Insights

После того как перемещаемое вокруг сцены и gazed на несколько объектов вы увидите данные, собранные в *служба Application Insights* портала.

1.  Вернитесь на портал службы Application Insights.

2.  Щелкните *обозревателя метрик*.

    ![Просмотрев собранных данных](images/AzureLabs-Lab309-54.png)

3.  Она откроется на вкладке, содержащий граф, которые представляют *событий и метрик* относящиеся к приложению. Как упоминалось выше, может занять некоторое время (до 1 часа) для данных для отображения на графике

    ![Просмотрев собранных данных](images/AzureLabs-Lab309-55.png)

4.  Щелкните *строке события* в *всего событий* каждой версии приложения, чтобы просмотреть подробный разбор события со значениями их имена.

    ![Просмотрев собранных данных](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Ваш завершения приложения службы Application Insights

Поздравляем, вы создали приложение смешанной реальности, которое использует службы Application Insights для отслеживания действий пользователей в приложении.

![результат курс](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Упражнения премии

**Упражнение 1**

Попробуйте порождении процесса, а не вручную, создание объектов ObjectInScene и установить их координаты на плоскости в сценариях. Таким образом, можно также попросить Azure наиболее популярных объект был (либо из взглядом или выражение с учетом результатов) и spawn *дополнительный* одного из этих объектов.

**Упражнение 2**

Чтобы отсортировать результаты Application Insights, время, чтобы получить наиболее важные данные и реализовать эти конфиденциальные данные времени в приложении.

