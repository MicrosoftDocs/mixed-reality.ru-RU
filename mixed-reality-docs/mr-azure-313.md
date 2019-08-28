---
title: MR и Azure 313 — служба центра Интернета вещей
description: Пройдите этот курс, чтобы узнать, как реализовать службу центра Интернета вещей Azure на виртуальной машине под управлением Ubuntu 16,4, а затем визуализировать данные сообщений с помощью Microsoft HoloLens или иммерсивного (VR) гарнитуры.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, ребро, центр Интернета вещей, учебник, API, уведомление, функции, таблицы, hololens, иммерсивное, VR, IOT, виртуальная машина, Ubuntu, Python
ms.openlocfilehash: ec669b799e7c46a9a4ed87674ed78e50f816c9e9
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047245"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

# <a name="mr-and-azure-313-iot-hub-service"></a>MR и Azure 313: Служба центра Интернета вещей

![результат курса](images/AzureLabs-Lab313-00.png)

В этом курсе вы узнаете, как реализовать **службу центра Интернета вещей Azure** на виртуальной машине под управлением операционной системы Ubuntu 16,4. Затем **приложение-функция Azure** будет использоваться для получения сообщений от виртуальной машины Ubuntu и сохранения результатов в **службе таблиц Azure**. Затем вы сможете просматривать эти данные с помощью **Power BI** на гарнитуре Microsoft HoloLens или ИММЕРСИВНОЕ (VR).

Содержимое этого курса применимо к IOT Edgeным устройствам, но в рамках этого курса фокус будет находиться в среде виртуальной машины, поэтому доступ к физическому устройству пограничным устройства не требуется.

Прополнив этот курс, вы научитесь:

- Разверните **модуль IOT Edge** на виртуальной машине (Ubuntu 16 OS), которая будет представлять ваше устройство Интернета вещей.
- Добавьте **модель Tensorflow Azure пользовательское визуальное распознавание** в модуль ребра с кодом, который будет анализировать изображения, хранящиеся в контейнере.
- Настройте модуль для отправки сообщения результатов анализа обратно в **службу центра Интернета вещей**.
- Используйте **приложение-функция Azure** для хранения сообщения в **таблице Azure**.
- Настройте **Power BI** , чтобы получить сохраненное сообщение и создать отчет.
- Визуализируйте данные сообщений IoT в **Power BI**.

К службам, которые вы будете использовать, относятся:

- **Центр Интернета вещей Azure** — это служба Microsoft Azure, которая позволяет разработчикам подключаться к ресурсам IOT, отслеживать их и управлять ими. Дополнительные сведения см. на странице [ **службы центра Интернета вещей Azure** ](https://azure.microsoft.com/en-au/services/iot-hub/).

- **Реестр контейнеров Azure** — это служба Microsoft Azure, которая позволяет разработчикам хранить образы контейнеров для различных типов контейнеров. Дополнительные сведения см. на странице [ **службы реестра контейнеров Azure** ](https://azure.microsoft.com/en-au/services/container-registry/).

- **Azure приложение-функция** — это Microsoft Azure служба, которая позволяет разработчикам запускать в Azure небольшие фрагменты кода "функции". Это позволяет делегировать работу в облако, а не локальное приложение, которое может иметь множество преимуществ. **Функции Azure** поддерживают несколько языков разработки, включая C\#, F\#, Node. js, Java и PHP. Дополнительные сведения см. на странице [ **функций Azure** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Служба хранилища Azure: Таблицы** — это служба Microsoft Azure, которая позволяет разработчикам хранить структурированные, отличные от SQL данные в облаке, делая их легко доступными в любом месте. Служба может похвастаться проект без схемы, позволяя развитию таблиц по мере необходимости и, таким образом, очень гибкой. Дополнительные сведения см. на странице [ **таблиц Azure** .](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

В этом курсе вы узнаете, как настроить и использовать службу центра Интернета вещей, а затем визуализировать ответ, предоставленный устройством. Вы сможете применить эти концепции к настраиваемой программе установки службы центра Интернета вещей, которая может быть построена.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> MR и Azure 313: Служба центра Интернета вещей</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Предварительные требования

Наиболее актуальные предварительные требования для разработки с использованием смешанной реальности, включая Microsoft HoloLens, см. в статье [Установка средств](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Python. Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018). Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.

Требуется следующее оборудование и программное обеспечение:

- Windows 10 для дизайнеров с обновлением (или более поздней версии), **режим разработчика включен**

    > [!WARNING]
    > Невозможно запустить виртуальную машину с помощью Hyper-V в Windows 10 Домашняя.

- Пакет SDK для Windows 10 (последняя версия)
- В HoloLens **включен режим разработчика**
- Visual Studio 2017.15.4 (используется только для доступа к Cloud Explorer Azure)
- Доступ к Интернету для Azure и для службы центра Интернета вещей. Для получения дополнительных сведений перейдите [по ссылке на страницу службы центра Интернета вещей](https://azure.microsoft.com/en-au/services/iot-hub/) .
- Модель машинного обучения. Если вы не готовы использовать модель, [вы можете использовать модель, предоставленную в этом курсе](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- Программное обеспечение **Hyper-V** , включенное на компьютере разработки Windows 10.
- Виртуальная машина под управлением Ubuntu (16,4 или 18,4), выполняемая на компьютере разработки, или можно использовать отдельный компьютер под управлением Linux (Ubuntu 16,4 или 18,4). Дополнительные сведения о создании виртуальной машины в Windows с помощью Hyper-V см. в [разделе «перед](#before-you-start)началом работы». (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Перед началом

1. Настройка и тестирование HoloLens. Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup).
2. Рекомендуется выполнять **настройку** калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя).

Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).

Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).

3. Настройте виртуальную **машину Ubuntu** с помощью **Hyper-V**. Следующие ресурсы помогут вам в процессе.
    1.  Сначала перейдите по этой ссылке, чтобы [скачать ISO-образ Ubuntu 16.04.4 LTS (Xenial Xerus)](http://au.releases.ubuntu.com/16.04/). Выберите **образ настольного компьютера 64-разрядный компьютер (AMD64)** .
    2.  Убедитесь, что на компьютере с Windows 10 включен **Hyper-V** . Вы можете перейти по этой ссылке, чтобы получить рекомендации по [установке и включению Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Запустите Hyper-V и создайте новую виртуальную машину Ubuntu. Вы можете перейти по этой ссылке, чтобы получить пошаговое [руководство по созданию виртуальной машины с помощью Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). При запросе на **установку операционной системы из файла загрузочного образа**выберите ранее ЗАГРУЖЕНный ISO-образ **Ubuntu** .

    > [!NOTE]
    > Использование **быстрого создания Hyper-V** не рекомендуется.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Глава 1. Получение модели Пользовательское визуальное распознавание

С этим курсом у вас будет доступ к [предварительно созданной модели пользовательское визуальное распознавание](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) , которая обнаруживает клавиатуры и мыши на изображениях. Если вы используете это, перейдите к [главе 2](#chapter-2---the-container-registry-service).

Однако можно выполнить следующие действия, если вы хотите использовать собственную модель Пользовательское визуальное распознавание:

1. В **проекте пользовательское визуальное распознавание** перейдите на вкладку **Performance (производительность** ).

    > [!WARNING]
    > Для экспорта модели модель должна использовать *компактный* домен. Вы можете изменить домен моделей в параметрах проекта.

    ![Вкладка "производительность"](images/AzureLabs-Lab313-01.png)

2. Выберите **итерацию** , которую необходимо экспортировать, и щелкните **Export (экспорт**). Появится колонка.

    ![Колонка экспорта](images/AzureLabs-Lab313-02.png)

3. В колонке щелкните **файл DOCKER**.

    ![Выбор DOCKER](images/AzureLabs-Lab313-03.png)

4. Щелкните **Linux** в раскрывающемся меню и выберите **скачать**.

    ![Нажмите кнопку Скачать.](images/AzureLabs-Lab313-04.png)

5. Распакуйте содержимое. Он будет использоваться позже в этом курсе.

## <a name="chapter-2---the-container-registry-service"></a>Глава 2. Служба реестра контейнеров

**Служба реестра контейнеров** — это репозиторий, который используется для размещения контейнеров.

**Служба центра Интернета вещей** , которая будет построена и использована в этом курсе, ссылается на **службу реестра контейнеров** , чтобы получить контейнеры для развертывания на пограничном устройстве.

1. Сначала перейдите по [ссылке на портал Azure](https://portal.azure.com/)и войдите в систему с вашими учетными данными.

2. Перейдите к разделу **Создание ресурса** и найдите **Реестр контейнеров**.

    ![реестр контейнеров](images/AzureLabs-Lab313-05.png)

3. Щелкните **создать**.

    ![](images/AzureLabs-Lab313-06.png)

4. Задайте параметры установки службы:

    1. Вставьте имя проекта, в этом примере — **иоткрегистри**.

    2. Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки и управления выставлением счетов за сбор ресурсов Azure. Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.

    3. Задайте расположение службы.

    4. Установите для параметра **пользователь с правами администратора** значение **включено**.

    5. Задайте для параметра **номер SKU** значение **базовый**. 

    ![](images/AzureLabs-Lab313-07.png)

5. Щелкните **создать** и дождитесь создания служб. 

6. Когда появится уведомление об успешном создании *реестра контейнеров*, щелкните **Перейти к ресурсу** , который будет перенаправлен на страницу службы.

    ![](images/AzureLabs-Lab313-08.png)

7. На странице Служба *реестра контейнеров* щелкните **ключи доступа**.

8. Запишите (вы можете использовать Блокнот) со следующими параметрами:
    1. **Сервер входа**
    2. **Имен**
    3. **Пароль**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Глава 3. Служба центра Интернета вещей

Теперь вы начнете создавать и настраивать **службу центра Интернета вещей**.

1. Если вы еще не вошли в систему, войдите на [портал Azure](https://portal.azure.com).

2.  После входа в систему щелкните **создать ресурс** в верхнем левом углу и найдите **центр Интернета вещей**и нажмите клавишу **Ввод**.

 ![Поиск учетной записи хранения](images/AzureLabs-Lab313-10.png)

3.  На новой странице будет представлено описание службы **учетной записи хранения** . В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать экземпляр этой службы.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-11.png)

4.  После нажатия кнопки **создать**появится панель:

    1. Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure. Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.

        > Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Выберите нужное **Расположение** (Используйте то же расположение для всех служб, создаваемых в этом курсе).

    3. Вставьте нужное **имя** для этого экземпляра службы.    

5.  В нижней части страницы щелкните **далее: Размер и масштаб**.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-12.png)

6.  На этой странице выберите **ценовую категорию и уровень масштабирования** (если это ваш первый экземпляр службы центра Интернета вещей, для вас должен быть доступен бесплатный уровень).  

7.  Щелкните **Проверка и создать**.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-13.png)

8.  Проверьте параметры и нажмите кнопку **создать**.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-14.png)

9. После того как уведомление появится, уведомляя об успешном создании службы *центра Интернета вещей* , щелкните **Перейти к ресурсу** , который будет перенаправлен на страницу службы.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-15.png)

10. Прокрутите боковую панель слева, пока вы не увидите *Автоматическое управление устройствами*, щелкните **IOT Edge**.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-16.png)

11. В появившемся окне щелкните **Add IOT Edge Device (добавить устройство**). Справа появится колонка.

12. В колонке укажите для нового устройства **идентификатор устройства** (имя по своему усмотрению). Затем нажмите кнопку **сохранить**. *Первичный* и *вторичный ключи* будут автоматически формироваться, если **Автоматическое создание** тактов было создано автоматически.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-17.png)

13. Вы вернетесь к разделу *устройства IOT Edge* , где будет указано новое устройство. Щелкните новое устройство (выделено красным цветом на рисунке ниже). 

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-18.png)

14. На появившейся странице *сведений об устройстве* сделайте копию **строки подключения** (первичный ключ).

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-19.png)

15. Вернитесь на панель слева и щелкните *политики общего доступа*, чтобы открыть ее. 

16. На появившейся странице щелкните **iothubowner**, и в правой части экрана появится колонка. 

17. Запишите (в Блокноте) **строку подключения** (первичный ключ) для последующего использования при настройке *строки подключения* для устройства.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Глава 4. Настройка среды разработки

Чтобы создать и развернуть модули для *центра Интернета вещей*, вам потребуется установить следующие компоненты на компьютере разработки под Windows 10:

1.  [DOCKER для Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), будет предложено создать учетную запись для загрузки. 

    [![Скачать DOCKER для Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Для запуска DOCKER требуется *Windows 10 Pro*, *Enterprise 14393*или *Windows Server 2016 RTM*. Если вы используете другие версии Windows 10, можно попробовать установить DOCKER с помощью [панели элементов DOCKER](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3,6](https://www.python.org/downloads/).

    [![скачать Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (также называется VS Code)](https://code.visualstudio.com/download).

    [![Скачать VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

После установки программного обеспечения, упомянутого выше, необходимо перезагрузить компьютер.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Глава 5. Настройка среды Ubuntu

Теперь можно перейти к настройке устройства **под управлением ОС Ubuntu**. Выполните следующие действия, чтобы установить необходимое программное обеспечение для развертывания контейнеров на доске:

> [!IMPORTANT]
> Перед выполнением команд терминала с помощью команды **sudo** необходимо выполнить от имени администратора. такого
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Откройте **терминал Ubuntu**и используйте следующую команду для установки **PIP**:

    > [! Подсказка] можно легко открыть *терминал* с помощью сочетания клавиш: **CTRL + ALT + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  В этой главе вам может быть предложено, по *терминалу*, получить разрешение на использование хранилища устройства и ввести **y/n** (да или нет), ввести **"y"** , а затем нажать клавишу **Ввод** , чтобы принять.

3.  После завершения этой команды используйте следующую команду, чтобы установить фигурную **скобку**:

    ```bash
        sudo apt install curl
    ```

4.  После установки **PIP** и **фигур** используйте следующую команду для установки **среды выполнения IOT Edge**. это необходимо для развертывания модулей на доске и управления этими модулями:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. На этом этапе вам будет предложено открыть *файл конфигурации среды выполнения*, чтобы вставить **строку подключения устройства**, которая была записана (в Блокноте) при создании **службы центра Интернета вещей** (в[шаге 14 раздела 3](#chapter-3---the-iot-hub-service)). Чтобы открыть этот файл, выполните в терминале следующую строку:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. Появится файл **config. YAML** , который будет готов к редактированию:

    > [!WARNING]
    > При открытии этот файл может быть несколько запутанным. Будет изменен текст этого файла в самом терминале. 

    1.  Используйте клавиши со стрелками на клавиатуре для прокрутки вниз (необходимо прокрутить немного вниз), чтобы перейти к строке, содержащей ":

        " **\<ДОБАВЬТЕ СТРОКУ ПОДКЛЮЧЕНИЯ УСТРОЙСТВА &GT;** ".

    2. Замените строку, **включая квадратные скобки**, **строкой подключения устройства** , отмеченной ранее.

7. После ввода строки подключения нажмите клавиши **CTRL + X** , чтобы сохранить файл. Появится запрос на подтверждение, введя **Y**. Затем нажмите клавишу **Ввод** , чтобы подтвердить. Вернемся к обычному терминалу. 

8. После успешного выполнения этих команд будет установлена **Среда выполнения IOT Edge**. После инициализации среда выполнения будет запускаться отдельно при каждом включении устройства и будет находиться в фоновом режиме, ожидая развертывания модулей из **службы центра Интернета вещей**.

9.  Выполните следующую командную строку, чтобы инициализировать *среду выполнения IOT Edge*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Если вы внесете изменения в файл. YAML или указанную выше настройку, вам потребуется снова выполнить указанную выше строку перезагрузки в окне *терминала*.

10. Проверьте состояние *среды выполнения IOT Edge* , выполнив следующую командную строку. Среда выполнения должна отображаться с состоянием **активно (работает)** в зеленом тексте.

    ```bash
        sudo systemctl status iotedge
    ```

11. Нажмите клавиши **CTRL + C** , чтобы закрыть страницу состояние. Чтобы убедиться, что *Среда выполнения IOT Edge* правильно извлекать контейнеры, введите следующую команду:

    ```bash
        sudo docker ps
    ```

12. Появится список с двумя (2) контейнерами. Это модули по умолчанию, которые автоматически создаются службой центра Интернета вещей (edgeAgent и edgeHub). После создания и развертывания собственных модулей они будут отображаться в этом списке под заданными по умолчанию.

## <a name="chapter-6---install-the-extensions"></a>Глава 6. Установка расширений

> [!IMPORTANT]
> Следующие несколько глав (6-9) будут выполняться на компьютере с Windows 10.

1. Откройте **VS Code**.

2. Нажмите кнопку **расширения** (квадрат) на левой панели VS Code, чтобы открыть **Панель расширения**.

3. Найдите и установите следующие расширения (как показано на рисунке ниже).

    1. Azure IoT Edge
    2. Набор средств Azure IoT Toolkit
    3. Docker   

    ![Создание контейнера](images/AzureLabs-Lab313-24.png)

4. После установки расширений закройте и снова откройте VS Code.

5. Если VS Code открыть еще раз, перейдите к разделу **Просмотр** > **интегрированного терминала**.

6. Теперь будет установлен **Cookiecutter**. В окне терминала выполните следующую команду Bash:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Указание] Если у вас возникли проблемы с этой командой: 
    >1. Перезапустите VS Code и (или) компьютер.
    >2. Может потребоваться переключить **терминал VS Code** на тот, который использовался для установки Python, например **PowerShell** (особенно если среда Python уже установлена на компьютере). Открыв окно терминала, вы увидите раскрывающееся меню в правой части окна терминала.
     ![Создание контейнера](images/AzureLabs-Lab313-24b.png) 
    >3. Убедитесь, что путь установки **Python** добавлен в качестве **переменной среды** на компьютере. Cookiecutter должен быть частью того же пути расположения. Чтобы получить [Дополнительные сведения о переменных среды](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), перейдите по этой ссылке. 

7. После завершения установки **Cookiecutter** необходимо перезапустить компьютер, чтобы **Cookiecutter** был распознан как команда в среде системы.

## <a name="chapter-7---create-your-container-solution"></a>Глава 7. Создание решения-контейнера

На этом этапе необходимо создать контейнер с модулем, который будет помещен в *Реестр контейнеров*. После отправки контейнера вы будете использовать службу *ребра центра Интернета вещей* , чтобы развернуть ее на устройстве, где выполняется *IOT Edge среды выполнения*.

1. В VS Code выберите пункт **Просмотреть** > **палитру команд**.

2. В палитре найдите и запустите **Azure IOT Edge: Новое решение**IOT ребро.

3. Перейдите в расположение, в котором нужно создать решение. Нажмите клавишу **Ввод** , чтобы принять расположение.

4. Укажите имя для решения. Нажмите клавишу **Ввод** , чтобы подтвердить указанное имя.

5. Теперь вам будет предложено выбрать платформу шаблонов для решения. Щелкните **модуль Python**. Нажмите клавишу **Ввод** , чтобы подтвердить этот вариант.

6. Присвойте имя модулю. Нажмите клавишу **Ввод** , чтобы подтвердить имя модуля. Обязательно запишите имя модуля (в Блокноте), так как оно будет использовано позже.

7. На палитре появится предварительно созданный адрес *репозитория образов DOCKER* . Он будет выглядеть следующим образом:

    **localhost: 5000/— имя модуля**. 

8. Удалите **localhost: 5000.** на его месте вставьте адрес **сервера входа** в *Реестр контейнеров* , который вы заметили при создании **службы реестра контейнеров** ([на шаге 8 главы 2](#chapter-2---the-container-registry-service)). Нажмите клавишу **Ввод** , чтобы подтвердить адрес.

9. На этом этапе будет создан решение, содержащее шаблон для модуля Python, и его структура будет отображаться на **вкладке "Обзор"** в области VS Code в левой части экрана. Если **вкладка "Обзор"** не открыта, ее можно открыть, нажав кнопку "сверху" на панели слева.

    ![Создание контейнера](images/AzureLabs-Lab313-25.png)

10. Последний шаг в этой главе — щелкнуть и открыть **env-файл**на **вкладке "Обзор"** и добавить **имя пользователя** и **пароль** *реестра контейнеров* . Этот файл игнорируется Git, но при построении контейнера задаются учетные данные для доступа к **службе реестра контейнеров**.

    ![Создание контейнера](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Глава 8. изменение решения контейнера

Теперь вы сможете завершить решение контейнера, обновив следующие файлы:

- *скрипт<span></span>Main. корректировки* Python.
- *требования. txt*.
- *развертывание. Template. JSON*.
- *Dockerfile. AMD64*

Затем вы создадите папку *Images* , используемую сценарием Python, чтобы проверить, соответствуют ли образы *модели пользовательское визуальное распознавание*. Наконец, вы добавите файл *labels. txt* , чтобы облегчить чтение модели, и файл *model. Pb* , который является моделью.

1. После открытия VS Code перейдите в папку модуля и найдите сценарий с именем **<span></span>Main. Корректировка**. Дважды щелкните, чтобы открыть его.

2. Удалите содержимое файла и вставьте следующий код:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Откройте файл с именем **требований. txt**и замените его содержимое следующим:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Откройте файл **Deployment. Template. JSON**и замените его содержимое следующим правилом:

    1. Так как вы будете иметь собственную уникальную структуру JSON, вам потребуется изменить ее вручную (вместо копирования примера). Чтобы сделать это простым, используйте приведенное ниже изображение в качестве инструкции.
    2. Области, которые будут выглядеть иначе, но которые **не следует изменять**, выделяются желтым цветом.
    3. **Разделы, которые необходимо удалить, отмечены красным цветом.**
    4. Будьте внимательны, чтобы удалить нужные квадратные скобки, а также удалить запятые.

        ![Создание контейнера](images/AzureLabs-Lab313-27.png)

    5. Заполненный JSON должен выглядеть, как на следующем рисунке (Однако, с уникальными отличиями: *имя пользователя, пароль или модуль/ссылки на модуль*):

        ![Создание контейнера](images/AzureLabs-Lab313-28.png)

5.  Откройте файл с именем **Dockerfile. AMD64**и замените его содержимое следующим:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Щелкните правой кнопкой мыши папку, расположенную под названием **модули** (она будет иметь имя, указанное ранее). в примере ниже он называется *писонмодуле*) и щелкните **создать папку**. Назовите папку **Images**.

7.  Внутри папки добавьте несколько изображений, содержащих мышь или клавиатуру. Это будут образы, которые будут анализироваться моделью Tensorflow.

    > [!WARNING]
    > Если вы используете собственную модель, необходимо изменить ее, чтобы она отражала собственные данные моделей.

8.  Теперь необходимо получить файлы **labels. txt** и **model. Pb** из папки Model, которая была ранее скачана (или создана на основе собственного **Пользовательская служба визуального распознавания**) в [главе 1](#chapter-1---retrieve-the-custom-vision-model). Создав файлы, поместите их в свое решение вместе с другими файлами. Окончательный результат должен выглядеть следующим образом:

    ![Создание контейнера](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Глава 9. Упаковка решения в качестве контейнера

1.  Теперь вы можете «упаковать» файлы в контейнер и отправить их в **Реестр контейнеров Azure**. В VS Code откройте интегрированный *терминал* (**Просмотр** > **интегрированного терминала** или **CTRL**+ **\`** ) и используйте следующую строку для входа в **DOCKER** (замените значения элемента выполните команду с учетными данными **реестра контейнеров Azure (запись контроля доступа)** :

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Щелкните правой кнопкой мыши файл **Deployment. Template. JSON**и выберите **Build IOT Edge Solution**. Этот процесс сборки занимает довольно много времени (в зависимости от устройства), поэтому будьте готовы к ожиданию. После завершения процесса сборки файл **Deployment. JSON** будет создан в новой папке с именем **config**.

    ![создать развертывание](images/AzureLabs-Lab313-30.png)

3. Снова откройте **палитру команд** и выполните поиск **Azure: Войдите в**систему. Следуйте инструкциям на экране, используя учетные данные учетной записи Azure. VS Code предоставит возможность *копирования и открытия*, которая скопирует код устройства, который вскоре потребуется, и откройте веб-браузер по умолчанию. При появлении запроса вставьте код устройства, чтобы проверить подлинность компьютера.

    ![копирование и открытие](images/AzureLabs-Lab313-31.png)

4. После входа вы увидите, что в нижней части панели " *Обзор* " находится новый раздел под названием **устройства центра Интернета вещей Azure**. Щелкните этот раздел, чтобы развернуть его.

    ![Пограничное устройство](images/AzureLabs-Lab313-32.png)

5. Если устройство не указано здесь, необходимо щелкнуть правой кнопкой мыши узел *устройства центра Интернета вещей Azure*и выбрать команду **задать строку подключения центра Интернета вещей**. Вы увидите, что палитра **команд** (в верхней части VS Code) предложит ввести *строку подключения*. Это *строка подключения* , записанная в конце [главы 3](#chapter-3---the-iot-hub-service). После копирования строки в используйте клавишу **Ввод** .    

6. Устройство должно быть загружено и отображено. Щелкните правой кнопкой мыши имя устройства и выберите пункт **Создать развертывание для одного устройства**.

    ![создать развертывание](images/AzureLabs-Lab313-33b.png)

7. Появится командная строка *проводника* , где можно перейти к папке **config** , а затем выбрать файл **Deployment. JSON** . Выбрав этот файл, нажмите кнопку **Выбор манифеста развертывания ребра** .

    ![создать развертывание](images/AzureLabs-Lab313-34.png)

8. На этом этапе вы предоставили **службе центра Интернета вещей** манифест, чтобы развернуть контейнер в качестве модуля из **реестра контейнеров Azure**, эффективно развертывая его на устройстве.

9. Чтобы просмотреть сообщения, отправленные с устройства в центр Интернета вещей, щелкните правой кнопкой мыши имя устройства в разделе **устройства центра Интернета вещей Azure** и в панели **обозревателя** щелкните **Start Monitoring D2C Message**. Сообщения, отправляемые с устройства, должны появиться в окне терминала VS. Подождите, так как это может занять некоторое время. Сведения об отладке и проверке успешности развертывания см. в следующей главе.

Теперь этот модуль будет перебирать изображения в папке **Images** и анализировать их с каждой итерацией. Очевидно, что это лишь демонстрация того, как получить базовую модель машинного обучения для работы в среде IoT Edge устройства. 

Чтобы расширить функциональные возможности этого примера, можно выполнить несколько способов. Один из них может включать в себя некоторый код в контейнере, который фиксирует фотографии с веб-камеры, подключенной к устройству, и сохраняет изображения в папке Images. 

Другой способ — скопировать образы с устройства IoT в контейнер. Для этого можно выполнить следующую команду в терминале устройства IoT (возможно, небольшое приложение может выполнить задание, если вы захотите автоматизировать процесс). Эту команду можно проверить, запустив ее вручную из расположения папки, в которой хранятся файлы:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Глава 10-Отладка среды выполнения IoT Edge

Ниже приведен список командных строк и советов, помогающих отслеживать и отлаживать действия по обмену сообщениями со *средой выполнения IOT Edge*на **устройстве Ubuntu**. 

- Проверьте состояние *среды выполнения IOT Edge* , выполнив следующую командную строку:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Не забудьте нажать клавиши **CTRL + C**, чтобы завершить Просмотр состояния.

- Перечислите уже развернутые контейнеры. Если *Служба центра Интернета вещей* успешно развернула контейнеры, они будут отображены с помощью следующей командной строки:

    ```bash
        sudo iotedge list
    ```

    или

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Приведенный выше вариант — хороший способ проверить, успешно ли развернут ваш модуль, так как он появится в списке. в противном случае вы увидите **только** *edgeHub* и *edgeAgent*.

- Чтобы отобразить журналы кода контейнера, выполните следующую командную строку:

    ```bash
        journalctl -u iotedge
    ```

**Полезные команды для управления средой выполнения IoT Edge:**

-  Чтобы удалить все контейнеры на узле, выполните следующие действия.

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Чтобы прерывать работу *IOT Edge среды выполнения*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Глава 11. Создание службы таблиц 

Вернитесь на портал Azure, где вы создадите службу таблиц Azure, создав ресурс хранилища.

1. Если вы еще не вошли в систему, войдите на [портал Azure](https://portal.azure.com).

2. После входа в систему щелкните **создать ресурс**в верхнем левом углу и найдите **учетную запись хранения**и нажмите клавишу **Ввод** , чтобы начать поиск.

3. После появления щелкните Учетная **запись хранения — BLOB-объект, файл, таблица и очередь** из списка.

    ![Поиск учетной записи хранения](images/AzureLabs-Lab313-35.png)

4. На новой странице будет представлено описание службы **учетной записи хранения** . В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать экземпляр этой службы.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-36.png)

5. После нажатия кнопки **создать**появится панель:

    1. Вставьте нужное **имя** для этого экземпляра службы (*необходимо указать все символы в нижнем регистре*).

    2. В качестве **модели развертывания**щелкните **Resource Manager**.

    3. Для **типа учетной записи**в раскрывающемся меню выберите пункт **хранилище (общее назначение**версии 1).

    4. Щелкните соответствующее **Расположение**.
    
    5. В раскрывающемся меню репликация щелкните **доступ для чтения — геоизбыточное хранилище (RA-GRS)** .

    6. Для **повышения производительности**щелкните **стандартный**.

    7. В разделе **Обязательное безопасное перемещение** щелкните **отключено**.

    8. В раскрывающемся меню **подписки** выберите подходящую подписку.

    9. Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки и управления выставлением счетов за сбор ресурсов Azure. Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.

        > Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Оставьте **виртуальные сети** **отключенными**, если это возможно.

    11. Нажмите кнопку **Создать**.

        ![Заполнение сведений о хранилище](images/AzureLabs-Lab313-37.png)

6. После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.

7. После создания экземпляра службы на портале отобразится уведомление. Щелкните уведомления, чтобы изучить новый экземпляр службы.

    ![уведомление о новом хранилище](images/AzureLabs-Lab313-38.png)

8. Нажмите кнопку " **Переход к ресурсу** " в уведомлении, и вы будете перенаправлены на новую страницу обзора экземпляра службы хранилища.

    ![Переход к ресурсу](images/AzureLabs-Lab313-39.png)

9. На странице Обзор в правой части щелкните **таблицы**.
    
    ![таблице](images/AzureLabs-Lab313-40.png)

10. Панель справа изменится на отображение сведений о **службе таблиц** , где необходимо добавить новую таблицу. Для этого нажмите кнопку **+ Table (+ таблица** ) в левом верхнем углу.

    ![Открытие таблиц](images/AzureLabs-Lab313-41.png)

11. Будет отображена новая страница, где необходимо ввести **имя таблицы**. Это имя, которое будет использоваться для ссылки на данные в приложении в последующих главах (создание приложение-функция и Power BI). В качестве имени вставьте **иотмессажес** (вы можете выбрать собственное, просто запомните его, если оно используется далее в этом документе) и нажмите кнопку **ОК**. 

12. После создания новой таблицы ее можно будет увидеть на странице **службы таблиц** (в нижней части).

    ![создана новая таблица](images/AzureLabs-Lab313-42.png)  

13. Теперь щелкните **ключи доступа** и создайте копию имени и **ключа** **учетной записи хранения** (с помощью Блокнота). Эти значения будут использоваться далее в этом курсе при создании **приложение-функция Azure**.

    ![создана новая таблица](images/AzureLabs-Lab313-43.png) 

14. Снова с помощью панели слева перейдите к разделу *Служба таблиц* и щелкните **таблицы** (или **Обзор таблиц**в новых порталах) и скопируйте **URL-адрес таблицы** (с помощью Блокнота). Это значение будет использоваться далее в этом курсе при связывании таблицы с приложением **Power BI** .

    ![создана новая таблица](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Глава 12. Заполнение таблицы Azure

Теперь, когда учетная запись хранения **службы таблиц** была настроена, можно добавить в нее данные, которые будут использоваться для хранения и извлечения информации. Редактирование таблиц можно выполнить с помощью **Visual Studio**.

1. Откройте **Visual Studio** (**не** Visual Studio Code).

2. В меню щелкните **Просмотреть** > **Cloud Explorer**.

    ![открыть Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. **Cloud Explorer** откроется как закрепленный элемент (подождите, так как загрузка может занять некоторое время).

    > [!WARNING] 
    > Если подписка, использованная для создания *учетных записей хранения* , не отображается, убедитесь, что у вас есть: 
    > - Войдите в ту же учетную запись, которая использовалась для портала Azure.
    > - Выберите подписку на странице управления учетными записями (может потребоваться применить фильтр из параметров учетной записи):  
    >
    >   ![Найти подписку](images/AzureLabs-Lab313-46.png)

4. Будут показаны облачные службы Azure. Найдите **учетные записи хранения** и щелкните стрелку слева от нее, чтобы развернуть учетные записи.

    ![Открытие учетных записей хранения](images/AzureLabs-Lab313-47.png)

5. После развертывания вновь созданная **учетная запись хранения** должна быть доступна. Щелкните стрелку слева от хранилища, а затем после разворачивания найдите **таблицы** и щелкните стрелку рядом с ней, чтобы открыть **таблицу** , созданную в последней главе. Дважды щелкните **таблицу**.

6. Таблица откроется в центре окна Visual Studio. Щелкните значок таблицы с рядом с **+** ним (плюс).

    ![Добавить новую таблицу](images/AzureLabs-Lab313-48.png)

7. Появится окно с запросом на *Добавление сущности*. Вы создадите только одну сущность, хотя она будет иметь три свойства. Вы увидите, что *PartitionKey* и *RowKey* уже предоставлены, так как они используются таблицей для поиска данных. 

    ![ключ секции и строки](images/AzureLabs-Lab313-49.png)

8. Обновите следующие значения:

    - Имя: **PartitionKey**, значение: **PK_IoTMessages** 

    - Имя: **RowKey**, значение: **RK_1_IoTMessages** 

9. Затем щелкните **Добавить свойство** (в левом нижнем углу окна *добавить сущность* ) и добавьте следующее свойство:

    - **Мессажеконтент**в виде *строки*оставьте значение пустым.

10. Таблица должна соответствовать таблице, показанной на рисунке ниже:

    ![добавить правильные значения](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > Причина, по которой сущность имеет номер 1 в ключе строки, — это потому, что может потребоваться добавить дополнительные сообщения, если вы хотите поэкспериментировать с этим курсом.

11. По завершении нажмите кнопку **ОК** . Теперь таблица готова к использованию.

## <a name="chapter-13---create-an-azure-function-app"></a>Глава 13. Создание приложение-функция Azure 

Теперь пришло время создать *приложение-функция Azure*, который будет вызываться *службой центра Интернета вещей* для хранения сообщений *IOT Edge* устройства в службе **таблиц** , созданной в предыдущей главе.

Сначала необходимо создать файл, который позволит вашей функции Azure загружать нужные библиотеки.

1.  Откройте **Блокнот** (нажмите клавишу *Windows*и введите *Блокнот*).

    ![открыть Блокнот](images/AzureLabs-Lab313-51.png)

2.  При открытии блокнота вставьте в него структуру JSON. После этого сохраните его на рабочем столе как **Project. JSON**. Этот файл определяет библиотеки, которые будет использовать функция. Если вы использовали NuGet, он покажется знакомым.
    
    > [!WARNING]
    > Важно, чтобы именование было правильным; Убедитесь, что у него нет расширения файла **. txt** . Ниже приведены справочные сведения.
    >
    > ![Сохранение JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Войдите на [портал Azure](https://portal.azure.com).

4.  После входа в систему щелкните **создать ресурс** в верхнем левом углу и выполните поиск по запросу **приложение-функция**и нажмите клавишу **Ввод** , чтобы выполнить поиск. Щелкните *приложение-функция* из результатов, чтобы открыть новую панель.

    ![Поиск приложения функции](images/AzureLabs-Lab313-53.png)

5.  На новой панели будет представлено описание службы **приложение-функция** . В нижнем левом углу этой панели нажмите кнопку " **создать** ", чтобы создать связь с этой службой.

    ![экземпляр приложения функции](images/AzureLabs-Lab313-54.png)

6.  После нажатия кнопки **создать**заполните следующие поля:

    1. В качестве **имени приложения**вставьте нужное имя для этого экземпляра службы.

    2. Выберите **подписку**.

    3. Выберите ценовую категорию, подходящую для вас. Если вы впервые создаете **службу приложение-функция**, вам будет доступен бесплатный уровень.

    4. Выберите **группу ресурсов** или создайте новую. Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки и управления выставлением счетов за сбор ресурсов Azure. Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.

        > Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Для **ОС**щелкните Windows, так как это Целевая платформа.

    6. Выберите **план размещения** (в этом учебнике используется **план потребления**).

    7. Выберите **Расположение** (выберите то же расположение, что и хранилище, созданное на предыдущем шаге).

    8. В разделе **хранилище** **необходимо выбрать службу хранилища, созданную на предыдущем шаге**.

    9. Вам не потребуется *Application Insights* в этом приложении, поэтому вы можете оставить его без изменений.

    10. Нажмите кнопку **Создать**.

        ![создать новый экземпляр](images/AzureLabs-Lab313-55.png)

7.  После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.

8.  После создания экземпляра службы на портале отобразится уведомление.

    ![новое уведомление](images/AzureLabs-Lab313-56.png)

9.  Щелкните уведомление, когда развертывание завершится успешно (завершено).

10. Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы. 

    ![Переход к ресурсу](images/AzureLabs-Lab313-57.png)

11. В левой части новой панели щелкните **+** значок (плюс) рядом с пунктом *функции*, чтобы создать новую функцию.

    ![Добавить новую функцию](images/AzureLabs-Lab313-58.png)

12. На центральной панели появится окно создания **функции** . Прокрутите вниз и щелкните пользовательская **функция**.

    ![Пользовательская функция](images/AzureLabs-Lab313-59.png)

13. Прокрутите страницу вниз до пункта **центр Интернета вещей (концентратор событий)** , а затем щелкните его.

    ![Пользовательская функция](images/AzureLabs-Lab313-60.png)

14. В колонке центр **Интернета вещей (концентратор событий)** задайте для **C#** параметра язык значение и нажмите кнопку **создать**.

    ![Пользовательская функция](images/AzureLabs-Lab313-61.png)

15. В окне, которое появится, убедитесь, что выбран **центр Интернета вещей** , а имя поля *центр Интернета* вещей соответствует имени созданной ранее *службы центра Интернета вещей* ([на шаге 8 главы 3](#chapter-3---the-iot-hub-service)). Затем нажмите кнопку **выбрать** .

    ![Пользовательская функция](images/AzureLabs-Lab313-62.png)

16. Вернитесь в колонку **центр Интернета вещей (концентратор событий)** и щелкните **создать**.

    ![Пользовательская функция](images/AzureLabs-Lab313-63.png)

17. Вы будете перенаправлены в редактор функций.

    ![Пользовательская функция](images/AzureLabs-Lab313-64.png)

18. Удалите весь код в нем и замените его следующим:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. Измените следующие переменные, чтобы они соответствовали соответствующим значениям (значения**таблицы** и **хранилища** , начиная с [шага 11 и 13, соответственно, из раздела 11](#chapter-11---create-table-service)), которые будут находиться в вашей учетной **записи хранения**:

    - **TableName**с именем **таблицы** , расположенной в вашей учетной **записи хранения**.
    - **таблеурл**с URL-адресом **таблицы** , расположенной в вашей **учетной записи хранения**.
    - **storageAccountName**, указав имя значения, соответствующее имени **учетной записи хранения** .
    - **storageAccountKey**с ключом, полученным в ранее созданной службе хранилища.

    ![Пользовательская функция](images/AzureLabs-Lab313-65.png)

20. После ввода кода нажмите кнопку **сохранить**.

21. Затем щелкните **\<** значок (стрелка) в правой части страницы.

    ![Пользовательская функция](images/AzureLabs-Lab313-66.png)

22. Панель будет продвигаться справа. На этой панели нажмите кнопку **Отправить**и отобразится *Обозреватель файлов* .

23. Перейдите к и щелкните файл **Project. JSON** , созданный ранее в блокноте, а затем нажмите кнопку **Открыть** . Этот файл определяет библиотеки, которые будет использовать функция.

    ![Пользовательская функция](images/AzureLabs-Lab313-67.png)

24. После отправки файл появится на панели справа. Щелкнув его, вы откроете его в редакторе **функций** . Он должен выглядеть **точно** так же, как и следующий образ.

    ![Пользовательская функция](images/AzureLabs-Lab313-68.png)

25. На этом этапе было бы неплохо протестировать возможности функции для хранения сообщения в *таблице*. В правой верхней части окна щелкните **тест**.

    ![Пользовательская функция](images/AzureLabs-Lab313-69.png)

26. Вставьте сообщение в **текст запроса**, как показано на рисунке выше, и щелкните **Run (выполнить**). 

27. Функция будет запущена, отображая состояние результата (вы увидите зеленое **состояние 202**, расположенное выше окна *вывод* , что означает успешный вызов):

    ![результат вывода](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Глава 14. Просмотр активных сообщений

Если теперь открыть Visual Studio (**не** Visual Studio Code), вы можете визуализировать результат тестового сообщения, так как он будет храниться в области строк *мессажеконтент* .

![Пользовательская функция](images/AzureLabs-Lab313-71.png)

После того как служба таблиц и приложение-функция на месте, в таблице *иотмессажес* будут отображаться сообщения устройства Ubuntu. Если оно еще не запущено, запустите устройство еще раз, и вы сможете просматривать сообщения о результатах с устройства и модуля в таблице с помощью Visual Studio *Cloud Explorer*.

![Визуализация данных](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Глава 15-Power BIная установка

Для визуализации данных с вашего устройства Интернета вещей, которое будет настроено **Power BI** (версия для настольной системы), можно получить данные из только что созданной службы *таблиц* . Затем версия *HoloLens* Power BI будет использовать эти данные для визуализации результата.

1.  Откройте Microsoft Store в Windows 10 и выполните поиск **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Скачайте приложение. После завершения загрузки откройте его.

3.  Войдите в *Power BI* с помощью **учетной записи Microsoft 365**. Чтобы зарегистрироваться, вы можете перенаправлены в браузер. После регистрации вернитесь в приложение Power BI и снова выполните вход.

4.  Щелкните **получить данные** , а затем — **еще...** .

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Щелкните **Azure**, **хранилище таблиц Azure**, а затем щелкните **подключить**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  При создании службы таблиц вам будет предложено вставить **URL-адрес таблицы** , собранный ранее ([на шаге 13 главы 11](#chapter-11---create-table-service)). После вставки URL-адреса удалите часть пути, ссылающуюся на таблицу "вложенную папку" (которая была Иотмессажес в этом курсе). Окончательный результат должен отобразиться на рисунке ниже. Затем нажмите кнопку **ОК**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  При создании табличного хранилища вам будет предложено вставить указанный ранее **ключ** к хранилищу (см.[Шаг 11 главы 11](#chapter-11---create-table-service)). Затем щелкните **подключить**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Отобразится **Панель Навигатор** , установите флажок рядом с таблицей и щелкните **Load (загрузить**).

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. Таблица теперь загружена на Power BI, но для ее вывода требуется запрос. Для этого щелкните правой кнопкой мыши имя таблицы, расположенное на **панели поля** в правой части экрана. Затем щелкните **изменить запрос**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. **Редактор Power Query** откроется в виде нового окна, в котором отображается таблица. Щелкните **запись** слова в столбце *содержимое* таблицы, чтобы визуализировать сохраненное содержимое.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Щелкните по **таблице**в левом верхнем углу окна. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Нажмите кнопку **закрыть & применить**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Завершив загрузку запроса, на **панели «поля**» в правой части экрана заполните поля, соответствующие **имени** и значению параметров, чтобы визуализировать содержимое столбца **мессажеконтент** .

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Щелкните значок " **синий диск** " в левом верхнем углу окна, чтобы сохранить свою работу в выбранной папке.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Теперь можно нажать кнопку Опубликовать, чтобы отправить таблицу в рабочую область. При появлении запроса щелкните **Моя рабочая область** и нажмите кнопку *выбрать*. Дождитесь, пока отобразится успешный результат отправки.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> В следующей главе описывается только для HoloLens. Power BI в настоящее время не выделенные в качестве иммерсивного приложения, но вы можете запустить версию рабочего стола на портале Windows Mixed Reality (Клифф House) через классическое приложение.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Глава 16-отображение данных Power BI в HoloLens

1. В HoloLens Войдите в **Microsoft Store**, коснувшись его значка в списке приложений.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. Найдите и скачайте приложение **Power BI** .

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. Запустите **Power BI** из списка приложений. 

4. **Power BI** может попросить вас войти в учетную **запись Microsoft 365**.

5. В пределах приложения Рабочая область должна отображаться по умолчанию, как показано на рисунке ниже. Если это не происходит, просто щелкните значок рабочей области в левой части окна.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Ваша работа над приложением центра Интернета вещей завершена

Поздравляем! вы успешно создали службу центра Интернета вещей с имитацией устройства с виртуальными машинами. Устройство может передавать результаты модели машинного обучения в службу таблиц Azure, что облегчается приложение-функция Azure, которые считываются в Power BI и выводятся в виде визуализации в Microsoft HoloLens.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Премиальные упражнения

### <a name="exercise-1"></a>Упражнение 1

Разверните структуру обмена сообщениями, хранящуюся в таблице, и отобразите ее в виде диаграммы. Вам может потребоваться получить дополнительные данные и сохранить их в одной и той же таблице для последующего отображения.

### <a name="exercise-2"></a>Упражнение 2

Создайте дополнительный модуль "запись камеры" для развертывания на доске IoT, чтобы он мог записывать образы через камеру для анализа.
