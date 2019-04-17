---
title: Г-н и 304 Azure — распознавание лиц.
description: Выполните этот курс, чтобы узнать, как реализовать распознавание лиц Azure в приложениях смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанного реальность, academy, unity, учебник, api, сталкиваются с распознавания, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603808"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>Г-н и Azure 304: Распознавание лиц.

![результат выполнения этого курса](images/AzureLabs-Lab4-00.png)

В этом курсе вы узнаете, как для добавления возможностей распознавания лиц с приложением смешанной реальности, с помощью Azure Cognitive Services, с помощью API распознавания лиц Майкрософт.

*Azure API распознавания лиц* — это служба Майкрософт, которая предоставляет разработчикам наиболее эффективные алгоритмы распознавания лиц, все это в облаке. *API распознавания лиц* имеет две основные функции: обнаружение с помощью атрибутов лиц и распознавание. Это позволяет разработчикам просто задать набор групп для лиц, а затем отправить изображения запрос в службу позже, чтобы определить, к которому принадлежит грани. Дополнительные сведения см. в статье [страницы распознавания лиц Azure](https://azure.microsoft.com/services/cognitive-services/face/).

После выполнения этого курса, у вас будет смешанной реальности HoloLens приложения, который будет осуществлять следующее:

1. Используйте **коснитесь жест** начать захват изображения с помощью встроенного HoloLens камеры. 
2. Отправьте записанный образ для *API распознавания лиц Azure* службы.
3. Получать результаты проверки *API распознавания лиц* алгоритм.
4. Используйте простой интерфейс пользователя, для отображения имени соответствующих пользователей.

Вы изучите способы получения результатов от службы API распознавания лиц в приложение на базе Unity смешанной реальности.

В приложении зависит от пользователя о том, как интегрировать результаты проектированию. Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity. Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> Г-н и Azure 304: Распознавание лиц.</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс основное внимание уделяется HoloLens, можно также применить полученные знания в этот курс поможет вам Windows Mixed Reality иммерсивную (VR). Поскольку иммерсивную (VR) не имеют доступных камеры, вам потребуется внешний камеры, подключенном к ПК. При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки иммерсивную (VR).

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#. Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.). Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .

Рекомендуется следующее оборудование и программное обеспечение для этого курса:

- На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)
- [Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика](install-the-tools.md)
- [Последний пакет SDK Windows 10](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Камера, подключенном к ПК (для разработки иммерсивных гарнитуры)
- Доступ к Интернету для настройки Azure и извлечения API распознавания лиц

## <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).
2.  Настроить и проверить ваш HoloLens. Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя). 

Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).

Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Глава 1 - портала Azure

Чтобы использовать *API распознавания лиц* службы в Azure, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.

1.  Во-первых, войдите в [портал Azure](https://portal.azure.com). 

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо будет создать его. Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.

2.  После входа в систему щелкните **New** в левом верхнем углу, а поиск *API распознавания лиц*, нажмите клавишу **ввод**.

    ![Поиск api распознавания лиц](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > Слово **New** может были заменены **создать ресурс**, в новых порталов.

3.  Новая страница будет предоставить описание *API распознавания лиц* службы. В нижней левой части этого запроса, выберите **создать** кнопку, чтобы создать ассоциацию с этой службой.

    ![сведения об api лиц](images/AzureLabs-Lab4-02.png)

4.  Когда вы перейдете на **создать**:

    1. Вставьте желаемого имени для данного экземпляра службы.

    2. Выберите подписку.

    3. Выберите ценовую категорию, соответствующие, если это первое время создания *служба API распознавания лиц*, уровень "бесплатный" (с именем F0) должны быть доступны для вас.

    4. Выберите **группы ресурсов** или создайте новую. Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure. Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов). 

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Приложения UWP, **Person Maker**, которая будет использоваться далее, необходимо использовать «Западная часть США» для расположения.

    6. Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.

    7. Выберите **создайте *.**

        ![Создание сталкиваются с api службы](images/AzureLabs-Lab4-03.png)

5.  Когда вы перейдете на **создать *** имеется ожидания службы должен быть создан, это может занять около минуты.

6.  Уведомление будет отображаться на портале, после создания экземпляра службы.

    ![уведомление о создании службы](images/AzureLabs-Lab4-04.png)

7.  Щелкните уведомлений для просмотра в новом экземпляре службы.

    ![Перейти к ресурсов уведомлений](images/AzureLabs-Lab4-05.png)

8.  Когда будете готовы, нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.

    ![доступ сталкиваются ключи api](images/AzureLabs-Lab4-06.png)

9.  В этом руководстве описано приложение должно выполнять вызовы к службе, что можно сделать с помощью подписки службы «key». Из *быстрого запуска* странице из вашей *API распознавания лиц* первая точка службы имеет номер 1, до *получите ключи.*

10. На *службы* выберите либо синюю **ключи** гиперссылку (если на странице "Быстрый запуск"), или **ключи** ссылку в меню навигации служб (слева, обозначенное с помощью " ключ "значок), чтобы увидеть ключи.

    > [!NOTE] 
    > Запишите один из ключей и защитить его, так как он понадобится позже.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Глава 2 - Использование приложения универсальной платформы Windows «Person Maker»

Не забудьте загрузить предварительно созданные приложении универсальной платформы Windows с именем [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Это приложение не конечный продукт, этот курс, просто средство для создания вашего Azure операций, которые будут зависят от более поздней версии проекта.

**Person Maker** позволяет создавать Azure операций, которые связаны с людьми и групп пользователей. Приложение помещает все необходимые сведения в формате, который можно затем позже использоваться FaceAPI для распознавания лиц людей, вы добавили. 

> [ВАЖНО] **Person Maker** использует некоторые основные регулирования, чтобы гарантировать, что не может превышать число вызовов службы в минуту для **бесплатная подписка уровня**. Изменит на красный зеленый текст в верхней и обновления как «АКТИВНОЕ», когда происходит регулирование; Если это так просто ожидания приложения (он будет ждать его рядом сохраняют доступ к службе лиц, обновление «IN-активный» при его можно снова использовать).

Это приложение использует *Microsoft.ProjectOxford.Face* библиотеки, которые вы сможете наиболее полно использовать API распознавания лиц. Эта библиотека доступна бесплатно в виде пакета NuGet. Дополнительные сведения об этом и аналогично API-интерфейсы [не забудьте посетить справочная статья API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Ниже приведены шаги, необходимые, инструкции для выполнения этих действий ниже документа. **Person Maker** приложение позволит вам:
>
> - Создание *лица группу*, который состоит из нескольких пользователей, которые необходимо связать с ней группу. С помощью учетной записи Azure можно разместить несколько групп.
>
> - Создание *Person*, который является членом группы пользователя. У каждого пользователя есть ряд *лиц* изображений, связанных с ним.
>
> -  Назначить *сталкиваются образы* для *Person*, чтобы разрешить службе Azure Face API для распознавания *Person* соответствующим *лиц*.
>
> -  *Обучение* вашей *Azure сталкиваются с API службы*.

Имейте в виду, поэтому для обучения это приложение для распознавания людей, вам десяти (10) крупным планом фотографий каждого человека, который вы хотите добавить в группу пользователя. Приложение Windows 10 камера может помочь с учетом. Необходимо убедиться, что каждой фотографии снят (избежать Размытие, скрывая или выполняется слишком далеко от субъекта), иметь фотографии в формате jpg или png, с размером файла образа, его размер не **4 МБ**и не менее, чем **1 КБ**.

> [!NOTE]
> Если выполнить этот учебник, не используйте собственного грани для обучения, HoloLens, загружаемых, не проверяя самостоятельно. Используйте шрифт, коллеги или специалист учащегося.

Под управлением **Person Maker**:

1.  Откройте **PersonMaker** папку и дважды щелкните *решение PersonMaker* чтобы открыть его с *Visual Studio*.

2.  Один раз *PersonMaker решение* еще открыт, убедитесь, что:

    1. *Конфигурации решения* присваивается **Отладка**.

    2. *Платформа решения* присваивается **x86**

    3. *Целевую платформу* — **локальный компьютер**.

    4.  Также может потребоваться *восстановить пакеты NuGet* (щелкните правой кнопкой мыши *решение* и выберите **восстановить пакеты NuGet**).

3.  Нажмите кнопку *локального компьютера* и запустится приложение. Имейте в виду, что на экране меньшего размера, все содержимое может не отображаться, хотя можно более детальном на его просмотр.

    ![пользовательский интерфейс для создателя Person](images/AzureLabs-Lab4-07.png)

4.  Вставить вашей **ключ проверки подлинности Azure**, который должен иметь, из вашего *API распознавания лиц* службы в Azure.

5.  Вставьте:

    1. *Идентификатор* вы хотите назначить *лица группу*. Идентификатор должен быть в нижнем регистре без пробелов. Запишите этот идентификатор, так как она понадобится позже в проекте Unity.
    2. *Имя* вы хотите назначить *лица группу* (может содержать пробелы).


6.  Нажмите клавишу **создать лица группу** кнопки. Под кнопкой появится сообщение с подтверждением.

> [!NOTE]
> Если у вас есть ошибка «Отказано в доступе», проверьте расположение, установленные для службы Azure. Как уже говорилось выше, это приложение предназначен для «Западная часть США».

> [!IMPORTANT]
> Обратите внимание, что можно также щелкнуть **получить группу известные** кнопки: это если вы уже создали лица группу и требуется использовать его, а не создавать новый. Имейте в виду, если щелкнуть *создать лица группу* с группой известных также будет извлечена группу.

7.  Вставить *имя* из *Person* вы хотите создать.

    1. Нажмите кнопку **создать Person** кнопки.

    2. Под кнопкой появится сообщение с подтверждением.

    3. Если вы хотите удалить пользователя, созданный ранее, можно написать имя в текстовом поле и нажмите клавишу **удалить пользователя**

8.  Убедитесь, что известно расположение десяти (10) фотографий пользователя, которого вы хотите добавить в группу.

9.  Нажмите клавишу **создать и открыть папку** чтобы открыть обозреватель Windows к папке, связанный пользователю. Добавление изображений десяти (10) в папке. Они должны иметь *JPG* или *PNG* формат файла.

10. Щелкните **отправить в Azure**. Счетчик покажет состояние отправки, следуют сообщение после ее завершения.

11. После завершения счетчика и выводится сообщение с подтверждением щелкните **обучения** для обучения службы.

Когда процесс завершится, вы будете готовы переместить в Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Глава 3 - Настройка проекта Unity

Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.

1.  Откройте *Unity* и нажмите кнопку **New**. 

    ![Начните новый проект Unity.](images/AzureLabs-Lab4-08.png)

2.  Теперь необходимо будет указать имя проекта Unity. Вставить **MR_FaceRecognition**. Убедитесь, что тип проекта присваивается **3D**. Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги). Щелкните **создать проект**.

    ![Укажите сведения для нового проекта Unity.](images/AzureLabs-Lab4-09.png)

3.  С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**. Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**. Изменение **внешнего редактора скриптов** для **Visual Studio 2017**. Закрыть **предпочтения** окна.

    ![Обновите настройки редактора скриптов.](images/AzureLabs-Lab4-10.png)

4.  Перейдите к **файл > Параметры сборки** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.

    ![Создавайте окно "Параметры", переключить платформу для универсальной платформы Windows.](images/AzureLabs-Lab4-11.png)

5.  Перейдите к **файл > Параметры сборки** и убедитесь, что:

    1. **Целевое устройство** присваивается **HoloLens**

        > Иммерсивную, задайте **целевое устройство** для *любого устройства*.

    2. **Тип сборки** присваивается **D3D**
    3. **Пакет SDK для** присваивается **самую новую установленную**
    4. **Версия Visual Studio** присваивается **самую новую установленную**
    5. **Сборка и запуск** присваивается **локального компьютера**
    6. Сохраните сцены и добавить его к сборке. 

        1. Это сделать, выбрав **добавьте откройте сцены**. Сохранение окно будет отображаться.

            ![Нажмите кнопку Добавить кнопку open сцены](images/AzureLabs-Lab4-12.png)

        2. Выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.

            ![Создание новой папки scripts](images/AzureLabs-Lab4-13.png)

        3. Откройте только что созданный **сцены** папку, а затем в **имя файла**: текстовое поле, тип **FaceRecScene**, нажмите клавишу **Сохранить**.

            ![Присвойте имя новой сцены.](images/AzureLabs-Lab4-14.png)

    7. Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.

6. В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится. 

    ![Открытие параметров проигрывателя.](images/AzureLabs-Lab4-15.png)

7. В этой панели необходимо проверить некоторые настройки:

    1. В **другие параметры** вкладке:

        1. **Сценарии** **версии среды выполнения** должно быть **экспериментальные** (.NET 4.6 эквивалент). Это изменение вызовет необходимость перезапуска редактора.
        2. **Создание сценариев серверной части** должно быть **.NET**
        3. **Уровень совместимости API** должно быть **.NET 4.6**

            ![Обновите другие параметры.](images/AzureLabs-Lab4-16.png)
      
    2. В рамках **параметров публикации** в списке **возможности**, проверьте:

        - **internetClient**
        - **Webcam**

            ![Обновление параметров публикации.](images/AzureLabs-Lab4-17.png)

    3. Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.

        ![Обновление параметров R X.](images/AzureLabs-Lab4-18.png)

8.  Вернитесь в *параметры построения*, **Unity C# проекты** больше не отображается серым, установите флажок рядом с это. 
9.  Закройте окно Параметры построения.
10. Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).

## <a name="chapter-4---main-camera-setup"></a>Главе 4 - Main Camera

> [!IMPORTANT]
> Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете [загрузить этот .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)и импортировать его в проект в качестве [Custom Пакет](https://docs.unity3d.com/Manual/AssetPackages.html). Имейте в виду, что этот пакет также включает Импорт *Newtonsoft DLL*, описываемое в [Глава 5](#chapter-5--import-the-newtonsoft.json-library). Таким образом импортированы, можно продолжить выполнение после [Глава 6](#chapter-6-create-the-faceanalysis-class).

1.  В *иерархии* панели, выберите **Main Camera**.

2.  После выбора можно видеть все компоненты **Main Camera** в *панели Инспектора*.

    1. **Объекта Camera** должен иметь имя **Main Camera** (Обратите внимание, правильность написания!)

    2. Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания!)

    3. Убедитесь, что **преобразование положения** присваивается **0, 0, 0**

    4. Задайте **очистить флаги** для **сплошным цветом**

    5. Задайте **фона** цвет компонента камеры для **черная, альфа-значение 0 (шестнадцатеричный код: #00000000)**

        ![Установка компонентов камеры](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Глава 5 – импорт библиотеки Newtonsoft.Json

> [!IMPORTANT]
> Если вы импортировали .unitypackage в [последняя глава](#chapter-4--main-camera-setup), можно пропустить в этой главе.

Для десериализации и сериализации объектов получаемых и отправляемых в службу программ-роботов необходимо скачать *Newtonsoft.Json* библиотеки. Вы найдете совместимой версии упорядочены с правильной структурой папок Unity в этом [файл пакета Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Чтобы импортировать библиотеки:

1.  Скачайте пакет Unity.
2.  Щелкните **активы**, **импортировать пакет**, **пользовательского пакета**.

    ![Импорт библиотеки Newtonsoft.Json](images/AzureLabs-Lab4-20.png)

3.  Найдите загруженный пакет Unity и нажмите кнопку Открыть.
4.  Убедитесь, что все компоненты пакета установлен флажок и нажмите кнопку **импорта**.

    ![Импорт библиотеки Newtonsoft.Json](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Глава 6 - создание класса FaceAnalysis

Класс FaceAnalysis предназначена для размещения методы, необходимые для взаимодействия со службой Azure распознавания лиц. 

- После отправки образа записи службы, его анализ его и идентификация лиц в и определить, если любой принадлежат известных человека. 
- При обнаружении известного человека, этот класс отображается его имя в виде текста пользовательского интерфейса в сцене.

Чтобы создать *FaceAnalysis* класса:

 1. Щелкните правой кнопкой мыши в *папку Assets* находится в панели «проект», затем щелкните **создать** > **папку**. Вызовите папке **сценариев**. 

    ![Создайте класс FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Дважды щелкните папку, только что создали, чтобы открыть его. 
3.  Щелкните правой кнопкой мыши внутри папки, а затем **создать**  >   **C# сценарий**. Вызовите сценарий *FaceAnalysis*. 
4.  Дважды щелкните новый *FaceAnalysis* скрипт, чтобы открыть его в Visual Studio 2017.
5.  Введите следующие пространства имен выше *FaceAnalysis* класса:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Теперь необходимо добавить все объекты, которые используются для deserialising. Эти объекты должны быть добавлены **за пределами** из *FaceAnalysis* сценария (под нижней фигурная скобка). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. *Start()* и *Update()* методы не будут использоваться, поэтому теперь удалите их. 

8.  Внутри *FaceAnalysis* добавьте следующие переменные:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Замените **ключ** и **personGroupId** ваш ключ службы и идентификатор группы, которую вы создали ранее.

9.  Добавить *Awake()* метод, который инициализирует класс, добавив *ImageCapture* класс Main Camera и вызывает метод создания метки:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Добавить *CreateLabel()* метод, который создает *метка* объект для отображения результатов:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Добавить *DetectFacesFromImage()* и *GetImageAsByteArray()* метод. Первое из них будет запрашивать службу распознавания лиц для обнаружения любые возможные лиц отправленного изображения, а второй, необходимая для преобразования записанного образа в массив байтов:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Добавить *IdentifyFaces()* метод, который запрашивает *службы распознавания лиц* для идентификации любой известных лиц, обнаружен ранее отправленного изображения. Запрос возвращает идентификатор определенного пользователя, но не имя:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Добавить *GetPerson()* метод. Предоставляя пользователя, идентификатор, этот метод затем запросы *службы распознавания лиц* для возврата имени определенного пользователя:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Не забудьте **Сохранить** изменения, прежде чем вернуться в редактор Unity.
15.  В редакторе Unity перетащите FaceAnalysis скрипт из папки скриптов в панель «проект» для объекта Main Camera в *панели иерархии*. Новый компонент скрипта таким образом будут добавляться к камере Main. 

![FaceAnalysis месте на главной камеры](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Глава 7 - создание класса ImageCapture

Цель *ImageCapture* класс — размещение методы, необходимые для взаимодействия с вашей *службы распознавания лиц Azure* проанализируйте образ будет записан, идентификация лиц на его и Определение, входит ли он известных человека. При обнаружении известного человека, этот класс отображается его имя в виде текста пользовательского интерфейса в сцене.

Чтобы создать *ImageCapture* класса:
 
1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, вы создали ранее, а затем щелкните **создать**,  **C# сценарий**. Вызовите сценарий *ImageCapture*. 
2.  Дважды щелкните новый *ImageCapture* скрипт, чтобы открыть его в Visual Studio 2017.
3.  Введите следующие пространства имен над классом ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Внутри *ImageCapture* добавьте следующие переменные:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Добавить *Awake()* и *Start()* методы, необходимые для инициализации класса и разрешить HoloLens для захвата жесты пользователя:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Добавить *TapHandler()* который вызывается, когда пользователь выполняет *коснитесь* жестов:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Добавить *ExecuteImageCaptureAndAnalysis()* метод, который начнется процесс записи образа:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Добавление обработчиков, которые вызываются после завершения процесса отслеживания photo:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Не забудьте **Сохранить** изменения, прежде чем вернуться в редактор Unity.

## <a name="chapter-8---building-the-solution"></a>Глава 8 - построения решения

Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш HoloLens.

Прежде чем сделать, убедитесь, что:

-   Все параметры, упомянутые в главе 3 настроены правильно. 
-   Сценарий *FaceAnalysis* присоединяется к объекта Main Camera. 
-   Оба **ключом проверки подлинности** и **идентификатор группы** были заданы в *FaceAnalysis* скрипта.

Этот момент можно приступать к построению решения. После построения решения, вы будете готовы для развертывания приложения.

Чтобы начать процесс построения:

1.  Сохраните текущую сцену, щелкнув файл, сохраните.
2.  Перейдите к файлу, параметры сборки, щелкните Добавить откройте сцены.
3.  Убедитесь, что к такту Unity C# проектов.

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  Нажмите клавишу сборки. При этом Unity запустится окно проводника, где необходимо создать, а затем выберите папку, чтобы создать приложение в. Создайте эту папку прямо сейчас, в рамках проекта Unity и назовите его приложение. Затем выбранные папки приложения, нажмите клавишу "Выбор папки". 
5.  Unity начнется при создании проекта, в папку приложения. 
6.  Один раз Unity завершил построение (может занять некоторое время), откроется окно проводника в папке построения.

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  Откройте папку приложения и затем открыть новое решение проект (как показано выше, MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>Глава 9 - развертывания приложения

Для развертывания на HoloLens:

1.  Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика**. Выполните указанные ниже действия.

    1. Хотя носить вашей HoloLens, откройте **параметры**.
    2. Перейдите к **сеть и Интернет > Wi-Fi > Дополнительные параметры**
    3. Примечание **IPv4** адрес.
    4. Затем перейдите к **параметры**, а затем в **обновление и безопасность > для разработчиков** 
    5. Включен режим разработчика.

2.  Перейдите к новой сборки Unity ( *приложения* папки) и откройте файл решения с *Visual Studio*.
3.  В списке выберите конфигурацию решения **Отладка**.
4.  В платформу решения, выберите **x86**, **удаленный компьютер**. 

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  Перейдите к **меню "сборка"** и щелкнуть **развернуть решение**, чтобы загрузить неопубликованное приложение для вашего HoloLens.
6.  Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!

> [!NOTE]
> Чтобы развернуть иммерсивных гарнитура, переключите **платформа решения** для *локального компьютера*и задайте **конфигурации** для *Отладка*, с *x86* как **платформы**. Затем развернуть на локальный компьютер, с помощью **меню "сборка"**, выбрав *развернуть решение*. 


## <a name="chapter-10---using-the-application"></a>Глава 10 - с помощью приложения

1.  Носить HoloLens, запустите это приложение.
2.  Рассмотрим пользователя, которая была зарегистрирована с *API распознавания лиц*. Убедитесь в следующем.

    -  Лица крупным не слишком удаленных и четко видны
    -  Освещение среды не слишком темный

3.  Используйте жест касания для записи фотографии лица.
4.  Подождите, пока приложение для отправки запроса анализа и получения ответа.
5.  Если пользователь был успешно распознан, его имя будет отображаться как текст пользовательского интерфейса.
6.  Можно повторить процесс отслеживания с помощью жеста касания каждые несколько секунд.

## <a name="your-finished-azure-face-api-application"></a>Готовое приложение API распознавания лиц Azure

Поздравляем, вы создали приложение смешанной реальности, которое использует службу распознавания лиц Azure для обнаружения лиц в образе и идентификации все известные лица.

![результат выполнения этого курса](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Упражнения премии

### <a name="exercise-1"></a>Упражнение 1

**API распознавания лиц Azure** достаточно производителен, чтобы обнаружить до 64 лиц в одном образе. Расширения приложения, таким образом, он может распознавания лиц, два или три, среди других пользователей.

### <a name="exercise-2"></a>Упражнение 2

**API распознавания лиц Azure** он также может предоставить обратно все виды сведений об атрибутах. Интегрируйте в приложение. Это может быть еще более интересное в сочетании с [API распознавания эмоций](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).
