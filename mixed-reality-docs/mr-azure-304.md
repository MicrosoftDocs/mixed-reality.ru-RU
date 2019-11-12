---
title: MR и Azure 304 — распознавание лиц
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, распознавание лиц, hololens, иммерсивное, VR
ms.openlocfilehash: 23676684c2ec325f9d6f1924e7a0bad14d41f13e
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926784"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR и Azure 304: распознавание лиц

![результат выполнения этого курса](images/AzureLabs-Lab4-00.png)

В этом курсе вы узнаете, как добавить возможности распознавания лиц в приложение смешанной реальности с помощью Cognitive Services Azure с API распознавания лиц Майкрософт.

*Azure API распознавания лиц* — это служба Майкрософт, которая предоставляет разработчикам самые современные алгоритмы, все в облаке. *API распознавания лиц* имеет две основные функции: обнаружение лиц с помощью атрибутов и распознавание лиц. Это позволяет разработчикам просто задать набор групп для лиц, а затем отправить образы запросов в службу позже, чтобы определить, кому принадлежит лицо. Дополнительные сведения см. на [странице распознавания лиц Azure](https://azure.microsoft.com/services/cognitive-services/face/).

Прополнив этот курс, вы получите приложение HoloLens для смешанной реальности, которое сможет сделать следующее:

1. Используйте **жест касания** , чтобы начать запись изображения с помощью встроенной камеры HoloLens. 
2. Отправьте захваченный образ в службу *API распознавания лиц Azure* .
3. Получение результатов алгоритма *API распознавания лиц* .
4. Используйте простой пользовательский интерфейс для просмотра имени сопоставленных людей.

Вы узнаете, как получить результаты из службы API распознавания лиц в приложении смешанной реальности на основе Unity.

В приложении вы будете выполнять интеграцию результатов с вашей структурой. Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity. Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> MR и Azure 304: распознавание лиц</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс в основном ориентирован на HoloLens, вы можете также применить сведения, которые вы узнаете в этом курсе, к головным телефонам Windows Mixed Reality (VR). Так как у головных гарнитур нет доступных камер, вам потребуется внешняя камера, подключенная к компьютеру. При работе с курсом вы увидите заметки о любых изменениях, которые могут потребоваться для поддержки головных телефонов (VR).

## <a name="prerequisites"></a>Необходимые условия

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#. Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018). Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.

Для этого курса рекомендуется следующее оборудование и программное обеспечение:

- ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)
- [Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика](install-the-tools.md)
- [Последний пакет SDK для Windows 10](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Камера, подключенная к компьютеру (для разработки в увлекательной гарнитуре)
- Доступ к Интернету для установки Azure и извлечения API распознавания лиц

## <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).
2.  Настройка и тестирование HoloLens. Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя). 

Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).

Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Глава 1. портал Azure

Чтобы использовать службу *API распознавания лиц* в Azure, необходимо настроить экземпляр службы, чтобы сделать ее доступной для приложения.

1.  Сначала войдите на [портал Azure](https://portal.azure.com). 

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо создать ее. Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.

2.  Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу и выполните поиск по *API распознавания лиц*нажмите клавишу **Ввод**.

    ![Поиск API распознавания лиц](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > Слово **New** может быть заменено на **создать ресурс**в новых порталах.

3.  На новой странице будет представлено описание службы *API распознавания лиц* . В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать связь с этой службой.

    ![сведения об API распознавания лиц](images/AzureLabs-Lab4-02.png)

4.  После нажатия кнопки **создать**:

    1. Вставьте нужное имя для этого экземпляра службы.

    2. Выберите подписку.

    3. Выберите ценовую категорию, подходящую для вас. Если вы впервые создаете *службу API распознавания лиц*, вам будет доступен бесплатный уровень (с именем F0).

    4. Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure. Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов. 

        > Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Приложение UWP, которое вы используете **позже, должно**использовать "Западная часть США" для расположения.

    6. Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.

    7. Выберите **создать *.**

        ![Создание службы API распознавания лиц](images/AzureLabs-Lab4-03.png)

5.  После нажатия кнопки **создать *** необходимо подождать, пока не будет создана служба, а это может занять некоторое время.

6.  После создания экземпляра службы на портале отобразится уведомление.

    ![уведомление о создании службы](images/AzureLabs-Lab4-04.png)

7.  Щелкните уведомления, чтобы изучить новый экземпляр службы.

    ![Переход к уведомлению о ресурсе](images/AzureLabs-Lab4-05.png)

8.  Когда будете готовы, нажмите кнопку **Перейти к ресурсу** в уведомлении, чтобы изучить новый экземпляр службы.

    ![ключи API лиц для доступа](images/AzureLabs-Lab4-06.png)

9.  В рамках этого руководства приложение должно будет вызывать службу, что выполняется с помощью ключа подписки вашей службы. На странице *быстрого запуска* службы *API распознавания лица* первая точка — номер 1, чтобы *взять ключи.*

10. На странице *Служба* выберите гиперссылку «синие **ключи** » (если на странице быстрого запуска) или ссылку « **ключи** » в меню навигации служб (слева, обозначенном значком «ключ»), чтобы отобразить ключи.

    > [!NOTE] 
    > Запишите либо один из ключей, и защитите его, так как он понадобится позже.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Глава 2. Использование приложения UWP "Person Maker"

Обязательно загрузите предварительно созданное приложение UWP с именем [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Это приложение не является конечным продуктом для этого курса. это просто средство, которое поможет вам создать свои записи Azure, на которые последует последующий проект.

**Person Maker** позволяет создавать записи Azure, связанные с людьми и группами людей. Приложение поместит всю необходимую информацию в формате, который впоследствии может использоваться Фацеапи, чтобы распознать лиц, которые были добавлены. 

> СУЩЕСТВЕННО **Person Maker** использует некоторое базовое регулирование, чтобы не превысить количество вызовов службы за минуту для **бесплатного уровня подписки**. Зеленый текст в верхней части изменится на красный и будет обновляться как активный при регулировании. Если это так, просто дождитесь приложения (будет ожидать, пока он сможет продолжить доступ к службе распознавания лиц, обновив его как "IN-ACTIVE", когда его можно будет использовать).

В этом приложении используются библиотеки *Microsoft. прожектоксфорд. Face* , которые позволяют полностью использовать API распознавания лиц. Эта библиотека доступна бесплатно в качестве пакета NuGet. Дополнительные сведения об этих и похожих API-интерфейсах см. [в справочной статье по API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Это лишь необходимые шаги. инструкции по выполнению этих действий приведены ниже в документе. Приложение **Person Maker** позволит вам:
>
> - Создайте *группу Person*, которая состоит из нескольких людей, которые вы хотите связать с ней. С помощью учетной записи Azure можно разместить несколько групп людей.
>
> - Создайте *пользователя*, который является членом группы людей. С каждым лицом связано несколько изображений, связанных с *лицом* .
>
> -  Назначьте *пользователю* *изображения* лиц, чтобы служба Azure API распознавания лиц могла распознать *человека* с *помощью соответствующего лица*.
>
> -  Обучить *службу API распознавания лиц Azure*.

Имейте в виду, что чтобы обучить это приложение для распознавания людей, вам потребуется десять (10) закрываемых фотографий каждого человека, которого вы хотите добавить в вашу группу лиц. Приложение для фотосистемы Windows 10 поможет вам сделать это. Необходимо убедиться в том, что каждая фотография является ясной (Избегайте размытия, скрытия или слишком далекого края, от субъекта), постарайтесь иметь фотографию в формате JPG или PNG, размер файла изображения не должен превышать **4 МБ**и не должен быть меньше **1 КБ**.

> [!NOTE]
> Если вы используете этот учебник, не используйте собственные лица для обучения, как при помещении HoloLens на, вы не сможете взглянуть на себя. Воспользуйтесь лицом коллеги или учащегося.

Работающая программа **Person Maker**:

1.  Откройте папку **персонмакер** и дважды щелкните *решение персонмакер* , чтобы открыть его в *Visual Studio*.

2.  После открытия *решения персонмакер* убедитесь в том, что:

    1. Для *конфигурации решения* задано значение **Отладка**.

    2. *Платформа решения* установлена в значение " **x86** "

    3. *Целевая платформа* — **локальный компьютер**.

    4.  Также может потребоваться *восстановить пакеты NuGet* (щелкните *решение* правой кнопкой мыши и выберите пункт **восстановить пакеты NuGet**).

3.  Щелкните *локальный компьютер* , и приложение запустится. Имейте в виду, что на небольших экранах все содержимое может не отображаться, хотя можно прокручивать его вниз для просмотра.

    ![Пользовательский интерфейс Person Maker](images/AzureLabs-Lab4-07.png)

4.  Вставьте **ключ проверки подлинности Azure**, который вам необходим, из службы *API распознавания лиц* в Azure.

5.  Вставляет

    1. *Идентификатор* , который необходимо назначить *группе лиц*. Идентификатор должен быть строчным, без пробелов. Запишите этот идентификатор, так как он потребуется позже в проекте Unity.
    2. *Имя* , которое нужно назначить *группе Person* (может содержать пробелы).


6.  Нажмите кнопку **создать группу Person** . Под кнопкой появится сообщение с подтверждением.

> [!NOTE]
> При наличии ошибки "доступ запрещен" проверьте расположение, заданное для службы Azure. Как упоминалось выше, это приложение предназначено для "Западная часть США".

> [!IMPORTANT]
> Вы заметите, что можно также нажать кнопку **извлечь известную группу** : Если вы уже создали группу лиц и хотите использовать ее, а не создать новую. Имейте в виду, что если щелкнуть *создать группу лиц* с известной группой, будет также получена группа.

7.  Введите *имя* *пользователя* , которого вы хотите создать.

    1. Нажмите кнопку **создать пользователя** .

    2. Под кнопкой появится сообщение с подтверждением.

    3. Если вы хотите удалить ранее созданного пользователя, вы можете записать его в текстовое поле и нажать клавишу **Delete Person** .

8.  Убедитесь, что вы знаете расположение десяти (10) фотографий человека, которого вы хотите добавить в группу.

9.  Нажмите кнопку **создать и откройте папку** , чтобы открыть проводник Windows в папке, связанной с пользователем. Добавьте в папку десять изображений (10). Эти файлы должны иметь формат *JPG* или *PNG* .

10. Щелкните **отправить в Azure**. Счетчик показывает состояние отправки, за которым следует сообщение после его завершения.

11. Когда счетчик будет завершен и появится сообщение с подтверждением, щелкните " **обучение** ", чтобы обучить службу.

После завершения процесса вы можете перейти в Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Глава 3. Настройка проекта Unity

Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.

1.  Откройте *Unity* и нажмите кнопку **создать**. 

    ![Запуск нового проекта Unity.](images/AzureLabs-Lab4-08.png)

2.  Теперь необходимо указать имя проекта Unity. Вставка **MR_FaceRecognition**. Убедитесь, что для типа проекта задано значение **3D**. Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше). Затем нажмите кнопку **создать проект**.

    ![Укажите сведения о новом проекте Unity.](images/AzureLabs-Lab4-09.png)

3.  При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**. Перейдите к разделу **изменение параметров >** , а затем в новом окне перейдите к разделу **Внешние инструменты**. Измените **Редактор внешних скриптов** на **Visual Studio 2017**. Закройте окно **настройки** .

    ![Обновить настройки редактора скриптов.](images/AzureLabs-Lab4-10.png)

4.  Затем перейдите в раздел **файл > параметры сборки** и переключите платформу на **универсальная платформа Windows**, нажав кнопку **коммутатора платформы** .

    ![Окно "параметры сборки". Переключите платформу в UWP.](images/AzureLabs-Lab4-11.png)

5.  Перейдите в раздел **файл > параметры сборки** и убедитесь в том, что:

    1. **Целевое устройство** имеет значение **HoloLens**

        > Для впечатляющих головных телефонов задайте для параметра **целевое устройство** *любое устройство*.

    2. Для **типа сборки** задано значение **D3D**
    3. **Пакет SDK** установлен в значение " **Последняя установка** "
    4. Для **версии Visual Studio** установлено значение " **Последняя установка** "
    5. **Сборка и запуск** настроены на **локальный компьютер**
    6. Сохраните сцену и добавьте ее в сборку. 

        1. Для этого выберите **Добавить открытые сцены**. Появится окно сохранения.

            ![Нажмите кнопку Добавить кнопку "открыть сцены"](images/AzureLabs-Lab4-12.png)

        2. Нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».

            ![Создать новую папку скриптов](images/AzureLabs-Lab4-13.png)

        3. Откройте созданную папку **сцены** , а затем в текстовом поле **имя файла**введите **фацерексцене**, а затем нажмите кнопку **сохранить**.

            ![Присвойте имя новой сцене.](images/AzureLabs-Lab4-14.png)

    7. Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.

6. В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* . 

    ![Откройте параметры проигрывателя.](images/AzureLabs-Lab4-15.png)

7. На этой панели необходимо проверить несколько параметров:

    1. На вкладке **другие параметры** выполните следующие действия.

        1. **Версия среды выполнения** сценариев должна быть **экспериментальной** (эквивалент .NET 4,6). Изменение этого триггера приведет к необходимости перезапуска редактора.
        2. **Серверная часть сценариев** должна быть **.NET**
        3. **Уровень совместимости API** должен быть **.NET 4,6**

            ![Обновите другие параметры.](images/AzureLabs-Lab4-16.png)
      
    2. На вкладке **Параметры публикации** в разделе **возможности**установите флажок:

        - **InternetClient**
        - **Бесед**

            ![Обновляются параметры публикации.](images/AzureLabs-Lab4-17.png)

    3. На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .

        ![Обновите параметры X R.](images/AzureLabs-Lab4-18.png)

8.  Вернувшись в *параметры сборки*, **проекты C# Unity** больше не заключаются. Установите флажок рядом с этим. 
9.  Закройте окно параметры сборки.
10. Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).

## <a name="chapter-4---main-camera-setup"></a>Глава 4 — Настройка основной камеры

> [!IMPORTANT]
> Если вы хотите пропустить компонент *установки Unity, установленный* в этом курсе, и продолжить работу с кодом, [Скачайте этот файл. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)и импортируйте его в проект как [пользовательский пакет](https://docs.unity3d.com/Manual/AssetPackages.html). Имейте в виду, что этот пакет также включает в себя импорт *библиотеки DLL Newtonsoft*, описанной в [главе 5](#chapter-5--import-the-newtonsoftjson-library). После импорта можно продолжить с [раздела 6](#chapter-6---create-the-faceanalysis-class).

1.  На панели *Иерархия* выберите **основную камеру**.

2.  После выбора вы сможете увидеть все компоненты **основной камеры** на *панели инспектора*.

    1. **Объект Camera** должен называться **основной камерой** (Обратите внимание на орфографию!)

    2. Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на правописание).

    3. Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .

    4. Установить для **чистых флагов** **сплошной цвет**

    5. Установить черный цвет **фона** для компонента камеры **, альфа 0 (шестнадцатеричный код: #00000000)**

        ![Настройка компонентов камеры](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Глава 5 — Импорт библиотеки Newtonsoft. JSON

> [!IMPORTANT]
> Если вы импортировали ". пакет unitypackage" в [последней главе](#chapter-4---main-camera-setup), эту главу можно пропустить.

Чтобы упростить десериализацию и сериализацию объектов, полученных и отправленных службе Bot, необходимо скачать библиотеку *Newtonsoft. JSON* . Совместимая версия уже организована с правильной структурой папок Unity в этом [файле пакета Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Чтобы импортировать библиотеку, сделайте следующее:

1.  Скачайте пакет Unity.
2.  Щелкните **ресурсы**, **импортировать пакет**, **пользовательский пакет**.

    ![Импорт библиотеки Newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  Найдите скачанный пакет Unity и нажмите кнопку Открыть.
4.  Убедитесь, что все компоненты пакета являются тактовыми, и нажмите кнопку **Импорт**.

    ![Импорт библиотеки Newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Глава 6. Создание класса Фацеаналисис

Класс Фацеаналисис предназначен для размещения методов, необходимых для взаимодействия со службой распознавания лиц Azure. 

- После отправки службой образа записи он будет анализировать и определять лица в и определять, принадлежат ли какие-либо лица известному человеку. 
- Если обнаружено известное лицо, этот класс будет отображать его имя в виде текста пользовательского интерфейса в сцене.

Чтобы создать класс *фацеаналисис* , сделайте следующее:

 1. Щелкните правой кнопкой мыши *папку Assets* , расположенную на панели проект, а затем выберите **создать** > **папку**. Вызовите **скрипты**папки. 

    ![Создайте класс Фацеаналисис.](images/AzureLabs-Lab4-22.png)

2.  Дважды щелкните только что созданную папку, чтобы открыть ее. 
3.  Щелкните правой кнопкой мыши внутри папки, а затем выберите **создать** >  **C# скрипт**. Вызовите скрипт *фацеаналисис*. 
4.  Дважды щелкните новый скрипт *фацеаналисис* , чтобы открыть его в Visual Studio 2017.
5.  Введите следующие пространства имен над классом *фацеаналисис* :

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Теперь необходимо добавить все объекты, используемые для десериалисинг. Эти объекты должны быть добавлены **за пределами** сценария *фацеаналисис* (под нижней фигурной скобкой). 

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
7. Методы *Start ()* и *Update ()* не будут использоваться, поэтому удалите их сейчас. 

8.  В классе *фацеаналисис* добавьте следующие переменные:

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
    > Замените **ключ** и **персонграупид** ключом службы и идентификатором созданной ранее группы.

9.  Добавьте метод " *спящий ()* ", который инитиалисес класс, добавив класс *Имажекаптуре* в основную камеру и вызовет метод создания метки:

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

10. Добавьте метод *CreateLabel ()* , который создает объект *Label* для вывода результатов анализа:

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

11. Добавьте метод *детектфацесфромимаже ()* и *жетимажеасбитеаррай ()* . Первый из них запросит службу распознавания лиц обнаружить любое возможное лицо в отправленном изображении, а Последнее необходимо преобразовать записанный образ в массив байтов:

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

12. Добавьте метод *идентифифацес ()* , который запрашивает *службу распознавания лиц* для определения известных лиц, обнаруженных ранее в отправленном изображении. Запрос возвратит идентификатор идентифицированного человека, но не имя:

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

            // Serialize to Json format
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

13. Добавьте метод *-Person ()* . Указав идентификатор пользователя, этот метод затем запрашивает *службу распознавания лиц* , чтобы вернуть имя идентифицированного человека:

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

14.  Не забудьте **сохранить** изменения перед возвратом в редактор Unity.
15.  В редакторе Unity перетащите сценарий Фацеаналисис из папки скрипты на панели проект в главный объект Camera на *панели Иерархия*. Новый компонент скрипта будет добавлен в основную камеру. 

![Размещение Фацеаналисис на основной камере](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Глава 7. Создание класса Имажекаптуре

Класс *имажекаптуре* предназначен для размещения методов, необходимых для взаимодействия со *службой распознавания лиц Azure* , для анализа образа, который будет записан, определения лиц в нем и определения принадлежности к известному человеку. Если обнаружено известное лицо, этот класс будет отображать его имя в виде текста пользовательского интерфейса в сцене.

Чтобы создать класс *имажекаптуре* , сделайте следующее:
 
1.  Щелкните правой кнопкой мыши в созданной ранее папке **Scripts** , а затем выберите **создать**,  **C# скрипт**. Вызовите скрипт *имажекаптуре*. 
2.  Дважды щелкните новый скрипт *имажекаптуре* , чтобы открыть его в Visual Studio 2017.
3.  Введите следующие пространства имен над классом Имажекаптуре:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  В классе *имажекаптуре* добавьте следующие переменные:

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

5.  Добавьте методы *спящего режима ()* и *Start ()* , необходимые для инициализироватьи класса, и разрешите HoloLens захватывать жесты пользователя:

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

6.  Добавьте *тафандлер ()* , который вызывается, когда пользователь выполняет жест *касания* :

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

7.  Добавьте метод *ексекутеимажекаптуреанданалисис ()* , который начнет процесс записи образа:

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

8.  Добавьте обработчики, вызываемые при завершении процесса записи фотографий:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Не забудьте **сохранить** изменения перед возвратом в редактор Unity.

## <a name="chapter-8---building-the-solution"></a>Глава 8. Создание решения

Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на HoloLens.

Перед этим убедитесь в том, что:

-   Все параметры, упомянутые в главе 3, заданы правильно. 
-   *Фацеаналисис* скрипта прикреплен к главному объекту Camera. 
-   **Ключ проверки подлинности** и **идентификатор группы** заданы в сценарии *фацеаналисис* .

Этот момент готов к созданию решения. После сборки решения вы будете готовы к развертыванию приложения.

Чтобы начать процесс сборки:

1.  Сохраните текущую сцену, щелкнув файл, сохранить.
2.  Последовательно выберите пункты файл, параметры сборки и добавить открытые сцены.
3.  Убедитесь, что проект Unity C# является тактовым.

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  Нажмите кнопку сборка. После этого Unity запустит окно проводника, в котором необходимо создать, а затем выбрать папку для построения приложения. Создайте эту папку прямо сейчас, в проекте Unity и назовите ее приложение. Затем выберите папку приложения и нажмите кнопку Выбрать папку. 
5.  Unity начнет сборку проекта в папку приложения. 
6.  После завершения сборки Unity (может занять некоторое время) он откроет окно проводника в расположении сборки.

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  Откройте папку приложения, а затем откройте решение нового проекта (как показано выше, MR_FaceRecognition. sln).


## <a name="chapter-9---deploying-your-application"></a>Глава 9. Развертывание приложения

Для развертывания на HoloLens выполните следующие действия.

1.  Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика**. Выполните указанные ниже действия.

    1. Людьми HoloLens, откройте **Параметры**.
    2. Последовательно выберите пункты **сеть & интернет > Wi-Fi > дополнительные параметры**
    3. Запишите **IPv4** -адрес.
    4. Затем вернитесь к **параметрам**и **обновите & > безопасности для разработчиков** . 
    5. Задайте режим разработчика на.

2.  Перейдите к новой сборке Unity (папка *приложения* ) и откройте файл решения в *Visual Studio*.
3.  В конфигурации решения выберите **Отладка**.
4.  На платформе решения выберите **x86**, **Удаленный компьютер**. 

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  Перейдите в **меню "сборка** " и щелкните " **Развернуть решение**", чтобы загружать неопубликованные приложение в HoloLens.
6.  Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.

> [!NOTE]
> Чтобы выполнить развертывание в иммерсивное *виртуальную*гарнитуру, задайте для **платформы решения** значение локальный компьютер и задайте для параметра **Конфигурация** значение *Отладка*( *x86* в качестве **платформы**). Затем выполните развертывание на локальном компьютере с помощью **меню "сборка**" и выберите пункт " *Развернуть решение*". 


## <a name="chapter-10---using-the-application"></a>Глава 10. Использование приложения

1.  Людьми HoloLens, запустите приложение.
2.  Взгляните на пользователя, зарегистрированного в *API распознавания лиц*. Убедитесь в следующем.

    -  Лицо человека не является слишком отдаленным и ясно видимым
    -  Освещение среды не слишком темнее

3.  Используйте жест касания, чтобы захватить изображение человека.
4.  Подождите, пока приложение отправит запрос на анализ и получите ответ.
5.  Если пользователь успешно распознал, его имя будет отображаться как текст пользовательского интерфейса.
6.  Процесс записи можно повторить с помощью жеста касания каждые несколько секунд.

## <a name="your-finished-azure-face-api-application"></a>Готовое приложение Azure API распознавания лиц

Поздравляем! вы создали приложение смешанной реальности, которое использует службу распознавания лиц Azure для обнаружения лиц в образе и определения известных лиц.

![результат выполнения этого курса](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Премиальные упражнения

### <a name="exercise-1"></a>Упражнение 1

**API распознавания лиц Azure** достаточно мощный, чтобы обнаружить до 64 лиц в одном образе. Расширьте приложение, чтобы оно могло распознать два или три лица, среди многих других людей.

### <a name="exercise-2"></a>Упражнение 2

**API распознавания лиц Azure** также может предоставлять все виды информации об атрибутах. Интегрируйте его в приложение. Это может быть еще более интересно при объединении с [API распознавания эмоций](https://azure.microsoft.com/services/cognitive-services/emotion/).
