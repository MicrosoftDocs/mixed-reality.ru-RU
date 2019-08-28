---
title: MR и Azure 302B — пользовательское видение
description: Пройдите этот курс, чтобы научиться обучить модель машинного обучения, а затем использовать обученную модель для распознавания похожих объектов в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, пользовательское видение, hololens, иммерсивное, VR
ms.openlocfilehash: b173648e2e829e94e47306277bd7814a19842cae
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047212"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR и Azure 302B: Пользовательское представление

В этом курсе вы узнаете, как распознать пользовательское визуальное содержимое в предоставленном образе, используя возможности Пользовательское визуальное распознавание Azure в приложении смешанной реальности.

Эта служба позволит обучить модель машинного обучения с помощью образов объектов. После этого обученная модель будет использоваться для распознавания похожих объектов, как это обеспечивается с помощью камеры Microsoft HoloLens или камеры, подключенной к компьютеру для использования в качестве впечатляющих (VR) гарнитур.

![результат курса](images/AzureLabs-Lab302b-00.png)

Azure Пользовательское визуальное распознавание — это служба Microsoft, которая позволяет разработчикам создавать пользовательские классификаторы изображений. Эти классификаторы можно использовать с новыми образами для распознавания или классификации объектов внутри этого нового изображения. Служба предоставляет простой, простой в использовании веб-портал для упрощения процесса. Дополнительные сведения см. на [странице Пользовательская служба визуального распознавания Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

После завершения этого курса у вас будет приложение смешанной реальности, которое сможет работать в двух режимах:

-   **Режим анализа**. Настройка пользовательская служба визуального распознавания вручную путем отправки образов, создания тегов и обучения службы для распознавания различных объектов (в данном случае это мышь и клавиатура). Затем вы создадите приложение HoloLens, которое будет записывать изображения с помощью камеры и попытается распознать эти объекты в реальном мире.

-   **Режим обучения**. Вы будете реализовывать код, который включит режим обучения в приложении. Режим обучения позволяет записывать изображения с помощью камеры HoloLens, передавать записанные образы в службу и обучить пользовательскую модель концепции.

В этом курсе вы узнаете, как получить результаты из Пользовательская служба визуального распознавания в пример приложения на основе Unity. Вы сможете применить эти понятия к настраиваемому приложению, которое вы можете собрать.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> MR и Azure 302B: Пользовательское представление</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс в основном ориентирован на HoloLens, вы можете также применить сведения, которые вы узнаете в этом курсе, к головным телефонам Windows Mixed Reality (VR). Так как у головных гарнитур нет доступных камер, вам потребуется внешняя камера, подключенная к компьютеру. При работе с курсом вы увидите заметки о любых изменениях, которые могут потребоваться для поддержки головных телефонов (VR).

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#. Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018). Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.

Для этого курса рекомендуется следующее оборудование и программное обеспечение:

- ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)
- [Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK для Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Камера, подключенная к компьютеру (для разработки в увлекательной гарнитуре)
- Доступ к Интернету для установки Azure и получение API Пользовательское визуальное распознавание
- Последовательность из пяти (5) образов (рекомендуется десять (10)) для каждого объекта, который вы хотите Пользовательская служба визуального распознавания распознать. При желании вы можете использовать образы, [которые уже предоставлены в этом курсе (мышь компьютера и клавиатура) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Перед началом

1.  Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).
2.  Настройка и тестирование HoloLens. Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя). 

Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).

Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Глава 1. портал Пользовательская служба визуального распознавания

Чтобы использовать *Пользовательская служба визуального распознавания* в Azure, необходимо настроить экземпляр службы, чтобы сделать его доступным для приложения.

1.  Сначала [перейдите на главную страницу *Пользовательская служба визуального распознавания* ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Нажмите кнопку " **начать работу** ".

    ![](images/AzureLabs-Lab302b-01.png)

3.  Войдите на портал *Пользовательская служба визуального распознавания* .

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо создать ее. Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.

4.  После первого входа в систему вам будет предложено ввести *условия использования панели Сервис* . Установите флажок, чтобы принять условия. Затем нажмите кнопку **принимаю**.

    ![](images/AzureLabs-Lab302b-03.png)

5.  Принимаю условия, вы будете переходить к разделу *проекты* на портале. Щелкните **Новый проект**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  На правой стороне появится вкладка, в которой будет предложено указать некоторые поля для проекта.

    1.  Вставьте *имя* проекта.

    2.  Вставьте *Описание* проекта (необязательно).

    3.  Выберите *группу ресурсов* или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure. Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.

    4. Задание *типов проектов* для **классификации**
    
    5. Задайте *домены* как **Общие**.

        ![](images/AzureLabs-Lab302b-05.png)

        > Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  По завершении нажмите кнопку **создать проект**. Вы будете перенаправлены на страницу пользовательская служба визуального распознавания, проект.

## <a name="chapter-2---training-your-custom-vision-project"></a>Глава 2. обучение проекта Пользовательское визуальное распознавание

На портале Пользовательское визуальное распознавание основной целью является обучение проекта для распознавания конкретных объектов в изображениях. Требуется по крайней мере пять образов (5), хотя для каждого объекта, который нужно распознать, рекомендуется использовать по меньшей мере десять (10). [Вы можете использовать образы, предоставляемые в этом курсе (мышь компьютера и клавиатура)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Обучение проекта Пользовательская служба визуального распознавания:

1.  Нажмите кнопку рядом с пунктом **теги.** **+**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Добавьте **имя** объекта, который вы хотите распознать. Щелкните **Save**(Сохранить).

    ![](images/AzureLabs-Lab302b-07.png)

3.  Обратите внимание, что добавлен **тег** (может потребоваться перезагрузить страницу, чтобы она отображалась). Установите флажок рядом с новым тегом, если он еще не установлен.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Щелкните **Добавить изображения** в центре страницы.

    ![](images/AzureLabs-Lab302b-09.png)

5.  Щелкните **Обзор локальные файлы**, найдите, а затем выберите изображения, которые нужно передать, с минимальным числом (5). Помните, что все эти образы должны содержать объект для обучения.

    > [!NOTE]
    >  Для отправки можно выбрать несколько образов за раз.

6.  Просмотрев изображения на вкладке, выберите соответствующий тег в поле **Мои теги** .

    ![](images/AzureLabs-Lab302b-10.png)

7.  Щелкните **upload Files (отправить файлы**). Файлы начнут отправляться. Получив подтверждение отправки, нажмите кнопку **Готово**.

    ![](images/AzureLabs-Lab302b-11.png)

8.  Повторите тот же процесс, чтобы создать новый **тег** с именем **Keyboard** и загрузить в него соответствующие фотографии. После создания новых тегов снимите **флажок** *мыши* , чтобы отобразить окно *Добавление изображений* .

9.  После настройки обоих тегов щелкните " **обучение**", после чего начнется создание первой итерации для обучения.

    ![](images/AzureLabs-Lab302b-12.png)

10. После завершения сборки вы увидите две кнопки с именем сделать **URL-адрес** **по умолчанию** и прогноз. Щелкните сначала **создать значение по умолчанию** , а затем щелкните **URL-адрес прогноза**.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > В качестве URL-адреса конечной точки, предоставленной из этого, задается любая *Итерация* , помеченная как используемая по умолчанию. Таким образом, если позднее вы выполните новую *итерацию* и обновите ее по умолчанию, вам не потребуется изменять код.

11. После того как вы щелкнули *URL-адрес прогноза*, откройте *Блокнот*, скопируйте и вставьте **URL-адрес** и **ключ прогноза**, чтобы его можно было извлечь, когда он понадобится позже в коде.

    ![](images/AzureLabs-Lab302b-14.png)

12. Щелкните **шестеренки** в правом верхнем углу экрана.

    ![](images/AzureLabs-Lab302b-15.png)

13. Скопируйте **ключ обучения** и вставьте его в *Блокнот*для последующего использования.

    ![](images/AzureLabs-Lab302b-16.png)

14. Также скопируйте **идентификатор проекта**, а также вставьте его в файл *блокнота* для последующего использования.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Глава 3. Настройка проекта Unity

Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.

1.  Откройте *Unity* и нажмите кнопку **создать**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  Теперь необходимо указать имя проекта Unity. Вставьте **азурекустомвисион.** Убедитесь, что для шаблона проекта задано значение **3D**. Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше). Затем нажмите кнопку **создать проект**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**. Перейдите к разделу **изменение* > *настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**. Измените **Редактор внешних скриптов** на **Visual Studio 2017**. Закройте окно **настройки** .

    ![](images/AzureLabs-Lab302b-19.png)

4.  Затем перейдите в раздел **файл > параметры сборки** и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.

    ![](images/AzureLabs-Lab302b-20.png)

5.  Несмотря на то что в **файле > параметры сборки** , убедитесь в том, что:

    1.  **Целевое устройство** имеет значение **Hololens**

        > Для впечатляющих головных телефонов задайте для параметра **целевое устройство** *любое устройство*.
        
    2.  Для **типа сборки** задано значение **D3D**
    3.  **Пакет SDK** установлен в значение " **Последняя установка** "
    4.  Для **версии Visual Studio** установлено значение " **Последняя установка** "
    5.  **Сборка и запуск** настроены на **локальный компьютер**
    6.  Сохраните сцену и добавьте ее в сборку. 

        1. Для этого выберите **Добавить открытые сцены**. Появится окно сохранения.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».

            ![](images/AzureLabs-Lab302b-22.png)

        3. Откройте созданную папку **сцены** , а затем в текстовом поле *имя файла* введите **Кустомвисионсцене**, а затем щелкните **Save (сохранить**).

            ![](images/AzureLabs-Lab302b-23.png)

            > Помните, что сцены Unity необходимо сохранять в папке Assets , так как они должны быть связаны с проектом Unity. Создание папки «сцены» (и других аналогичных папок) — типичный способ структуризации проекта Unity.
            
    7.  Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.

        ![](images/AzureLabs-Lab302b-24.png)

6.  В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .

7. На этой панели необходимо проверить несколько параметров:

    1.  На вкладке **другие параметры** выполните следующие действия.

        1.  **Версия среды выполнения сценариев** должна быть **экспериментальной (эквивалент .NET 4,6)** , что вызовет необходимость перезапуска редактора.

        2. **Серверная часть сценариев** должна быть **.NET**

        3. **Уровень совместимости API** должен быть **.NET 4,6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  На вкладке **Параметры публикации** в разделе **возможности**установите флажок:

        1. **InternetClient**

        2.  **Бесед**

        3. **Звук**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .

    ![](images/AzureLabs-Lab302b-27.png)

8.  Назад в *параметрах сборки* *проекты\# Unity C* больше не заключаются; установите флажок рядом с этим.

9.  Закройте окно параметры сборки.

10.  Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Глава 4. Импорт библиотеки DLL Newtonsoft в Unity

> [!IMPORTANT]
> Если вы хотите пропустить компонент *установки Unity* , установленный в этом курсе, и продолжить работу с кодом, скачайте этот [Azure-MR-302B. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в [главе 6 ](#chapter-6---create-the-customvisionanalyser-class).

Для работы с этим курсом необходимо использовать библиотеку **Newtonsoft** , которую можно добавить в ресурсы в качестве библиотеки DLL. Пакет, содержащий [эту библиотеку, можно скачать по этой ссылке](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Чтобы импортировать библиотеку Newtonsoft в проект, используйте пакет Unity, прилагаемый к этому курсу.

1.  Добавьте *.пакет unitypackage* в Unity с помощью команды меню **Настраиваемый* *пакет* *Импорт* > *активов* > * .

2.  В появившемся окне **Импорт пакета Unity** убедитесь, что выбраны все компоненты **подключаемых модулей** (включая).

    ![](images/AzureLabs-Lab302b-28.png)

3.  Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.

4.  Перейдите в папку **Newtonsoft** в разделе **подключаемые модули** в представлении проекта и выберите *подключаемый модуль Newtonsoft. JSON*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  Выбрав *подключаемый модуль Newtonsoft. JSON* , убедитесь, что **все платформы** не установлены, убедитесь, что **всаплайер** также не **установлен**, а затем нажмите кнопку **Применить**. Это необходимо только для того, чтобы убедиться, что файлы настроены правильно.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Пометка этих подключаемых модулей настраивает их для использования только в редакторе Unity. В папке WSA имеется другой набор, который будет использоваться после экспорта проекта из Unity.

6.  Далее необходимо открыть папку **WSA** в папке **Newtonsoft** Вы увидите копию того же файла, который вы только что настроили. Выберите файл, а затем в инспекторе убедитесь, что
    -   **Все платформы** не **отмечены** 
    -   **только** **Всаплайер** **установлен**
    -   **Установлен** **процесс не**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Глава 5 — Настройка камеры

1.  На панели Иерархия выберите *основную камеру*.

2.  После выбора вы сможете увидеть все компоненты *основной камеры* на *панели инспектора*.

    1.  Объект *Camera* должен называться **основной камерой** (Обратите внимание на орфографию!)

    2.  Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на правописание).

    3.  Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .

    4.  Установите для параметра **сбросить флаги** **сплошной цвет** (не обращайте внимания на иммерсивное гарнитуру).

    5.  Задайте черный цвет **фона** для компонента камеры **, альфа-канал 0 (шестнадцатеричный код: #00000000)** (не учитывать это для иммерсивного головного телефона).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Глава 6. Создание класса Кустомвисионаналисер.

На этом этапе вы готовы написать некоторый код.

Вы начнете с класса *кустомвисионаналисер* .

> [!NOTE]
> Вызовы **Пользовательская служба визуального распознавания** , выполненные в приведенном ниже коде, выполняются с помощью **REST API пользовательское визуальное распознавание**. С помощью этой функции вы узнаете, как реализовать этот API и использовать его (это полезно для понимания того, как реализовать что-то подобное). Имейте в виду, что корпорация Майкрософт предлагает **пакет SDK для пользовательская служба визуального распознавания** , который также можно использовать для вызова службы. Дополнительные сведения см. в статье [ПОЛЬЗОВАТЕЛЬСКАЯ служба визуального распознавания SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) .

Этот класс отвечает за:

-   Загрузка последнего образа, записанного в виде массива байтов.

-   Отправка массива байтов в экземпляр *Пользовательская служба визуального распознавания* Azure для анализа.

-   Получение ответа в виде строки JSON.

-   Десериализация ответа и передача полученного *прогноза* классу *сценеорганисер* , который будет позаботиться о том, как должен отображаться ответ.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши *папку Asset* , расположенную на *панели проект*, и выберите команду **Создать > папку**. Вызовите **скрипты**папки.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Дважды щелкните только что созданную папку, чтобы открыть ее.

3.  Щелкните правой кнопкой мыши внутри папки и выберите команду **создать** > **сценарий\# C**. Назовите сценарий *кустомвисионаналисер*.

4.  Дважды щелкните новый скрипт *кустомвисионаналисер* , чтобы открыть его в **Visual Studio**.

5.  Обновите пространства имен в верхней части файла, чтобы они соответствовали следующим условиям.

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  В классе *кустомвисионаналисер* добавьте следующие переменные:

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
    > Убедитесь, что вы вставили **ключ прогноза** в переменную **Предиктионкэй** и свою **конечную точку прогнозирования** в переменную **предиктионендпоинт** . Вы скопировали их в *Блокнот* ранее в этом курсе.

7.  Необходимо добавить код для "спящего" **()** , чтобы инициализировать переменную экземпляра:

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

8.  Удалите методы **Start ()** и **Update ()** .

9.  Затем добавьте соподпрограмму (с помощью статического метода **жетимажеасбитеаррай ()** ниже), который будет получать результаты анализа изображения, захваченного классом *имажекаптуре* .

    > [!NOTE]
    > В соподпрограмме **аналисеимажекаптуре** есть вызов класса *сценеорганисер* , который вы еще создали. Поэтому **оставьте эти строки комментариями в настоящий момент**.

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

10.  Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Глава 7. Создание класса Кустомвисионобжектс

Класс, который вы создадите, теперь является классом *кустомвисионобжектс* .

Этот скрипт содержит несколько объектов, используемых другими классами для сериализации и десериализации вызовов, выполненных в *Пользовательская служба визуального распознавания*.

> [!WARNING]
> Важно отметить конечную точку, которую предоставляет Пользовательская служба визуального распознавания, так как следующая структура JSON настроена для работы с [*пользовательское визуальное распознавание PREDICTION v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Если у вас другая версия, может потребоваться обновить приведенную ниже структуру.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши в папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** . Вызовите скрипт *кустомвисионобжектс*.

2.  Дважды щелкните новый скрипт **кустомвисионобжектс** , чтобы открыть его в **Visual Studio**.

3.  Добавьте следующие пространства имен в начало файла:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Удалите методы **Start ()** и **Update ()** внутри класса *кустомвисионобжектс* . Этот класс теперь должен быть пустым.

5.  Добавьте следующие классы **за** пределами класса *кустомвисионобжектс* . Эти объекты используются библиотекой *Newtonsoft* для сериализации и десериализации данных ответа:

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Глава 8. Создание класса Воицерекогнизер

Этот класс будет распознавать речевой ввод пользователя.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши в папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** . Вызовите скрипт *воицерекогнизер*.

2.  Дважды щелкните новый скрипт **воицерекогнизер** , чтобы открыть его в **Visual Studio**.

3.  Добавьте следующие пространства имен над классом *воицерекогнизер* :

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Затем добавьте следующие переменные в класс *воицерекогнизер* над методом *Start ()* :

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

5.  Добавьте методы " **спящий ()** " и " **Начало" ()** , второй из которых будет настраивать *Ключевые слова* пользователя, распознаваемые при связывании тега с изображением:

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

6.  Удалите метод **Update ()** .

7.  Добавьте следующий обработчик, вызываемый при распознавании речевого ввода:

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

8.  Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.

> [!NOTE]
> Не беспокойтесь о коде, который может показаться ошибочным, так как в ближайшее время будут предоставлены дальнейшие занятия, которые будут устранены.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Глава 9. Создание класса Кустомвисионтраинер

Этот класс будет связывать серию веб-вызовов для обучения *Пользовательская служба визуального распознавания*. Каждый вызов будет подробно рассмотрен прямо над кодом.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши в папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** . Вызовите скрипт *кустомвисионтраинер*.

2.  Дважды щелкните новый скрипт *кустомвисионтраинер* , чтобы открыть его в **Visual Studio**.

3.  Добавьте следующие пространства имен над классом *кустомвисионтраинер* :

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Затем добавьте следующие переменные в класс *кустомвисионтраинер* над методом **Start ()** . 

    > [!NOTE]
    > URL-адрес обучения, используемый здесь, приведен в документации по *пользовательское визуальное распознавание обучения 1,2* и имеет структуру: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Дополнительные сведения см. в справочном справочнике по [*пользовательское визуальное распознавание Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > Важно отметить, что конечная точка, предоставляемая Пользовательская служба визуального распознавания, обеспечивает режим обучения, так как используемая структура JSON (в классе **кустомвисионобжектс** ) настроена для работы с [*пользовательское визуальное распознавание Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). При наличии другой версии может потребоваться обновить структуру *объектов* .

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
    > Убедитесь, что вы добавили **ключ службы** (ключ обучения) и значение **идентификатора проекта** , которое вы заговорили ранее. Это значения, собранные на [портале ранее в ходе курса (глава 2, шаг 10 и выше)](#chapter-2---training-your-custom-vision-project).

5.  Добавьте следующие методы **Start ()** и **спящего режима ()** . Эти методы вызываются при инициализации и содержат вызов для настройки пользовательского интерфейса:

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

6.  Удалите метод **Update ()** . Этот класс не будет нужен.

7.  Добавьте метод **рекуесттагселектион ()** . Этот метод является первым, который вызывается, когда изображение было записано и сохранено на устройстве и теперь готово к отправке в *Пользовательская служба визуального распознавания*, чтобы обучить его. Этот метод отображает в пользовательском интерфейсе обучения набор ключевых слов, которые пользователь может использовать для отметки записанного изображения. Он также оповещает класс *воицерекогнизер* , чтобы начать прослушивание пользователя для ввода голоса.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Добавьте метод **верифитаг ()** . Этот метод будет принимать ввод голоса, распознаваемый классом **воицерекогнизер** , и проверять его допустимость, а затем начинать процесс обучения.

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

9.  Добавьте метод **субмитимажефортраининг ()** . Этот метод начнет процесс обучения Пользовательская служба визуального распознавания. Первым шагом является получение **идентификатора тега** из службы, связанной с проверенным речевым входом пользователя. Затем **идентификатор тега** будет отправлен вместе с изображением.

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

10. Добавьте метод **траинкустомвисионпрожект ()** . После отправки и пометки образа будет вызван этот метод. Он создаст новую итерацию, которая будет обучена всеми предыдущими изображениями, отправленными в службу, а также только что отправленное изображение. После завершения обучения этот метод вызывает метод, чтобы задать созданную итерацию **по умолчанию**, чтобы конечная точка, используемая для анализа, была последней обученной итерацией.

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

11. Добавьте метод **сетдефаултитератион ()** . Этот метод задаст ранее созданную и обученную итерацию *по умолчанию*. После завершения этот метод должен удалить предыдущую итерацию, существующую в службе. На момент написания этого курса в службе можно одновременно использовать не более десяти итераций (10) одновременно.

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

12. Добавьте метод **делетепревиауситератион ()** . Этот метод найдет и удалит предыдущую нестандартную итерацию:

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

13. Последний метод для добавления в этом классе — метод **жетимажеасбитеаррай ()** , используемый в веб-вызовах для преобразования изображения, захваченного в массив байтов.

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

14. Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Глава 10. Создание класса Сценеорганисер

Этот класс будет:

-   Создайте объект **курсора** для присоединения к основной камере.

-   Создайте объект **Label** , который будет отображаться, когда служба распознает реальные объекты.

-   Настройте основную камеру, присоединив к ней соответствующие компоненты.

-   В **режиме анализа**, порождение меток во время выполнения, в соответствующем мировом пространстве относительно положения основной камеры и вывода данных, полученных от пользовательская служба визуального распознавания.

-   В **режиме обучения**Порождение пользовательского интерфейса, в котором будут отображаться различные этапы процесса обучения.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши в папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** . Назовите сценарий *сценеорганисер*.

2.  Дважды щелкните новый скрипт *сценеорганисер* , чтобы открыть его в **Visual Studio**.

3.  Вам потребуется только одно пространство имен, удалите остальные из класса *сценеорганисер* .

    ```csharp
    using UnityEngine;
    ```

4.  Затем добавьте следующие переменные в класс *сценеорганисер* над методом **Start ()** :

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

5.  Удалите методы **Start ()** и **Update ()** .

6.  Непосредственно под переменными добавьте метод " **спящий ()** ", который инициализирует класс и настраивает сцену.

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

7.  Теперь добавьте метод **креатекамеракурсор ()** , который создает и позиционирует основной курсор камеры, и метод **CreateLabel ()** , который создает объект **метки анализа** .

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

8. Добавьте метод **сеткамерастатус ()** , который будет работать с сообщениями, предназначенными для сетки текста, предоставляющей состояние камеры.

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

9. Добавьте методы **плацеаналисислабел ()** и **сеттагстоластлабел ()** , которые будут порождать и отображать данные из пользовательская служба визуального распознавания в сцене.

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

10. Наконец, добавьте метод **креатетраинингуи ()** , который ПОРОЖДАЕТ пользовательский интерфейс, отображающий несколько стадий процесса обучения, когда приложение находится в режиме обучения. Этот метод также будет использоваться для создания объекта состояния камеры.

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

11. Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.

> [!IMPORTANT]
> Прежде чем продолжить, откройте класс **кустомвисионаналисер** и в методе **аналиселастимажекаптуред ()** раскомментируйте следующие строки:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Глава 11. Создание класса Имажекаптуре

Следующий класс, который предстоит создать, — это класс *имажекаптуре* .

Этот класс отвечает за:

-   Запись изображения с помощью камеры HoloLens и сохранение его в папке *приложения* .

-   Обработка жестов касания от пользователя.

-   Поддержание значения *перечисления* , определяющего, будет ли приложение запускаться в режиме *анализа* или *обучения* .

Чтобы создать этот класс, сделайте следующее:

1.  Перейдите к созданной ранее папке **Scripts** .

2.  Щелкните правой кнопкой мыши внутри папки и выберите команду **Создать > сценарий\# C**. Назовите сценарий *имажекаптуре*.

3.  Дважды щелкните новый скрипт **имажекаптуре** , чтобы открыть его в **Visual Studio**.

4.  Замените пространства имен в верхней части файла следующим:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Затем добавьте следующие переменные в класс *имажекаптуре* над методом **Start ()** :

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

6.  Теперь необходимо добавить код для методов **"спящий" ()** и **"начало" ()** :

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
    > В режиме *анализа* метод **тафандлер** выступает в качестве параметра для запуска или завершения цикла записи фотографий.
    >
    > В режиме *обучения* он будет записывать изображение с камеры.
    >
    > Когда курсор горит зеленым, это означает, что Камера доступна для получения образа.
    >
    > Красный цвет курсора означает, что камера занята.

8.  Добавьте метод, используемый приложением для запуска процесса записи образа и сохранения образа.

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

9.  Добавьте обработчики, которые будут вызываться при записи фотографии и при ее готовности к анализу. Затем результат передается в *кустомвисионаналисер* или *кустомвисионтраинер* в зависимости от того, в каком режиме установлен код.

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

10. Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.

11. Теперь, когда все сценарии завершены, вернитесь в редактор Unity, а затем перетащите класс **сценеорганисер** из папки Scripts в основной объект **Camera** на *панели Иерархия*.

## <a name="chapter-12---before-building"></a>Глава 12-перед сборкой

Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на HoloLens.

Перед этим убедитесь в том, что:

- Все параметры, упомянутые в [главе 2](#chapter-2---training-your-custom-vision-project) , заданы правильно.

- Все поля на **главной камере**, панели инспектора, назначаются должным образом.

- **Сценеорганисер** скрипта прикреплен к главному объекту **Camera** .

- Убедитесь, что вы вставили **ключ прогноза** в переменную **предиктионкэй** .

- Вы вставили **конечную точку прогнозирования** в переменную **предиктионендпоинт** .

- Вы вставили **ключ обучения** в переменную **траинингкэй** класса *кустомвисионтраинер* .

- Вы вставили **идентификатор проекта** в переменную **projectId** класса *кустомвисионтраинер* .

## <a name="chapter-13---build-and-sideload-your-application"></a>Глава 13. Создание и загружать неопубликованные приложения

Чтобы начать процесс *сборки* :

1.  Выберите **файл > параметры сборки**.

2.  **Проекты тактов Unity\# C**.

3.  Щелкните **Сборка**. Unity запустит окно **проводника** , в котором необходимо создать, а затем выбрать папку для сборки приложения. Создайте эту папку сейчас и назовите ее **app**Name. Затем в выбранной папке **приложения** щелкните **выбрать папку**.

4.  Unity начнет сборку проекта в папку **приложения** .

5.  После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).

Для развертывания на HoloLens выполните следующие действия.

1.  Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика**. Выполните указанные ниже действия.

    1.  Людьми HoloLens, откройте **Параметры**.

    2.  Выберите сетевые &**Дополнительные параметры** **сети Интернет** > **Wi-Fi** > 

    3.  Запишите **IPv4** -адрес.

    4.  Затем вернитесь к параметрами **Обновите & безопасности** > **для разработчиков** .

    5.  Задайте **режим разработчика на**.

2.  Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.

3.  В *конфигурации решения* выберите **Отладка**.

4.  На *платформе решения*выберите **x86, удаленный компьютер**. Вам будет предложено вставить **IP-адрес** удаленного устройства (в данном случае это HoloLens).

    ![](images/AzureLabs-Lab302b-34.png)

5. Перейдите в меню **Сборка** и щелкните **Развернуть решение** , чтобы загружать неопубликованные приложение в HoloLens.

6. Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.

> [!NOTE]
> Чтобы выполнить развертывание в иммерсивное виртуальную гарнитуру, задайте для **платформы решения** значение *локальный компьютер*и задайте для параметра **Конфигурация** значение *Отладка*( *x86* в качестве **платформы**). Затем выполните развертывание на локальном компьютере с помощью пункта меню " **Сборка** " и выберите *Развернуть решение*. 

## <a name="to-use-the-application"></a>Чтобы использовать приложение, выполните следующие действия.

Чтобы переключить функциональные возможности приложения между режимом *обучения* и режимом *прогнозирования* , необходимо обновить переменную **аппмоде** , расположенную в методе спящего режима **()** , расположенном в классе *имажекаптуре* .

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
или диспетчер конфигурации служб
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

В режиме *обучения* :

- Взгляните на **мышь** или **клавиатуру** и используйте **жест касания**.

- Затем появится текст с запросом на указание тега.

- Например, с помощью **мыши** или **клавиатуры**.


В режиме прогнозирования:

- Взгляните на объект и используйте **жест касания**.

- Появится текст, предоставляющий обнаруженный объект, с наибольшей вероятностью (это нормализованное значение).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Глава 14. Оценка и усовершенствование модели Пользовательское визуальное распознавание

Чтобы сделать службу более точной, необходимо продолжить обучение модели, используемой для прогнозирования. Это достигается благодаря использованию нового приложения, в котором используются оба режима *обучения* и *прогнозирования* , при этом требуется посетить портал, что рассматривается в этой главе. Будьте готовы к повторному посещению портала, чтобы постоянно улучшать модель.

1. Снова перейдите на портал Azure Пользовательское визуальное распознавание и в проекте выберите вкладку прогнозы (в верхнем центре страницы ):

    ![](images/AzureLabs-Lab302b-35.png)

2. Вы увидите все образы, которые были отправлены в вашу службу во время работы приложения. При наведении указателя мыши на изображения они будут предоставлять прогнозы, сделанные для этого образа:

    ![](images/AzureLabs-Lab302b-36.png)

3. Выберите один из образов, чтобы открыть его. После открытия вы увидите прогнозы, сделанные для этого изображения справа. Если прогнозы были правильными и вы хотите добавить этот образ в модель обучения службы, щелкните поле ввода " *Мои теги* " и выберите тег, который нужно связать. По завершении нажмите кнопку *сохранить и закрыть* в правом нижнем углу и продолжайте переходить к следующему изображению.

    ![](images/AzureLabs-Lab302b-37.png)

4. Когда вы вернетесь к сетке изображений, вы заметите, что изображения, в которые были добавлены теги (и сохранены), будут удалены. Если вы нашли какие-либо изображения, на которых нет элемента с тегами, их можно удалить, щелкнув такт на этом изображении (это можно сделать для нескольких изображений), а затем нажать кнопку *Удалить* в правом верхнем углу страницы сетки. В следующем всплывающем окне можно щелкнуть *Да, удалить* или *нет*, чтобы подтвердить удаление или отменить его соответственно. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Когда вы будете готовы к продолжению, нажмите зеленую кнопку « *обучение* » в правом верхнем углу. Модель службы будет обучена всеми предоставленными вами образами (что сделает его более точным). После завершения обучения обязательно нажмите кнопку *сделать по умолчанию* , чтобы ваш *прогнозирующий URL-адрес* продолжал использовать самую последнюю итерацию службы.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Законченное приложение API Пользовательское визуальное распознавание

Поздравляем! вы создали приложение для смешанной реальности, которое использует API Azure Пользовательское визуальное распознавание для распознавания реальных объектов, обучения модели службы и получения уверенности в том, что появлялось.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Премиальные упражнения

### <a name="exercise-1"></a>Упражнение 1

Обучить **Пользовательская служба визуального распознавания** для распознавания большего числа объектов.

### <a name="exercise-2"></a>Упражнение 2

Чтобы расширить свои знания, выполните следующие упражнения.

Подавать звуковой сигнал при распознавании объекта.

### <a name="exercise-3"></a>Упражнение 3

Используйте API для переобучения службы с теми же изображениями, которые анализирует приложение, чтобы сделать службу более точной (одновременное прогнозирование и обучение).
