---
title: Г-н и 313 - служба центра Интернета вещей Azure
description: Выполните этот курс, чтобы узнать, как реализовать службу центра Интернета вещей на виртуальной машине под управлением Ubuntu 16.4, а затем визуализировать данные сообщения с помощью Microsoft HoloLens или иммерсивных Гарнитура (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, edge, edge Интернета вещей, руководство, api, уведомления, функции, таблицы, hololens, насыщенные, виртуальной реальности, Интернета, виртуальная машина, ubuntu, python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597569"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

# <a name="mr-and-azure-313-iot-hub-service"></a>Г-н и Azure 313: Служба центра Интернета вещей

![результат курс](images/AzureLabs-Lab313-00.png)

В рамках этого курса вы узнаете, как реализовать **службы центра Интернета вещей** на виртуальной машине под управлением операционной системы Ubuntu 16.4. **Приложение-функцию Azure** будет использоваться для получения сообщений из виртуальной Машине Ubuntu и сохранить результат в **службу таблиц Azure**. Затем можно просматривать с помощью **Power BI** на Microsoft HoloLens или иммерсивных Гарнитура (VR).

Содержимое этого курса *применимо* на устройствах IoT Edge на то, что для целей этого курса, основное внимание будет уделено среде виртуальной машины, чтобы доступ к физическому устройству Edge не требуется.

Выполнив этот курс, вы узнаете следующее:

- Развертывание **модуля IoT Edge** к виртуальной машине (Ubuntu 16 ОС), который будет представлять устройства Интернета вещей.
- Добавить **модели Tensorflow Azure Custom Vision** в модуле Edge с кодом, который будет анализировать образы, хранящиеся в контейнере.
- Настройка модуля для отправки сообщения результата анализа обратно в ваш **службы центра Интернета вещей**.
- Используйте **приложение-функцию Azure** для сохранения сообщения в **таблиц Azure**.
- Настройка **Power BI** для сбора сохраненного сообщения и создать отчет.
- Визуализируйте данные сообщения Интернета вещей в **Power BI**.

К службам, которые будут использоваться относятся:

- **Центр Интернета вещей Azure** — это служба Microsoft Azure, что позволяет разработчикам подключение, мониторинг и управление, ресурсов Интернета вещей. Дополнительные сведения см. в статье [ **службы центра Интернета вещей** страницы](https://azure.microsoft.com/en-au/services/iot-hub/).

- **Реестр контейнеров Azure** — это служба Microsoft Azure, которую разработчики могут хранить образы контейнеров, для различных типов контейнеров. Дополнительные сведения см. в статье [ **службы реестра контейнеров Azure** страницы](https://azure.microsoft.com/en-au/services/container-registry/).

- **Azure приложения-функции** — служба Microsoft Azure, которая позволяет разработчикам запускать небольшие фрагменты кода, «», в функциях Azure. Это позволяет делегировать работу в облаке, а не локального приложения, который может иметь множество преимуществ. **Функции Azure** поддерживает несколько языков разработки, в том числе C\#, F\#, Node.js, Java и PHP. Дополнительные сведения см. в статье [ **"функции Azure"** страницы](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Хранилище Azure: Таблицы** — это служба Microsoft Azure, которая позволяет разработчикам хранить структурированные, отличные от SQL, данные в облаке, сделаете его доступным для в любом месте. Служба может похвастаться макета без схемы, позволяя развитие таблиц, при необходимости и таким образом обладает большой гибкостью. Дополнительные сведения см. в статье [ **таблицы Azure** страницы](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Этот курс поможет, как установить и использовать службы центра Интернета вещей и последующей визуализации ответ предоставлялся через устройство. Это будет необходимо применение этих понятий для пользовательской установки службы центра Интернета вещей, возможно, вы разрабатываете.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> Г-н и Azure 313: Служба центра Интернета вещей</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>предварительные требования

Наиболее актуальные предварительные требования для разработки с помощью смешанной реальности, в том числе с Microsoft HoloLens, откройте страницу [установить средства](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) статьи.

> [!NOTE]
> Этот учебник предназначен для разработчиков, имеющих минимальный опыт с Python. Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.). Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по сравнению, перечисленных ниже.

Требуется следующее оборудование и программное обеспечение:

- Windows 10 Fall Creators Update (или более поздней версии), **включен режим разработчика**

    > [!WARNING]
    > Невозможно запустить виртуальную машину с помощью Hyper-V в Windows 10 Home Edition.

- Пакет SDK для Windows 10 (последняя версия)
- A HoloLens **включен режим разработчика**
- Visual Studio 2017.15.4 (используется только для доступа к Azure Cloud Explorer)
- Доступ к Интернету для Azure, а также для службы центра Интернета вещей. Дополнительные сведения, выполните инструкции из этого [ссылку на страницу службы центра Интернета вещей](https://azure.microsoft.com/en-au/services/iot-hub/)
- Модель машинного обучения. Если у вас нет собственных, готовая к использованию модели [можно использовать модель, предоставляемую в этом курсе](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- **Hyper-V** включено на компьютере разработки Windows 10 по.
- Виртуальной машине под управлением Ubuntu (16.4 или 18.4. в случае), работает на компьютере разработки или в качестве альтернативы можно использовать отдельный компьютер под управлением Linux (Ubuntu 16.4 или 18.4. в случае). Можно найти дополнительные сведения о том, как создать виртуальную Машину в Windows с помощью Hyper-V в [«Перед началом работы» главы](#before-you-start). () https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Прежде чем начать

1. Настроить и проверить ваш HoloLens. Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup).
2. Рекомендуется выполнять **калибровки** и **настройке датчика** начале разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя).

Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).

Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).

3. Настройка вашей **виртуальной машины Ubuntu** с помощью **Hyper-V**. Следующие ресурсы помогут вам в процессе.
    1.  Во-первых, перейдите по ссылке для [загрузить ISO-образ Ubuntu 16.04.4 LTS (Xenial Xerus)](http://au.releases.ubuntu.com/16.04/). Выберите **образа настольной системы ПК (AMD64) 64-разрядных**.
    2.  Убедитесь, что **Hyper-V** включена на компьютере Windows 10. Перейдите по этой ссылке рекомендации [Установка и включение Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Запустите Hyper-V и создайте новую виртуальную Машину Ubuntu. Перейдите по этой ссылке для [Поэтапное руководство о том, как создать виртуальную Машину с Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). При запросе к **«Установить операционную систему из файла загрузочного образа»** выберите **Ubuntu ISO** у вас есть загрузки ранее.

    > [!NOTE]
    > С помощью **Hyper-V быстрое создание** не рекомендуется.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Глава 1 - извлечь Custom Vision модель

В этом курсе вы получите доступ к [предварительно созданные модели Custom Vision](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) , обнаруживает клавиатуры и мыши из образов. Если вы используете это, перейдите к разделу [Глава 2](#chapter-2---the-container-registry-service).

Тем не менее если вы хотите использовать собственную модель Custom Vision можно выполните следующие действия.

1. В вашей **Custom Vision проекта** перейдите **производительности** вкладки.

    > [!WARNING]
    > Необходимо использовать модель *compact* домена, для экспорта модели. Можно изменить модели домена в параметрах проекта.

    ![Вкладка "производительность"](images/AzureLabs-Lab313-01.png)

2. Выберите **итерации** вы хотите экспортировать и щелкнуть **Экспорт**. Появится колонка.

    ![колонка "Экспорт"](images/AzureLabs-Lab313-02.png)

3. В колонке щелкните **файл Docker**.

    ![Выберите docker](images/AzureLabs-Lab313-03.png)

4. Нажмите кнопку **Linux** в раскрывающемся меню и затем щелкните на **загрузить**.

    ![Щелкните "скачать"](images/AzureLabs-Lab313-04.png)

5. Распакуйте содержимое. Он понадобится позже в этом курсе.

## <a name="chapter-2---the-container-registry-service"></a>Глава 2 - службе реестра контейнеров

**Службы реестра контейнеров** — это репозиторий, используемого для размещения контейнеров.

**Службы центра Интернета вещей** будет построить и использовать в этом курсе, ссылается на **службы реестра контейнеров** для получения контейнеров для развертывания в устройство Edge.

1. Во-первых, выполните это [ссылку на портал Azure](https://portal.azure.com/)и войдите, используя свои учетные данные.

2. Перейдите к **создать ресурс** и найдите **реестр контейнеров**.

    ![реестр контейнеров](images/AzureLabs-Lab313-05.png)

3. Щелкните **создание**.

    ![](images/AzureLabs-Lab313-06.png)

4. Настройте параметры службы:

    1. Вставить имя проекта, в этом примере она называется **IoTCRegistry**.

    2. Выберите **группы ресурсов** или создайте новую. Для отслеживания, контроля доступа, подготовки и управлять, выставление счетов для коллекции активов Azure позволяет группе ресурсов. Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).

    3. Задайте расположение службы.

    4. Задайте **пользователя с правами администратора** для **включить**.

    5. Задайте **SKU** для **основные**. 

    ![](images/AzureLabs-Lab313-07.png)

5. Нажмите кнопку **создать** и подождите создать службы. 

6. Когда появляется уведомление сообщающий об успешном создании *реестр контейнеров*, щелкните **перейти к ресурсу** перенаправление на страницу службы.

    ![](images/AzureLabs-Lab313-08.png)

7. В *реестр контейнеров* странице службы, щелкнув **ключи доступа**.

8. Запишите (можно использовать в блокноте) со следующими параметрами:
    1. **Сервер входа**
    2. **Имя пользователя**
    3. **Пароль**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Глава 3 - центр Интернета вещей

Теперь рассмотрим создание и настройка вашей **службы центра Интернета вещей**.

1. Если еще не выполнил вход, вход в [портал Azure](https://portal.azure.com).

2.  После входа в систему, щелкните **создать ресурс** в левом верхнем углу, а поиск **центра Интернета вещей**и нажмите кнопку **ввод**.

 ![Поиск учетной записи хранения](images/AzureLabs-Lab313-10.png)

3.  Новая страница будет предоставить описание **учетной записи хранения** службы. В нижней левой части этого запроса, нажмите кнопку **создать** кнопку, чтобы создать экземпляр этого службу.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-11.png)

4.  Когда вы перейдете на **создать**, будут отображаться панели:

    1. Выберите **группы ресурсов** или создайте новую. Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure. Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Выберите соответствующее **расположение** (используйте то же расположение во всех службах, создаваемых в этом курсе).

    3. Вставить нужный **имя** для данного экземпляра службы.    

5.  В нижней части страницы щелкните **далее: Размер и масштаб**.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-12.png)

6.  На этой странице выберите ваш **цены и масштабирование уровня** (если это ваш первый экземпляр службы центра Интернета вещей, уровень "бесплатный" должна быть доступна для вас).  

7.  Щелкните **Просмотр и создание**.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-13.png)

8.  Просмотрите параметры и нажмите кнопку **создать**.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-14.png)

9. После уведомления всплывает сообщающий об успешном создании *центра Интернета вещей* службы, щелкните **перейти к ресурсу** перенаправление на страницу службы.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-15.png)

10. Прокрутите содержимое боковой панели в левой части до *автоматическое управление устройствами*, щелкните на **IoT Edge**.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-16.png)

11. В окне справа щелкните **добавить устройство IoT Edge**. Колонка будет отображаться справа.

12. В колонке укажите новое устройство **идентификатор устройства** (имя по своему усмотрению). Щелкните **Сохранить**. *Основной* и *вторичные ключи* будет автоматически создавать, если у вас есть **автоматическое создание** отмечен.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-17.png)

13. Произойдет переход к *пограничные устройства Интернета вещей* раздел, где будут перечислены новое устройство. Щелкните на новом устройстве (выделено красным цветом на изображении ниже). 

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-18.png)

14. На *сведений об устройстве* страницы, которая отображается, сделайте копию **строку подключения** (первичный ключ).

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-19.png)

15. Вернитесь на панель слева и нажмите кнопку *политики общего доступа*, чтобы открыть его. 

16. На открывшейся странице щелкните **iothubowner**, и колонка будет отображаться в правой части экрана. 

17. Запишите (в «Блокнот») **строку подключения** (первичный ключ), для последующего использования при задании *строку подключения* к устройству.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Глава 4 - Настройка среды разработки

Для создания и развертывания модулей для *концентратора IoT Edge*, потребуются следующие компоненты, установленные на компьютере разработки под управлением Windows 10:

1.  [Docker для Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), он запрашивает, следует создать учетную запись, чтобы иметь возможность загрузить. 

    [![скачать docker для windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Требуется docker *Windows 10 PRO*, *Enterprise 14393*, или *Windows Server 2016 RTM*, для запуска. Если вы используете другие версии Windows 10, установку можно произвести с помощью Docker [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3.6](https://www.python.org/downloads/).

    [![скачать python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (также называется VS Code)](https://code.visualstudio.com/download).

    [![скачать VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

После установки программного обеспечения, упомянутых выше, необходимо перезагрузить компьютер.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Глава 5 - Настройка среды Ubuntu

Теперь можно перейти к настройке устройства **под управлением ОС Ubuntu**. Выполните следующие действия, чтобы установить необходимое программное обеспечение для развертывания контейнеров на плате.

> [!IMPORTANT]
> Всегда должны предваряться команд терминала с помощью **sudo** для запуска в качестве пользователя с правами администратора. Например:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Откройте **терминалов Ubuntu**и используйте следующую команду для установки **pip**:

    > [! УКАЗАНИЕ] можно открыть *терминалов* очень просто с помощью сочетания клавиш: **Ctrl + Alt + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  В этой главе, может появиться запрос, по *терминалов*, для разрешения использования хранилища на устройстве, так и для ввода **д/н** (Да или нет), тип **«y»** и нажмите клавишу **Ввод** ключ, чтобы принять.

3.  После выполнения этой команды, используйте следующую команду для установки **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Один раз **pip** и **curl** будут установлены, используйте следующую команду для установки **среды выполнения IoT Edge**, это необходимо для развертывания и управления модулями на плате:

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

5. На этом этапе вам будет предложено открыть *файл конфигурации среды выполнения*, вставляемый **Device Connection String**, который вы взяли (в в блокноте), при создании **службы центра Интернета вещей**  ([на шаге 14, Глава 3](#chapter-3---the-iot-hub-service)). Выполните приведенную ниже строку в окне терминала, чтобы открыть этот файл:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. **Config.yaml** файл будет отображается, вы сможете изменить:

    > [!WARNING]
    > При открытии файла, может быть несколько запутанным. Можно в редактирования этого файла текста *терминалов* сам. 

    1.  Клавиши со стрелками на клавиатуре для прокрутки вниз (необходимо будет выполнить прокрутку вниз немного способом), для доступа к строке, которая содержит»:

        "**\<ДОБАВЬТЕ СТРОКУ ПОДКЛЮЧЕНИЯ УСТРОЙСТВА &GT;**«.

    2. Замените строки, **включая скобки**, с помощью **Device Connection String** отмечали ранее.

7. С помощью строки подключения в месте, на клавиатуре нажмите клавишу **Ctrl + X** ключи для сохранения файла. Вам будет предложено подтвердить, введя **Y**. Затем нажмите клавишу **ввод** ключ для подтверждения. Вы вернетесь к обычному *терминалов*. 

8. Как только эти команды все выполняются успешно, будет установлен **среды выполнения IoT Edge**. После инициализации среды выполнения на свой собственный каждый раз при включении устройства запустится и будет расположен в фоновом режиме, Ожидание модули для развертывания из **службы центра Интернета вещей**.

9.  Выполните следующую команду для инициализации *среды выполнения IoT Edge*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > При внесении изменений в yaml-файл или указанные действия по настройке, необходимо будет снова, запустите приведенную выше строку перезапуска в рамках *терминалов*.

10. Проверьте *среды выполнения IoT Edge* состояние, выполнив следующую команду. Среда выполнения должен отображаться с состоянием **активный (запущено)** зеленым цветом.

    ```bash
        sudo systemctl status iotedge
    ```

11. Нажмите клавишу **Ctrl-C** ключей, чтобы закрыть страницу состояния. Можно убедиться, что *среды выполнения IoT Edge* извлекает контейнеров правильно, введя следующую команду:

    ```bash
        sudo docker ps
    ```

12. Должен появиться список с контейнерами два (2). Это значение по умолчанию модули, которые создаются автоматически службой центра Интернета вещей (edgeAgent и edgeHub). После создания и развертывания собственных модулей, они будут отображаться в этом списке, под по умолчанию.

## <a name="chapter-6---install-the-extensions"></a>Глава 6 - Установка расширения

> [!IMPORTANT]
> Далее несколько глав посвящены (6 – 9) должны быть выполнены на компьютере Windows 10.

1. Откройте **VS Code**.

2. Щелкните **расширения** кнопки (квадрат) на левой панели из VS Code, чтобы открыть **панели расширений**.

3. Поиск Чтобы установить, следующие расширения (как показано на рисунке ниже).

    1. Azure IoT Edge
    2. Azure IoT Toolkit
    3. Docker   

    ![Создание контейнера](images/AzureLabs-Lab313-24.png)

4. После установки расширения, закройте и снова откройте VS Code.

5. С помощью VS Code откройте еще раз, перейдите к **Вид > встроенный терминал**.

6. Будет выполнена установка **Cookiecutter**. В окне терминала выполните следующую команду bash:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! УКАЗАНИЕ] при наличии проблем с помощью следующей команды: 
    >1. Перезапустите VS Code и / или на компьютере.
    >2. Может потребоваться переключиться **терминал VS Code** на тот, который вы использовали для установки Python, т. е. **Powershell** (особенно если на компьютере уже установлена среда Python). В окне терминала вы найдете в раскрывающемся меню в правой части терминала.
     ![Создание контейнера](images/AzureLabs-Lab313-24b.png) 
    >3. Убедитесь, что **Python** путь установки добавляется как **переменной среды** на вашем компьютере. Cookiecutter должны входить в один и тот же путь расположения. Выполните инструкции из этого [ссылку на дополнительные сведения о переменных среды](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), 

7. Один раз **Cookiecutter** закончил установку всех продуктов, то необходимо перезапустить компьютер, таким образом, чтобы **Cookiecutter** распознается как команду, в среде вашей системы.

## <a name="chapter-7---create-your-container-solution"></a>Глава 7 - создание решения с контейнерами

На этом этапе необходимо создать контейнер, в модуле, помещаемых в *реестр контейнеров*. После отправки контейнера, вы воспользуетесь *концентратора IoT Edge* службы для развертывания на устройстве, работающего в *среды выполнения IoT Edge*.

1. В VS Code щелкните **представление > палитру команд**.

2. В палитре, искать и запускать **Edge Интернета вещей Azure: Новое решение Iot Edge**.

3. Перейдите в расположение, где вы хотите создать решение. Нажмите клавишу **ввод** ключ, чтобы принять расположение.

4. Присвойте имя для решения. Нажмите клавишу **ввод** ключ, чтобы подтвердить ваш предоставленное имя.

5. Теперь вам будет предложено выбрать framework шаблона для вашего решения. Нажмите кнопку **модуль Python**. Нажмите клавишу **ввод** ключ, чтобы подтвердить этот выбор.

6. Присвойте имя для вашего модуля. Нажмите клавишу **ввод** ключ, чтобы подтвердить имя модуля. Убедитесь, что внимание (с помощью «блокнота») и имя модуля, так как он используется в более поздней версии.

7. Обратите внимание, предварительно созданные *репозиторий образов Docker* адрес будет отображаться в палитре. Он имеет вид:

    **localhost:5000 / имя МОДУЛЯ -**. 

8. Удалить **localhost:5000**и в его место вставки *реестр контейнеров* **сервер входа** адрес, который вы записали при создании **контейнера Служба реестра** ([на шаге 8, Глава 2](#chapter-2---the-container-registry-service)). Нажмите клавишу **ввод** ключ для проверки адреса.

9. На этом этапе создается решение, содержащее шаблон для вашего модуля Python и его структура будет отображаться в **изучение вкладку**, окна VS Code, в левой части экрана. Если **изучение вкладку** является не открыто, его можно открыть, нажав кнопку верхнего уровня, на панели слева.

    ![Создание контейнера](images/AzureLabs-Lab313-25.png)

10. Последний шаг для этой главы — щелкните и откройте **env-файле**, изнутри **изучение вкладку**и добавьте ваш *реестр контейнеров* **имяпользователя** и **пароль**. Этот файл игнорируется git, но на создание приложений контейнера, будет задать учетные данные для доступа к **службы реестра контейнеров**.

    ![Создание контейнера](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Глава 8 - изменения решения с контейнерами

Теперь завершим решение контейнера, обновив следующие файлы:

- *основной<span></span>.py* скрипт python.
- *файл Requirements.txt*.
- *Deployment.Template.JSON*.
- *Dockerfile.AMD64*

После этого создается *образы* папку, используемую скрипт python для проверки изображений, будет сравниваться с вашей *Custom Vision модели*. Наконец, вы добавите *labels.txt* файл, чтобы облегчить чтение модели и *model.pb* файл, который является модель.

1. С помощью VS Code откройте, перейдите к папке модуля и найдите скрипт с именем **основной<span></span>.py**. Дважды щелкните, чтобы открыть его.

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

3.  Откройте файл с именем **requirements.txt**и замените его содержимое следующим:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Откройте файл с именем **deployment.template.json**и замените его следующее содержимое ниже рекомендации:

    1. Поскольку будет иметь свои собственные, уникальным, структура JSON, необходимо будет вручную изменить (вместо того, чтобы скопировать пример). Чтобы облегчить этот процесс, используйте под изображением в качестве руководства.
    2. Области, будет выглядеть иначе к вам, но какие **не следует изменять, выделяется желтым цветом**.
    3. **Разделы, которые необходимо удалить, — это выделенный красным значком.**
    4. Не забудьте удалить правильный квадратные скобки, а также удалять запятые.

        ![Создание контейнера](images/AzureLabs-Lab313-27.png)

    5. Завершенные JSON должен выглядеть приблизительно так: (менее, с вашей уникальных различий: *ссылки на имя пользователя/пароль/модуль имя или модуля*):

        ![Создание контейнера](images/AzureLabs-Lab313-28.png)

5.  Откройте файл с именем **Dockerfile.amd64**и замените его содержимое следующим:

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

6.  Щелкните правой кнопкой мыши по папке **модули** (он будет иметь имя, указанное ранее; в далее в примере работу, он называется *pythonmodule*) и щелкните **новую папку**. Назовите папку **образы**.

7.  В папке добавьте некоторые образы, содержащие мыши или клавиатуры. Это будет изображения, которые будут проанализированы с помощью модели Tensorflow.

    > [!WARNING]
    > Если вы используете собственную модель, необходимо будет изменить его в соответствии с собственными данными модели.

8.  Теперь необходимо будет получить **labels.txt** и **model.pb** файлы из папки модели, предыдущие загруженный (или созданы из собственных **пользовательская служба визуального распознавания** ), в [главе 1](#chapter-1---retrieve-the-custom-vision-model). Когда файлы, поместите их в решении, вместе с другими файлами. Окончательный результат должен выглядеть как на следующем рисунке:

    ![Создание контейнера](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Глава 9 - пакет решения как контейнеры

1.  Теперь вы готовы «упаковка» файлов в качестве контейнера и передать их в вашей **реестр контейнеров Azure**. В VS Code откройте *интегрированный терминал* (**представление > встроенный терминал / CTRL + "**) и используйте следующую строку для входа с использованием **Docker** (замените значения команду с учетными данными вашей **реестр контейнеров Azure (ACR)**):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Щелкните правой кнопкой мыши на файле **deployment.template.json**и нажмите кнопку **построить решение IoT Edge**. Этот процесс сборки занимает некоторое время (в зависимости от устройства), поэтому будьте готовы подождать. После завершения процесса построения, **deployment.json** файла должны быть созданы в новую папку с именем **config**.

    ![Создание развертывания](images/AzureLabs-Lab313-30.png)

3. Откройте **палитру команд** еще раз и выполните поиск **Azure: Войдите в**. Следуйте инструкциям на экране, используя свои учетные данные учетной записи Azure; VS Code предоставит вам возможность *копирование и открытие*, которая скопирует кода устройства скоро потребуется и откройте веб-браузере по умолчанию. Когда запрос, вставьте код устройства, для проверки подлинности компьютера.

    ![копирование и открытие](images/AzureLabs-Lab313-31.png)

4. Один раз со знаком в можно заметить, в нижней части *Проводник* панели новый раздел с именем **устройства центра Интернета вещей Azure**. Щелкните здесь, чтобы развернуть его.

    ![устройство Edge](images/AzureLabs-Lab313-32.png)

5. Если устройство здесь нет, необходимо будет щелкнуть правой кнопкой мыши *устройства центра Интернета вещей Azure*, а затем нажмите кнопку **задать строку подключения центра Интернета вещей**. Вы увидите, **палитру команд** (в верхней части VS Code), будет предлагать ввести ваш *строку подключения*. Это *строку подключения* вы записали в конце [Глава 3](#chapter-3---the-iot-hub-service). Нажмите клавишу **ввод** ключа, после копирования строки в.    

6. Устройство должно загружаются и отображаются. Щелкните правой кнопкой мыши имя устройства, а затем нажмите кнопку **Создание развертывания для одного устройства**.

    ![Создание развертывания](images/AzureLabs-Lab313-33b.png)

7. Вы получите *проводнике* строки, где вы можете перейти к **config** папку, а затем выберите **deployment.json** файла. С помощью этого файла, выбранного, щелкните **выбрать Edge манифест развертывания** кнопки.

    ![Создание развертывания](images/AzureLabs-Lab313-34.png)

8. На этом этапе вы предоставили вашей **службы центра Интернета вещей** с манифестом для него для развертывания контейнера, как модуль, из вашего **реестр контейнеров Azure**, эффективно развернуть его в устройстве.

9. Чтобы просмотреть сообщения, отправляемые с устройства в центр Интернета вещей, снова щелкните правой кнопкой мыши имя устройства в **устройства центра Интернета вещей Azure** раздела **Explorer** панели и щелкните **начать наблюдение Сообщения D2C**. Сообщения, отправляемые с устройства должны появиться в окне терминала VS. Сохраняйте Терпение, так как это может занять некоторое время. См. в разделе Далее отладки и проверки, если развертывание прошло успешно.

Этот модуль теперь будет повторяться, между ними в **образы** папки и анализировать их, с каждой итерацией. Это очевидно, что просто показывает, как получить основные машинного обучения модели для работы в среде устройств IoT Edge. 

Чтобы расширить функциональные возможности в этом примере, можно продолжить несколькими способами. Один из способов может быть включая некоторый код в контейнере, который фиксирует фотографий с веб-камера, подключенная к устройству, сохраняет изображения в папке images. 

Еще одним способом можете скопировать изображений из устройства в контейнер. Является удобным способом для этого выполните следующую команду на устройстве Интернета вещей терминалов (возможно небольшое приложение может выполнять задания, если вы хотели бы автоматизировать процесс). Эта команда можно проверить, запустив его вручную из папки, где хранятся файлы:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Глава 10 - отладки в среду выполнения IoT Edge

Ниже приведены список командные строки и советы, которые помогут отслеживать и отлаживать действия обмена сообщениями из *среды выполнения IoT Edge*, из вашего **устройство Ubuntu**. 

- Проверьте *среды выполнения IoT Edge* состояние, выполнив следующую команду:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Не забудьте нажать **Ctrl + C**, чтобы завершить, просмотрите ее состояние.

- Список контейнеров, развернутых в настоящее время. Если *службы центра Интернета вещей* развернул контейнеры успешно, они будут отображаться, выполнив следующую команду:

    ```bash
        sudo iotedge list
    ```

    или

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Выше показан хороший способ проверить ли модуль успешно развернуто, так как он будет отображаться в списке; в противном случае будет **только** см. в разделе *edgeHub* и *edgeAgent*.

- Чтобы отобразить код журналы контейнера, выполните следующую команду:

    ```bash
        journalctl -u iotedge
    ```

**Полезные команды для управления в среду выполнения Edge Интернета вещей:**

-  Чтобы удалить все контейнеры на узле:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Чтобы остановить *среды выполнения IoT Edge*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Глава 11. Создание службы таблиц 

Перейдите назад на портал Azure, которой будет создаваться в службу таблиц Azure, создав ресурс хранилища.

1. Если еще не выполнил вход, вход в [портал Azure](https://portal.azure.com).

2. После входа в систему, щелкните **создать ресурс**в левом верхнем углу, а поиск **учетной записи хранения**и нажмите клавишу **ввод** ключ, следует начать поиск.

3. После ее значок появился, нажмите кнопку **учетная запись хранения — большой двоичный объект, файл, таблица, очередь** из списка.

    ![Поиск учетной записи хранения](images/AzureLabs-Lab313-35.png)

4. Новая страница будет предоставить описание **учетной записи хранения** службы. В нижней левой части этого запроса, нажмите кнопку **создать** кнопку, чтобы создать экземпляр этого службу.

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-36.png)

5. Когда вы перейдете на **создать**, будут отображаться панели:

    1. Вставить нужный **имя** для данного экземпляра службы (*должны указываться прописными буквами*).

    2. Для **модели развертывания**, нажмите кнопку **Resource manager**.

    3. Для **тип учетной записи**, с помощью раскрывающегося списка, щелкните **хранилища (общего назначения версии 1)**.

    4. Щелкните соответствующий **расположение**.
    
    5. Для **репликации** в раскрывающемся меню щелкните **Read-access геоизбыточного хранилища (RA-GRS)**.

    6. Для **производительности**, нажмите кнопку **стандартный**.

    7. В рамках **требуется безопасное перемещение** щелкните **отключено**.

    8. Из **подписки** в раскрывающемся меню выберите соответствующую подписку.

    9. Выберите **группы ресурсов** или создайте новую. Для отслеживания, контроля доступа, подготовки и управлять, выставление счетов для коллекции активов Azure позволяет группе ресурсов. Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Оставьте **виртуальные сети** как **отключено**, если этот вариант для вас.

    11. Нажмите кнопку **Создать**.

        ![Заполните сведения о хранилище](images/AzureLabs-Lab313-37.png)

6. Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.

7. Уведомление будет отображаться на портале, после создания экземпляра службы. Щелкните уведомлений для просмотра в новом экземпляре службы.

    ![новое уведомление хранилища](images/AzureLabs-Lab313-38.png)

8. Нажмите кнопку **перейти к ресурсу** кнопки в уведомления, а также будут выполнены на новую страницу Общие сведения о службе хранилища экземпляра.

    ![Перейти к ресурсу](images/AzureLabs-Lab313-39.png)

9. На странице обзора, в правой части окна щелкните **таблиц**.
    
    ![Таблицы](images/AzureLabs-Lab313-40.png)

10. На правой панели появятся **службы таблиц** сведения, в которой необходимо добавить новую таблицу. Это можно сделать, щелкнув **+ таблицы** кнопку в левом верхнем углу.

    ![Открытие таблиц](images/AzureLabs-Lab313-41.png)

11. Новая страница отображается, при котором необходимо ввести **имя таблицы**. Это имя, которое будет использовать для обращения к данным в приложении в последующих главах (Создание приложения-функции и Power BI). Вставить **IoTMessages** как имя (вы можете выбрать собственные, просто запомните его при использовании этого документа) и нажмите кнопку **ОК**. 

12. После создания новой таблицы, можно будет увидеть в **службы таблиц** страницы (внизу).

    ![создать новую таблицу](images/AzureLabs-Lab313-42.png)  

13. Теперь щелкните **ключи доступа** и сделайте копию **имя учетной записи хранения** и **ключ** (с помощью вашей Блокнот), эти значения понадобятся позже в этом курсе, при создании **Приложения-функции azure**.

    ![создать новую таблицу](images/AzureLabs-Lab313-43.png) 

14. С помощью панели слева, прокрутите до *службы таблиц* раздела и нажмите кнопку **таблиц** (или **обзор таблиц**, на более новые порталах) и сделайте копию  **URL-адрес таблицы** (с помощью вашей блокнота). Это значение будет использовать позже в этом курсе, при связывании таблицы вашей **Power BI** приложения.

    ![создать новую таблицу](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Глава 12 - завершение таблицы Azure

Теперь, когда ваш **службы таблиц** учетной записи хранения установлен и настроен, пришло время для добавления данных, который будет использоваться для хранения и извлечения данных. Редактирование таблиц можно сделать с помощью **Visual Studio**.

1. Откройте **Visual Studio** (**не** Visual Studio Code).

2. В меню **представление > Cloud Explorer**.

    ![Откройте cloud explorer](images/AzureLabs-Lab313-45.png)

3. **Cloud Explorer** будут открываться как закрепленного элемента (быть пациента, так как загрузка может занять время).

    > [!WARNING] 
    > Если подписка использовалась для создания вашего *учетные записи хранения* не отображается, убедитесь, что у вас есть: 
    > - Вход в ту же учетную запись, которая использовалась для портала Azure.
    > - Выбранные подписки на странице управления учетными записями (может потребоваться применить фильтр из параметров учетной записи):  
    >
    >   ![найти подписку](images/AzureLabs-Lab313-46.png)

4. Будут показаны облачных служб Azure. Найти **учетные записи хранения** и щелкните стрелку влево, чтобы развернуть учетные записи.

    ![Откройте учетные записи хранения](images/AzureLabs-Lab313-47.png)

5. После развернут, только что созданный **учетной записи хранения** должны быть доступны. Щелкните стрелку слева от хранилища и найдите после, развернута, **таблиц** и щелкните стрелку рядом с ним, чтобы отобразить **таблицы** созданный в предыдущей главе. Дважды щелкните ваш **таблицы**.

6. Таблица откроется в центре окна Visual Studio. Щелкните значок таблицы с **+** (плюс) на нем.

    ![Добавление новой таблицы](images/AzureLabs-Lab313-48.png)

7. Откроется окно с запроса позволяет *Добавление сущности*. Вы создадите только одну сущность, на то, что он будет иметь три свойства. Можно будет заметить, что *PartitionKey* и *RowKey* уже предоставляются, так как они используются в таблице для поиска данных. 

    ![ключ раздела и строки](images/AzureLabs-Lab313-49.png)

8. Обновите следующие значения:

    - Имя: **PartitionKey**, значение: **PK_IoTMessages** 

    - Имя: **RowKey**, значение: **RK_1_IoTMessages** 

9. Щелкните **добавить свойство** (в левом нижнем углу *Добавление сущности* окна) и добавьте следующее свойство:

    - **Содержимое MessageContent**, как *строка*, оставьте значение пустым.

10. Таблица должна совпадать с той, на рисунке ниже:

    ![добавить правильные значения](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > Почему сущность имеет номер 1 в ключ строки, так как может потребоваться добавить дополнительные сообщения, следует желании поэкспериментировать с помощью этого курса.

11. Нажмите кнопку **ОК** при завершении работы. Таблица теперь готов для использования.

## <a name="chapter-13---create-an-azure-function-app"></a>Глава 13 - Создание приложения-функции Azure 

Пришло время теперь для создания *приложение-функцию Azure*, которого будет вызываться *службы центра Интернета вещей* для хранения *IoT Edge* устройства сообщений в **таблицы** Служба, которая была создана в предыдущей главе.

Во-первых необходимо создать файл, который позволит загружать библиотеки, необходимые функции Azure.

1.  Откройте **Блокнот** (нажмите клавишу *ключ Windows*и тип *Блокнот*).

    ![Откройте в блокноте](images/AzureLabs-Lab313-51.png)

2.  Откройте Блокнот вставьте в него приведенную ниже структуру JSON. Как только вы это сделали, сохраните его на рабочем столе как **project.json**. Этот файл определяет библиотеки, которые будет использовать функции. При использовании NuGet, будут вам знакомы.
    
    > [!WARNING]
    > Очень важно, что система именования является верным; обеспечить его **нет .txt** расширение файла. Ниже приведены ссылки.
    >
    > ![JSON, сохранение](images/AzureLabs-Lab313-52.png)

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

3.  Войдите в [портала Azure](https://portal.azure.com).

4.  После входа в систему щелкните **создать ресурс** в левом верхнем углу, а поиск **приложения-функции**и нажмите клавишу **ввод** искомый ключ. Нажмите кнопку *приложения-функции* из результатов, чтобы открыть новую область.

    ![Поиск приложения-функции](images/AzureLabs-Lab313-53.png)

5.  Новая панель предоставляет описание **приложения-функции** службы. В левом нижнем этой панели, щелкните **создать** кнопку, чтобы создать ассоциацию с данным службы.

    ![экземпляре приложения-функции](images/AzureLabs-Lab313-54.png)

6.  Когда вы перейдете на **создать**, задайте приведенные ниже:

    1. Для **имя_приложения**, вставить желаемого имени для данного экземпляра службы.

    2. Выберите **подписки**.

    3. Выберите ценовую категорию, соответствующие, если это первое время создания **функция службы приложений**, уровень "бесплатный" должны быть доступны для вас.

    4. Выберите **группы ресурсов** или создайте новую. Для отслеживания, контроля доступа, подготовки и управлять, выставление счетов для коллекции активов Azure позволяет группе ресурсов. Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).

        > Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Для **ОС**, нажмите кнопку Windows, так как целевую платформу.

    6. Выберите **текущему плану размещения и** (этот учебник использование **план потребления**.

    7. Выберите **расположение** (выберите то же расположение, как хранилище, вы создали на предыдущем шаге)

    8. Для **хранения** разделе **необходимо выбрать службу хранения, созданную на предыдущем шаге**.

    9. Вам не потребуется *Application Insights* в этом приложении, поэтому вы можете оставить его **Off**.

    10. Нажмите кнопку **Создать**.

        ![Создайте новый экземпляр](images/AzureLabs-Lab313-55.png)

7.  Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.

8.  Уведомление будет отображаться на портале, после создания экземпляра службы.

    ![новое уведомление](images/AzureLabs-Lab313-56.png)

9.  Щелкните уведомление, после успешного развертывания (завершено).

10. Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы. 

    ![Перейти к ресурсу](images/AzureLabs-Lab313-57.png)

11. В левой части новой панели, щелкните **+** (плюс) значок рядом с полем *функции*, чтобы создать новую функцию.

    ![Добавление новой функции](images/AzureLabs-Lab313-58.png)

12. На центральной панели **функция** откроется окно создания. Прокрутите дальше и щелкните **пользовательская функция**.

    ![Пользовательская функция](images/AzureLabs-Lab313-59.png)

13. Прокрутите страницу вниз, далее, пока не найдете **центра Интернета вещей (концентратора событий)**, затем щелкните его.

    ![Пользовательская функция](images/AzureLabs-Lab313-60.png)

14. В **центра Интернета вещей (концентратора событий)** задать колонке **языка** для **C#** и выберите команду **новый**.

    ![Пользовательская функция](images/AzureLabs-Lab313-61.png)

15. Убедитесь, что в окне, которое будет отображаться, **центра Интернета вещей** выбран и имя *центра Интернета вещей* соответствует поле с именем вашей *службы центра Интернета вещей* , у вас есть созданный ранее ([на шаге 8, Глава 3](#chapter-3---the-iot-hub-service)). Нажмите кнопку **выберите** кнопки.

    ![Пользовательская функция](images/AzureLabs-Lab313-62.png)

16. Вернитесь на **центра Интернета вещей (концентратора событий)** щелкните **создать**.

    ![Пользовательская функция](images/AzureLabs-Lab313-63.png)

17. Вы будете перенаправлены к редактору функции.

    ![Пользовательская функция](images/AzureLabs-Lab313-64.png)

18. Удалите весь код в нем и замените его следующим кодом:

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

19. Измените следующие переменные, таким образом, чтобы они соответствуют соответствующие значения (**таблицы** и **хранения** значения, из [шаг с 11 и 13, соответственно, глава 11](#chapter-11---create-table-service)), Вы найдете в вашей **учетной записи хранения**:

    - **tableName**, именем вашего **таблицы** в вашей **учетной записи хранения**.
    - **tableURL**, URL-адресом вашей **таблицы** в вашей **учетной записи хранения**.
    - **storageAccountName**, именем значение, соответствующее имя вашей **учетной записи хранения** имя.
    - **storageAccountKey**, с ключом, полученным в службе хранилища, созданный ранее.

    ![Пользовательская функция](images/AzureLabs-Lab313-65.png)

20. С помощью кода в месте, нажмите кнопку **Сохранить**.

21. Затем щелкните **\<** значок (стрелка), в правой части страницы.

    ![Пользовательская функция](images/AzureLabs-Lab313-66.png)

22. Панель будет слайд в справа. В этой панели, щелкните **отправить**и *браузер файлов* будет отображаться.

23. Перейдите к и нажмите кнопку, **project.json** файл, который вы создали в **Блокнот** ранее и нажмите кнопку **откройте** кнопки. Этот файл определяет библиотеки, на которые будет использовать функции.

    ![Пользовательская функция](images/AzureLabs-Lab313-67.png)

24. Когда файл отправлен, он будет отображаться на панели справа. Если щелкнуть его, откроется его в **функция** редактора. Он должен выглядеть **точно** так же, как следующему изображению.

    ![Пользовательская функция](images/AzureLabs-Lab313-68.png)

25. На этом этапе было бы неплохо для тестирования возможности этой функции для сохранения сообщения на ваш *таблицы*. В верхней правой части окна, щелкните **теста**.

    ![Пользовательская функция](images/AzureLabs-Lab313-69.png)

26. Вставка сообщения в **текст запроса**, как показано в показанном выше рисунке и нажмите кнопку на **запуска**. 

27. Функция будет выполняться, отображения состояния результата (появится зеленая **состояние 202 Accepted**выше *вывода* окно, которое означает, что он был успешно выполнен вызов):

    ![Выходной результат](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Глава 14 - представление активных сообщений

Если теперь открыть Visual Studio (**не** Visual Studio Code), вы можете визуализировать сообщения результатами теста, так как он будет храниться в *содержимое MessageContent* строка области.

![Пользовательская функция](images/AzureLabs-Lab313-71.png)

С помощью службы таблиц и приложения-функции на месте, Ubuntu сообщения устройства будет отображаться в вашей *IoTMessages* таблицы. Если еще не работает, запустите устройства и вы сможете видны результат сообщения с устройства и модуль, в пределах таблицы, с помощью Visual Studio *Cloud Explorer*.

![Визуализация данных](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Глава 15 - установки Power BI

Для визуализации данных из устройства Интернета ВЕЩЕЙ, помогут вам настроить **Power BI** (версии), для сбора данных из *таблицы* службы, который вы только что создали. *HoloLens* версию Power BI будет использовать эти данные для визуализации результат.

1.  Откройте Microsoft Store в Windows 10 и выполните поиск **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Скачайте приложение. После завершения загрузки, откройте его.

3.  Войдите на *Power BI* с вашей **учетной записи Microsoft 365**. Вы может перенаправляться в браузере, чтобы зарегистрироваться. После вы зарегистрировались, вернитесь в приложение Power BI и снова войти в систему.

4.  Щелкните **получить данные** и выберите команду **более...** .

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Нажмите кнопку **Azure**, **Azure Table Storage**, затем щелкните **Connect**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Вам будет предложено вставить **URL-адрес таблицы** собранными ранее ([на шаге 13 Глава 11](#chapter-11---create-table-service)), при создании службы таблиц. После вставки URL-адрес, удалите часть пути, относящаяся к таблице «вложенную папку», (который был IoTMessages, в этом курсе). Окончательный результат должен быть, показанной на рисунке ниже. Нажмите кнопку на **ОК**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Вам будет предложено вставить **ключ к хранилищу** , записанными ([на шаге 11 Глава 11](#chapter-11---create-table-service)) ранее при создании хранилище таблиц. Нажмите кнопку на **Connect**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Объект **панель "Navigator"** будет отображаться, установите флажок рядом с таблицы и щелкните **нагрузки**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. Таблица теперь загружена в Power BI, но он требует запрос для отображения значения в нем. Чтобы сделать это, щелкните правой кнопкой мыши на имя таблицы, расположенных в **«поля»** в правой части экрана. Нажмите кнопку на **изменить запрос**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Объект **редактора Power Query** откроется в новом окне, отображение таблицы. Щелкните слово **записи** в *содержимого* столбец таблицы, для визуализации хранимых содержимого.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Щелкните **в таблице**, в верхней левой части окна. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Щелкните **закрыть и применить**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. После завершения загрузки запроса, в **«поля»**, в правой части экрана, установите флажки рядом с соответствующими параметрами **имя** и **значение**, визуализация **содержимое MessageContent** содержимое столбца.

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Щелкните **значок синей диска** в левой верхней части окна, чтобы сохранить результаты работы в папку по своему усмотрению.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Теперь можно щелкнуть "Опубликовать" для передачи таблицы в рабочей области. При появлении запроса, щелкните **Моя рабочая область** и нажмите кнопку *выберите*. Подождите вывести результат успешной отправки.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> Следующая глава — определенные HoloLens. Power BI не является доступна в качестве иммерсивные приложения, однако запуском настольной версии на портале Windows смешанной реальности (также называемые со скалы дома), через классическое приложение.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Глава 16 - Power BI для отображения данных на HoloLens

1. На ваш HoloLens, войдите в **Microsoft Store**, можно просмотреть, выбрав его значок в списке приложений.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. Найдите и загрузите **Power BI** приложения.

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. Запуск **Power BI** из списка приложений. 

4. **Power BI** может потребоваться выполнить вход в ваш **учетной записи Microsoft 365**.

5. Один раз в приложении, в рабочей области должен отображаться по умолчанию как показано на рисунке ниже. Если, не произойдет, просто щелкните значок рабочую область в левой части окна.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Ваш завершения приложения Интернета вещей

Поздравляем, вы успешно создали службу центра Интернета вещей с имитацией устройства Edge виртуальной машины. Устройства могут взаимодействовать результатов модели в службе таблиц Azure, с помощью приложения-функции Azure, который считывается в Power BI и визуализации в Microsoft HoloLens машинного обучения.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Упражнения премии

### <a name="exercise-1"></a>Упражнение 1

Разверните структуру обмена сообщениями, хранящиеся в таблице и отобразить ее в виде графа. Можно собирать данные и сохраните его в той же таблице, отображаемый более поздней версии.

### <a name="exercise-2"></a>Упражнение 2

Создайте дополнительный модуль «запись с камеры» для развертывания на доске Интернета вещей, таким образом, служба может записывать образы через камеру для анализа.
