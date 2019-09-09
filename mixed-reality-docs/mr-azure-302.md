---
title: MR и Azure 302 — компьютерное зрение
description: Пройдите этот курс, чтобы узнать, как распознать визуальное содержимое в предоставленном образе с помощью Компьютерное зрение Azure в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, компьютерное зрение, hololens, иммерсивное, VR
ms.openlocfilehash: 9cc526afdc36b8056afd61948fea5cf98015bb35
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047196"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR и Azure 302: Компьютерное зрение

В этом курсе вы узнаете, как распознать визуальное содержимое в предоставленном образе, используя возможности Компьютерное зрение Azure в приложении смешанной реальности.

Результаты распознавания будут отображаться в виде описательных тегов. Эту службу можно использовать без обучения модели машинного обучения. Если для реализации требуется обучение модели машинного обучения, см. статью [MR and Azure 302B](mr-azure-302b.md).

![результат лаборатории](images/AzureLabs-Lab2-000.png)

Microsoft Компьютерное зрение — это набор интерфейсов API, предназначенных для предоставления разработчикам возможности обработки и анализа изображений (с возвращаемыми сведениями) с использованием расширенных алгоритмов из облака. Разработчики отправляют URL-адрес образа или изображения, а алгоритмы Microsoft API компьютерного зрения анализируют визуальное содержимое на основе входных данных, выбранных пользователем, которые затем могут возвращать информацию, в том числе определение типа и качества изображения, обнаружение людей-лиц ( Возврат координат), добавление тегов или категоризация изображений. Дополнительные сведения см. на [странице API компьютерного зрения Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Прополнив этот курс, вы получите приложение HoloLens для смешанной реальности, которое сможет сделать следующее:

1.  С помощью жеста касания Камера HoloLens захватывает изображение.
2.  Образ будет отправлен в службу API компьютерного зрения Azure. 
3.  Распознанные объекты будут перечислены в простой группе пользовательского интерфейса, расположенной в сцене Unity.

В приложении вы будете выполнять интеграцию результатов с вашей структурой. Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity. Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> MR и Azure 302: Компьютерное зрение</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс в основном ориентирован на HoloLens, вы можете также применить сведения, которые вы узнаете в этом курсе, к головным телефонам Windows Mixed Reality (VR). Так как у головных гарнитур нет доступных камер, вам потребуется внешняя камера, подключенная к компьютеру. При работе с курсом вы увидите заметки о любых изменениях, которые могут потребоваться для поддержки головных телефонов (VR).

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#. Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018). Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.

Для этого курса рекомендуется следующее оборудование и программное обеспечение:

- ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)
- [Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK для Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Камера, подключенная к компьютеру (для разработки в увлекательной гарнитуре)
- Доступ к Интернету для установки Azure и извлечения API компьютерного зрения

## <a name="before-you-start"></a>Перед началом

1.  Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).
2.  Настройка и тестирование HoloLens. Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя). 

Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).

Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Глава 1 — портал Azure

Чтобы использовать службу *API компьютерного зрения* в Azure, необходимо настроить экземпляр службы, чтобы сделать ее доступной для приложения.

1.  Сначала войдите на [портал Azure](https://portal.azure.com). 

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо создать ее. Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.

2.  Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу, найдите *API компьютерного зрения*и нажмите клавишу **Ввод**.

    ![Создание нового ресурса в Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > Слово **New** может быть заменено на **создать ресурс**в новых порталах.
 
3.  На новой странице будет представлено описание службы *API компьютерного зрения* . В нижнем левом углу этой страницы нажмите кнопку **создать** , чтобы создать связь с этой службой.

    ![Сведения о службе API компьютерного зрения](images/AzureLabs-Lab2-01.png)
 
4.  После нажатия кнопки **создать**:

    1. Вставьте нужное **имя** для этого экземпляра службы.
    2. Выберите **подписку**.
    3. Выберите **ценовую категорию** , подходящую для вас. Если вы впервые создаете службу *API компьютерного зрения* , вам будет доступен бесплатный уровень (с именем F0).
    4. Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure. Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов. 

        > Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Определите расположение группы ресурсов (при создании новой группы ресурсов). В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение. Некоторые ресурсы Azure доступны только в определенных регионах.

    6. Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.
    7. Нажмите кнопку Создать.

        ![Сведения о создании службы](images/AzureLabs-Lab2-02.png)

5.  После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.
6.  После создания экземпляра службы на портале отобразится уведомление.

    ![Просмотреть новое уведомление для новой службы](images/AzureLabs-Lab2-03.png) 
 
7.  Щелкните уведомление, чтобы просмотреть новый экземпляр службы. 

    ![Нажмите кнопку Переход к ресурсу.](images/AzureLabs-Lab2-04.png)
 
8. Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы. Вы будете перенаправлены на новый экземпляр службы API компьютерного зрения. 

    ![Новая служба API компьютерного зрения](images/AzureLabs-Lab2-05.png)
 
9.  В рамках этого руководства приложение должно будет вызывать службу, что выполняется с помощью ключа подписки вашей службы.
10. На странице *Быстрый запуск* службы *API компьютерного зрения* , перейдите к первому шагу, *Возьмите ключи*и щелкните **ключи** (это можно также сделать, щелкнув синие клавиши-гиперссылки, расположенные в меню навигации службы. отмечается значком ключа). При этом будут раскрыты *ключи*службы.
11. Сделайте копию одного из отображаемых ключей, так как это потребуется позже в проекте. 

12. Вернитесь на страницу *быстрого запуска* и извлеките конечную точку. Имейте в виду, что в зависимости от региона (что, если это так, вам потребуется внести изменения в код), это может быть иначе. Создать копию этой конечной точки для последующего использования:

    ![Новая служба API компьютерного зрения](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Вы можете проверить, какие конечные точки находятся [здесь](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). 

## <a name="chapter-2--set-up-the-unity-project"></a>Глава 2 — Настройка проекта Unity

Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.

1.  Откройте *Unity* и нажмите кнопку **создать**. 

    ![Запуск нового проекта Unity.](images/AzureLabs-Lab2-06.png)

2.  Теперь необходимо указать имя проекта Unity. Вставьте **MR_ComputerVision**. Убедитесь, что для типа проекта задано значение **3D**. Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше). Затем нажмите кнопку **создать проект**.

    ![Укажите сведения о новом проекте Unity.](images/AzureLabs-Lab2-07.png)

3.  При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**. Перейдите к разделу **изменение параметров >** , а затем в новом окне перейдите к разделу **Внешние инструменты**. Измените **Редактор внешних скриптов** на **Visual Studio 2017**. Закройте окно **настройки** .

    ![Обновить настройки редактора скриптов.](images/AzureLabs-Lab2-08.png)

4.  Затем перейдите в раздел **файл > параметры сборки** и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.

    ![Окно "параметры сборки". Переключите платформу в UWP.](images/AzureLabs-Lab2-10.png)

5.  Несмотря на то что в **файле > параметры сборки** , убедитесь в том, что:

    1. **Целевое устройство** имеет значение **HoloLens**

        > Для впечатляющих головных телефонов задайте для параметра **целевое устройство** *любое устройство*.

    2. Для **типа сборки** задано значение **D3D**
    3. **Пакет SDK** установлен в значение " **Последняя установка** "
    4. Для **версии Visual Studio** установлено значение " **Последняя установка** "
    5. **Сборка и запуск** настроены на **локальный компьютер**
    6. Сохраните сцену и добавьте ее в сборку.

        1. Для этого выберите **Добавить открытые сцены**. Появится окно сохранения.
        
            ![Нажмите кнопку Добавить кнопку "открыть сцены"](images/AzureLabs-Lab2-11.png)

        2. Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».

            ![Создать новую папку скриптов](images/AzureLabs-Lab2-12.png)

        3. Откройте только что созданную папку **сцены** , а затем в поле *имя файла*: введите **MR_ComputerVisionScene**, а затем нажмите кнопку **сохранить**.

            ![Присвойте имя новой сцене.](images/AzureLabs-Lab2-13.png)

            > Помните, что сцены Unity необходимо сохранять в папке *Assets* , так как они должны быть связаны с проектом Unity. Создание папки «сцены» (и других аналогичных папок) — типичный способ структуризации проекта Unity.

    7. Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.

6. В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* . 

    ![Откройте параметры проигрывателя.](images/AzureLabs-Lab2-14.png)

7. На этой панели необходимо проверить несколько параметров:

    1. На вкладке **другие параметры** выполните следующие действия.

        1. **Версия среды выполнения сценариев** должна быть **стабильной** (эквивалент .NET 3,5).
        2. **Серверная часть сценариев** должна быть **.NET**
        3. **Уровень совместимости API** должен быть **.NET 4,6**

            ![Обновите другие параметры.](images/AzureLabs-Lab2-15.png)
      
    2. На вкладке **Параметры публикации** в разделе **возможности**установите флажок:

        1. **InternetClient**
        2. **Бесед**

            ![Обновляются параметры публикации.](images/AzureLabs-Lab2-16.png)

    3. На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .

        ![Обновите параметры X R.](images/AzureLabs-Lab2-17.png)

8.  Назад в *параметрах сборки* проект _Unity C#_  больше не является серым. Установите флажок рядом с этим. 
9.  Закройте окно параметры сборки.
10. Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).

## <a name="chapter-3--main-camera-setup"></a>Глава 3 — Настройка основной камеры

> [!IMPORTANT]
> Если вы хотите пропустить компонент *установки Unity, установленный* в этом курсе, и продолжить работу с кодом, скачайте этот файл [. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), импортируйте его в проект как [пользовательский пакет](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в [главе 5](#chapter-5--create-the-resultslabel-class).

1.  На *панели Иерархия*выберите **основную камеру**. 
2.  После выбора вы сможете увидеть все компоненты **основной камеры** на *панели инспектора*.

    1. **Объект Camera** должен называться **основной камерой** (Обратите внимание на орфографию!)
    2. Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на правописание).
    3. Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .
    4. Установите для параметра **сбросить флаги** **сплошной цвет** (не обращайте внимания на иммерсивное гарнитуру).
    5. Задайте черный цвет **фона** для компонента камеры **, альфа-канал 0 (шестнадцатеричный код: #00000000)** (не учитывать это для иммерсивного головного телефона).

        ![Обновите компоненты камеры.](images/AzureLabs-Lab2-18.png)
 
3.  Далее необходимо создать простой объект Cursor, присоединенный к **основной камере**, который поможет разместить выходные данные анализа изображений во время работы приложения. Этот курсор определит центральную точку фокуса камеры.

Чтобы создать курсор, сделайте следующее:

1.  На *панели Иерархия*щелкните правой кнопкой мыши **основную камеру**. В разделе **3D-объект**щелкните **Sphere**.

    ![Выберите объект курсора.](images/AzureLabs-Lab2-19.png)
 
2.  Переименуйте **сферу** в **курсор** (дважды щелкните объект курсора или нажмите клавишу "F2" с выделенным объектом) и убедитесь, что он находится в качестве дочернего элемента **основной камеры**.

3.  На *панели Иерархия*щелкните **курсор**левой кнопкой мыши. Выбрав курсор, измените следующие переменные на *панели инспектора*:

    1. Установить для параметра " *Преобразование* " значение **0, 0, 5**
    2. Установите *масштаб* **0,02, 0,02, 0,02**

        ![Обновите расположение и масштаб преобразования.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Глава 4 — Настройка системы меток

После записи образа с камерой HoloLens этот образ будет отправлен в экземпляр службы *API компьютерного зрения Azure* для анализа. 

Результаты этого анализа будут представлять собой список распознаваемых объектов, именуемых **тегами**. 

Для отображения этих тегов в месте, где была создана фотография, будут использоваться метки (в виде трехмерного текста в мировом пространстве).

В следующих шагах показано, как настроить объект **Label** .

1.  Щелкните правой кнопкой мыши в любом месте панели Иерархия (расположение не имеет значения), в разделе **трехмерный объект**добавьте **трехмерный текст**. Назовите его **LabelText**.

    ![Создание трехмерного текстового объекта.](images/AzureLabs-Lab2-21.png)
 
2.  На *панели Иерархия*щелкните **LabelText**. Выбрав **LabelText** , настройте следующие переменные на *панели инспектора*:

    1. Установить значение **0, 0,** 0
    2. Установите **масштаб** **0,01, 0,01, 0,01**
    3. В **сетке текста**компонента:
    4. Замените весь текст в **тексте**на "..."        
    5. Установить **привязку** к **середине по центру**
    6. Задать **Выравнивание** по **центру**
    7. Установите **размер табуляции** **4**
    8. Задайте **Размер шрифта** **50**
    9. Задать **Цвет** для **#FFFFFFFF**

    ![Компонент текста](images/AzureLabs-Lab2-21-5.png)

3.  Перетащите **LabelText** из *панели Иерархия*в *папку Asset*на *панели проект*. Это сделает **LabelText** prefab, чтобы его можно было создать в коде.

    ![Создайте prefab объекта LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  Необходимо удалить **LabelText** с *панели Иерархия*, чтобы она не отображалась в открывающей сцене. Так как теперь это prefab, который будет вызываться для отдельных экземпляров из папки Assets, не нужно размещать его в сцене. 
5.  Итоговая структура объектов на *панели Иерархия* должна выглядеть так, как показано на рисунке ниже:

    ![Окончательная структура панели иерархии.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Глава 5 — Создание класса Ресултслабел

Первый скрипт, который необходимо создать, — это класс *ресултслабел* , который отвечает за следующее: 

- Создание меток в соответствующем мировом пространстве относительно положения камеры.
- Отображение тегов из изображения устраняйте.

Чтобы создать этот класс, сделайте следующее: 

1.  Щелкните правой кнопкой мыши на *панели проект*, а затем **Создайте > папку**. Назовите папку **Scripts**. 

    ![Создайте папку Scripts.](images/AzureLabs-Lab2-24.png)

2.  Создав папку **Scripts** , дважды щелкните ее, чтобы открыть. Затем в этой папке щелкните правой кнопкой мыши и выберите **Создать >** затем  **C# сценарий**. Назовите сценарий *ресултслабел*. 

3.  Дважды щелкните новый скрипт *ресултслабел* , чтобы открыть его в **Visual Studio**.

4.  Внутри класса вставьте следующий код в класс *ресултслабел* :

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

6.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.
7.  В *редакторе Unity*щелкните и перетащите класс *Ресултслабел* из папки **сценарии** в объект **Main** на *панели Иерархия*.
8.  Щелкните **основную камеру** и посмотрите на *Панель инспектора*.

Вы заметите, что из скрипта, который вы только что переместили в камеру, есть два поля: **Курсор** и **Метка prefab**.

9.  Перетащите объект с именем **cursor** с *панели иерархий* в область **курсора**, как показано на рисунке ниже.
10. Перетащите объект с именем **LabelText** из *папки Assets (ресурсы* ) на *панели проекта* в гнездо с именем **Label prefab**, как показано на рисунке ниже. 

    ![Установите целевые объекты ссылок в Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Глава 6 — создание класса Имажекаптуре

Следующий класс, который предстоит создать, — это класс *имажекаптуре* . Этот класс отвечает за:

-   Запись изображения с помощью камеры HoloLens и сохранение его в папке приложения.
-   Захват жестов касания от пользователя.

Чтобы создать этот класс, сделайте следующее: 

1.  Перейдите к созданной ранее папке **Scripts** . 
2.  Щелкните правой кнопкой мыши внутри папки, **Создайте скрипт C# >** . Вызовите скрипт *имажекаптуре*. 
3.  Дважды щелкните новый скрипт *имажекаптуре* , чтобы открыть его в **Visual Studio**.
4.  Добавьте следующие пространства имен в начало файла:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Затем добавьте следующие переменные в класс *имажекаптуре* над методом *Start ()* :

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
Переменная **тапскаунт** сохранит количество жестов касаний, полученных от пользователя. Этот номер используется в именах захваченных образов.

6.  Теперь необходимо добавить код для методов *"спящий" ()* и *"начало" ()* . Они будут вызываться при инициализации класса:

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
 
Метод *тафандлер ()* увеличивает число касаний, полученных от пользователя, и использует текущую позицию курсора для определения места размещения новой метки.

Затем этот метод вызывает метод *ексекутеимажекаптуреанданалисис ()* , чтобы начать основные функциональные возможности этого приложения.

8.  После записи и сохранения образа будут вызваны следующие обработчики. Если процесс выполнен успешно, результат передается в *висионманажер* (который еще создается) для анализа.

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
 
9.  Затем добавьте метод, используемый приложением для запуска процесса записи образа и сохранения образа.

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
> На этом этапе вы увидите ошибку на *панели консоли редактора Unity*. Это обусловлено тем, что код ссылается на класс *висионманажер* , который будет создан в следующей главе.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Глава 7 — вызов Azure и анализ изображений

Последним скриптом, который необходимо создать, является класс *висионманажер* . 

Этот класс отвечает за:

-   Загрузка последнего образа, записанного в виде массива байтов.
-   Отправка массива байтов в экземпляр службы *API компьютерного зрения Azure* для анализа.
-   Получение ответа в виде строки JSON.
-   Десериализация ответа и передача результирующих тегов классу *ресултслабел* .
 
Чтобы создать этот класс, сделайте следующее:

1.  Дважды щелкните папку **Scripts** , чтобы открыть ее. 
2.  Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать C# > скрипт**. Назовите сценарий *висионманажер*. 
3.  Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.
4.  Обновите пространства имен, как показано ниже, в верхней части класса *висионманажер* :

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  В верхней части скрипта, *внутри* класса *висионманажер* (над методом *Start ()* ), теперь необходимо создать два *класса* , которые будут представлять Десериализованный ответ JSON из Azure:

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
    > В классах *тагдата* и *аналиседобжект* должен быть добавлен атрибут *[System. Serializable]* , прежде чем объявление может быть десериализовано с помощью библиотек Unity.

6.  В классе Висионманажер следует добавить следующие переменные:

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
    > Убедитесь, что **ключ проверки подлинности** вставлен в переменную **authorizationkey согласно инструкциям** . Вы заговорили **ключ проверки подлинности** в начале этого курса, [раздел 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > Переменная **висионаналисисендпоинт** может отличаться от той, которая указана в этом примере. **Западная часть США** относится к экземплярам службы, созданным для региона "Западная часть США". Обновите его, указав [URL-адрес конечной точки](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). Вот несколько примеров того, что может выглядеть:
    > - Западная Европа:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Юго-Восточная Азия:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Восточная Австралия:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Теперь необходимо добавить код для спящего режима. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Затем добавьте соподпрограмму (с помощью метода статического потока ниже), который будет получать результаты анализа изображения, захваченного классом *имажекаптуре* . 

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

9.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.
10. В редакторе Unity щелкните и перетащите классы *висионманажер* и *Имажекаптуре* из папки **сценарии** в **основной объект Camera** на *панели Иерархия*. 

## <a name="chapter-8--before-building"></a>Глава 8 – перед сборкой

Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на HoloLens.
Перед этим убедитесь в том, что:

-   Все параметры, упомянутые в [главе 2](#chapter-2--set-up-the-unity-project) , заданы правильно. 
-   Все скрипты присоединяются к **главному объекту Camera** . 
-   Все поля на *панели инспектора основной камеры* назначены должным образом.
-   Убедитесь, что **ключ проверки подлинности** вставлен в переменную **authorizationkey согласно инструкциям** .
-   Убедитесь, что вы также проверили конечную точку в сценарии *висионманажер* и соответствуете *региону (в этом* документе по умолчанию используется *Запад-US* ).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Глава 9 — Создание решения UWP и загружать неопубликованные приложения
Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.

1.  Выберите файл *Параметры* - сборки **> параметры сборки...**
2.  В окне " *параметры сборки* " щелкните **Сборка**.

    ![Создание приложения из Unity](images/AzureLabs-Lab2-26.png)

3.  Если это еще не так, то проекты Ticks **Unity C#** .
4.  Щелкните **Сборка**. Unity запустит окно *проводника* , в котором необходимо создать, а затем выбрать папку для сборки приложения. Создайте эту папку сейчас и назовите ее *app*Name. Затем выберите папку *приложения* и нажмите кнопку **выбрать папку**. 
5.  Unity начнет сборку проекта в папку *приложения* . 
6.  После того как Unity завершит сборку (может занять некоторое время), он откроет окно *проводника* в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).

## <a name="chapter-10--deploy-to-hololens"></a>Глава 10 — развертывание в HoloLens

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

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Перейдите в **меню "сборка** " и щелкните " **Развернуть решение**", чтобы загружать неопубликованные приложение в HoloLens.
6.  Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.

> [!NOTE]
> Чтобы выполнить развертывание в иммерсивное *виртуальную*гарнитуру, задайте для **платформы решения** значение локальный компьютер и задайте для параметра **Конфигурация** значение *Отладка*( *x86* в качестве **платформы**). Затем выполните развертывание на локальном компьютере с помощью **меню "сборка**" и выберите пункт " *Развернуть решение*". 

## <a name="your-finished-computer-vision-api-application"></a>Законченное API компьютерного зрения приложение

Поздравляем! вы создали приложение смешанной реальности, которое использует API компьютерного зрения Azure для распознавания реальных объектов и отображает уверенность в том, что было обнаружено.

![результат лаборатории](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Премиальные упражнения

### <a name="exercise-1"></a>Упражнение 1

Так же, как вы использовали параметр *Tags* (как свидетельствует в *конечной точке* , используемой в *висионманажер*), расширьте приложение, чтобы обнаружить другие сведения. Ознакомьтесь с другими параметрами [, к которым](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)у вас есть доступ.

### <a name="exercise-2"></a>Упражнение 2

Отображение возвращенных данных Azure в более удобном для общения и удобочитаемом виде, возможно, скрытия чисел. Хотя робот может говорить пользователю.
