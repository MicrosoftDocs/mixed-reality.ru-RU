---
title: Г-н и Azure 302 - компьютерного зрения
description: Выполните этот курс, чтобы узнать, как распознать визуального содержимого в образ, предоставленный, использование компьютерного зрения Azure в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, компьютерного зрения, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597889"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>Г-н и Azure 302: Компьютерное зрение

В рамках этого курса вы узнаете как распознать визуальное содержимое в указанный образ, с помощью возможностей компьютерного зрения Azure в приложении смешанной реальности.

Результаты распознавания будут отображаться как теги с описанием. Эту службу можно использовать без необходимости для обучения модели машинного обучения. Если реализация требует от обучения модели машинного обучения, см. в разделе [MR и Azure 302b](mr-azure-302b.md).

![Результат лаборатории](images/AzureLabs-Lab2-000.png)

Компьютерного зрения Microsoft — это набор API-интерфейсов позволяет предоставить разработчикам с обработка изображений и анализ (с помощью возвращают сведения), с помощью усовершенствованных алгоритмов, все из облака. Разработчики добавьте изображение или URL-адрес изображения, и алгоритмы API компьютерного зрения Microsoft анализировать визуальное содержимое, в зависимости от входных данных, выбранного пользователя, который затем можно получить сведения, включая определение типа и качества изображения, обнаружить (человеческих лиц возвращение их координаты) и меток или классификации изображений. Дополнительные сведения см. в статье [страницы API компьютерного зрения Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

После выполнения этого курса, у вас будет смешанной реальности HoloLens приложения, который будет осуществлять следующее:

1.  С помощью жеста касания, камеры HoloLens записать образ.
2.  Изображение будет отправляться службы API компьютерного зрения Azure компьютера. 
3.  Объект, который распознается отображаются в группе простого пользовательского интерфейса, расположенный в сцене Unity.

В приложении зависит от пользователя о том, как интегрировать результаты проектированию. Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity. Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> Г-н и Azure 302: Компьютерное зрение</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс основное внимание уделяется HoloLens, можно также применить полученные знания в этот курс поможет вам Windows Mixed Reality иммерсивную (VR). Поскольку иммерсивную (VR) не имеют доступных камеры, вам потребуется внешний камеры, подключенном к ПК. При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки иммерсивную (VR).

## <a name="prerequisites"></a>предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#. Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.). Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .

Рекомендуется следующее оборудование и программное обеспечение для этого курса:

- На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)
- [Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Камера, подключенном к ПК (для разработки иммерсивных гарнитуры)
- Доступ к Интернету для настройки Azure и API компьютерного зрения извлечения

## <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).
2.  Настроить и проверить ваш HoloLens. Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя). 

Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).

Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Глава 1 – портала Azure

Чтобы использовать *API компьютерного зрения* службы в Azure, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.

1.  Во-первых, войдите в [портал Azure](https://portal.azure.com). 

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо будет создать его. Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.

2.  После входа в систему щелкните **New** в левом верхнем углу, а поиск *API компьютерного зрения*и нажмите кнопку **ввод**.

    ![Создание нового ресурса в Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > Слово **New** может были заменены **создать ресурс**, в новых порталов.
 
3.  Новая страница будет предоставить описание *API компьютерного зрения* службы. В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать ассоциацию с этой службой.

    ![Сведения о службе api компьютерного зрения компьютера](images/AzureLabs-Lab2-01.png)
 
4.  Когда вы перейдете на **создать**:

    1. Вставить нужный **имя** для данного экземпляра службы.
    2. Выберите **подписки**.
    3. Выберите **Ценовая** подходит для вас, если это первое времени на создание *API компьютерного зрения* службы, уровень "бесплатный" (с именем F0) должны быть доступны для вас.
    4. Выберите **группы ресурсов** или создайте новую. Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure. Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов). 

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Определите расположение для группы ресурсов (Если вы создаете новую группу ресурсов). Расположение оптимально подойдет в регионе, в котором приложение будет работать. Некоторые ресурсы Azure доступны только в определенных регионах.

    6. Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.
    7. Нажмите кнопку Создать.

        ![Сведения о создании службы](images/AzureLabs-Lab2-02.png)

5.  Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.
6.  Уведомление будет отображаться на портале, после создания экземпляра службы.

    ![См. в разделе новое уведомление для новой службы](images/AzureLabs-Lab2-03.png) 
 
7.  Щелкните уведомление, чтобы изучить ваш новый экземпляр службы. 

    ![Нажмите кнопку Go для ресурсов.](images/AzureLabs-Lab2-04.png)
 
8. Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы. Откроется в новом экземпляре службы API компьютерного зрения. 

    ![В новой службе API компьютерного зрения](images/AzureLabs-Lab2-05.png)
 
9.  В этом руководстве описано приложение должно выполнять вызовы в службу, которая осуществляется с помощью ключа подписки вашей службы.
10. Из *быстрого запуска* странице из вашей *API компьютерного зрения* службы, перейдите к первому шагу *получите ключи*и нажмите кнопку **ключи** () Это можно также сделать, щелкнув синий гиперссылки ключи, расположенный в меню навигации служб, обозначенное с помощью значок ключа). Это позволит службе *ключи*.
11. Сделайте копию один из отображаемых разделов, так как он потребуется позже в проекте. 

12. Вернитесь к *быстрого запуска* странице и оттуда выборку конечной точки. Имейте в виду, вам может различаться в зависимости от региона (который в противном случае необходимо будет внести изменения в код позже). Сделайте копию этой конечной точки для дальнейшего использования:

    ![В новой службе API компьютерного зрения](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Вы можете проверить, каковы конечных точках [здесь](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). 

## <a name="chapter-2--set-up-the-unity-project"></a>Глава 2 – Настройка проекта Unity

Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.

1.  Откройте *Unity* и нажмите кнопку **New**. 

    ![Начните новый проект Unity.](images/AzureLabs-Lab2-06.png)

2.  Теперь необходимо будет указать имя проекта Unity. Вставить **MR_ComputerVision**. Убедитесь, что тип проекта присваивается **3D**. Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги). Щелкните **создать проект**.

    ![Укажите сведения для нового проекта Unity.](images/AzureLabs-Lab2-07.png)

3.  С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**. Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**. Изменение **внешнего редактора скриптов** для **Visual Studio 2017**. Закрыть **предпочтения** окна.

    ![Обновите настройки редактора скриптов.](images/AzureLabs-Lab2-08.png)

4.  Перейдите к **файл > Параметры сборки** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** кнопку, чтобы применить выбранные параметры.

    ![Создавайте окно "Параметры", переключить платформу для универсальной платформы Windows.](images/AzureLabs-Lab2-10.png)

5.  Оставаясь в **файл > Параметры сборки** и убедитесь, что:

    1. **Целевое устройство** присваивается **HoloLens**

        > Иммерсивную, задайте **целевое устройство** для *любого устройства*.

    2. **Тип сборки** присваивается **D3D**
    3. **Пакет SDK для** присваивается **самую новую установленную**
    4. **Версия Visual Studio** присваивается **самую новую установленную**
    5. **Сборка и запуск** присваивается **локального компьютера**
    6. Сохраните сцены и добавить его к сборке.

        1. Это сделать, выбрав **добавьте откройте сцены**. Сохранение окно будет отображаться.
        
            ![Нажмите кнопку Добавить кнопку open сцены](images/AzureLabs-Lab2-11.png)

        2. Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.

            ![Создание новой папки scripts](images/AzureLabs-Lab2-12.png)

        3. Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **MR_ComputerVisionScene**, нажмите кнопку **Сохранить** .

            ![Присвойте имя новой сцены.](images/AzureLabs-Lab2-13.png)

            > Следует помнить, что необходимо сохранить в Unity кадром *активы* папку, так как они должны быть связаны с проектом Unity. Создание папки сцены (и другие аналогичные папки) — это типичный способ структурирования проекта Unity.

    7. Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.

6. В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится. 

    ![Открытие параметров проигрывателя.](images/AzureLabs-Lab2-14.png)

7. В этой панели необходимо проверить некоторые настройки:

    1. В **другие параметры** вкладке:

        1. **Версия среды выполнения сценариев** должно быть **стабильной** (.NET 3.5 эквивалент).
        2. **Создание сценариев серверной части** должно быть **.NET**
        3. **Уровень совместимости API** должно быть **.NET 4.6**

            ![Обновите другие параметры.](images/AzureLabs-Lab2-15.png)
      
    2. В рамках **параметров публикации** в списке **возможности**, проверьте:

        1. **internetClient**
        2. **Webcam**

            ![Обновление параметров публикации.](images/AzureLabs-Lab2-16.png)

    3. Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.

        ![Обновление параметров R X.](images/AzureLabs-Lab2-17.png)

8.  Вернитесь в *параметры построения* _Unity C#_  проектов больше не отображается серым, установите флажок рядом с это. 
9.  Закройте окно Параметры построения.
10. Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).

## <a name="chapter-3--main-camera-setup"></a>Глава 3 — Настройка Main Camera

> [!IMPORTANT]
> Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), импортировать его в проект в качестве [пользовательского пакета ](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 5](#chapter-5--create-the-resultslabel-class).

1.  В *панели иерархии*выберите **Main Camera**. 
2.  После выбора можно видеть все компоненты **Main Camera** в *панели Инспектора*.

    1. **Объекта Camera** должен иметь имя **Main Camera** (Обратите внимание, правильность написания!)
    2. Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания!)
    3. Убедитесь, что **преобразование положения** присваивается **0, 0, 0**
    4. Задайте **очистить флаги** для **Одноцветная** (игнорировать это для иммерсивных гарнитура).
    5. Задайте **фона** цвет компонента камеры для **черная, альфа-значение 0 (шестнадцатеричный код: #00000000)** (игнорировать это для иммерсивных гарнитура).

        ![Обновления компонентов камеры.](images/AzureLabs-Lab2-18.png)
 
3.  Далее необходимо создать простой «курсор» объект, присоединяемый к **Main Camera**, обеспечивают размещение анализ образов выходные данные при приложения. Этот курсор определит центральную точку фокуса камеры.

Чтобы создать курсора:

1.  В *панели иерархии*, щелкните правой кнопкой мыши **Main Camera**. В разделе **трехмерный объект**, щелкните **Sphere**.

    ![Выберите объект курсора.](images/AzureLabs-Lab2-19.png)
 
2.  Переименуйте **Sphere** для **курсор** (дважды щелкните объект курсора или нажмите кнопку «F2» клавиатуры объект выбран) и убедитесь, что он находится в качестве дочернего элемента **Main Camera**.

3.  В *панели иерархии*, щелчок левой кнопкой на **курсор**. Курсор выбран, настройте следующие переменные в *панели Инспектора*:

    1. Задайте *преобразование положения* для **0, 0, 5**
    2. Задайте *масштабирования* для **0,02, 0,02, 0,02**

        ![Обновление преобразования положение и размер.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Глава 4 – установки системы метки

Созданный изображение с камеры HoloLens, этот образ будет отправляться в *API компьютерного зрения Azure* экземпляр службы для анализа. 

Результаты этого анализа будет представлять собой список распознанных объекты, называемые **теги**. 

Эти теги отображаются в указанном месте снимок был сделан, будет использовать метки (в виде трехмерного текста в абсолютном пространстве).

Ниже будет показано, как настроить **метка** объекта.

1.  Щелкните правой кнопкой мыши в любом месте панели «иерархии» (расположение не имеет значения, на этом этапе) в разделе **трехмерный объект**, добавьте **трехмерного текста**. Назовите его **LabelText**.

    ![Создание трехмерного текста объекта.](images/AzureLabs-Lab2-21.png)
 
2.  В *панели иерархии*, щелчок левой кнопкой на **LabelText**. С помощью **LabelText** флажок установлен, настройте следующие переменные в *панели Инспектора*:

    1. Задайте **позиции** для **0,0,0**
    2. Задайте **масштабирования** для **0,01, 0,01, 0,01**
    3. В компоненте **Mesh текст**:
    4. Замените весь текст в **текст**, с помощью «...»        
    5. Задайте **привязки** для **в середине**
    6. Задайте **выравнивание** для **Center**
    7. Задайте **размера табуляции** для **4**
    8. Задайте **размер шрифта** для **50**
    9. Задайте **цвет** для **#FFFFFFFF**

    ![Компонент текста](images/AzureLabs-Lab2-21-5.png)

3.  Перетащите **LabelText** из *панели иерархии*, в *папке Asset*с соблюдением в *проекта панели*. Это сделает **LabelText** готового блока, так что он может быть создано в коде.

    ![Создайте prefab LabelText объекта.](images/AzureLabs-Lab2-22.png)
 
4.  Следует удалить **LabelText** из *панели иерархии*, так что он не отображается в сцене открытия. Так как это готового блока, который будет вызвать в отдельных экземплярах из папки средств, нет необходимости чтобы сохранить его в сцене. 
5.  Структура результирующий объект в *панели иерархии* должно быть, как показано на рисунке ниже:

    ![Окончательная структура панели иерархии.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Глава 5 – создать класс ResultsLabel

Первый скрипт, чтобы создать *ResultsLabel* класс, который отвечает за следующее: 

- Создание метки в соответствующие мировом пространстве, относительно положения камеры.
- Отображение тегов из Anaysis изображения.

Для создания этого класса: 

1.  Щелкните правой кнопкой мыши в *проекта панели*, затем **Создать > Папка**. Назовите папку **сценариев**. 

    ![Создайте папку scripts.](images/AzureLabs-Lab2-24.png)

2.  С помощью **сценариев** папке создайте, дважды щелкните его, чтобы открыть. Затем в этой папке, щелкните правой кнопкой мыши и выберите **Создать >** затем  **C# сценарий**. Назовите сценарий *ResultsLabel*. 

3.  Дважды щелкните новый *ResultsLabel* скрипт, чтобы открыть его с **Visual Studio**.

4.  Внутри класса вставьте следующий код в *ResultsLabel* класса:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.
7.  Вернитесь в *редактора Unity*щелкните и перетащите *ResultsLabel* класса из **сценарии** папку для **Main Camera** объекта в  *Панель иерархии*.
8.  Щелкните **Main Camera** и просмотрите *панели Инспектора*.

Обратите внимание, что из сценария, который пользователь перетащил в камеру, содержатся два поля: **Курсор** и **метки Prefab**.

9.  Перетащите объект вызывается **курсор** из *панели иерархии* в слот с именем **курсор**, как показано на рисунке ниже.
10. Перетащите объект вызывается **LabelText** из *папку Assets* в *панель проекта* в слот с именем **метка Prefab**, как показано на изображение ниже. 

    ![Задайте целевые объекты ссылки в Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Глава 6 – создать класс ImageCapture

Далее нужно создать класс является *ImageCapture* класса. Этот класс отвечает за:

-   Создание образа с помощью камеры HoloLens и сохранив его в папке приложения.
-   Записи жесты Tap от пользователя.

Для создания этого класса: 

1.  Перейдите к **сценариев** папку, созданную ранее. 
2.  Щелкните правой кнопкой мыши внутри папки **Создать > C# сценарий**. Вызовите сценарий *ImageCapture*. 
3.  Дважды щелкните новый *ImageCapture* скрипт, чтобы открыть его с **Visual Studio**.
4.  Добавьте следующие пространства имен в начало файла:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Затем добавьте следующие переменные внутри *ImageCapture* класса выше *Start()* метод:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount** хранятся в переменной число жестов касания, собранные от пользователя. Это число используется в именах образы, созданные.

6.  Код для *Awake()* и *Start()* методы теперь должен быть добавлен. Это будет вызываться при инициализации класса.

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Реализуйте обработчик, который будет вызываться при возникновении жеста касания. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
*TapHandler()* метод увеличивает на единицу числом ответвлений, собранные от пользователя и использует текущей позиции курсора для определения места для размещения новую метку.

Этот метод вызывает *ExecuteImageCaptureAndAnalysis()* метод для начала основные функциональные возможности этого приложения.

8.  После создания и сохранения изображения будет вызываться следующие обработчики. Если процесс прошел успешно, результат передается *VisionManager* (который вы еще для создания) для анализа.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  Затем добавьте метод, который приложение использует для запуска процесса захвата образа и сохранения образа.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> На этом этапе вы заметите ошибку в *панель консоли редактора Unity*. Это так, как код ссылается на *VisionManager* класс, который будет создан в следующей главе.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Глава 7 – вызов к Azure и анализ образов

— Последний скрипт, чтобы создать *VisionManager* класса. 

Этот класс отвечает за:

-   Загрузка последней версии образа, записано в виде массива байтов.
-   Массив байтов для отправки вашего *API компьютерного зрения Azure* экземпляр службы для анализа.
-   Получение ответа как строку JSON.
-   Десериализации ответа и передачи итоговый теги для *ResultsLabel* класса.
 
Для создания этого класса:

1.  Дважды щелкните **сценариев** папки, чтобы открыть его. 
2.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**. Назовите сценарий *VisionManager*. 
3.  Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.
4.  Обновите пространства имен должны совпадать, как показано ниже, в верхней части *VisionManager* класса:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  В верхней части сценария *внутри* *VisionManager* класс (выше *Start()* метод), необходимо создать два *классы* , Представляет Десериализованный ответ JSON от Azure:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *TagData* и *AnalysedObject* классы должны иметь *[System.Serializable]* атрибут, добавленный перед объявлением, чтобы иметь возможность десериализации в Unity библиотеки.

6.  В классе VisionManager следует добавить следующие переменные:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Убедитесь, что вы вставляете вашей **ключом проверки подлинности** в **authorizationKey** переменной. Будет записанными вашей **ключом проверки подлинности** в начале этого курса [главе 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > **VisionAnalysisEndpoint** переменной может отличаться от указанного в этом примере. **Западно-нам** строго относится к экземплярам службы, созданные для западной части США. Обновить его с вашей [URL-адрес конечной точки](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); здесь являются некоторые примеры того, что это может выглядеть так:
    > - Западная Европа: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Юго-Восточной Азии: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Восточная Австралия: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Теперь необходимо добавить код для Awake. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Добавьте соподпрограмме (методом статического потока под ним), которой будет получать результаты анализа, изображения, охватываемым *ImageCapture* класса. 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.
10. Обратно в редакторе Unity, щелкните и перетащите *VisionManager* и *ImageCapture* классы из **сценарии** папку **Main Camera**объекта в *панели иерархии*. 

## <a name="chapter-8--before-building"></a>Глава 8 – перед сборкой

Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш HoloLens.
Прежде чем сделать, убедитесь, что:

-   Все параметры, упомянутые в [Глава 2](#chapter-2--set-up-the-unity-project) заданы правильно. 
-   Все сценарии, присоединяются к **Main Camera** объекта. 
-   Все поля в *главной панели Инспектора камеры* назначаются должным образом.
-   Убедитесь, что вы вставляете вашей **ключом проверки подлинности** в **authorizationKey** переменной.
-   Убедитесь, что вы также проверили конечной точки вашей *VisionManager* скрипт, и что он выравнивает по *вашей* регион (в этом документе используется *западно-нам* по умолчанию).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Глава 9 – построения решения универсальной платформы Windows и загружать неопубликованные приложения
Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.

1.  Перейдите к *параметры сборки* - **файл > Параметры сборки...**
2.  Из *параметры построения* окно, нажмите кнопку **построения**.

    ![Создание приложения из Unity](images/AzureLabs-Lab2-26.png)

3.  Если не сделали, установите **Unity C# проекты**.
4.  Щелкните **Сборка**. Unity приведет к запуску *проводнике* окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в. Создайте эту папку и назовите его *приложения*. Затем с помощью *приложения* папку, нажмите клавишу **Выбор папки**. 
5.  Unity начнется построение проекта для *приложения* папки. 
6.  Один раз Unity завершил построение (может занять некоторое время), он будет открыт *проводнике* окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).

## <a name="chapter-10--deploy-to-hololens"></a>Глава 10 — развертывание в HoloLens

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

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Перейдите к **меню "сборка"** и щелкнуть **развернуть решение**, чтобы загрузить неопубликованное приложение для вашего HoloLens.
6.  Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!

> [!NOTE]
> Чтобы развернуть иммерсивных гарнитура, переключите **платформа решения** для *локального компьютера*и задайте **конфигурации** для *Отладка*, с *x86* как **платформы**. Затем развернуть на локальный компьютер, с помощью **меню "сборка"**, выбрав *развернуть решение*. 

## <a name="your-finished-computer-vision-api-application"></a>Готового приложения API компьютерного зрения

Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Azure API компьютерного зрения для распознавания объектов реального мира и отображения уверенность в том, что было показано выше.

![Результат лаборатории](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Упражнения премии

### <a name="exercise-1"></a>Упражнение 1

Так же, как вы использовали *теги* параметра (как видно в *конечной точки* используется в *VisionManager*), расширение приложения для обнаружения других сведений о; взглянем на какие другие параметры, у вас есть доступ к [здесь](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).

### <a name="exercise-2"></a>Упражнение 2

Отображение возвращаемых данных Azure, более естественный и для чтения, возможно скрытие чисел. Так, будто программы-робота, может обращаться к пользователю.
