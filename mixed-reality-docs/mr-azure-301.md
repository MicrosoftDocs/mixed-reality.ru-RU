---
title: Г-н и 301 Azure - перевода
description: Выполните этот курс, чтобы узнать, как реализовать Translator Text API Azure в приложениях смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, translator text API, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603608"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br>

# <a name="mr-and-azure-301-language-translation"></a>Г-н и Azure 301: систем перевода.

В рамках этого курса вы узнаете, как добавить возможности перевода приложений в смешанной реальности, с помощью Azure Cognitive Services, с помощью API перевода текстов.

![Конечный продукт](images/AzureLabs-Lab1-00.png)

API перевода текстов — перевод службы, который работает в практически в реальном времени. Службы облачных, и, с помощью вызова REST API, приложение можно сделать использовать технологии нейронный машинный перевод, перевод текста на другой язык. Дополнительные сведения см. в статье [страницы API перевода текстов Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

По завершении этого курса вы получите с приложением смешанной реальности, которое будет осуществлять следующее:

1.  Пользователь будет говорите в микрофон, подключенный к иммерсивных Гарнитура (VR) (или встроенный микрофон HoloLens).
2.  Приложение будет захвата диктовка и отправить его на API перевода текстов Azure.
3.  Результат перевода будет отображаться в группе простой пользовательский Интерфейс в сцене Unity.

Этот курс ознакомят вас для получения результатов от службы перевода в приложение на базе Unity образец. Это будет необходимо применение этих понятий в пользовательское приложение, возможно, вы разрабатываете.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> Г-н и Azure 301: систем перевода.</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens. При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens. При использовании HoloLens, вы можете заметить некоторые echo во время записи голоса.

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#. Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.). Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .

Рекомендуется следующее оборудование и программное обеспечение для этого курса:

- На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)
- [Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Наушники с помощью встроенного микрофона (если гарнитура отсутствует встроенный mic, а также докладчиков)
- Доступ к Интернету для Azure установки и перевода извлечения

## <a name="before-you-start"></a>Прежде чем начать

- Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).
- Код в этом руководстве, позволит вам для записи с микрофона устройства по умолчанию, подключенном к ПК. Убедитесь, что на устройстве "микрофон" по умолчанию имеет значение устройству, которое планируется использовать для записи голоса.
- Чтобы разрешить Систему, чтобы включить режим диктовки, перейдите в раздел **параметры > о конфиденциальности > речи, рукописного ввода и введя** и нажмите кнопку **Включение службы распознавания речи и ввода предложения**.
- При использовании микрофон и наушники – (или встроен) вашего гарнитуры, убедитесь, что параметр «После я wear Мой гарнитуры, перейдите на mic гарнитура» включена в **параметры > смешанной реальности > аудио- и речи**.

   ![Параметры смешанной реальности](images/AzureLabs-Lab1-00-5.png)

   ![Параметр "микрофон"](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Имейте в виду, что при разработке для иммерсивных гарнитура, для этой лабораторной работы, возможно возникновение проблем звуковые выходные данные на устройстве. Это из-за проблемы с Unity, в котором исправлена в более поздних версиях Unity (Unity 2018.2). Проблема не позволяет изменять на устройстве звуковые выходные данные по умолчанию во время выполнения Unity. Решения убедитесь, что выполнены описанные выше действия и закройте и снова откройте редактор, если эта проблема проявляется.

## <a name="chapter-1--the-azure-portal"></a>Глава 1 – портала Azure

Чтобы использовать Azure Translator API, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.

1.  Войдите в [портала Azure](https://portal.azure.com).

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо будет создать его. Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.

2.  После входа в систему щелкните **New** в верхнем левом углу и выполните поиск «Translator Text API». Выберите **введите**.

    ![Новый ресурс](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > Слово **New** может были заменены **создать ресурс**, в новых порталов.

3.  Новая страница будет предоставить описание *API перевода текстов* службы. В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать ассоциацию с данным службы.

    ![Создание Translator Text API службы](images/AzureLabs-Lab1-03.png)

4.  Когда вы перейдете на **создать**:

    1. Вставить нужный **имя** для данного экземпляра службы.
    2. Выберите соответствующее **подписки**.
    3. Выберите **Ценовая** подходит для вас, если это первое времени на создание *Translator текстовая служба*, уровень "бесплатный" (с именем F0) должны быть доступны для вас.
    4. Выберите **группы ресурсов** или создайте новую. Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure. Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как многому) в группе общих ресурсов).

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов). Расположение оптимально подойдет в регионе, в котором приложение будет работать. Некоторые ресурсы Azure доступны только в определенных регионах.
    6. Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.
    7. Щелкните **Создать**.

        ![Нажмите кнопку "Создать".](images/AzureLabs-Lab1-04.png)

5.  Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.
6.  Уведомление будет отображаться на портале, после создания экземпляра службы. 

    ![Azure уведомление о создании службы](images/AzureLabs-Lab1-05.png)

7.  Щелкните уведомление, чтобы изучить ваш новый экземпляр службы. 

    ![Перейдите к всплывающее окно ресурсов.](images/AzureLabs-Lab1-06.png)

8.  Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы. Откроется в новом экземпляре Translator Text API службы. 

    ![Страница службы API текст перевода](images/AzureLabs-Lab1-07.png)

9.  В этом руководстве описано приложение должно выполнять вызовы в службу, которая осуществляется с помощью ключа подписки вашей службы. 
10. Из *быстрого запуска* странице вашего *Translator Text* службы, перейдите к первому шагу *получите ключи*и нажмите кнопку **ключи** (вы можете также выполнить эту операцию, щелкнув синий гиперссылки ключи, расположенный в меню навигации служб, обозначенное с помощью значок ключа). Это позволит службе *ключи*.
11. Сделайте копию один из отображаемых разделов, так как он потребуется позже в проекте. 

## <a name="chapter-2--set-up-the-unity-project"></a>Глава 2 – Настройка проекта Unity

Настроить и проверить ваш иммерсивных гарнитуры смешанной реальности.

> [!NOTE]
> Вам не потребуется контроллеры движения курс с демороликами. Если вам требуется поддерживает настройку иммерсивных гарнитура, [выполните следующие действия](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов:

1.  Откройте *Unity* и нажмите кнопку **New**. 

    ![Начните новый проект Unity.](images/AzureLabs-Lab1-08.png)

2.  Теперь необходимо будет указать имя проекта Unity. Вставить **MR_Translation**. Убедитесь, что тип проекта присваивается **3D**. Задайте *расположение* в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги). Щелкните **создать проект**.

    ![Укажите сведения для нового проекта Unity.](images/AzureLabs-Lab1-09.png)

3.  С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**. Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**. Изменение **внешнего редактора скриптов** для **Visual Studio 2017**. Закрыть **предпочтения** окна.

    ![Обновите настройки редактора скриптов.](images/AzureLabs-Lab1-10.png)

4.  Перейдите к **файл > Параметры сборки** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.

    ![Создавайте окно "Параметры", переключить платформу для универсальной платформы Windows.](images/AzureLabs-Lab1-11.png)

5.  Перейдите к **файл > Параметры сборки** и убедитесь, что:

    1. **Целевое устройство** присваивается **любого устройства**.

        > Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.

    2. **Тип сборки** присваивается **D3D**
    3. **Пакет SDK для** присваивается **самую новую установленную**
    4. **Версия Visual Studio** присваивается **самую новую установленную**
    5. **Сборка и запуск** присваивается **локального компьютера**
    6. Сохраните сцены и добавить его к сборке.

        1. Это сделать, выбрав **добавьте откройте сцены**. Сохранение окно будет отображаться.

            ![Нажмите кнопку Добавить кнопку open сцены](images/AzureLabs-Lab1-12.png)

        2. Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.

            ![Создание новой папки scripts](images/AzureLabs-Lab1-13.png)

        3. Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **MR_TranslationScene**, нажмите клавишу **Сохранить**.

            ![Присвойте имя новой сцены.](images/AzureLabs-Lab1-14.png)

            > Следует помнить, что необходимо сохранить в Unity кадром *активы* папку, так как они должны быть связаны с проектом Unity. Создание папки сцены (и другие аналогичные папки) — это типичный способ структурирования проекта Unity.

    7. Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.

6. В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится. 

    ![Открытие параметров проигрывателя.](images/AzureLabs-Lab1-15.png)

7. В этой панели необходимо проверить некоторые настройки:

    1. В **другие параметры** вкладке:

        1. **Версия среды выполнения сценариев** должно быть **стабильной** (.NET 3.5 эквивалент).
        2. **Создание сценариев серверной части** должно быть **.NET**
        3. **Уровень совместимости API** должно быть **.NET 4.6**

            ![Обновите другие параметры.](images/AzureLabs-Lab1-16.png)
      
    2. В рамках **параметров публикации** в списке **возможности**, проверьте:

        1. **internetClient**
        2. **"Микрофон"**

            ![Обновление параметров публикации.](images/AzureLabs-Lab1-17.png)

    3. Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.

        ![Обновление параметров R X.](images/AzureLabs-Lab1-18.png)

8.  Вернитесь в **параметры построения**, *Unity C# проекты* больше не отображается серым, установите флажок рядом с это. 
9.  Закройте окно Параметры построения.
10. Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).

## <a name="chapter-3--main-camera-setup"></a>Глава 3 — Настройка Main Camera

> [!IMPORTANT]
> Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете [загрузить этот .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), импортировать его в проект в качестве [ *Пользовательского пакета*](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 5](#chapter-5--create-the-results-class). По-прежнему необходимо будет создать проект Unity.

1.  В *панели иерархии*, вы найдете объект с именем **Main Camera**, этот объект представляет вашей точки зрения «head» приложения «в».
2.  С помощью панели мониторинга Unity перед глазами, выберите **GameObject камеры Main**. Можно будет заметить, что *панели Инспектора* (обычно находится в правой части панели мониторинга) будут отображаться различные компоненты, *GameObject*, с помощью *преобразования* в верхней, за которым следует *камеры*и некоторые другие компоненты. Необходимо будет сбросить преобразование объекта Main Camera, поэтому расположено верно.
3.  Чтобы сделать это, выберите **шестеренки** значок рядом с камеры *преобразования* компонента, а затем выбрав **сбросить**. 

    ![Сбросьте преобразование Main Camera.](images/AzureLabs-Lab1-19.png)
 
4.  *Преобразования* компонент должен выглядеть так:

    1. *Позиции* присваивается **0, 0, 0**
    2. *Поворот* присваивается **0, 0, 0**
    3. И *масштабирования* присваивается **1, 1, 1**

        ![Преобразование информации для камеры](images/AzureLabs-Lab1-20.png)

5.  Далее с помощью **Main Camera** объекта выбран, см. в разделе **добавить компонент** расположенную в нижней части *панели Инспектора*. 
6.  Выберите эту кнопку и поиск (либо путем ввода *источника аудио* в поле поиска или перехода в разделах) для компонента, который вызывается **источника аудио** как показано ниже и выберите его (нажмите клавишу ВВОД на нем Кроме того, работает).
7.  *Источника аудио* добавляется компонент **Main Camera**, как показано ниже.

    ![Добавление компонента источника аудио.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Для Microsoft HoloLens, необходимо также изменить следующим образом, являются частью **камеры** компонентом вашего **Main Camera**:
    > - **Очистите флаги:** Сплошным цветом.
    > - **Фон** "черная, альфа-канал 0" — Hex цвет: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Глава 4 – холст отладки программы установки

Чтобы отобразить вход и выход преобразования, необходимо создать основной пользовательский Интерфейс. Для этого курса вы создадите объект Canvas пользовательского интерфейса с несколькими объектами «Text» для отображения данных.

1.  Щелкните правой кнопкой мыши пустую часть области *панели иерархии*в разделе **пользовательского интерфейса**, добавьте **холст**.

    ![Добавьте новый объект Canvas пользовательского интерфейса.](images/AzureLabs-Lab1-22.png)

2.  Холст объект выбран, в *панели Инспектора* (в компоненте «Canvas»), измените **режим рендеринга** для **мировом пространстве**. 
3.  Затем измените следующие параметры в *панели Инспектора Rect преобразования*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Ширина* - 500
    3. *Высота* - 300
    4. *Масштаб* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![Обновление преобразования rect полотна.](images/AzureLabs-Lab1-23.png)
 
4.  Щелкните правой кнопкой мыши **холст** в *панели иерархии*в разделе **пользовательского интерфейса**и добавьте **панели**. Это **панели** предоставит фон, текст, который будет отображаться в сцене.
5.  Щелкните правой кнопкой мыши **панели** в *панели иерархии*в разделе **пользовательского интерфейса**и добавьте **текстовый объект**. Повторите этот процесс, пока не будут созданы четыре объекта текст пользовательского интерфейса в целом (подсказка: при наличии первый объект «Text» выбран, можно просто нажать клавишу **«Ctrl» + было "**, его придется продублировать, пока у вас будет четыре в целом). 
6.  Для каждого **текстовый объект**, выберите его и использовать ниже таблицы для установки параметров *панели Инспектора*.

    1. Для *преобразования Rect* компонента:

        | Имя                   | Преобразование - *позиции*             | Ширина      | Высота    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Для **текст (скрипт)** компонента:


        | Имя                   | Текста               | Размер шрифта    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Состояние "микрофон": | 20           |
        | AzureResponseLabel     | Azure веб-ответа | 20           |
        | DictationLabel         |   Вы только что сказали:   | 20           |
        | TranslationResultLabel |    Перевод:    | 20           |

        ![Введите соответствующие значения для меток пользовательского интерфейса.](images/AzureLabs-Lab1-24.png)

    3. Кроме того, сделать стиль шрифта **Полужирный**. Это сделает текст более удобным для чтения.

        ![Жирный шрифт.](images/AzureLabs-Lab1-25.png)

7.  Для каждого *текст пользовательского интерфейса объекта* в [Глава 5](#chapter-5--create-the-results-class), создайте новый *дочерних* **текст пользовательского интерфейса объекта**. Эти дочерние объекты будут отображаться выходные данные приложения. Создание *дочерних* объектов через щелкните правой кнопкой мыши ваш предполагаемого родительского (например *MicrophoneStatusLabel*), а затем выберите **пользовательского интерфейса** , а затем выберите **текст**.
8.  Для каждого из этих дочерних элементов, выберите его и используйте ниже таблицы для установки параметров на панели инспектора.

    1. Для **преобразования Rect** компонента:

        | Имя                  | Преобразование - *позиции* | Ширина      | Высота    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. Для **текст (скрипт)** компонента:

        | Имя                  | Текста          | Размер шрифта    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Затем выберите параметр выравнивания «центр» для каждого компонента текста:

    ![Выравнивание текста.](images/AzureLabs-Lab1-26.png)

10. Чтобы обеспечить **дочерних текст пользовательского интерфейса** объектов можно легко читать, изменять их *цвет*. Это можно сделать, нажав кнопку на панели (в настоящее время «черный») рядом с полем *цвет*. 

    ![Введите соответствующие значения для выходных данных текст пользовательского интерфейса.](images/AzureLabs-Lab1-27.png)
 
11. Затем в новый, слишком мало, *цвет* измените *цвет Hex* для: **0032EAFF**

    ![Обновите цвет на синий.](images/AzureLabs-Lab1-28.png)
 
12. Ниже приведен способ **пользовательского интерфейса** должен выглядеть.
    1.  В *панели иерархии*:

        ![Иметь иерархию в предоставленный структуры.](images/AzureLabs-Lab1-29.png)

    2.  В *сцены* и *игр представления*:

        ![У представлений сцены и игра в ту же структуру.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Глава 5 – создать класс результатов

Первый скрипт, чтобы создать *результаты* класс, который отвечает за предоставление способ увидеть результаты преобразования. Класс хранит и отображаются следующие сведения: 

- Результат ответа из Azure.
- Состояние "микрофон". 
- Результат диктовки (голоса в текст).
- Результат преобразования.

Для создания этого класса: 

1.  Щелкните правой кнопкой мыши в *проекта панели*, затем **Создать > Папка**. Назовите папку **сценариев**. 
 
    ![Создайте папку scripts.](images/AzureLabs-Lab1-31.png)

    ![Откройте папку «скрипты».](images/AzureLabs-Lab1-32.png)
 
2.  С помощью **сценариев** папке создайте, дважды щелкните его, чтобы открыть. Затем в этой папке, щелкните правой кнопкой мыши и выберите **Создать >** затем  **C# сценарий**. Назовите сценарий *результаты*. 

    ![Создание первого скрипта.](images/AzureLabs-Lab1-33.png)
 
3.  Дважды щелкните новый *результатов* скрипт, чтобы открыть его с **Visual Studio**.
4.  Вставьте следующие пространства имен:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  Внутри класса вставьте следующие переменные:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  Затем добавьте *Awake()* метод, который будет вызываться при инициализации класса. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Наконец добавьте методы, которые отвечают за вывод различные сведения результатов в пользовательский интерфейс. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Глава 6 – создать *MicrophoneManager* класса

Вы собираетесь создать второй класс — *MicrophoneManager*.

Этот класс отвечает за:

- Обнаружение устройства записи, подключенные к гарнитуры или machine (выбирается по умолчанию).
- Запись звука (голос) и использовать режим диктовки сохранит их в виде строки.
- После приостановлена голоса, отправки диктовки к классу Translator.
- Разместите метод, который можно остановить записи голоса, при необходимости.

Для создания этого класса: 
1.  Дважды щелкните **сценариев** папки, чтобы открыть его. 
2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**. Назовите сценарий *MicrophoneManager*. 
3.  Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.
4.  Обновите пространства имен должны совпадать, как показано ниже, в верхней части *MicrophoneManager* класса:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Затем добавьте следующие переменные внутри *MicrophoneManager* класса:

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  Код для *Awake()* и *Start()* методы теперь должен быть добавлен. Это будет вызываться при инициализации класса.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  Вы можете *удалить* *Update()* метод, так как этот класс не будет его использовать.
8.  Теперь необходимо методы, которые приложение использует для запуска и остановки записи голоса и передать его в *Translator* класса, который вы создадите в ближайшее время. Скопируйте следующий код и вставьте его под *Start()* метод.

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Хотя это приложение не будет выполнять его, использовать *StopCapturingAudio()* метод также предоставляется здесь, вам понадобится реализовать возможность остановки записи звука в приложении.

9.  Теперь необходимо добавить обработчик, диктовки, который будет вызываться при остановке голоса. Этот метод затем передаст надиктованного текста для *Translator* класса.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Не забудьте сохранить изменения в Visual Studio перед возвратом к Unity.

> [!WARNING]  
> На этом этапе вы заметите ошибку в *консоли редактора Unity* панели («имя «Translator» не существует...»). Это так, как код ссылается на *Translator* класс, который будет создан в следующей главе.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Глава 7 – вызов к службе Azure и переводчика

— Последний скрипт, чтобы создать *Translator* класса. 

Этот класс отвечает за:

-   Проверка подлинности приложения с помощью *Azure*, в exchange для **маркер проверки подлинности**.
-   Используйте **маркер проверки подлинности** для отправки текста (полученные от *MicrophoneManager* класс) для перевода.
-   Получать переведенные результат и передать его в *результаты* класс для отображения в пользовательском Интерфейсе.

Для создания данного класса: 
1.  Перейдите к **сценариев** папку, созданную ранее. 
2.  Щелкните правой кнопкой мыши в **проекта панели**, **Создать > C# сценарий**. Вызовите сценарий *Translator*.
3.  Дважды щелкните новый *Translator* скрипт, чтобы открыть его **с помощью Visual Studio**.
4.  Добавьте следующие пространства имен в начало файла:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Затем добавьте следующие переменные внутри *Translator* класса:

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - Языки, которые вставлены в языках **перечисления** только в качестве примера. Вы можете добавить более, при необходимости; [API поддерживает более чем 60 языков](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (включая обычного русского или Марсианского)!
    > - Существует [более интерактивной страница, которая содержит доступные языки](https://www.microsoft.com/translator/business/languages/), но имейте в виду, страница отображается только для работы, если язык сайта имеет значение "en-us' (и на сайте Microsoft будет скорее всего, перенаправление на Ваш родной язык). Вы можете изменить язык сайта в нижней части страницы или изменение URL-адрес.
    > - **AuthorizationKey** значение в приведенном выше фрагменте кода должно быть **ключ** полученный при подписке на *API перевода текстов Azure*. Это изложено в [главе 1](#chapter-1--the-azure-portal).

6.  Код для *Awake()* и *Start()* методы теперь должен быть добавлен. 
7.  В этом случае код будет сделать вызов к *Azure* с помощью авторизации ключа, чтобы получить *маркера*.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > Токен истекает через 10 минут. В зависимости от сценария для приложения может потребоваться внести же сопрограммы вызывать несколько раз.

8.  Сопрограммы для получения маркера выглядит следующим образом:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Если вы изменяете имя метода IEnumerator **GetTokenCoroutine()**, необходимо обновить *StartCoroutine* и *StopCoroutine* вызовите строковые значения в приведенном выше коде. [Согласно документации по Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), чтобы остановить определенный *Соподпрограмме*, необходимо использовать метод значения строк.

9.  Затем добавьте соподпрограмме (с «поддержка» методом stream прямо под ним) для получения перевода текста, полученных *MicrophoneManager* класса. Этот код создает строку запроса для отправки *API перевода текстов Azure*, а затем использует внутренний класс Unity UnityWebRequest звонки в конечную точку с помощью строки запроса «Get». Результат затем используется для задания преобразования в объекте результатов. В приведенном ниже коде показана реализация:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.

## <a name="chapter-8--configure-the-unity-scene"></a>Глава 8 – Настройка сцене Unity

1.  Обратно в редакторе Unity, щелкните и перетащите *результатов* класс *из* **сценарии** папку **Main Camera** объекта в  *Панель иерархии*.
2.  Щелкните **Main Camera** и просмотрите *панели Инспектора*. Можно будет заметить, что в только что добавленного *скрипт* компонента есть четыре поля с пустыми значениями. Это выходные данные ссылки на свойства в коде. 
3.  Перетащите соответствующий **текст** объектов из *панели иерархии* для этих четырех позициях, как показано на рисунке ниже.

    ![Обновите ссылки на целевую с заданными значениями.](images/AzureLabs-Lab1-34.png)
  
4.  Далее щелкните и перетащите *Translator* класса из **сценарии** папку **Main Camera** объекта в *панели иерархии*. 
5.  Затем щелкните и перетащите *MicrophoneManager* класса из **сценарии** папку **Main Camera** объекта в *панели иерархии*. 
6.  Наконец, щелкните **Main Camera** и просмотрите *панели Инспектора*. Обратите внимание, что в скрипте, который вы перетащили на, есть два раскрывающихся списках, на которые вы сможете задать языки.
 
    ![Убедитесь, что языки предполагаемого перевода являются входными данными.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Глава 9-теста в смешанной реальности

На этом этапе необходимо проверить, что сцены реализован правильно.

Убедитесь, что:

- Все параметры, упомянутые в [главе 1](#chapter-1--the-azure-portal) заданы правильно. 
- *Результатов*, *Translator*, и *MicrophoneManager*, скрипты, присоединяются к **Main Camera** объекта. 
- Размещен ваш *API перевода текстов Azure* службы **ключ** в **authorizationKey** переменную *Translator* Скрипт.  
- Все поля в *главной панели Инспектора камеры* назначаются должным образом.
- Микрофон работает при выполнении в сцену (если это не так, убедитесь, что микрофон присоединенного *по умолчанию* устройства и что у вас есть [его правильно установить в Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

Можно проверить иммерсивных гарнитура, нажав клавишу **воспроизведение** кнопку *редактора Unity*.
Приложение должно работает через присоединенное иммерсивных гарнитуры.

> [!WARNING]  
> Если появится сообщение об ошибке, в консоли Unity о аудиоустройства по умолчанию изменение, сцены может не работать должным образом. Это из-за способа на портале смешанной реальности имеет дело с встроенные микрофоны применяется, в которых они имеются. Если эта ошибка возникает, просто остановить сцены и запустить снова и вещи должны работать как ожидалось.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Глава 10 – построение решения для универсальной платформы Windows и загрузки неопубликованных приложений на локальном компьютере

Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.

1.  Перейдите к **параметры сборки**: **Файл > Параметры сборки...**
2.  Из **параметры построения** окно, нажмите кнопку **построения**.

    ![Создавайте сцене Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Если не сделали, установите **Unity C# проекты**.
4.  Щелкните **Сборка**. Unity приведет к запуску *проводнике* окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в. Создайте эту папку и назовите его *приложения*. Затем с помощью *приложения* папку, нажмите клавишу **Выбор папки**. 
5.  Unity начнется построение проекта для *приложения* папки. 
6.  Один раз Unity завершил построение (может занять некоторое время), он будет открыт *проводнике* окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).

## <a name="chapter-11--deploy-your-application"></a>Глава 11 — развертывание приложения

Для развертывания приложения:

1.  Перейдите к новой сборки Unity ( *приложения* папки) и откройте файл решения с *Visual Studio*.
2.  В списке выберите конфигурацию решения **Отладка**.
3.  В платформу решения, выберите **x86**, **локальный компьютер**. 

    > Для Microsoft HoloLens, может быть проще устанавливать равным *удаленный компьютер*, таким образом, не связанном устройстве на компьютер. Однако необходимо будет выполнить следующее:
    > - Знать **IP-адрес** из HoloLens, которую можно найти в *параметры > сеть и Интернет > Wi-Fi > Дополнительно*; IPv4 — это адрес, следует использовать. 
    > - Убедитесь, *режим разработчика* — **на**; найдено в *параметры > обновление и безопасность > для разработчиков*.

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на вашем ПК.
5.  Приложения появятся в списке установленных приложений, Готово к запуску.
6.  После запуска приложение попросит авторизовать доступ к микрофону. Убедитесь, что щелкните **Да** кнопки.
7.  Теперь вы готовы начать перевод!

## <a name="your-finished-translation-text-api-application"></a>Готового приложения API перевода текстов

Поздравляем, вы создали приложение смешанной реальности, которое использует API Azure перевода текста для преобразования речи в переведенный текст.

![Конечный продукт.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Упражнения премии

### <a name="exercise-1"></a>Упражнение 1

Можно добавить функциональные возможности преобразования текста в речь в приложение таким образом, чтобы возвращаемый текст произнесении?

### <a name="exercise-2"></a>Упражнение 2

Позволяют пользователю изменять источник и выходные данные языки («from» и «по») в само приложение, приложение необходимо перестроить, каждый раз, чтобы изменить языки.
