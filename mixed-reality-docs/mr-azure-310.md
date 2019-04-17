---
title: Г-н и 310 Azure — обнаружение объектов
description: Выполните этот курс, чтобы узнать, как обучить модель машинного обучения, а затем используйте обученной модели для распознавания схожие объекты и их положение в реальном мире из приложения смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, пользовательской службе визуального распознавания, объект обнаружения, смешанный реальность, academy, unity, учебник, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597649"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

# <a name="mr-and-azure-310-object-detection"></a>Г-н и Azure 310: Обнаружение объектов

В рамках этого курса вы узнаете, как для распознавания пользовательского визуального содержимого и его пространственных место в указанное изображение, с помощью пользовательской службе визуального распознавания Azure «объект» возможности приложения смешанной реальности.

Эта служба позволит вам для обучения модели машинного обучения с использованием объекта изображения. Затем понадобится обученной модели для распознавания схожие объекты и приблизительное их расположение в реальном мире, предоставленный камеры из Microsoft HoloLens или веб-камеры подключиться к компьютеру для иммерсивную (VR).

![результат курс](images/AzureLabs-Lab310-00.png)

**Azure пользовательской службе визуального распознавания, обнаружение объекта** — это служба Майкрософт, что позволяет разработчикам создавать пользовательский образ классификаторов. Эти классификаторы затем можно с помощью новых образов для обнаружения объектов в рамках этого нового образа, предоставляя **границы рамки** в самом образе. Служба предоставляет простой, удобный, online портал для упрощения этого процесса. Дополнительные сведения по следующим ссылкам:

* [Custom Vision страница в Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Ограничения и квоты](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

По завершении этого курса вы получите с приложением смешанной реальности, которое будет осуществлять следующее:

1. Пользователь будет иметь возможность *помощи* в объект, который они обучения с помощью пользовательской концепции службы Azure, объект обнаружения. 
2. Пользователь будет использовать *коснитесь* жест быстрого проведения нужной информации на создание образа.
3. Приложение отправляет изображение пользовательской службы визуального распознавания Azure.
4. Будет существовать ответа от службы, который будет отображать результат распознавания как текст в абсолютном пространстве. Это будет выполняться через использование Microsoft HoloLens пространственных отслеживания, как способ основные сведения о распознанных объекта положение в мировых координатах, а затем использовать *тега* сопоставленный обнаруженных в образе, до Введите текст метки.

Курс также рассматривается вручную загрузки изображений, создание тегов, и обучение для распознавания различных службой объекты (в предоставленном примере чашку), по параметр *границ поле* в образе, отправке. 

> [!IMPORTANT]
> После создания и использования приложения, разработчику необходимо перейти обратно к пользовательской концепции службы Azure и определить прогноза, выполненных службой и определить, были ли правильно или нет (посредством добавления тегов, что-либо службы пропустили, и Настройка *ограничивающий поля*). Службу можно затем повторно обучить, которой будет увеличить вероятность его распознавание объектов реального мира.

Этот курс ознакомят вас для получения результатов из пользовательской концепции службы Azure, определение объекта, в основе Unity примера приложения. Это будет необходимо применение этих понятий в пользовательское приложение, возможно, вы разрабатываете.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> Г-н и Azure 310: Обнаружение объектов</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#. Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.). Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.

Рекомендуется следующее оборудование и программное обеспечение для этого курса:

- Компьютере разработки
- [Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Последний пакет SDK Windows 10](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Объект [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) с включенным режимом разработчика
- Доступ к Интернету для настройки Azure и извлечения пользовательской службы визуального распознавания
-  Ряд образов по крайней мере пятнадцать (15) являются обязательными) для каждого объекта, хотелось бы концепции Custom для распознавания. Если вы хотите, можно использовать образы, представленных в этом курсе [ряд пользовательских политик,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).
2.  Настроить и проверить ваш HoloLens. Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя). 

Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).

Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Глава 1 - портале пользовательской службе визуального распознавания

Чтобы использовать **пользовательская служба визуального распознавания Azure**, необходимо настроить экземпляр его, чтобы сделать доступными для приложения.

1.  Перейдите [для **пользовательская служба визуального распознавания** главной странице](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Щелкните **Приступая к работе**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Войдите на портал пользовательской службе визуального распознавания.

    ![](images/AzureLabs-Lab310-02.png)

4.  Если у вас еще нет учетной записи Azure, необходимо будет создать его. Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.

5.  После входа в первый раз, вам будет предложено с *условиями* панели. Установите флажок, чтобы *согласны с условиями*. Нажмите кнопку **принимаю**.

    ![](images/AzureLabs-Lab310-03.png)

6.  Согласии с условиями, теперь вы находитесь в *Мои проекты* раздел. Щелкните **новый проект**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Будет отображаться в области справа, который предложит задать некоторые поля для проекта.

    1.  Вставить имя проекта

    2.  Введите описание для проекта (**необязательно**)

    3.  Выберите **группы ресурсов** или создайте новую. Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure. Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как этих курсов) для распространенных группы ресурсов).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Если вы хотите [Дополнительные сведения о группах ресурсов Azure, перейдите к связанные документы](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  Задайте **типы проектов** как **обнаружение объектов (Предварительная версия)**.

8.  Когда вы закончите, нажмите кнопку **создать проект**, и вы будете перенаправлены на страницу проекта пользовательской службы визуального распознавания.


## <a name="chapter-2---training-your-custom-vision-project"></a>Глава 2 - обучение Custom Vision проекта

Один раз на портале Custom Vision, ваша основная задача заключается для обучения проекта распознавать определенные объекты на изображениях.

Необходимо по крайней мере 15 (15) образы для каждого объекта, которые требуется приложение для распознавания. Можно использовать образы, предоставленные в этом курсе ([ряд пользовательских политик,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Для обучения Custom Vision проекта:

1.  Щелкните **+** рядом с пунктом **теги**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Добавить **имя** для тега, который будет использоваться для связи изображений. В этом примере мы используем образы пользовательских политик, для распознавания, поэтому тега с именем, для этого **Cup**. Нажмите кнопку **Сохранить** после завершения.

    ![](images/AzureLabs-Lab310-07.png)

3.  Обратите внимание на **тега** был добавлен (может потребоваться перезагрузить страницу, чтобы он появился). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Щелкните **Добавление изображений** в центре страницы.

    ![](images/AzureLabs-Lab310-09.png)

5.  Щелкните **Обзор локальных файлов**и перейдите к изображениям, вы бы хотели отправить один объект, с минимальным благосостояние пятнадцать (15).

    > [!TIP]
    >  Можно выбрать несколько изображений одновременно, для отправки.

    ![](images/AzureLabs-Lab310-10.png)

6.  Нажмите клавишу **передача файлов** после выбора всех образов, вы бы хотели обучения проекта. Файлы начнется передача. Получив подтверждение отправки, нажмите кнопку **сделать**.

    ![](images/AzureLabs-Lab310-11.png)

7.  На этом этапе образы отправлен, но не добавлены проектные теги.

    ![](images/AzureLabs-Lab310-12.png)

8.  Добавить тег изображения, с помощью мыши. При наведении указателя мыши на изображение, выделение поможет нарисовав выбора вокруг вашего объекта автоматически. Если это не точное, можно создать собственные. Это достигается путем хранения щелкните левой кнопкой мыши и перетащив области выделения вплоть до охватывающих объекта. 

    ![](images/AzureLabs-Lab310-13.png) 

9. После выделенного объекта на изображении небольшой запрос запросит для *добавьте тег Region*. Выберите ранее созданный тег («Cup», в приведенном выше примере) или если вы добавляете дополнительные теги, введите в и нажмите кнопку **+ (плюс)** кнопки.

    ![](images/AzureLabs-Lab310-14.png) 

10. Для пометки Далее образа, можно щелкните стрелку справа от колонки или закройте колонку тега (щелкнув **X** в правом верхнем углу колонки) и нажмите кнопку Далее. Получив Далее готов, повторите ту же процедуру. Это необходимо сделайте для всех образов, которые вы отправили, пока они все помечаются. 

    > [!NOTE]
    >  Можно выбрать несколько объектов в одном образе, как на следующем рисунке: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. После пометки их все, щелкните на **с тегами** кнопки в левой части экрана, чтобы отобразить теги образов. 

    ![](images/AzureLabs-Lab310-16.png)

12. Теперь вы готовы для обучения службы. Нажмите кнопку **Train** начнется кнопку и первой итерации обучения.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. После построения, можно увидеть две кнопки с именем **сделать значением по умолчанию** и **прогноза URL-адрес**. Щелкните **сделать значением по умолчанию** сначала, затем щелкните **прогноза URL-адрес**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > Какое значение присваивается конечную точку, которая предоставляется из этого, *итерации* был помечен как по умолчанию. Таким образом, если вы позднее сделать новый *итерации* и обновить его по умолчанию, не потребуется изменять код.

14. Когда вы перейдете на **URL-адрес прогноза**откройте *Блокнот*, скопируйте и вставьте **URL-адрес** (также называется вашей **конечной точки прогноза**) и **прогноза-ключ службы**, так что его можно получить, когда это потребуется далее в коде.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Глава 3 - Настройка проекта Unity

Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.

1.  Откройте **Unity** и нажмите кнопку **New**.

    ![](images/AzureLabs-Lab310-21.png)

2.  Теперь необходимо будет указать имя проекта Unity. Вставить **CustomVisionObjDetection**. Убедитесь, что тип проекта присваивается **3D**и задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги). Щелкните **создать проект**.

    ![](images/AzureLabs-Lab310-22.png)

3.  С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**. Перейдите к **изменить* > *предпочтения** и затем в окне «Новый» перейдите к **внешние средства**. Изменение **внешнего редактора скриптов** для **Visual Studio**. Закрыть **предпочтения** окна.

    ![](images/AzureLabs-Lab310-23.png)

4.  Перейдите к **файл > Параметры сборки** и переключаться **платформы** для *универсальной платформы Windows*и затем щелкнув **переключения платформы** кнопки.

    ![](images/AzureLabs-Lab310-24.png)

5.  В том же **параметры построения** окна, задайте следующее:

    1.  **Целевое устройство** присваивается **HoloLens**        
    2.  **Тип сборки** присваивается **D3D**
    3.  **Пакет SDK для** присваивается **самую новую установленную**
    4.  **Версия Visual Studio** присваивается **самую новую установленную**
    5.  **Сборка и запуск** присваивается **локального компьютера**            
    6.  Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.

        ![](images/AzureLabs-Lab310-25.png)

6.  В том же **параметры построения** щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где **инспектор** находится.

7. В этой панели необходимо проверить некоторые настройки:

    1.  В **другие параметры** вкладке:

        1.  **Сценарии версии среды выполнения** должно быть **экспериментальный** (.NET 4.6 эквивалент), что вызовет необходимость перезапуска редактора.

        2. **Создание сценариев серверной части** должно быть **.NET**.

        3. **Уровень совместимости API** должно быть **.NET 4.6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  В рамках **параметров публикации** в списке **возможности**, проверьте:

        1. **internetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Последующих частях панели **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанный Windows Реальность SDK** добавляется.

        ![](images/AzureLabs-Lab310-29.png)

8.  Вернитесь в **параметры построения**, *Unity C\# проекты* больше не отображается серым: установите флажок рядом с это.

9.  Закрыть **параметры построения** окна.

10. В **редактор**, щелкните **изменить** > **параметры проекта** > **графики**.

    ![](images/AzureLabs-Lab310-30.png)

11. В **панели Инспектора** *параметры графики* будут открыты. Прокрутите вниз, пока не увидите массив с именем **всегда включать шейдеры**. Добавление слота, увеличив **размер** переменную на единицу (в данном случае оно имело значение 8, мы сделали 9). Новый слот будет отображаться, в последней позиции массива, как показано ниже:

    ![](images/AzureLabs-Lab310-31.png)

12. В области щелкните маленьких целевых круг рядом с слот, чтобы просмотреть список построителей текстур. Найдите **прежних версий шейдеры/Transparent/Диффузия** шейдера и дважды щелкните его. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Глава 4 — Импорт пакета CustomVisionObjDetection Unity

Для этого курса, вам будет предоставлен пакет средств Unity, которые называются **Azure-MR-310.unitypackage**. 

> [СОВЕТ] Любые объекты, поддерживаемые Unity, включая целые сцены можно упаковать в **.unitypackage** файл и экспорта / импорта в других проектах. Это максимально эффективным и безопасным способом, перемещать между различными **проектов Unity**.

Можно найти [Azure MR-310 пакет, который можно загрузить здесь](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  С помощью панели мониторинга Unity перед глазами, щелкните **активы** в меню в верхней части экрана, нажмите кнопку **Импорт пакета > пользовательского пакета**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Используйте средство выбора файлов для выбора **Azure-MR-310.unitypackage** пакета и нажмите кнопку **откройте**. Список компонентов для этого ресурса будет отображаться пользователю. Подтверждение импорта, щелкнув **импорта** кнопки.

    ![](images/AzureLabs-Lab310-34.png)

3.  После завершения импорта, можно заметить, что папки из пакета теперь были добавлены к **активы** папки. Такого рода структуру папок является типичным для проекта Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  **Материалы** папка содержит материал, используемый **помощи курсора**. 

    2.  **Подключаемые модули** папка содержит Библиотеку Newtonsoft, используемых в коде для десериализации веб-ответа службы. Два (2) разных версий содержащихся в папке, а также вложенную папку, необходимые для поддержки библиотеки с возможностью использования созданные редактора Unity и построения универсальной платформы Windows. 

    3.  **Prefabs** папка содержит prefabs, содержащихся в сцене. Таковы:

        1.  **GazeCursor**, курсор, используемый в приложении. Будет работать вместе с prefab SpatialMapping, чтобы иметь возможность разместить в сцене поверх физических объектов.
        2.  **Метка**, который является объектом пользовательского интерфейса, используемый для отображения тега объекта в сцену, при необходимости.
        3.  **SpatialMapping**, который является объект, который позволяет приложению использовать Создание виртуальной схемы, использование пространственных отслеживания Microsoft HoloLens.

    4.  **Сцены** папке, которая в настоящее время содержит предварительно созданные сцены курс с демороликами.

4.  Откройте **сцены** папку в **панель проекта**и дважды щелкните **ObjDetectionScene**, чтобы загрузить сцены, который будет использоваться для этого курса.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Включено без кода**, вы напишете код, выполнив этот курс.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Глава 5 - создание класса CustomVisionAnalyser.

На этом этапе вы готовы написать код. Вы начнете с **CustomVisionAnalyser** класса.

> [!NOTE]
> Вызовы **пользовательская служба визуального распознавания**, внесенных в код, показанный ниже, с помощью **Custom Vision REST API**. С помощью это, вы увидите, как реализовать и использовать этот API (полезно для понимания того, как выполнить что-то подобное самостоятельно). Имейте в виду, что корпорация Майкрософт предлагает **Custom Vision SDK** , может также использоваться для выполнения вызовов к службе. Дополнительные сведения см. в статье [статьи пакет SDK для компьютерного зрения Custom](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Этот класс отвечает за:

- Загрузка последней версии образа, записано в виде массива байтов.

- Отправка массива байтов подписки Azure **пользовательская служба визуального распознавания** экземпляра для анализа.

- Получение ответа как строку JSON.

- Десериализации ответа и передачи итоговый **прогноза** для **SceneOrganiser** класс, который берет на себя отображения ответа.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши в **папке Asset**, который находится в **панель проекта**, затем нажмите кнопку **создать** > **папку**. Вызовите папке **сценариев**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Дважды щелкните новую папку, чтобы открыть его.

3.  Щелкните правой кнопкой мыши внутри папки, а затем щелкните **создать** > **C\# скрипт**. Назовите сценарий **CustomVisionAnalyser.**

4.  Дважды щелкните новый **CustomVisionAnalyser** скрипт, чтобы открыть его с **Visual Studio.**

5.  Убедитесь, что у вас есть следующие пространства имен, в верхней части файла:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  В **CustomVisionAnalyser** добавьте следующие переменные:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Убедитесь, что вы вставляете вашей **прогноза-ключ службы** в **predictionKey** переменной и **конечной точки прогноза** в **predictionEndpoint**  переменной. Вы скопировали их [Блокнот ранее, в главе 2, шаге 14](#chapter-2---training-your-custom-vision-project).

7.  Код для **Awake()** теперь должен быть добавлен для инициализации переменной экземпляра:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Добавить соподпрограмме (с помощью статического **GetImageAsByteArray()** метод под ним), которой будет получать результаты анализа, изображения, охватываемым **ImageCapture** класс.

    > [!NOTE]
    > В **AnalyseImageCapture** соподпрограмме, имеется вызов **SceneOrganiser** класс, который вы еще для создания. Таким образом **оставлю их строк закомментирована сейчас**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. Удалить **Start()** и **Update()** методы, так как они не будут использоваться. 

10.  Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.

> [!IMPORTANT]
> Как упоминалось ранее, не беспокоясь о коде, который может появиться ошибка, как вы будете обеспечивать дополнительные классы в ближайшее время, которые будет устранить их.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Глава 6 - создание класса CustomVisionObjects

Класс, вы создадите теперь является **CustomVisionObjects** класса.

Этот скрипт содержит несколько объектов, используемых другими классами для сериализации и десериализации вызовы к пользовательской службы визуального распознавания.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Вызовите сценарий **CustomVisionObjects.**

2.  Дважды щелкните новый **CustomVisionObjects** скрипт, чтобы открыть его с **Visual Studio.**

3.  Убедитесь, что у вас есть следующие пространства имен, в верхней части файла:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Удалить **Start()** и **Update()** методов внутри **CustomVisionObjects** класса, этот класс будет очищен.

    > [!WARNING]
    > Очень важно, что вы внимательно выполните следующую инструкцию. Если поместить новый объявления классов внутри **CustomVisionObjects** класс, вы получите ошибки компиляции [Глава 10](#chapter-10---create-the-imagecapture-class), содержащее сведения о, **AnalysisRootObject** и  **BoundingBox** не найдены.

5.  Добавьте следующие классы *за пределами* **CustomVisionObjects** класса. Эти объекты используются **Newtonsoft** библиотеки для сериализации и десериализации данных ответа:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Глава 7 - создание класса SpatialMapping

Задаст этот класс **пространственных сопоставление Collider** в сцене таким образом, чтобы иметь возможность обнаруживать конфликты между виртуальных объектах и реальными объектами.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Вызовите сценарий **SpatialMapping.**

2.  Дважды щелкните новый **SpatialMapping** скрипт, чтобы открыть его с **Visual Studio.**

3.  Убедитесь, что у вас есть следующие пространства имен, упоминавшиеся **SpatialMapping** класса:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Затем добавьте следующие переменные внутри **SpatialMapping** класса выше **Start()** метод:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Добавить **Awake()** и **Start()**:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  Удалить **Update()** метод.

7.  Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Глава 8 - создать класс GazeCursor

Этот класс отвечает за Настройка курсора в нужное место в реальных пространстве с помощью **SpatialMappingCollider**, созданный в предыдущей главе.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Вызовите сценарий **GazeCursor**

2.  Дважды щелкните новый **GazeCursor** скрипт, чтобы открыть его с **Visual Studio.**

3.  Убедитесь, что у вас есть следующее пространство имен, указанное выше **GazeCursor** класса:

    ```csharp
    using UnityEngine;
    ```

4.  Затем добавьте следующую переменную внутри **GazeCursor** класса выше **Start()** метод. 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Обновление **Start()** метод следующим кодом:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Обновление **Update()** метод следующим кодом:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > Не волнуйтесь об ошибке для **SceneOrganiser** класс не найден, он будет создан в следующей главе.

7. Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Глава 9 — создать класс SceneOrganiser

Этот класс выполняет следующие действия:

-   Настройка *Main Camera* путем присоединения к нему соответствующие компоненты.

-   При обнаружении объекта, он будет отвечать за вычисление его позиции в реальном мире и место **тега метки** его рядом с соответствующим **имя тега**.    

Для создания этого класса:

1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Назовите сценарий **SceneOrganiser**.

2.  Дважды щелкните новый **SceneOrganiser** скрипт, чтобы открыть его с **Visual Studio.**

3.  Убедитесь, что у вас есть следующие пространства имен, упоминавшиеся **SceneOrganiser** класса:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Затем добавьте следующие переменные внутри **SceneOrganiser** класса выше **Start()** метод:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  Удалить **Start()** и **Update()** методы.

6.  Под переменные, добавить **Awake()** метод, который будет инициализировать класс и подготовить сцены.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Добавить **PlaceAnalysisLabel()** метод, который будет *создание их экземпляров* метки в сцене (который теперь является невидимой для пользователя). Он также помещает (также невидимый) quad где изображение размещается и перекрывается с реальным миром. Это важно, так как поле координаты получить от службы после анализа трассируются обратно в этом quad определить Приблизительное расположение объекта в реальном мире. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Добавить **FinaliseLabel()** метод. Он отвечает за:

    *   Установка *метка* текст с *тега* прогноза, будучи уверенными самый высокий.
    *   Вызов расчет *ограничивающий прямоугольник* четыре объекта, расположенный ранее, и перемещение метки в сцене.
    *   Настройка метки глубины с помощью Raycast к *ограничивающий прямоугольник*, которого следует конфликтуют с объектом в реальном мире.
    * Сброс процесс отслеживания, чтобы разрешить пользователю записывать другое изображение.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Добавить **CalculateBoundingBoxPosition()** метод, который включает ряд вычислений, необходимых для перевода *ограничивающий прямоугольник* координатах, полученных от службы и воссоздать их пропорционально на четыре.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.

    > [!IMPORTANT]
    > Прежде чем продолжить, откройте **CustomVisionAnalyser** класса и в **AnalyseLastImageCaptured()** метод, *раскомментируйте* следующие строки:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> Не волнуйтесь о **ImageCapture** класса сообщение «не удалось найти», он будет создан в следующей главе.


## <a name="chapter-10---create-the-imagecapture-class"></a>Глава 10 — создать класс ImageCapture

Далее нужно создать класс является **ImageCapture** класса.

Этот класс отвечает за:

*   Создание образа с помощью камеры HoloLens и сохранить его в *приложения* папки.
*   Обработка *коснитесь* жесты пользователя.

Для создания этого класса:

1.  Перейдите к **сценариев** папку, созданную ранее.

2.  Щелкните правой кнопкой мыши внутри папки, а затем щелкните **создать** > **C\# скрипт**. Назовите сценарий **ImageCapture**.

3.  Дважды щелкните новый **ImageCapture** скрипт, чтобы открыть его с **Visual Studio.**

4.  Замените следующие пространства имен в верхней части файла:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Затем добавьте следующие переменные внутри **ImageCapture** класса выше **Start()** метод:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  Код для **Awake()** и **Start()** теперь необходимо добавить методы:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Реализация обработчика, который будет вызываться при возникновении жеста касания:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Если курсор находится **зеленый**, это означает, что камера находится на изображение. Если курсор находится **red**, это означает, что камера занят.

8.  Добавьте метод, который приложение использует для запуска процесса захвата образа и сохранения образа:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  Добавление обработчиков, которые будут вызываться захваченный фотографии и когда он будет готов для анализа. Результат затем передается **CustomVisionAnalyser** для анализа.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Глава 11 - Настройка сценариев в сцене

Теперь, когда вы написали весь код, необходимые для этого проекта, пора установить сценарии в сцене, а также на prefabs, для их правильной.

1.  В рамках **редактора Unity**в **панели иерархии**выберите **Main Camera**.
2.  В **панели Инспектора**, с **Main Camera** , щелкните на **добавить компонент**, а затем найдите **SceneOrganiser** скрипт и Дважды щелкните, чтобы добавить его.

    ![](images/AzureLabs-Lab310-38.png)

3.  В **панель проекта**откройте **папку Prefabs**, перетащите **метка** prefab в *метка* пустой ссылочную целевую область, хранения в **SceneOrganiser** сценарий, который вы только что добавили к *Main Camera*, как показано на рисунке ниже:

    ![](images/AzureLabs-Lab310-39.png)

4.  В **панели иерархии**выберите **GazeCursor** потомком **Main Camera**.
5.  В **панели Инспектора**, с **GazeCursor** , щелкните на **добавить компонент**, а затем найдите **GazeCursor** скрипт и Дважды щелкните, чтобы добавить его.

    ![](images/AzureLabs-Lab310-40.png)

6.  Опять же, в **панели иерархии**выберите **SpatialMapping** потомком **Main Camera**.
7.  В **панели Инспектора**, с **SpatialMapping** , щелкните на **добавить компонент**, а затем найдите **SpatialMapping** скрипт и дважды щелкните, чтобы добавить его.

    ![](images/AzureLabs-Lab310-41.png)

Оставшиеся сценарии, которые вы еще не будет добавлен в коде в **SceneOrganiser** сценария во время выполнения.

## <a name="chapter-12---before-building"></a>Глава 12 - перед сборкой

Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш Microsoft HoloLens.

Прежде чем сделать, убедитесь, что:

-  Все параметры, упомянутые в [Глава 3](#chapter-3---set-up-the-unity-project) заданы правильно.
- Сценарий **SceneOrganiser** присоединяется к **Main Camera** объекта.
- Сценарий **GazeCursor** присоединяется к **GazeCursor** объекта.
- Сценарий **SpatialMapping** присоединяется к **SpatialMapping** объекта.
- В [Глава 5](#chapter-5---create-the-customvisionanalyser-class), шаг 6:

    - Убедитесь, что вы вставляете вашей **ключ службы прогноза** в **predictionKey** переменной.
    - Вы вставили вашей **конечной точки прогноза** в **predictionEndpoint** класса.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Глава 13 - построения решения универсальной платформы Windows и загружать неопубликованные приложения

Теперь вы готовы для построения приложения, как решение универсальной платформы Windows, вы сможете развернуть систему на Microsoft HoloLens. Чтобы начать процесс построения:

1.  Перейдите к **файл > Параметры сборки**.

2.  Такт **Unity C\# проекты**.

3.  Щелкните **Добавление открытых сцен**. Это добавит открытые сцены в сборке.

    ![](images/AzureLabs-Lab310-42.png)

4.  Щелкните **Сборка**. Unity приведет к запуску *проводнике* окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в. Создайте эту папку и назовите его **приложения**. Затем с помощью **приложения** щелкните папку, **Выбор папки**.

5.  Unity начнется построение проекта для **приложения** папки.

6.  Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).

7.  Чтобы развернуть систему на Microsoft HoloLens, вам потребуется IP-адрес этого устройства (для удаленного развертывания), и проверять их также имеет **режим разработчика** значение. Выполните указанные ниже действия.

    1.  Хотя носить вашей HoloLens, откройте **параметры**.

    2.  Перейдите к **сеть и Интернет** > **Wi-Fi** > **Дополнительные параметры**

    3.  Примечание **IPv4** адрес.

    4.  Затем перейдите к **параметры**, а затем в **обновление и безопасность** > **для разработчиков**

    5.  Задайте **режим разработчика** *на*.

8.  Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.

9.  В списке выберите конфигурацию решения **Отладка**.

10. В платформу решения, выберите **x86, удаленный компьютер**. Вам будет предложено вставить **IP-адрес** удаленного устройства (Microsoft HoloLens, таким образом, который вы записали).

    ![](images/AzureLabs-Lab310-43.png)

11. Перейдите к **построения** меню и щелкните **развернуть решение** для загрузки неопубликованных приложений для вашей HoloLens.

12. Приложения должны появиться в списке установленных приложений на вашей Microsoft HoloLens, Готово к запуску!

### <a name="to-use-the-application"></a>Использование приложения:

* Рассмотрим объект, который обучения с вашей **пользовательская служба визуального распознавания Azure, обнаружение объекта**и использовать **касания**.
* При обнаружении объекта абсолютном пространстве *текст метки* будет отображаться с именем тега.

> [!IMPORTANT]
> Каждый раз записать фотографию и отправить его в службу, можно вернуться на страницу службы и переобучить службу с вновь захваченного изображения. В начале, вы, вероятно, придется исправить *ограничивающий поля* более точные и переобучить службу.

> [!NOTE]
> Поместить текст метки может не отображаться рядом с объектом, когда датчиков Microsoft HoloLens и/или SpatialTrackingComponent в Unity не удается разместить соответствующие colliders, относительно объектов реального мира. Попробуйте использовать приложение в другой рабочей области, если это так.

## <a name="your-custom-vision-object-detection-application"></a>Ваше видение Custom, обнаружения объекта приложения

Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Azure Custom взгляд в будущее, API обнаружения объекта, который может распознать объекта из образа, а затем обеспечивают приблизительные позиционирование для этого объекта в трехмерном пространстве.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Упражнения премии

### <a name="exercise-1"></a>Упражнение 1

Добавление в текстовую подпись, использовать полупрозрачным куба для упаковки реальный объект в трехмерной *ограничивающий прямоугольник*.

### <a name="exercise-2"></a>Упражнение 2

Обучение пользовательской службы визуального распознавания для распознавания объектов.

### <a name="exercise-3"></a>Упражнение 3

Воспроизведение звука, когда объект был распознан.

### <a name="exercise-4"></a>Упражнение 4

Используйте API повторного обучения в службу с помощью те же образы, анализ приложения, так чтобы служба стала более точные (выполнять прогноза и одновременно обучения).
