---
title: MR и Azure 310 — обнаружение объектов
description: Пройдите этот курс, чтобы научиться обучить модель машинного обучения, а затем использовать обученную модель для распознавания похожих объектов и их позиций в реальном мире из приложения смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, пользовательское видение, обнаружение объектов, Смешанная реальность, Academy, Unity, учебник, API, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544459"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

# <a name="mr-and-azure-310-object-detection"></a>MR и Azure 310: Обнаружение объектов

В этом курсе вы узнаете, как распознать пользовательское визуальное содержимое и его пространственное расположение в предоставленном образе, используя возможности Azure Пользовательское визуальное распознавание "обнаружение объектов" в приложении смешанной реальности.

Эта служба позволит обучить модель машинного обучения с помощью образов объектов. Затем вы будете использовать обученную модель для распознавания похожих объектов и приближения их расположения в реальном мире, как это обеспечивается видеозаписью камеры Microsoft HoloLens или камера подключается к ПК для использования в режиме погружения (VR).

![результат курса](images/AzureLabs-Lab310-00.png)

**Пользовательское визуальное распознавание Azure, обнаружение объектов** — это служба Майкрософт, которая позволяет разработчикам создавать пользовательские классификаторы изображений. Эти классификаторы можно использовать с новыми образами для обнаружения объектов внутри этого нового изображения, предоставляя **границы рамки** в самом образе. Служба предоставляет простой, простой в использовании веб-портал для упрощения этого процесса. Дополнительные сведения см. по следующим ссылкам:

* [Страница Пользовательское визуальное распознавание Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Ограничения и квоты](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

После завершения этого курса у вас будет приложение смешанной реальности, которое сможет сделать следующее:

1. Пользователь сможет Взгляните на объект  , с которым они обучены с помощью пользовательская служба визуального распознавания Azure, обнаружения объектов. 
2. Пользователь будет использовать жест *касания* для записи изображения того, что они видят.
3. Приложение будет отправит образ в Пользовательская служба визуального распознавания Azure.
4. Будет получен ответ от службы, который будет отображать результат распознавания как текст в виде текста в мировом пространстве. Это будет выполнено с помощью пространственного отслеживания Microsoft HoloLens, чтобы понять расположение распознанного объекта в мире, а затем использовать *тег* , связанный с тем, что обнаруживается на изображении, чтобы предоставить текст метки.

Курс также охватывает ручную загрузку изображений, Создание тегов и обучение службы, чтобы распознать различные объекты (в предоставленном примере — чашку), установив *границу* в рамках отправляемого изображения. 

> [!IMPORTANT]
> После создания и использования приложения разработчик должен вернуться к Пользовательская служба визуального распознавания Azure и определить прогнозы, выполненные службой, и определить, были ли они верными (с помощью тегов все пропущенные службы и Настройка *ограничивающих прямоугольников*). Затем служба может быть переучена, что увеличит вероятность того, что она будет распознать реальные объекты мира.

В этом курсе вы узнаете, как получить результаты из Пользовательская служба визуального распознавания Azure, обнаружения объектов, в примере приложения на основе Unity. Вы сможете применить эти понятия к настраиваемому приложению, которое вы можете собрать.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> MR и Azure 310: Обнаружение объектов</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#. Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018). Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.

Для этого курса рекомендуется следующее оборудование и программное обеспечение:

- ПК для разработки
- [Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Последний пакет SDK для Windows 10](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017,4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) с включенным режимом разработчика
- Доступ к Интернету для установки Azure и извлечения Пользовательская служба визуального распознавания
-  Для каждого объекта, который необходимо распознать Пользовательское визуальное распознавание, требуется ряд по крайней мере пятнадцати (15) образов. При желании вы можете использовать образы, которые уже предоставлены в этом курсе, [серии – CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Прежде чем начать

1.  Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).
2.  Настройка и тестирование HoloLens. Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя). 

Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens).

Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Глава 1. портал Пользовательское визуальное распознавание

Чтобы использовать **Пользовательская служба визуального распознавания Azure**, необходимо настроить его экземпляр, чтобы сделать его доступным для приложения.

1.  Перейдите [на главную страницу **Пользовательская служба визуального распознавания** ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Щелкните **Начало работы**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Войдите на портал Пользовательское визуальное распознавание.

    ![](images/AzureLabs-Lab310-02.png)

4.  Если у вас еще нет учетной записи Azure, необходимо создать ее. Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.

5.  После первого входа в систему вам будет предложено ввести *условия использования панели Сервис* . Установите флажок, чтобы *принять условия*. Затем нажмите кнопку Принимаю.

    ![](images/AzureLabs-Lab310-03.png)

6.  Принимаю условия, вы теперь в разделе *Мои проекты* . Щелкните **Новый проект**.

    ![](images/AzureLabs-Lab310-04.png)

7.  На правой стороне появится вкладка, в которой будет предложено указать некоторые поля для проекта.

    1.  Вставка имени проекта

    2.  Вставка описания проекта (необязательно)

    3.  Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure. Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Если вы хотите [ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите к соответствующему документу](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) .

    4.  Задайте **типы проектов** как **Обнаружение объектов (Предварительная версия)** .

8.  После завершения нажмите кнопку **создать проект**, и вы будете перенаправлены на страницу проекта пользовательская служба визуального распознавания.


## <a name="chapter-2---training-your-custom-vision-project"></a>Глава 2. обучение проекта Пользовательское визуальное распознавание

На портале Пользовательское визуальное распознавание основной целью является обучение проекта для распознавания конкретных объектов в изображениях.

Для каждого объекта, который должен распознать ваше приложение, требуется по крайней мере пятнадцать (15) образов. Вы можете использовать образы, предоставленные в этом курсе ([серия – CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Обучение проекта Пользовательское визуальное распознавание:

1.  Нажмите кнопку рядом с пунктом **теги.** **+**

    ![](images/AzureLabs-Lab310-06.png)

2.  Добавьте **имя** тега, который будет использоваться для связывания изображений с. В этом примере мы используем образы – CUPS для распознавания, так что им присвоено имя **Tag.** По завершении нажмите кнопку **сохранить** .

    ![](images/AzureLabs-Lab310-07.png)

3.  Обратите внимание, что добавлен **тег** (может потребоваться перезагрузить страницу, чтобы она отображалась). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Щелкните **Добавить изображения** в центре страницы.

    ![](images/AzureLabs-Lab310-09.png)

5.  Щелкните **Обзор локальные файлы**и перейдите к изображениям, которые вы хотите передать для одного объекта, с минимальным числом пятнадцати (15).

    > [!TIP]
    >  Для отправки можно выбрать несколько образов за раз.

    ![](images/AzureLabs-Lab310-10.png)

6.  После выбора всех образов, с которыми вы хотите обучить проект, нажмите кнопку **отправить файлы** . Файлы начнут отправляться. Получив подтверждение отправки, нажмите кнопку **Готово**.

    ![](images/AzureLabs-Lab310-11.png)

7.  На этом этапе образы передаются, но не помечаются тегами.

    ![](images/AzureLabs-Lab310-12.png)

8.  Чтобы пометить изображения, используйте мышь. При наведении указателя мыши на изображение выделенный фрагмент поможет вам автоматически рисовать выделенный фрагмент вокруг объекта. Если он неточен, можно нарисовать собственный. Это достигается путем нажатия левой кнопки мыши и перетаскивания области выделения, чтобы охватить объект. 

    ![](images/AzureLabs-Lab310-13.png) 

9. После выбора объекта в изображении появляется небольшой запрос на *Добавление тега Region*. Выберите ранее созданный тег ("чашка" в приведенном выше примере) или, если вы добавляете дополнительные теги, введите его в и нажмите кнопку **+ (плюс)** .

    ![](images/AzureLabs-Lab310-14.png) 

10. Чтобы добавить тег к следующему изображению, можно щелкнуть стрелку справа от колонки или закрыть колонку тега (щелкнув значок **X** в правом верхнем углу колонки), а затем щелкнув следующее изображение. После подготовки следующего образа Повторите ту же процедуру. Сделайте это для всех отправленных образов, пока они не помечаются тегами. 

    > [!NOTE]
    >  Можно выбрать несколько объектов в одном изображении, как показано на рисунке ниже: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Получив все теги, нажмите кнопку с **тегами** в левой части экрана, чтобы отобразить изображения с тегами. 

    ![](images/AzureLabs-Lab310-16.png)

12. Теперь все готово для обучения службы. Нажмите кнопку **обучение** , и начнется первая итерация для обучения.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. После завершения сборки вы увидите две кнопки с именем сделать **URL-адрес** **по умолчанию** и прогноз. Щелкните сначала **создать значение по умолчанию** , а затем щелкните **URL-адрес прогноза**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > Конечной точке, предоставляемой из этого, присваивается любая *Итерация* , помеченная как используемая по умолчанию. Таким образом, если позднее вы выполните новую *итерацию* и обновите ее по умолчанию, вам не потребуется изменять код.

14. После того как вы щелкнули **URL-адрес прогноза**, откройте *Блокнот*и скопируйте и вставьте **URL-адрес** (также называемый прогнозной **конечной точкой**) и **ключ прогноза службы**, чтобы его можно было извлечь, когда он понадобится позже в коде.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Глава 3. Настройка проекта Unity

Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.

1.  Откройте **Unity** и нажмите кнопку **создать**.

    ![](images/AzureLabs-Lab310-21.png)

2.  Теперь необходимо указать имя проекта Unity. Вставьте **кустомвисионобждетектион**. Убедитесь, что для типа проекта задано значение **3D**, и задайте для **расположения** нужное значение (Помните, что ближе к корневым каталогам лучше). Затем нажмите кнопку **создать проект**.

    ![](images/AzureLabs-Lab310-22.png)

3.  При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**. Перейдите к разделу **изменение* > *настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**. Измените **Редактор внешних скриптов** на **Visual Studio**. Закройте окно **настройки** .

    ![](images/AzureLabs-Lab310-23.png)

4.  Затем перейдите в раздел **файл > параметры сборки** и переключите **платформу** на *универсальная платформа Windows*, а затем нажмите кнопку **коммутатора платформы** .

    ![](images/AzureLabs-Lab310-24.png)

5.  В том же окне **параметров сборки** убедитесь, что установлены следующие значения:

    1.  **Целевое устройство** имеет значение **HoloLens**        
    2.  Для **типа сборки** задано значение **D3D**
    3.  **Пакет SDK** установлен в значение " **Последняя установка** "
    4.  Для **версии Visual Studio** установлено значение " **Последняя установка** "
    5.  **Сборка и запуск** настроены на **локальный компьютер**            
    6.  Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.

        ![](images/AzureLabs-Lab310-25.png)

6.  В том же окне **параметров сборки** нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится **инспектор** .

7. На этой панели необходимо проверить несколько параметров:

    1.  На вкладке **другие параметры** выполните следующие действия.

        1.  **Версия среды выполнения сценариев** должна быть **экспериментальной** (эквивалент .NET 4,6), что вызовет необходимость перезапуска редактора.

        2. **Серверная часть сценариев** должна быть **.NET**.

        3. **Уровень совместимости API** должен быть **.NET 4,6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  На вкладке **Параметры публикации** в разделе **возможности**установите флажок:

        1. **InternetClient**

        2.  **Бесед**

        3. **спатиалперцептион**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  На панели в **параметрах XR** (см. ниже **Параметры публикации**), поддерживаемая **Виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .

        ![](images/AzureLabs-Lab310-29.png)

8.  Назад в **параметрах сборки** *проекты Unity\# C* больше не заключаются: установите флажок рядом с этим.

9.  Закройте окно **параметры сборки** .

10. В **редакторе**щелкните **изменить** > **проект параметры** > **графика**.

    ![](images/AzureLabs-Lab310-30.png)

11. На **панели инспектора** будут открыты *параметры графики* . Прокрутите вниз до тех пор, пока не появится массив с именем **всегда содержать шейдеры**. Добавьте слот, увеличив переменную **размера** на единицу (в этом примере она была 8, поэтому мы сделали это 9). В последней позиции массива появится новый слот, как показано ниже:

    ![](images/AzureLabs-Lab310-31.png)

12. В области щелкните маленький целевой круг рядом с слотом, чтобы открыть список шейдеров. Найдите устаревшие шейдеры, **прозрачный** и диффузный, а затем дважды щелкните его. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Глава 4. Импорт пакета Unity Кустомвисионобждетектион

Для этого курса вы предоставляете пакет ресурса Unity с именем **Azure-MR-310. пакет unitypackage**. 

> Советы Все объекты, поддерживаемые Unity, включая все сцены, можно упаковать в файл **пакет unitypackage** , а затем экспортировать или импортировать в другие проекты. Это самый надежный и эффективный способ перемещения ресурсов между различными **проектами Unity**.

[Пакет Azure-MR-310, который нужно скачать здесь,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)можно найти здесь.

1.  Теперь, когда панель мониторинга Unity находится перед вами, щелкните **ресурсы** в меню в верхней части экрана, а затем щелкните **Импорт пакета > настраиваемый пакет**.

    ![](images/AzureLabs-Lab310-33.png)

2.  С помощью средства выбора файлов выберите пакет **Azure-MR-310. пакет unitypackage** и нажмите кнопку **Открыть**. Отобразится список компонентов для этого актива. Подтвердите импорт, нажав кнопку " **Импорт** ".

    ![](images/AzureLabs-Lab310-34.png)

3.  После завершения импорта вы заметите, что папки пакета теперь добавлены в папку **Assets** . Такой тип структуры папок является типичным для проекта Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  В папке « **материалы** » содержится материал, используемый **курсором «взгляд**». 

    2.  Папка **plugins** содержит библиотеку DLL Newtonsoft, используемую кодом для десериализации веб-ответа службы. Две (2) версии, содержащиеся в папке и вложенной папке, необходимы для того, чтобы библиотека была использована и построена как в редакторе Unity, так и в сборке UWP. 

    3.  Папка **Prefabs** содержит Prefabs, содержащийся в сцене. Это:

        1.  **Газекурсор**, курсор, используемый в приложении. Будет работать вместе с Спатиалмаппинг prefab, чтобы их можно было разместить в сцене поверх физических объектов.
        2.  **Метка**, которая является объектом пользовательского интерфейса, используемым для вывода тега объекта в сцене при необходимости.
        3.  **Спатиалмаппинг**— это объект, который позволяет приложению использовать создание виртуальной схемы с помощью пространственного отслеживания Microsoft HoloLens.

    4.  Папка « **сцены** », в которой в настоящее время находится предварительно построенная сцена для этого курса.

4.  Откройте папку « **сцены** » на **панели «проект**» и дважды щелкните **обждетектионсцене**, чтобы загрузить сцену, которая будет использоваться для этого курса.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Код не включается**, вы пишете код, следуя этому курсу.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Глава 5. Создание класса Кустомвисионаналисер.

На этом этапе вы готовы написать некоторый код. Вы начнете с класса **кустомвисионаналисер** .

> [!NOTE]
> Вызовы **Пользовательская служба визуального распознавания**, выполненные в приведенном ниже коде, выполняются с помощью **REST API пользовательское визуальное распознавание**. С помощью этой функции вы узнаете, как реализовать этот API и использовать его (это полезно для понимания того, как реализовать что-то подобное). Имейте в виду, что корпорация Майкрософт предлагает **пакет SDK для пользовательское визуальное распознавание** , который также можно использовать для вызова службы. Дополнительные сведения см. в [статье пользовательское ВИЗУАЛЬНОЕ распознавание SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Этот класс отвечает за:

- Загрузка последнего образа, записанного в виде массива байтов.

- Отправка массива байтов в экземпляр **Пользовательская служба визуального распознавания** Azure для анализа.

- Получение ответа в виде строки JSON.

- Десериализация ответа и передача полученного **прогноза** классу **сценеорганисер** , который будет позаботиться о том, как должен отображаться ответ.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши **папку Asset**, расположенную на **панели проект**, и выберите команду **создать** > **папку**. Вызовите **скрипты**папки.

    ![](images/AzureLabs-Lab310-37.png)

2.  Дважды щелкните только что созданную папку, чтобы открыть ее.

3.  Щелкните правой кнопкой мыши внутри папки и выберите команду **создать** > **сценарий\# C**. Назовите сценарий **кустомвисионаналисер.**

4.  Дважды щелкните новый скрипт **кустомвисионаналисер** , чтобы открыть его в **Visual Studio.**

5.  Убедитесь, что в верхней части файла есть ссылки на следующие пространства имен:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  В классе **кустомвисионаналисер** добавьте следующие переменные:

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
    > Убедитесь, что вы вставили **ключ прогноза службы** в переменную **Предиктионкэй** , а **Прогноз-конечную точку —** в переменную **предиктионендпоинт** . Вы скопировали их в [Блокнот ранее, в главе 2, на шаге 14](#chapter-2---training-your-custom-vision-project).

7.  Необходимо добавить код для "спящего" **()** , чтобы инициализировать переменную экземпляра:

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

8.  Добавьте соподпрограмму (с помощью статического метода **жетимажеасбитеаррай ()** ниже), который будет получать результаты анализа изображения, захваченного классом **имажекаптуре** .

    > [!NOTE]
    > В соподпрограмме **аналисеимажекаптуре** есть вызов класса **сценеорганисер** , который вы еще создали. Поэтому **оставьте эти строки комментариями в настоящий момент**.

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

9. Удалите методы **Start ()** и **Update ()** , так как они не будут использоваться. 

10.  Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.

> [!IMPORTANT]
> Как упоминалось ранее, не беспокойтесь о коде, который может показаться ошибочным, так как в ближайшее время будут предоставлены дальнейшие занятия, которые будут устранены.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Глава 6. Создание класса Кустомвисионобжектс

Класс, который вы создадите, теперь является классом **кустомвисионобжектс** .

Этот скрипт содержит несколько объектов, используемых другими классами для сериализации и десериализации вызовов, выполненных в Пользовательская служба визуального распознавания.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши в  папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** . Вызовите скрипт **кустомвисионобжектс.**

2.  Дважды щелкните новый скрипт **кустомвисионобжектс** , чтобы открыть его в **Visual Studio.**

3.  Убедитесь, что в верхней части файла есть ссылки на следующие пространства имен:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Удалите методы **Start ()** и **Update ()** внутри класса **кустомвисионобжектс** . Теперь этот класс должен быть пустым.

    > [!WARNING]
    > Важно внимательно следовать следующей инструкции. Если поместить объявления нового класса в класс **кустомвисионобжектс** , в [главе 10](#chapter-10---create-the-imagecapture-class)будут возникнет ошибки компиляции, в которых говорится, что **аналисисрутобжект** и **BoundingBox** не найдены.

5.  Добавьте следующие классы *за* пределами класса **кустомвисионобжектс** . Эти объекты используются библиотекой **Newtonsoft** для сериализации и десериализации данных ответа:

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

6.  Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Глава 7. Создание класса Спатиалмаппинг

Этот класс настроит средство обнаружения для **пространственного сопоставления** в сцене, чтобы иметь возможность обнаруживать конфликты между виртуальными объектами и реальными объектами.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши в  папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** . Вызовите скрипт **спатиалмаппинг.**

2.  Дважды щелкните новый скрипт **спатиалмаппинг** , чтобы открыть его в **Visual Studio.**

3.  Убедитесь, что имеются следующие пространства имен, на которые ссылается класс **спатиалмаппинг** :

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Затем добавьте следующие переменные в класс **спатиалмаппинг** над методом **Start ()** :

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

5.  Добавьте параметр " **спящий ()** " и " **Начало" ()** :

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

6.  Удалите метод **Update ()** .

7.  Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Глава 8. Создание класса Газекурсор

Этот класс отвечает за настройку курсора в правильном расположении в реальном пространстве путем использования **спатиалмаппингколлидер**, созданного в предыдущей главе.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши в  папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** . Вызов скрипта **газекурсор**

2.  Дважды щелкните новый скрипт **газекурсор** , чтобы открыть его в **Visual Studio.**

3.  Убедитесь, что у вас есть следующее пространство имен, указанное выше класса **газекурсор** :

    ```csharp
    using UnityEngine;
    ```

4.  Затем добавьте следующую переменную в класс **газекурсор** выше метода **Start ()** . 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Обновите метод **Start ()** следующим кодом:

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

6.  Обновите метод **Update ()** , используя следующий код:

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
    > Не беспокойтесь об ошибке, когда класс **сценеорганисер** не найден, он будет создан в следующей главе.

7. Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Глава 9. Создание класса Сценеорганисер

Этот класс будет:

-   Настройте *основную камеру* , присоединив к ней соответствующие компоненты.

-   При обнаружении объекта он отвечает за вычисление его позиции в реальном мире и помещает **метку тега** рядом с соответствующим **именем тега**.    

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши в  папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** . Назовите сценарий **сценеорганисер**.

2.  Дважды щелкните новый скрипт **сценеорганисер** , чтобы открыть его в **Visual Studio.**

3.  Убедитесь, что имеются следующие пространства имен, на которые ссылается класс **сценеорганисер** :

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Затем добавьте следующие переменные в класс **сценеорганисер** над методом **Start ()** :

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

5.  Удалите методы **Start ()** и **Update ()** .

6.  Под переменными добавьте метод " **спящий ()** ", который будет инициализировать класс и настроить сцену.

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

7.  Добавьте метод **плацеаналисислабел ()** , который будет *создавать экземпляр* метки в сцене (которая на данный момент невидима для пользователя). Он также помещает четыре (невидимые) места размещения образа и пересекается с реальным миром. Это важно, поскольку координаты Box, полученные от службы после анализа, отправляются обратно в эту Quad, чтобы определить приблизительное расположение объекта в реальном мире. 

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

8.  Добавьте метод **финалиселабел ()** . Он отвечает за следующее:

    *   Установка для текста *метки* *тега* прогноза с наибольшей достоверностью.
    *   Вызов вычисления *ограничивающего прямоугольника* для объекта Quad, расположенного ранее, и размещение метки в сцене.
    *   Настройка глубины метки с помощью Райкаст к *ограничивающему прямоугольнику*, который должен конфликтовать с объектом в реальном мире.
    * Сброс процесса отслеживания, позволяющий пользователю записать другой образ.

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

9.  Добавьте метод **калкулатебаундингбокспоситион ()** , который содержит ряд вычислений, необходимых для преобразования координат ограничивающего *прямоугольника* , полученных из службы, и повторного создания их пропорционально четырем.

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

10. Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.

    > [!IMPORTANT]
    > Прежде чем продолжить, откройте класс **кустомвисионаналисер** и в методе **аналиселастимажекаптуред ()** раскомментируйте  следующие строки:
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
> Не беспокойтесь о сообщении о том, что класс **имажекаптуре** не найден, вы создадите его в следующей главе.


## <a name="chapter-10---create-the-imagecapture-class"></a>Глава 10. Создание класса Имажекаптуре

Следующий класс, который предстоит создать, — это класс **имажекаптуре** .

Этот класс отвечает за:

*   Запись изображения с помощью камеры HoloLens и сохранение его в папке *приложения* .
*   Обработка  жестов касания от пользователя.

Чтобы создать этот класс, сделайте следующее:

1.  Перейдите к созданной ранее папке **Scripts** .

2.  Щелкните правой кнопкой мыши внутри папки и выберите команду **создать** > **сценарий\# C**. Назовите сценарий **имажекаптуре**.

3.  Дважды щелкните новый скрипт **имажекаптуре** , чтобы открыть его в **Visual Studio.**

4.  Замените пространства имен в верхней части файла следующим:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Затем добавьте следующие переменные в класс **имажекаптуре** над методом **Start ()** :

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

6.  Теперь необходимо добавить код для методов **"спящий" ()** и **"начало" ()** :

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

7.  Реализуйте обработчик, который будет вызываться при возникновении жеста касания:

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
    > Когда курсор **горит зеленым**, это означает, что Камера доступна для получения образа. **Красный цвет**курсора означает, что камера занята.

8.  Добавьте метод, используемый приложением для запуска процесса записи образа, и сохраните образ:

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

9.  Добавьте обработчики, которые будут вызываться при записи фотографии и при ее готовности к анализу. Затем результат передается в **кустомвисионаналисер** для анализа.

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

10. Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Глава 11. Настройка сценариев в сцене

Теперь, когда вы написали весь код, необходимый для этого проекта, пора настроить скрипты в сцене и на Prefabs, чтобы они правильно ведут себя.

1.  В **редакторе Unity**на **панели Иерархия**выберите **основную камеру**.
2.  На **панели инспектора**с выбранной **основной камерой** щелкните **Добавить компонент**, найдите скрипт **сценеорганисер** и дважды щелкните, чтобы добавить его.

    ![](images/AzureLabs-Lab310-38.png)

3.  На **панели проект**откройте **папку Prefabs**, перетащите **метку** prefab в область входные данные целевого объекта *метки* пусто, в скрипте **Сценеорганисер** , который вы только что добавили к *основной камере*, как показано на изображение ниже:

    ![](images/AzureLabs-Lab310-39.png)

4.  На **панели Иерархия**выберите дочерний элемент **газекурсор** **основной камеры**.
5.  На **панели инспектора**с выбранным **Газекурсор** щелкните **Добавить компонент**, затем найдите скрипт **газекурсор** и дважды щелкните, чтобы добавить его.

    ![](images/AzureLabs-Lab310-40.png)

6.  Опять же, на **панели Иерархия**выберите дочерний элемент **спатиалмаппинг** **основной камеры**.
7.  На **панели инспектора**с выбранным **Спатиалмаппинг** щелкните **Добавить компонент**, затем найдите скрипт **спатиалмаппинг** и дважды щелкните, чтобы добавить его.

    ![](images/AzureLabs-Lab310-41.png)

Остальные скрипты, которые не были заданы, будут добавляться кодом в скрипте **сценеорганисер** во время выполнения.

## <a name="chapter-12---before-building"></a>Глава 12-перед сборкой

Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на Microsoft HoloLens.

Перед этим убедитесь в том, что:

-  Все параметры, упомянутые в [главе 3](#chapter-3---set-up-the-unity-project) , заданы правильно.
- **Сценеорганисер** скрипта прикреплен к главному объекту **Camera** .
- **Газекурсор** скрипта присоединен к объекту **газекурсор** .
- **Спатиалмаппинг** скрипта присоединен к объекту **спатиалмаппинг** .
- В [главе 5](#chapter-5---create-the-customvisionanalyser-class)шаг 6.

    - Убедитесь, что вы вставили **ключ прогноза службы** в переменную **предиктионкэй** .
    - Вы вставили **конечную точку прогнозирования** в класс **предиктионендпоинт** .

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Глава 13. Создание решения UWP и загружать неопубликованные приложения

Теперь вы готовы к созданию приложения в качестве решения UWP, которое можно будет развернуть на Microsoft HoloLens. Чтобы начать процесс сборки:

1.  Выберите **файл > параметры сборки**.

2.  **Проекты тактов Unity\# C**.

3.  Щелкните **Добавить открытые сцены**. При этом в сборку будет добавлена открытая сцена.

    ![](images/AzureLabs-Lab310-42.png)

4.  Щелкните **Сборка**. Unity запустит окно *проводника* , в котором необходимо создать, а затем выбрать папку для сборки приложения. Создайте эту папку сейчас и назовите ее **app**Name. Затем выберите папку **приложения** и щелкните **выбрать папку**.

5.  Unity начнет сборку проекта в папку **приложения** .

6.  После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).

7.  Чтобы выполнить развертывание в Microsoft HoloLens, вам потребуется IP-адрес этого устройства (для удаленного развертывания) и убедиться, что в нем также установлен **режим разработчика** . Выполните указанные ниже действия.

    1.  Людьми HoloLens, откройте **Параметры**.

    2.  Выберите сетевые &**Дополнительные параметры** **сети Интернет** > **Wi-Fi** > 

    3.  Запишите **IPv4** -адрес.

    4.  Затем вернитесь к параметрам и **Обновите & безопасности** > **для разработчиков** .

    5.  Задайте **режим разработчика** *на*.

8.  Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.

9.  В конфигурации решения выберите **Отладка**.

10. На платформе решения выберите **x86, удаленный компьютер**. Вам будет предложено вставить **IP-адрес** удаленного устройства (в данном случае — Microsoft HoloLens, который вы заметили).

    ![](images/AzureLabs-Lab310-43.png)

11. Перейдите в меню " **Сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение в HoloLens.

12. Теперь приложение должно появиться в списке установленных приложений в Microsoft HoloLens, готовом к запуску.

### <a name="to-use-the-application"></a>Чтобы использовать приложение, выполните следующие действия.

* Взгляните на объект, который вы обучили **Пользовательская служба визуального распознавания Azure, обнаружение объектов**и используйте **жест касания**.
* Если объект успешно обнаружен, *текст метки* в мировом пространстве будет отображаться с именем тега.

> [!IMPORTANT]
> Каждый раз, когда вы записываете фотографию и отправляете ее в службу, вы можете вернуться на страницу службы и переучить службу с новыми записанными образами. В начале вам, возможно, придется исправить *ограничивающие рамки* , чтобы они были более точными и переучить службу.

> [!NOTE]
> Размещенный текст метки может не располагаться рядом с объектом, когда датчики Microsoft HoloLens и (или) Спатиалтраккингкомпонент в Unity не могут поместить соответствующие конфликты, связанные с реальными объектами мира. Если это так, попробуйте использовать приложение на другой поверхности.

## <a name="your-custom-vision-object-detection-application"></a>Пользовательское визуальное распознавание, приложение обнаружения объектов

Поздравляем! вы создали приложение смешанной реальности, которое использует Пользовательское визуальное распознавание Azure, API обнаружения объектов, который может распознать объект из изображения, а затем выдать приблизительное место для этого объекта в трехмерном пространстве.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Премиальные упражнения

### <a name="exercise-1"></a>Упражнение 1

При добавлении к текстовой метке используйте полупрозрачный куб, чтобы обернуть реальный объект в трехмерный *ограничивающий прямоугольник*.

### <a name="exercise-2"></a>Упражнение 2

Обучить Пользовательская служба визуального распознавания для распознавания большего числа объектов.

### <a name="exercise-3"></a>Упражнение 3

Подавать звуковой сигнал при распознавании объекта.

### <a name="exercise-4"></a>Упражнение 4

Используйте API для переобучения службы с теми же изображениями, которые анализирует приложение, чтобы сделать службу более точной (одновременное прогнозирование и обучение).
