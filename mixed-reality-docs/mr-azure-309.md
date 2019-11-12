---
title: MR и Azure 309 — Application Insights
description: Пройдите этот курс, чтобы узнать, как собираются аналитики в отношении поведения пользователей в приложении смешанной реальности с помощью службы Application Insights Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, Application Insights, hololens, иммерсивное, VR
ms.openlocfilehash: 481fe3fc16ada06085a64c86867a1a892c76f2ad
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926897"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR и Azure 309: Application Insights

![окончательный продукт — запуск](images/AzureLabs-Lab309-00.png)

В этом курсе вы узнаете, как добавлять Application Insights возможности в приложение смешанной реальности с помощью API Application Insights Azure для получения сведений о поведении пользователей.

Application Insights — это служба Майкрософт, позволяющая разработчикам получать аналитические средства из своих приложений и управлять ими с помощью простого в использовании портала. Аналитика может представлять собой любое значение от производительности до настраиваемой информации, которую вы хотите получить. Дополнительные сведения см. на [странице Application Insights](https://azure.microsoft.com/services/application-insights/).

Прополнив этот курс, вы получите иммерсивное приложение для наушников, которое сможет сделать следующее:

1.  Позволяет пользователю взходить и перемещаться по сцене.
2.  Активируйте отправку аналитики в *службу Application Insights*, используя взгляд и близость к объектам в сцене.
3.  Приложение также будет вызывать службу, получая сведения о том, какой объект приближается к большинству пользователей, за последние 24 часа. Этот объект изменит свой цвет на зеленый.

В этом курсе вы узнаете, как получить результаты из службы Application Insights в примере приложения на основе Unity. Вы сможете применить эти понятия к настраиваемому приложению, которое вы можете собрать.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> MR и Azure 309: Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Хотя этот курс в основном ориентирован на гарнитуры Windows Mixed Reality (VR), вы также можете применить сведения, которые вы узнаете в этом курсе, к Microsoft HoloLens. Как вы пройдете вместе с курсом, вы увидите примечания о любых изменениях, которые могут потребоваться для поддержки HoloLens. При использовании HoloLens вы можете заметить некоторые эхо во время записи голоса.

## <a name="prerequisites"></a>Необходимые условия

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#. Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018). Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.

Для этого курса рекомендуется следующее оборудование и программное обеспечение:

- ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)
- [Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика](install-the-tools.md#installation-checklist)
- [Последний пакет SDK для Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика
- Набор наушников со встроенным микрофоном (если у гарнитуры нет встроенного микрофона и динамиков);
- Доступ к Интернету для установки Azure и Application Insights получение данных

## <a name="before-you-start"></a>Прежде чем начать

Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).

> [!WARNING] 
> Помните, что *Application Insights* данных занимает время, поэтому подождите. Если вы хотите проверить, получит ли служба ваши данные, ознакомьтесь с [главой 14](#chapter-14---the-application-insights-service-portal), в которой показано, как перемещаться по порталу.

## <a name="chapter-1---the-azure-portal"></a>Глава 1. портал Azure

Чтобы использовать *Application Insights*, необходимо создать и настроить *службу Application Insights* в портал Azure.

1.  Войдите на [портал Azure](https://portal.azure.com).

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, необходимо создать ее. Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.

2.  Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу, найдите *Application Insights*и нажмите клавишу **Ввод**.

    > [!NOTE]
    > Слово **New** может быть заменено на **создать ресурс**в новых порталах.

    ![Портал Azure](images/AzureLabs-Lab309-01.png)

3.  На новой странице справа будет представлено описание службы *Application Insights Azure* . В нижнем левом углу этой страницы нажмите кнопку **создать** , чтобы создать связь с этой службой.

    ![Портал Azure](images/AzureLabs-Lab309-02.png)

4.  После нажатия кнопки **создать**:

    1.  Вставьте нужное **имя** для этого экземпляра службы.

    2.  В качестве **типа приложения**выберите **Общие**.

    3.  Выберите подходящую **подписку**.

    4.  Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure. Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.

        > Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Выберите **Расположение**.

    6.  Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.

    7.  Щелкните **Создать**.

        ![Портал Azure](images/AzureLabs-Lab309-03.png)

5.  После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.

6.  После создания экземпляра службы на портале отобразится уведомление.

    ![Портал Azure](images/AzureLabs-Lab309-04.png)

7.  Щелкните уведомления, чтобы изучить новый экземпляр службы.

    ![Портал Azure](images/AzureLabs-Lab309-05.png)

8.  Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы. Вы будете перенаправлены на новый экземпляр *службы Application Insights* .

    ![Портал Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Не открывайте эту веб-страницу и легко получайте к ней доступ. чтобы увидеть собранные данные, вы будете регулярно возвращаться.

    > [!IMPORTANT]
    > Чтобы реализовать Application Insights, необходимо использовать три (3) конкретных значения: **ключ инструментирования**, **идентификатор приложения**и **ключ API**. Ниже вы узнаете, как получить эти значения из службы. Обязательно запишите эти значения на пустой странице *блокнота* , так как они будут использоваться в коде в ближайшее время.

9.  Чтобы найти **ключ инструментирования**, необходимо прокрутить список функций службы и выбрать пункт **свойства**. на вкладке отобразится **ключ службы**.

    ![Портал Azure](images/AzureLabs-Lab309-07.png)

10. Немного ниже **свойств**вы найдете **доступ к API**, который нужно щелкнуть. Панель справа предоставит **идентификатор приложения** .

    ![Портал Azure](images/AzureLabs-Lab309-08.png)

11. Если панель **идентификатор приложения** все еще открыта, нажмите кнопку **создать ключ API**, которая откроет панель *создать ключ API* .

    ![Портал Azure](images/AzureLabs-Lab309-09.png)

12. На панели теперь откройте *Создание ключа API* , введите описание и укажите **три поля**.

13. Нажмите кнопку **создать ключ**. Ваш **ключ API** будет создан и отображен. 

    ![Портал Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Это единственный момент, когда ваш **ключ службы** будет отображаться, поэтому убедитесь, что вы создали его копию.

## <a name="chapter-2---set-up-the-unity-project"></a>Глава 2. Настройка проекта Unity

Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.

1.  Откройте *Unity* и нажмите кнопку **создать**.

    ![Настройка проекта Unity](images/AzureLabs-Lab309-11.png)

2.  Теперь необходимо указать имя проекта Unity, вставить **MR\_Azure\_Application insights\_** . Убедитесь, что для *шаблона* задано значение **3D**. Задайте для *расположения нужное расположение* (Помните, что ближе к корневым каталогам лучше). Затем нажмите кнопку **создать проект**.

    ![Настройка проекта Unity](images/AzureLabs-Lab309-12.png)

3.  При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**. Перейдите к разделу **изменение параметров \>** , а затем в новом окне перейдите к разделу **Внешние инструменты**. Измените **Редактор внешних скриптов** на **Visual Studio 2017**. Закройте окно **настройки** .

    ![Настройка проекта Unity](images/AzureLabs-Lab309-13.png)

4.  Затем перейдите в раздел **файл \> параметры сборки** и переключите платформу на **универсальная платформа Windows**, нажав кнопку **коммутатора платформы** .

    ![Настройка проекта Unity](images/AzureLabs-Lab309-14.png)

5.  Перейдите в раздел **файл \> параметры сборки** и убедитесь в том, что:

    1.  **Целевое устройство** настроено для **любого устройства**

        > Для Microsoft HoloLens задайте для параметра **целевое устройство** значение *HoloLens*.

    2.  Для **типа сборки** задано значение **D3D**

    3.  **Пакет SDK** установлен в значение " **Последняя установка** "

    4.  **Сборка и запуск** настроены на **локальный компьютер**

    5.  Сохраните сцену и добавьте ее в сборку.

        1.  Для этого выберите **Добавить открытые сцены**. Появится окно сохранения.

            ![Настройка проекта Unity](images/AzureLabs-Lab309-15.png)

        2. Создайте новую папку для этой и любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее **сцены**.

            ![Настройка проекта Unity](images/AzureLabs-Lab309-16.png)

        3. Откройте только что созданную папку **сцены** , а затем в поле *имя файла:* введите **аппликатионинсигхтссцене**, а затем нажмите кнопку **сохранить**.

            ![Настройка проекта Unity](images/AzureLabs-Lab309-17.png)

6.  Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.

7.  В окне **параметры сборки** нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится **инспектор** .

    ![Настройка проекта Unity](images/AzureLabs-Lab309-18.png)

8. На этой панели необходимо проверить несколько параметров:

    1.  На вкладке **другие параметры** выполните следующие действия.

        1.  **Версия среды выполнения** сценариев должна быть **экспериментальной (эквивалент .NET 4,6)** , что вызовет необходимость перезапуска редактора.

        2.  **Серверная часть сценариев** должна быть **.NET**

        3.  **Уровень совместимости API** должен быть **.NET 4,6**

        ![Настройка проекта Unity](images/AzureLabs-Lab309-19.png)

    2.  На вкладке **Параметры публикации** в разделе **возможности**установите флажок:

        - **InternetClient**     

            ![Настройка проекта Unity](images/AzureLabs-Lab309-20.png)

    3.  На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .

        ![Настройка проекта Unity](images/AzureLabs-Lab309-21.png)

9.  Вернувшись в **параметры сборки**, **проекты C# Unity** больше не заключаются. Установите флажок рядом с этим.

10.  Закройте окно параметры сборки.

11.  Сохраните сцену и проект (**файл** > **сохранить сцену или файл** > **сохранить проект**).


## <a name="chapter-3---import-the-unity-package"></a>Глава 3. Импорт пакета Unity

> [!IMPORTANT]
> Если вы хотите пропустить *настройку Unity, настроили* компоненты этого курса, и продолжить работу с кодом, скачайте этот пакет [Azure-MR-309. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html). Это также будет содержать библиотеки DLL из следующей главы. После импорта продолжите работу в [**главе 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Чтобы использовать Application Insights в Unity, необходимо импортировать библиотеку DLL для нее вместе с библиотекой DLL Newtonsoft. В Unity существует известная ошибка, которая требует перенастройки подключаемых модулей после импорта. Эти действия (4-7 в этом разделе) больше не понадобятся после устранения ошибки.

Чтобы импортировать Application Insights в свой проект, убедитесь, что вы [скачали файл ". пакет unitypackage", содержащий подключаемые модули](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). Затем выполните следующие действия.

1.  Добавьте **. пакет unitypackage** в Unity с помощью параметра **активы \> импорт пакета \> настраиваемый пакет** меню.

2.  В появившемся окне **Импорт пакета Unity** убедитесь, что выбраны все компоненты **подключаемых модулей** (включая).

    ![Импорт пакета Unity](images/AzureLabs-Lab309-22.png)

3.  Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.

4.  Перейдите в папку **Insights** в разделе **подключаемые модули** в представлении проекта и выберите *только*следующие подключаемые модули:

    -   Microsoft. ApplicationInsights

    ![Импорт пакета Unity](images/AzureLabs-Lab309-23.png)

5.  Выбрав этот *подключаемый модуль* , убедитесь, что **все платформы** **не установлены**, убедитесь, что флажок **всаплайер** также не **установлен**, а затем нажмите кнопку **Применить**. Для этого нужно убедиться, что файлы настроены правильно.

    ![Импорт пакета Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Пометив подключаемые модули подобным образом, настройте их для использования только в редакторе Unity. В папке WSA имеется другой набор библиотек DLL, который будет использоваться после экспорта проекта из Unity.

6.  Далее необходимо открыть папку **WSA** в папке **Insights** . Вы увидите копию того же файла, который вы только что настроили. Выберите этот файл, а затем в инспекторе убедитесь, что **все платформы** неустановлены, убедитесь, что **установлен**флажок **только** **всаплайер** . Щелкните **Применить**.

    ![Импорт пакета Unity](images/AzureLabs-Lab309-25.png)

7. Теперь необходимо выполнить **шаги 4-6**, но для подключаемых модулей *Newtonsoft* . На снимке экрана ниже показано, как должен выглядеть результат.

    ![Импорт пакета Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Глава 4. Настройка камеры и пользовательских элементов управления

В этой главе будет настроена камера и элементы управления, позволяющие пользователю просматривать и перемещать сцену.

1.  Щелкните правой кнопкой мыши пустую область на панели Иерархия, а затем в поле **создать** > **пусто**.

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-26.png)

2.  Переименуйте новый пустой GameObject в **родительский элемент Camera**.

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-27.png)

3.  Щелкните правой кнопкой мыши пустую область на панели Иерархия, затем на **трехмерном объекте**, а затем в **сфере**.

4.  Переименуйте сферу в **правой части**.

5.  Задайте **Масштаб преобразования** правой части в **0,1, 0,1, 0,1**

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-28.png)

6.  Удалите компонент " **Сфера" сферы Sphere** с правой стороны, щелкнув **шестеренку** в компоненте " *Сфера" сферы* , а затем **удалив компонент**.

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-29.png)

7.  На панели Иерархия перетащите **основную камеру** и **правой рукой** объекты на **родительский объект Camera** .

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-30.png)

8.  Задайте для параметра **Расположение преобразования** как для **основной камеры** , так и для **правой стороны** объекта значение **0, 0, 0**.

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-31.png)

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Глава 5. Настройка объектов в сцене Unity

Теперь вы создадите базовые фигуры для сцены, с которыми может взаимодействовать пользователь.

1.  Щелкните правой кнопкой мыши пустую область на *панели Иерархия*, затем на **трехмерном объекте**, а затем выберите **плоскость**.

2.  Установите для параметра **Расположение преобразования** плоскости значение **0,-1, 0**.

3.  Установите **шкалу преобразования** плоскости в значение **5, 1, 5**.

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-33.png)

4.  Создайте базовый материал для использования с объектом **плоскости** , чтобы сделать другие фигуры более удобными для просмотра. Перейдите на *Панель проекта*, щелкните правой кнопкой мыши, а затем выберите **создать**, а затем — **Папка**, чтобы создать новую папку. Назовите **материалы**IT.

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-34.png) ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-35.png)

5.  Откройте папку **материалы** , щелкните правой кнопкой мыши, выберите **создать**, а затем — **материал**, чтобы создать новый материал. Назовите его **Blue**.

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-36.png) ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-37.png)

6.  Выбрав новый **синий** материал, Взгляните на *инспектор*и щелкните прямоугольное окно рядом с **албедо**. Выберите синий цвет (на рисунке ниже показан **шестнадцатеричный цвет: \#3592FFFF**). После выбора нажмите кнопку Закрыть.

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-38.png)

7.  Перетащите новый материал из папки **материалы** в созданную **плоскость**на сцене (или перетащите ее на объект **плоскости** в *иерархии*).

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-39.png)

8.  Щелкните правой кнопкой мыши пустую область на *панели Иерархия*, а затем на **трехмерном объекте, капсула**.

    -  Выбрав **капсулу** , **измените ее** *Расположение* на: **-10, 1, 0**.

9.  Щелкните правой кнопкой мыши пустую область на *панели Иерархия*, а затем выберите **трехмерный объект куб**.

    -  Выбрав **куб** , измените его *Расположение* **преобразования** на: **0, 0, 10**.

10. Щелкните правой кнопкой мыши пустую область на *панели Иерархия*, а затем на **трехмерном объекте, Sphere**.

    -  Выбрав **сферу** , **измените ее** *Расположение* на: **10, 0, 0**.

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Эти значения *позиций* являются *предложениями*. Вы можете устанавливать позиции объектов в соответствии с любыми требованиями, хотя это и проще для пользователей приложения, если расстояния между объектами не слишком далеко от камеры.

11. Когда приложение работает, оно должно иметь возможность определять объекты в сцене, чтобы добиться этого, они должны быть помечены тегами. Выберите один из объектов и на панели *инспектора* щелкните **Добавить тег...** , который заменит *инспектор* **тегами & слоями** .

    ![настроить объекты в сцене Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. Щелкните символ **+ (плюс)** , а затем введите имя тега **обжектинсцене**.

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Если вы используете другое имя для тега, необходимо *убедиться, что*это изменение также стало *датафроманалитикс*, *обжекттригжер*и скриптом позже, чтобы объекты были найдены и обнаружены в сцене.

13. Теперь, когда тег создан, необходимо применить его ко всем трем объектам. В *иерархии*удерживайте клавишу **SHIFT** , затем щелкните **капсулу**, **куб**и **сферу**, объекты, затем в *инспекторе*щелкните раскрывающееся меню рядом с **тегом**, а затем щелкните созданный тег *обжектинсцене* .

    ![настроить объекты в сцене Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Глава 6. Создание класса Аппликатионинсигхтстраккер

Первый скрипт, который необходимо создать, — это **аппликатионинсигхтстраккер**, который отвечает за:

1.  Создание событий на основе взаимодействия пользователя для отправки в Azure Application Insights.

2. Создание подходящих имен событий в зависимости от взаимодействия с пользователем.

3. Отправка событий в экземпляр службы Application Insights.

Чтобы создать этот класс, сделайте следующее:

1.  Щелкните правой кнопкой мыши на *панели проект*, а затем **Создайте** > **папку**. Назовите папку **Scripts**.

    ![Создание класса Аппликатионинсигхтстраккер](images/AzureLabs-Lab309-46.png)  ![Создание класса Аппликатионинсигхтстраккер](images/AzureLabs-Lab309-47.png)

2.  После создания папки **Scripts (скрипты** ) дважды щелкните ее, чтобы открыть. Затем в этой папке щелкните правой кнопкой мыши, **Создайте** >  **C# скрипт**. Назовите сценарий **аппликатионинсигхтстраккер**.

3.  Дважды щелкните новый скрипт **аппликатионинсигхтстраккер** , чтобы открыть его в **Visual Studio**.

4.  Обновите пространства имен в верхней части скрипта следующим образом:

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
    > Установите значения **instrumentationKey, applicationId и API_Key** соответствующим образом, используя *ключи службы* на портале Azure, как упоминалось в [главе 1](#chapter-1---the-azure-portal), шаг 9.

6.  Затем добавьте методы **Start ()** и **спящего режима ()** , которые будут вызываться при инициализации класса:

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

7.  Добавьте методы, отвечающие за отправку событий и метрик, зарегистрированных в приложении:

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

8.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-7---create-the-gaze-script"></a>Глава 7. Создание скрипта «взгляд»

Следующий скрипт для создания — это скрипт « **взгляд** ». Этот сценарий отвечает за создание *райкаст* , который будет проецирован вперед с *основной камеры*для определения объекта, на котором пользователь смотрит. В этом случае *райкаст* должен выяснить, просматривает ли пользователь объект с тегом **обжектинсцене** , а затем подсчитать, как *долго пользователь смотрит* на этот объект.

1.  Дважды щелкните папку **Scripts** , чтобы открыть ее.

2.  Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать** >  **C# скрипт**. Присвойте скрипту имя « **взгляд**».

3.  Дважды щелкните скрипт, чтобы открыть его в Visual Studio.

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

5.  Теперь необходимо добавить код для методов **спящего режима ()** и **Start ()** .

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

6.  В классе **взгляд** добавьте следующий код в метод **Update ()** для проецирования *райкаст* и обнаружения попадания целевого объекта:

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

7.  Добавьте метод **ресетфокуседобжект ()** для отправки данных в **Application Insights** , когда пользователь просматривает объект.

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

8.  Вы завершили выполнение скрипта " **взгляд** ". Сохраните изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Глава 8. Создание класса Обжекттригжер

Следующий сценарий, который необходимо создать, — это **обжекттригжер**, который отвечает за:

- Добавление компонентов, необходимых для конфликта на основной камере.
- Обнаружение того, приближается ли камера к объекту, помеченному как **обжектинсцене**.

Чтобы создать скрипт, выполните следующие действия.

1.  Дважды щелкните папку **Scripts** , чтобы открыть ее.

2.  Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать** >  **C# скрипт**. Назовите сценарий **обжекттригжер**.

3.  Дважды щелкните скрипт, чтобы открыть его в Visual Studio. Замените существующий код следующим:

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

4.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Глава 9. Создание класса Датафроманалитикс

Теперь необходимо создать скрипт **датафроманалитикс** , который отвечает за:

- Получение данных аналитики о том, какой объект использовался камерой в большинстве случаев.
- С помощью *ключей службы*, которые позволяют обмениваться данными с экземпляром службы Application Insights Azure.
- Сортировка объектов в сцене в соответствии с наибольшим числом событий.
- Изменение цвета материала наиболее приближенного объекта на *зеленый*.

Чтобы создать скрипт, выполните следующие действия.

1.  Дважды щелкните папку **Scripts** , чтобы открыть ее.

2.  Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать** >  **C# скрипт**. Назовите сценарий **датафроманалитикс**.

3.  Дважды щелкните скрипт, чтобы открыть его в Visual Studio.

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

6.  В классе **датафроманалитикс** сразу после метода **Start ()** добавьте следующий метод с именем **фетчаналитикс ()** . Этот метод отвечает за заполнение списка пар "ключ-значение" с помощью *GameObject* и количества заполнительных счетчиков событий. Затем он инициализирует соподпрограмму **жетвебрекуест ()** . Структура запроса вызова *Application Insights* можно найти в этом методе также в качестве конечной точки *URL-адреса запроса* .

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

7.  Непосредственно под методом **фетчаналитикс ()** добавьте метод с именем **жетвебрекуест ()** , который возвращает *IEnumerator*. Этот метод отвечает за запрос числа вызовов события, соответствующего определенному *GameObject*, в *Application Insights*. Когда возвращаются все отправленные запросы, вызывается метод **детерминевиннер ()** .

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
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

8.  Следующий метод — **детерминевиннер ()** , который сортирует список пар *GameObject* и *int* в соответствии с наибольшим числом событий. Затем он изменяет цвет материала *GameObject* на *зеленый* (в виде обратной связи с наибольшим числом). Отобразится сообщение с результатами аналитики.

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

9.  Добавьте структуру класса, которая будет использоваться для десериализации объекта JSON, полученного от *Application Insights*. Добавьте эти классы в самом низу файла класса **датафроманалитикс** **за пределами** определения класса.

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

10. Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-10---create-the-movement-class"></a>Глава 10. Создание класса перемещения

Сценарий **перемещения** — это следующий скрипт, который потребуется создать. Он отвечает за следующее:

- Перемещение основной камеры в соответствии с направлением, которое ищет камера.
- Добавление всех других скриптов в объекты сцены.

Чтобы создать скрипт, выполните следующие действия.

1.  Дважды щелкните папку **Scripts** , чтобы открыть ее.

2.  Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать** >  **C# скрипт**. Назовите **Перемещение**скрипта.

3.  Дважды щелкните скрипт, чтобы открыть его в *Visual Studio*.

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

5.  В классе **перемещения** *ниже* пустого метода **Update ()** вставьте следующие методы, позволяющие пользователю использовать контроллер руки для перемещения в виртуальном пространстве:

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

6.  Наконец, добавьте вызов метода в метод **Update ()** .

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Глава 11. Настройка ссылок на скрипты

В этой главе необходимо поместить скрипт **перемещения** на **родительский объект камеры** и задать его ссылки на целевые объекты. Затем этот скрипт будет обрабатывать размещение других сценариев, где они должны быть.

1.  В папке **скрипты** на *панели проекта*перетащите скрипт **перемещения** в **родительский объект Camera** , расположенный на *панели Иерархия*.

    ![Настройка ссылок на скрипты в сцене Unity](images/AzureLabs-Lab309-48.png)

2.  Щелкните **родительский элемент камеры**. На *панели Иерархия*перетащите **правой кнопкой мыши** объект, расположенный на *панели Иерархия* , на целевой объект ссылки, **контроллер**и на *панели инспектора*. Задайте для параметра **скорость пользователя** значение **5**, как показано на рисунке ниже.

    ![Настройка ссылок на скрипты в сцене Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Глава 12. Создание проекта Unity

Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.

1.  Перейдите к **параметрам сборки**(**файл** > **параметры сборки**).

2.  В окне " **параметры сборки** " щелкните **Сборка**.

    ![Создание проекта Unity для решения UWP](images/AzureLabs-Lab309-50.png)

3.  Откроется окно **проводника** , в котором будет предложено ввести расположение для сборки. Создайте новую папку (щелкнув **создать папку** в левом верхнем углу) и назовите ее **Build**.

    ![Создание проекта Unity для решения UWP](images/AzureLabs-Lab309-51.png)

    1.  Откройте папку "новые **сборки** " и создайте другую папку (с помощью **новой папки** еще раз) и назовите ее **MR\_Azure\_Application Insights\_** .

        ![Создание проекта Unity для решения UWP](images/AzureLabs-Lab309-52.png)

    2.  Выбрав папку **\_Azure\_Application\_Insights** , нажмите кнопку **выбрать папку**. Построение проекта займет около минуты.

4.  После *сборки*появится **окно проводника** , в котором отображается расположение нового проекта.

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>Глава 13. Развертывание MR_Azure_Application_Insights приложения на компьютере

Чтобы развернуть приложение **MR\_Azure\_\_Application Insights** на локальном компьютере:

1.  Откройте файл решения **\_Azure\_приложение\_Insights** в **Visual Studio**.

2.  На **платформе решения**выберите **x86, локальный компьютер**.

3.  В **конфигурации решения** выберите **Отладка**.

    ![Создание проекта Unity для решения UWP](images/AzureLabs-Lab309-53.png)

4.  Перейдите в **меню "сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютере.

5.  Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску.

6. Запустите приложение Mixed Reality.

7. Перемещайтесь по сцене, приближению к объектам и просматривая их, когда *служба Azure Insights* собрала достаточно данных событий, она настроит объект, который приближается к зеленому.

> [!IMPORTANT] 
> Хотя среднее время ожидания *событий и метрик* , собираемых службой, занимает около 15 минут, в некоторых случаях может потребоваться до 1 часа.

## <a name="chapter-14---the-application-insights-service-portal"></a>Глава 14. Портал службы Application Insights

После перемещения по сцене и газед на нескольких объектах можно просмотреть данные, собранные на портале *службы Application Insights* .

1.  Вернитесь на портал службы Application Insights.

2.  Щелкните *Обозреватель метрик*.

    ![Просмотр собранных данных](images/AzureLabs-Lab309-54.png)

3.  Он откроется на вкладке, содержащей граф, который представляет *события и метрики* , связанные с приложением. Как упоминалось выше, для отображения данных на диаграмме может потребоваться некоторое время (до 1 часа).

    ![Просмотр собранных данных](images/AzureLabs-Lab309-55.png)

4.  Щелкните *строку событий* в *общем количестве событий* по версии приложения, чтобы просмотреть подробное разбиение событий с их именами.

    ![Просмотр собранных данных](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Завершенное приложение службы Application Insights

Поздравляем, вы создали приложение смешанной реальности, которое использует службу Application Insights для мониторинга активности пользователей в приложении.

![результат курса](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Премиальные упражнения

**Упражнение 1**

Постарайтесь попытаться создать, а не вручную создавать объекты Обжектинсцене и задать их координаты на плоскости в скриптах. Таким образом, можно попросить Azure о том, какой из наиболее популярных объектов был (из результатов поиска или взгляда), и порождать *еще* один из этих объектов.

**Упражнение 2**

Отсортируйте результаты Application Insights по времени, чтобы получить наиболее актуальные данные и реализовать эти данные, учитывающие время, в приложении.

