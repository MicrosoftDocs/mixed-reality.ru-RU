---
title: Учебники по облачным службам Azure, часть 2. Интеграция службы хранилища Azure
description: Из этого курса вы узнаете, как реализовать Хранилище таблиц Azure и Хранилище BLOB-объектов Azure в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, unity, учебник, hololens, hololens 2, служба хранилища azure
ms.localizationpriority: high
ms.openlocfilehash: a8d91bc55b3ce73d6e1fb46e5d696d853adcf871
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376476"
---
# <a name="2-integrating-azure-storage"></a>2. Интеграция службы хранилища Azure

Из этого учебника вы узнаете, как сохранить данные сущности в Хранилище таблиц Azure и эскизы в Хранилище BLOB-объектов Azure. Эта функция позволяет хранить и получать *отслеживаемые объекты* с такими данными, как идентификатор, имя, эскиз и т. д., между сеансами и устройствами в облаке.

## <a name="objectives"></a>Задачи

* Познакомиться с основами службы хранилища Azure.
* Узнать, как хранить, изменять и получать данные из Хранилища таблиц.
* Узнать, как хранить и удалять изображения из Хранилища BLOB-объектов.

## <a name="understanding-azure-storage"></a>Общие сведения о службе хранилища Azure

**Служба хранилища Azure** — это решение Майкрософт для хранения данных в облаке, которое может охватывать множество сценариев и требований. Оно может быстро масштабироваться, а также быть легкодоступным для разработчиков. Все службы можно использовать из **учетной записи службы хранилища Azure**. В нашем случае мы будем использовать *Хранилище таблиц* и *Хранилище BLOB-объектов*.

Дополнительные сведения о [службах хранилища Azure](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview).

### <a name="azure-table-storage"></a>Хранилище таблиц Azure

Эти службы позволяют хранить данные в виде NoSQL. В этом проекте мы используем их для хранения информации об *отслеживаемом объекте* (например, имя, описание, идентификатор пространственной привязки и многое другое).

В контексте демонстрационного приложения требуются две таблицы: одна для хранения сведений о проекте с информацией о состоянии обученных моделей (подробнее об этом в учебнике [Интеграция Пользовательского визуального распознавания Azure](mr-learning-azure-03.md)), а вторая — для хранения сведений об *отслеживаемых объектах*.

Дополнительные сведения о [хранилище таблиц Azure](https://docs.microsoft.com/azure/storage/tables/table-storage-overview).

### <a name="azure-blob-storage"></a>Хранилище BLOB-объектов Azure

Эта служба позволяет хранить большие двоичные файлы. Ее можно использовать для хранения фотографий *отслеживаемых объектов* в виде эскиза.
Для демонстрационного приложения необходим один контейнер BLOB-объектов для хранения изображений.

Подробнее о [Хранилище BLOB-объектов Azure](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction).

## <a name="preparing-azure-storage"></a>Подготовка службы хранилища Azure

Для использования служб хранилища Azure потребуется учетная запись хранения Azure. Сведения о создании учетной записи хранения см. [здесь](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal). Дополнительные сведения об учетных записях хранения см. в [этой статье](https://docs.microsoft.com/azure/storage/common/storage-account-overview).

Как только у вас будет учетная запись хранения, вы сможете получить строку подключения на **портале Azure**, которая потребуется в следующем разделе этого урока.

### <a name="optional-azure-storage-explorer"></a>Обозреватель службы хранилища Azure (необязательно)

Хотя вы можете просматривать и проверять все изменения данных из пользовательского интерфейса в приложении, рекомендуется установить [Обозреватель службы хранилища Azure](https://azure.microsoft.com/features/storage-explorer/). Это средство позволяет визуально просматривать данные в службе хранилища Azure и существенно помогает при отладке и обучении.

> [!TIP]
> Для тестирования в редакторе Unity можно использовать локальный эмулятор:

> * в Windows 10 можно использовать [эмулятор хранения Azure](https://docs.microsoft.com/azure/storage/common/storage-use-emulator);
> * в MacOS/Linux можно использовать [образ Azurite](https://hub.docker.com/_/microsoft-azure-storage-azurite) для Docker.

## <a name="preparing-the-scene"></a>Подготовка сцены

В окне Hierarchy (Иерархия) найдите и выберите объект **DataManager**.

![mr-learning-azure](images/mr-learning-azure/tutorial2-section4-step1-1.png)

В окне Inspector (Инспектор) вы увидите, что в компоненте **DataManager (script)** (DataManager — скрипт) хранятся все параметры **службы хранилища Azure**. Все соответствующие параметры уже заданы, нужно просто заменить значение в поле *Connection String* (Строка подключения) на то, которое можно получить на портале Azure. Если вы используете локальное решение эмулятора хранения Azure, вы можете сохранить уже предоставленное значение для параметра *Connection String* (Строка подключения).

Компонент **DataManager (script)** (DataManager — скрипт) отвечает за взаимодействие с **Хранилищем таблиц** и **Хранилищем BLOB-объектов**, которые используются другими скриптами контроллера в компонентах пользовательского интерфейса.

## <a name="writing-and-reading-data-from-azure-table-storage"></a>Запись и чтение данных из Хранилища таблиц Azure

Все подготовлено, пора создать *отслеживаемый объект*.

Откройте приложение на устройстве HoloLens, щелкните **Set Object** (Настроить объект), вы увидите, как объект *EnterObjectName* станет активным в иерархии. В этом меню щелкните *панель поиска* и введите имя, которое вы хотите дать *отслеживаемому объекту*. После указания имени нажмите кнопку **Set object** (Настроить объект). При этом будет создан *отслеживаемый объект* в Хранилище таблиц Azure, и вы увидите **карту объекта**.

Эта **карта объекта** является представлением пользовательского интерфейса *отслеживаемого объекта* и будет играть важную роль в этой серии учебников.

Теперь щелкните *текстовое поле* описания и введите Car (Автомобиль), после этого нажмите кнопку **Save** (Сохранить), чтобы сохранить изменения. Остановите работу приложения и запустите его повторно.

Теперь щелкните **Search Object** (Поиск объекта) и введите на *панели поиска* имя, которое задавалось при создании *отслеживаемого объекта*. Вы увидите, что **карта объекта** со всеми данными извлекается из **Хранилища таблиц Azure**.

Вы можете закрывать **карту объекта**, создавать *отслеживаемые объекты* и изменять их данные.

> [!TIP]
> Если вы установили [Обозреватель службы хранилища Azure](https://azure.microsoft.com/features/storage-explorer/), просмотрите таблицу *объектов*, и вы увидите там созданный *отслеживаемый объект*.

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>Отправка и скачивание изображения из Хранилища BLOB-объектов Azure

В этом разделе вы будете использовать Хранилище BLOB-объектов Azure для отправки и скачивания изображений, которые будут использоваться в качестве эскизов для *отслеживаемых объектов*.

> [!NOTE]
> В этом учебнике приложение будет делать фотографии для отправки изображений в Хранилище BLOB-объектов. Если вы запускаете его локально из редактора Unity, убедитесь в наличии подключенной к компьютеру веб-камеры.

Откройте приложение на устройстве HoloLens, щелкните **Set Object** (Настроить объект) и введите на *панели поиска* Car (Автомобиль). Теперь вы увидите **карту объекта**, нажмите кнопку **Camera** (Камера), и вам будет предложено выполнить жест касания для фотосъемки. После фотосъемки вы увидите сообщение об активной передаче, а через некоторое время там, где раньше был заполнитель, должно появиться изображение.

Теперь перезапустите приложение и найдите *отслеживаемый объект*, а ранее отправленное изображение должно появиться в виде эскиза.

## <a name="deleting-image-from-azure-blob-storage"></a>Удаление изображения из Хранилища BLOB-объектов Azure

В предыдущем разделе вы передавали новые изображения в Хранилище BLOB-объектов Azure. В этом разделе вы удалите эскиз для *отслеживаемых объектов*.

Откройте приложение на устройстве HoloLens, щелкните **Set Object** (Настроить объект) и введите на *панели поиска* Car (Автомобиль). Теперь вы увидите **карту объекта** с эскизом, нажмите кнопку **Delete** (Удалить). Вы увидите, что эскиз заменится изображением заполнителя.

Теперь перезапустите приложение и найдите *отслеживаемый объект* ранее удаленного эскиза, вы должны увидеть только изображение заполнителя.

## <a name="congratulations"></a>Поздравляем!

Из этого учебника вы узнали, как с помощью службы хранилища Azure можно сохранять неструктурированные данные (например, в нашем случае **отслеживаемые объекты** и двоичные файлы) в виде эскизов для демонстрационного приложения **HoloLens 2** в облаке.

Из следующего учебника вы узнаете, как использовать Пользовательское визуальное распознавание Azure для обнаружения изображений, связанных с *отслеживаемым объектом*.

[Следующее руководство: 3. Интеграция Пользовательского визуального распознавания Azure](mr-learning-azure-03.md)
