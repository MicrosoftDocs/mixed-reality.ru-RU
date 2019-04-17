---
title: Г-н и Azure 302b - Custom vision
description: Выполните этот курс, чтобы узнать, как обучить модель машинного обучения, а затем используйте обученной модели для распознавания схожие объекты в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, в пользовательской службе визуального распознавания, hololens, создающий эффект присутствия, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599999"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>Г-н и Azure 302b: Пользовательской службе визуального распознавания

В рамках этого курса вы узнаете распознавание пользовательского визуального содержимого в рамках предоставленного образа, используя возможности визуального распознавания Azure в приложении смешанной реальности.

Эта служба позволит вам для обучения модели машинного обучения с использованием объекта изображения. Затем используется обученной модели для распознавания сходных объектов, предоставленный камеры Microsoft HoloLens или камеры, подключенном к ПК для иммерсивную (VR).

![результат курс](images/AzureLabs-Lab302b-00.png)

Azure пользовательской службе визуального распознавания является Microsoft Cognitive Service, что позволяет разработчикам создавать классификаторы пользовательского образа. Эти классификаторы можно использовать с помощью новых образов для распознавания, или для классификации, объекты в рамках этого нового образа. Служба предоставляет простой, удобный, online портал для упрощения процесса. Дополнительные сведения см. в статье [пользовательская служба визуального распознавания Azure страницы](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

По завершении этого курса у вас будет приложение смешанной реальности, в которое будут иметь возможность работать в двух режимах:

-   **Режим анализа**: Настройка пользовательской службы визуального распознавания вручную путем отправки изображений, создание тегов и службу обучения для распознавания различных объектов (в данном вариантов мыши и клавиатуры). Затем вы создадите приложение HoloLens, которое будет создание образов с помощью камеры и постараемся понять эти объекты в реальном мире.

-   **Режима обучения**: вы реализуете код, который позволит «Обучение режим» в приложении. Режим обучения позволит вам для записи образов с помощью камеры HoloLens, загрузите захваченного изображения в службу и обучения модели пользовательской службе визуального распознавания.

Этот курс ознакомят вас для получения результатов из пользовательской службы визуального распознавания в приложение на базе Unity образец. Это будет необходимо применение этих понятий в пользовательское приложение, возможно, вы разрабатываете.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> Г-н и Azure 302b: Пользовательской службе визуального распознавания</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Камера, подключенном к ПК (для разработки иммерсивных гарнитуры)
- Доступ к Интернету для настройки Azure и извлечения пользовательский API компьютерного зрения
- Ряд по крайней мере пять (5) образов (десяти (10) рекомендуется) для каждого объекта, на котором вы хотите пользовательской службы визуального распознавания для распознавания. При желании можно использовать [изображений, представленных в этом курсе (компьютерной мыши и клавиатуры) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).
2.  Настроить и проверить ваш HoloLens. Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя). 

Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).

Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Глава 1 - портале службы пользовательской службе визуального распознавания

Чтобы использовать *пользовательская служба визуального распознавания* в Azure, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.

1.  Во-первых, [перейдите к *пользовательская служба визуального распознавания* главной странице](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Щелкните **приступить к работе** кнопки.

    ![](images/AzureLabs-Lab302b-01.png)

3.  Войдите в *пользовательская служба визуального распознавания* портала.

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо будет создать его. Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.

4.  После входа в первый раз, вам будет предложено с *условиями* панели. Щелкните флажок, чтобы принять условия. Нажмите кнопку на **принимаю**.

    ![](images/AzureLabs-Lab302b-03.png)

5.  Согласии с условиями, вы перейдете к *проекты* раздел на портале. Щелкните **новый проект**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  Будет отображаться в области справа, который предложит задать некоторые поля для проекта.

    1.  Вставить *имя* для вашего проекта.

    2.  Вставить *описание* для проекта (*необязательно*).

    3.  Выберите *группы ресурсов* или создайте новую. Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure. Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).

    4. Задайте *типы проектов* для **классификации**
    
    5. Задайте *домены* как **Общие**.

        ![](images/AzureLabs-Lab302b-05.png)

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  Когда вы закончите, нажмите кнопку **создать проект**, вы будете перенаправлены к пользовательской службы визуального распознавания страницы проекта.

## <a name="chapter-2---training-your-custom-vision-project"></a>Глава 2 - обучение Custom Vision проекта

Один раз на портале Custom Vision ваша основная задача заключается для обучения проекта распознавать определенные объекты на изображениях. Требуется по крайней мере пять (5) изображения, хотя десяти (10) является предпочтительным для каждого объекта, которые требуется приложение для распознавания. [Можно использовать образы, предоставленные в этом курсе (компьютерной мыши и клавиатуры)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Для обучения проект пользовательской службы визуального распознавания:

1.  Щелкните **+** рядом с пунктом **теги.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Добавить **имя** объекта, чтобы распознать. Щелкните **Сохранить**.

    ![](images/AzureLabs-Lab302b-07.png)

3.  Обратите внимание на **тега** был добавлен (может потребоваться перезагрузить страницу, чтобы он появился). Установите флажок рядом с новый тег, если он еще не установлен.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Щелкните **добавить образы** в центре страницы.

    ![](images/AzureLabs-Lab302b-09.png)

5.  Щелкните **Обзор локальных файлов**и поиска, а затем выберите образы, вы хотите отправить, минимальная — пять (5). Помните, что все эти образы должен содержать объект, который при обучении.

    > [!NOTE]
    >  Можно выбрать несколько изображений одновременно, для отправки.

6.  Как только вы видите образы на вкладке, выберите соответствующую метку в **Мои теги** поле.

    ![](images/AzureLabs-Lab302b-10.png)

7.  Щелкните **передача файлов**. Файлы начнется передача. Получив подтверждение отправки, нажмите кнопку **сделать**.

    ![](images/AzureLabs-Lab302b-11.png)

8.  Повторите этот процесс для создания нового **тега** с именем **клавиатуры** и загрузить соответствующий фотографии для него. Убедитесь, что **снимите** *мыши* после создания новых тегов, поэтому, чтобы показать *Добавление изображений* окна.

9.  Когда оба тега, Настройка, щелкните **Train**, и первой итерации обучения начнет сборку.

    ![](images/AzureLabs-Lab302b-12.png)

10. После построения, можно увидеть две кнопки с именем **сделать значением по умолчанию** и **прогноза URL-адрес**. Щелкните **сделать значением по умолчанию** сначала, затем щелкните **прогноза URL-адрес**.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > URL-адрес конечной точки, который предоставляется из этого, присваивается какое *итерации* был помечен как по умолчанию. Таким образом, если вы позднее сделать новый *итерации* и обновить его по умолчанию, не потребуется изменять код.

11. Когда вы перейдете на *прогноза URL-адрес*откройте *Блокнот*, скопируйте и вставьте **URL-адрес** и **прогноза ключ**, чтобы пользователь мог его необходимо получить в том случае, когда это потребуется далее в коде.

    ![](images/AzureLabs-Lab302b-14.png)

12. Щелкните **шестеренки** в верхней правой части экрана.

    ![](images/AzureLabs-Lab302b-15.png)

13. Копировать **ключ обучения** и вставьте его в *Блокнот*, для последующего использования.

    ![](images/AzureLabs-Lab302b-16.png)

14. Также скопируйте вашей **идентификатор проекта**, а также вставьте его в вашей *Блокнот* файл для последующего использования.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Глава 3 - Настройка проекта Unity

Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.

1.  Откройте *Unity* и нажмите кнопку **New**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  Теперь необходимо будет указать имя проекта Unity. Вставить **AzureCustomVision.** Убедитесь, что шаблон проекта присваивается **3D**. Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги). Щелкните **создать проект**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**. Перейдите к **изменить* > *предпочтения** и затем в окне «Новый» перейдите к **внешние средства**. Изменение **внешнего редактора скриптов** для **Visual Studio 2017**. Закрыть **предпочтения** окна.

    ![](images/AzureLabs-Lab302b-19.png)

4.  Перейдите к **файл > Параметры сборки** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** кнопку, чтобы применить выбранные параметры.

    ![](images/AzureLabs-Lab302b-20.png)

5.  Оставаясь в **файл > Параметры сборки** и убедитесь, что:

    1.  **Целевое устройство** присваивается **Hololens**

        > Иммерсивную, задайте **целевое устройство** для *любого устройства*.
        
    2.  **Тип сборки** присваивается **D3D**
    3.  **Пакет SDK для** присваивается **самую новую установленную**
    4.  **Версия Visual Studio** присваивается **самую новую установленную**
    5.  **Сборка и запуск** присваивается **локального компьютера**
    6.  Сохраните сцены и добавить его к сборке. 

        1. Это сделать, выбрав **добавьте откройте сцены**. Сохранение окно будет отображаться.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.

            ![](images/AzureLabs-Lab302b-22.png)

        3. Откройте только что созданный **сцены** папку, а затем в *имя файла:* текстовое поле, тип **CustomVisionScene**, нажмите кнопку на **Сохранить**.

            ![](images/AzureLabs-Lab302b-23.png)

            > Следует помнить, что необходимо сохранить в Unity кадром *активы* папку, так как они должны быть связаны с проектом Unity. Создание папки сцены (и другие аналогичные папки) — это типичный способ структурирования проекта Unity.
            
    7.  Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.

        ![](images/AzureLabs-Lab302b-24.png)

6.  В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.

7. В этой панели необходимо проверить некоторые настройки:

    1.  В **другие параметры** вкладке:

        1.  **Сценарии версии среды выполнения** должно быть **экспериментальная (эквивалент 4.6 .NET)**, что вызовет необходимость перезапуска редактора.

        2. **Создание сценариев серверной части** должно быть **.NET**

        3. **Уровень совместимости API** должно быть **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  В рамках **параметров публикации** в списке **возможности**, проверьте:

        1. **internetClient**

        2.  **Webcam**

        3. **"Микрофон"**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.

    ![](images/AzureLabs-Lab302b-27.png)

8.  Вернитесь в *параметры построения* *Unity C\# проекты* больше не отображается серым, установите флажок рядом с это.

9.  Закройте окно Параметры построения.

10.  Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Глава 4 – Импорт Newtonsoft DLL в Unity

> [!IMPORTANT]
> Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 6](#chapter-6---create-the-customvisionanalyser-class).

Этот курс требует использования **Newtonsoft** библиотеки, который можно добавить как библиотеку DLL ресурсов. Пакет, содержащий [эту библиотеку можно загрузить по этой ссылке](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Чтобы импортировать библиотеки Newtonsoft в проект, используйте пакет Unity, который прилагается этот курс.

1.  Добавить *.unitypackage* к Unity с помощью **активы* > *импорта* *пакета*  >  *Custom* *пакета** пункт меню.

2.  В **Импорт пакета Unity** который появится убедитесь, что все, что в разделе (вплоть до) **подключаемые модули** выбран.

    ![](images/AzureLabs-Lab302b-28.png)

3.  Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.

4.  Перейдите к **Newtonsoft** папке **подключаемые модули** в представлении проекта и выберите *подключаемый модуль Newtonsoft.Json*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  С *подключаемый модуль Newtonsoft.Json* выбран, убедитесь, что **Any платформы** — **unchecked**, убедитесь, что флажок **WSAPlayer** также **unchecked**, затем нажмите кнопку **применить**. Это, чтобы убедиться, что файлы настроены правильно.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Пометка этих подключаемых модулей позволяет настроить их только для использования в редакторе Unity. Существует другой набор их в папке WSA, которая будет использоваться после проект будет экспортирован из Unity.

6.  Затем необходимо открыть **WSA** папку, в пределах **Newtonsoft** папки. Вы увидите копию тот же файл, который вы только что настроили. Выберите файл и затем в инспекторе, убедитесь, что
    -   **Любой платформе** является **unchecked** 
    -   **только** **WSAPlayer** является **проверки**
    -   **Не обрабатывать** является **проверки**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Глава 5 - Настройка камеры

1.  На панели «иерархии» выберите *Main Camera*.

2.  После выбора можно видеть все компоненты *Main Camera* в *панели Инспектора*.

    1.  *Камеры* объект должен иметь имя **Main Camera** (Обратите внимание, правильность написания!)

    2.  Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания!)

    3.  Убедитесь, что **преобразование положения** присваивается **0, 0, 0**

    4.  Задайте **очистить флаги** для **Одноцветная** (игнорировать это для иммерсивных гарнитура).

    5.  Задайте **фона** цвет камеры компонент **черная, альфа-значение 0 (шестнадцатеричный код: #00000000)** (игнорировать это для иммерсивных гарнитура).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Глава 6 - создание класса CustomVisionAnalyser.

На этом этапе вы готовы написать код.

Вы начнете с *CustomVisionAnalyser* класса.

> [!NOTE]
> Вызовы **пользовательская служба визуального распознавания** внесенные в код, показанный ниже производятся с использованием **Custom Vision REST API**. С помощью это, вы увидите, как реализовать и использовать этот API (полезно для понимания того, как выполнить что-то подобное самостоятельно). Имейте в виду, что корпорация Майкрософт предлагает **Custom Vision Service SDK** , может также использоваться для выполнения вызовов к службе. Дополнительные сведения см. в статье [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) статьи.

Этот класс отвечает за:

-   Загрузка последней версии образа, записано в виде массива байтов.

-   Отправка массива байтов подписки Azure *пользовательская служба визуального распознавания* экземпляра для анализа.

-   Получение ответа как строку JSON.

-   Десериализации ответа и передачи итоговый *прогноза* для *SceneOrganiser* класс, который берет на себя отображения ответа.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши в *папке Asset* в *панель проекта*, нажмите кнопку **Создать > Папка**. Вызовите папке **сценариев**.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Дважды щелкните папку, только что создали, чтобы открыть его.

3.  Щелкните правой кнопкой мыши внутри папки, а затем щелкните **создать** > **C\# скрипт**. Назовите сценарий *CustomVisionAnalyser*.

4.  Дважды щелкните новый *CustomVisionAnalyser* скрипт, чтобы открыть его с **Visual Studio**.

5.  Обновите пространства имен в верхней части файла в соответствии со следующим:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  В *CustomVisionAnalyser* добавьте следующие переменные:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Убедитесь, что вы вставляете вашей **ключ прогноза** в **predictionKey** переменной и **конечной точки прогноза** в **predictionEndpoint** переменной. Вы скопировали их *Блокнот* ранее в этом курсе.

7.  Код для **Awake()** теперь должен быть добавлен для инициализации переменной экземпляра:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Удалить методы **Start()** и **Update()**.

9.  Добавьте соподпрограмме (с помощью статического **GetImageAsByteArray()** метод под ним), которой будет получать результаты анализа, изображения, охватываемого *ImageCapture* класса.

    > [!NOTE]
    > В **AnalyseImageCapture** соподпрограмме, имеется вызов *SceneOrganiser* класс, который вы еще для создания. Таким образом **оставлю их строк закомментирована сейчас**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Глава 7 - создание класса CustomVisionObjects

Класс, вы создадите теперь является *CustomVisionObjects* класса.

Этот скрипт содержит некоторое количество объектов, используемые другими классами для сериализации и десериализации вызовы к *пользовательская служба визуального распознавания*.

> [!WARNING]
> Очень важно, что вы запишите конечную точку, пользовательской службы визуального распознавания предоставляет вам, как ниже JSON структура настроен для работы с [ *версии 2.0 Custom Vision прогноза*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). При наличии другой версии, может потребоваться обновить ниже структуру.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Вызовите сценарий *CustomVisionObjects*.

2.  Дважды щелкните новый **CustomVisionObjects** скрипт, чтобы открыть его с **Visual Studio**.

3.  Добавьте следующие пространства имен в начало файла:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Удалить **Start()** и **Update()** методов внутри *CustomVisionObjects* класса; этот класс будет очищен.

5.  Добавьте следующие классы **за пределами** *CustomVisionObjects* класса. Эти объекты используются *Newtonsoft* библиотеки для сериализации и десериализации данных ответа:

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Глава 8 - создать класс VoiceRecognizer

Этот класс будет распознавать голосовой ввод от пользователя.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Вызовите сценарий *VoiceRecognizer*.

2.  Дважды щелкните новый **VoiceRecognizer** скрипт, чтобы открыть его с **Visual Studio**.

3.  Добавьте следующие пространства имен выше *VoiceRecognizer* класса:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Затем добавьте следующие переменные внутри *VoiceRecognizer* класса выше *Start()* метод:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Добавить **Awake()** и **Start()** методы, последний из которых будет установлен пользователь *ключевые слова* распознаваемый при связывании тег для образа:

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  Удалить **Update()** метод.

7.  Добавьте следующий обработчик, который вызывается каждый раз, когда распознается голосовой ввод:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.

> [!NOTE]
> Не беспокойтесь о коде, который может появиться ошибка, как вы будете обеспечивать дополнительные классы скоро, которые будет устранить их.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Глава 9 — создать класс CustomVisionTrainer

Этот класс будет цепочку серию вызовов веб-обучение *пользовательская служба визуального распознавания*. Каждый вызов будет быть подробно прямо над кодом.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Вызовите сценарий *CustomVisionTrainer*.

2.  Дважды щелкните новый *CustomVisionTrainer* скрипт, чтобы открыть его с **Visual Studio**.

3.  Добавьте следующие пространства имен выше *CustomVisionTrainer* класса:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Затем добавьте следующие переменные внутри *CustomVisionTrainer* класса выше **Start()** метод. 

    > [!NOTE]
    > Обучение URL-адрес, используемый здесь предоставляется в рамках *Custom Vision обучения 1.2* документации, и имеют структуру: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Дополнительные сведения см. в статье [ *Справочник по версии 1.2 обучения Custom Vision API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > Очень важно, что вы запишите конечную точку, пользовательской службы визуального распознавания обеспечивает для режима обучения, как использовать структуру JSON (в пределах **CustomVisionObjects** класс) настроен для работы с [  *Custom визуального распознавания v1.2 обучения*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). При наличии другой версии, может потребоваться обновить *объектов* структуры.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Убедитесь, что добавляемые вашей **ключ службы** (ключ обучения) значение и **идентификатор проекта** , значение которого вы записали предыдущих; это значения вы [собранные на портале ранее в курс () Глава 2, шаг 10 и более поздние версии)](#chapter-2---training-your-custom-vision-oroject).

5.  Добавьте следующий **Start()** и **Awake()** методы. Эти методы вызываются для инициализации и включает вызов для настройки пользовательского интерфейса:

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  Удалить **Update()** метод. Этот класс не потребуется.

7.  Добавить **RequestTagSelection()** метод. Этот метод является первым должен быть вызван, если образ записывается и хранятся в устройстве и готов к отправке *пользовательская служба визуального распознавания*, чтобы выполнить его обучение. Этот метод отображает в обучающем пользовательского интерфейса, набор ключевые слова, которые пользователь может использовать для пометки образа, захваченное. Приложение также уведомляет *VoiceRecognizer* класса, чтобы начать прослушивание голосовой ввод пользователя.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Добавить **VerifyTag()** метод. Этот метод будет получать голосовой ввод, распознаваемые **VoiceRecognizer** класса и проверьте его допустимость и затем начать процесс обучения.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Добавить **SubmitImageForTraining()** метод. Этот метод начнется процесс обучения пользовательской службы визуального распознавания. Первым шагом является извлечение **идентификатор тега** из службы, связанной с проверенного речевой ввод от пользователя. **Идентификатор тега** будет отправлен вместе с изображением.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Добавить **TrainCustomVisionProject()** метод. Когда образ будет отправлен и тегами, этот метод будет вызываться. Он создаст новую итерацию, будут обучены с предыдущие образы, отправить в службу, а также образ только что отправленного. После завершения обучения, этот метод будет вызывать метод, позволяющий настраивать только что созданный **итерации** как **по умолчанию**, таким образом, чтобы конечная точка используется для анализа последних обученной итерации.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Добавить **SetDefaultIteration()** метод. Этот метод будет задан ранее созданный и обученной итерации как *по умолчанию*. После завершения этого метода будет необходимо удалить предыдущей итерации, существующие в службе. Во время написания этого курса ограничено максимальное десяти (10) итераций должно быть в то же время в службе.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Добавить **DeletePreviousIteration()** метод. Этот метод будет найти и удалить предыдущей итерации не по умолчанию:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. Последний метод для добавления в этот класс является **GetImageAsByteArray()** метод, используемый на веб-вызывает преобразовать изображение, создаваемое в массив байтов.

    ```csharp
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

14. Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Глава 10 — создать класс SceneOrganiser

Этот класс выполняет следующие действия:

-   Создание **курсор** объект необходимо подключить к Main Camera.

-   Создание **метка** объекта, которое будет отображаться, когда служба распознает реальных объектов.

-   Настройка Main Camera, подключив к ней соответствующие компоненты.

-   При работе в **режим анализа**, породить метки во время выполнения, в соответствующие абсолютном относительно положения объекта Main Camera и отобразить данные, полученные из пользовательской службы визуального распознавания.

-   При работе в **режим обучения**, создавать пользовательский Интерфейс, который будет отображаться на разных этапах процесса обучения.

Для создания этого класса:

1.  Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**. Назовите сценарий *SceneOrganiser*.

2.  Дважды щелкните новый *SceneOrganiser* скрипт, чтобы открыть его с **Visual Studio**.

3.  Вам потребуется только одно пространство имен, удалите остальные выше *SceneOrganiser* класса:

    ```csharp
    using UnityEngine;
    ```

4.  Затем добавьте следующие переменные внутри *SceneOrganiser* класса выше **Start()** метод:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  Удалить **Start()** и **Update()** методы.

6.  Прямо под переменные, добавить **Awake()** метод, который будет инициализировать класс и подготовить сцены.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  Теперь добавьте **CreateCameraCursor()** метод, который создает и помещает курсор Main Camera, и **CreateLabel()** метод, который создает **Метка анализа** объекта .

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Добавить **SetCameraStatus()** метод, который будет обрабатывать сообщения, предназначенные для текста сетки, предоставление состояния камеры.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Добавить **PlaceAnalysisLabel()** и **SetTagsToLastLabel()** методов, которые будут создавать и отображать данные из пользовательской службы визуального распознавания на сцене.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Наконец, добавьте **CreateTrainingUI()** метод, который запустит пользовательский Интерфейс, отображение несколько этапов процесса обучения, в том случае, когда приложение находится в режиме обучения. Этот метод также будет иметь использовали для создания объекта состояния камеры.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.

> [!IMPORTANT]
> Прежде чем продолжить, откройте **CustomVisionAnalyser** класса и в **AnalyseLastImageCaptured()** метод, *раскомментируйте* следующие строки:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Глава 11. Создание класса ImageCapture

Далее нужно создать класс является *ImageCapture* класса.

Этот класс отвечает за:

-   Создание образа с помощью камеры HoloLens и сохранить его в *приложения* папки.

-   Обработка жесты Tap от пользователя.

-   Обслуживание *перечисления* значение, определяющее, если приложение будет запущено *Analysis* режиме или *обучения* режим.

Для создания этого класса:

1.  Перейдите к **сценариев** папку, созданную ранее.

2.  Щелкните правой кнопкой мыши внутри папки, а затем щелкните **Создать > C\# скрипт**. Назовите сценарий *ImageCapture*.

3.  Дважды щелкните новый **ImageCapture** скрипт, чтобы открыть его с **Visual Studio**.

4.  Замените следующие пространства имен в верхней части файла:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Затем добавьте следующие переменные внутри *ImageCapture* класса выше **Start()** метод:

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Реализуйте обработчик, который будет вызываться при возникновении жеста касания.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > В *Analysis* режиме **TapHandler** метод действует как переключатель для запуска или остановки цикла захват фото.
    >
    > В *обучения* режим, она будет запись образа с камеры.
    >
    > Когда курсор имеет зеленый цвет, это означает, что камера находится на изображение.
    >
    > Когда курсор отображается красным цветом, это означает, что камера занят.

8.  Добавьте метод, который приложение использует для запуска процесса захвата образа и сохранения образа.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  Добавление обработчиков, которые будут вызываться захваченный фотографии и когда он будет готов для анализа. Результат затем передается *CustomVisionAnalyser* или *CustomVisionTrainer* в зависимости от того, какой режим включен код.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.

11. Теперь, после завершения всех сценариев, вернитесь в редакторе Unity, а затем щелкните и перетащите **SceneOrganiser** класса из **сценарии** папку **Main Camera** объект в *панели иерархии*.

## <a name="chapter-12---before-building"></a>Глава 12 - перед сборкой

Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш HoloLens.

Прежде чем сделать, убедитесь, что:

- Все параметры, упомянутые в [Глава 2](#chapter-2---training-your-custom-vision-project) заданы правильно.

- Все поля в **Main Camera**, панели Инспектора назначаются должным образом.

- Сценарий **SceneOrganiser** присоединяется к **Main Camera** объекта.

- Убедитесь, что вы вставляете вашей **ключ прогноза** в **predictionKey** переменной.

- Вы вставили вашей **конечной точки прогноза** в **predictionEndpoint** переменной.

- Вы вставили вашей **ключ обучения** в **trainingKey** переменной, *CustomVisionTrainer* класса.

- Вы вставили вашей **идентификатор проекта** в **projectId** переменной, *CustomVisionTrainer* класса.

## <a name="chapter-13---build-and-sideload-your-application"></a>Глава 13 - сборки и загружать неопубликованные приложения

Чтобы начать *построения* процесс:

1.  Перейдите к **файл > Параметры сборки**.

2.  Такт **Unity C\# проекты**.

3.  Щелкните **Сборка**. Unity приведет к запуску **проводнике** окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в. Создайте эту папку и назовите его **приложения**. Затем с помощью **приложения** щелкните папку, **Выбор папки**.

4.  Unity начнется построение проекта для **приложения** папки.

5.  Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).

Для развертывания на HoloLens:

1.  Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика**. Выполните указанные ниже действия.

    1.  Хотя носить вашей HoloLens, откройте **параметры**.

    2.  Перейдите к **сеть и Интернет** > **Wi-Fi** > **Дополнительные параметры**

    3.  Примечание **IPv4** адрес.

    4.  Затем перейдите к **параметры**, а затем в **обновление и безопасность** > **для разработчиков**

    5.  Задайте **режим разработчика на**.

2.  Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.

3.  В *конфигурации решения* выберите **Отладка**.

4.  В *платформа решения*выберите **x86, удаленный компьютер**. Вам будет предложено вставить **IP-адрес** удаленного устройства (HoloLens, таким образом, который вы записали).

    ![](images/AzureLabs-Lab302b-34.png)

5. Перейдите к **построения** меню и щелкните **развернуть решение** для загрузки неопубликованных приложений для вашей HoloLens.

6. Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!

> [!NOTE]
> Чтобы развернуть иммерсивных гарнитура, переключите **платформа решения** для *локального компьютера*и задайте **конфигурации** для *Отладка*, с *x86* как **платформы**. Затем развернутое в локальном компьютера, с помощью **построения** пункта меню, выбрав *развернуть решение*. 

## <a name="to-use-the-application"></a>Использование приложения:

Для переключения между функциональные возможности приложения *обучения* режим и *прогноза* режиме, необходимо обновить **Тип_приложения** переменных, который находится в **Awake()** метод, расположенными в пределах *ImageCapture* класса.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
или диспетчер конфигурации служб
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

В *обучения* режиме:

- Рассмотрим **мыши** или **клавиатуры** и использовать **касания**.

- После этого текст будет отображаться, предлагающее укажите тег.

- Указано либо **мыши** или **клавиатуры**.


В *прогноза* режиме:

- Посмотреть на объект и использовать **касания**.

- Текст будет отображаться, предоставляющего объект обнаружил с наибольшей вероятностью (это нормализуется).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Глава 14 - оценить и улучшить модель Custom Vision

Для предоставления доступа к службе более точные, необходимо будет по-прежнему для обучения модели, используемые для прогнозирования. Это достигается с помощью нового приложения с обоими *обучения* и *прогноза* режимов; по второй необходимости перейдите на портал, являющийся, что рассматривается в этой главе. Будьте готовы вернитесь на портал много раз, чтобы постоянно улучшать модели.

1. Снова перейдите на портал Azure Custom Vision и после входа в проект, выберите *прогнозов* вкладке (в центре верхней части страницы):

    ![](images/AzureLabs-Lab302b-35.png)

2. Вы увидите все образы, которые были отправлены в службу, пока приложение запущено. Если навести указатель мыши над изображениями, им будет предоставлен прогнозы, которые были внесены для этого образа:

    ![](images/AzureLabs-Lab302b-36.png)

3. Выберите один из свои образы, чтобы открыть его. После open, вы увидите, что прогнозы для изображения справа. Если вы прогнозы были правильными, и вы хотите добавить этот образ для обучения модели службы, нажмите кнопку *Мои теги* поле ввода, а также выбрать тег, который вы хотите связать. Когда вы закончите, нажмите кнопку *сохраните и закройте* кнопку в правом нижнем углу и перейдите к следующему изображению.

    ![](images/AzureLabs-Lab302b-37.png)

4. Когда вы будете обратно к сетке образов, вы заметите образов, которые вы добавления тегов (и сохранения), будут удалены. Если вы найдете все образы, которые вы считаете, что заключенные в теги элемента в них нет, их, можно удалить, щелкая деления в этом образе (это можно сделать для нескольких образов) и выбрав *удалить* в правом верхнем углу страницы сетки. Во всплывающем ниже, можно нажать *Да, удалить* или *нет*, чтобы подтвердить удаление, или отменить его, соответственно. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Когда будете готовы продолжить, нажмите зеленую кнопку *Train* кнопки в правом верхнем углу. Модель службы будут обучены все образы которых теперь предоставляются (которые будут обеспечивают более высокую точность). После завершения обучения обязательно откройте *сделать значением по умолчанию* еще раз кнопку, чтобы вашей *прогноза URL-адрес* продолжает использовать самые последние итерации службы.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Готового приложения пользовательский API компьютерного зрения

Поздравляем, вы создали приложение смешанной реальности, которое использует API компьютерного зрения Custom Azure распознать объекты реального мира, обучения модели службы и отображать уверенность в том, что было показано выше.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Упражнения премии

### <a name="exercise-1"></a>Упражнение 1

Обучение вашей **пользовательская служба визуального распознавания** для распознавания объектов.

### <a name="exercise-2"></a>Упражнение 2

Как способ расширить полученные сведения выполните следующие упражнения:

Воспроизведение звука, когда объект был распознан.

### <a name="exercise-3"></a>Упражнение 3

Используйте API повторного обучения в службу с помощью те же образы, анализ приложения, так чтобы служба стала более точные (выполнять прогноза и одновременно обучения).
