---
title: Пользовательские каналы данных с удаленным взаимодействием holographic
description: Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное подключение Holographic.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: a862fa52695c7bfb94b58c6c0b85606a112835da
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434274"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="549e8-104">Пользовательские каналы данных с удаленным взаимодействием holographic</span><span class="sxs-lookup"><span data-stu-id="549e8-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="549e8-105">Это руководство относится к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="549e8-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="549e8-106">Используйте пользовательские каналы данных для отправки пользовательских данных через установленное удаленное соединение.</span><span class="sxs-lookup"><span data-stu-id="549e8-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="549e8-107">Для пользовательских каналов данных требуется пользовательское ведущее приложение и пользовательское приложение проигрывателя, так как оно обеспечивает взаимодействие между двумя пользовательскими приложениями.</span><span class="sxs-lookup"><span data-stu-id="549e8-107">Custom data channels require a custom host app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="549e8-108">Простой пример для проверки связи можно найти в примерах узлов и проигрывателей в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="549e8-108">A simple ping-pong example can be found in the host and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="549e8-109">Раскомментируйте ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` в файлах Самплехостмаин. h/Самплеплайермаин. h, чтобы включить пример кода.</span><span class="sxs-lookup"><span data-stu-id="549e8-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleHostMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="549e8-110">Создание пользовательского канала данных</span><span class="sxs-lookup"><span data-stu-id="549e8-110">Create a custom data channel</span></span>


<span data-ttu-id="549e8-111">Для создания пользовательского канала данных требуются следующие поля:</span><span class="sxs-lookup"><span data-stu-id="549e8-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="549e8-112">После успешной установки подключения можно инициировать создание новых каналов данных с помощью узла и (или) стороны проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="549e8-112">After a connection was successfully established, the creation of new data channels can be initiated from either the host side and/or the player side.</span></span> <span data-ttu-id="549e8-113">Ремотеконтекст и Плайерконтекст предоставляют для этого метод ```CreateDataChannel()```.</span><span class="sxs-lookup"><span data-stu-id="549e8-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="549e8-114">Первый параметр — это идентификатор канала, который используется для идентификации канала данных в операциях сусекуент.</span><span class="sxs-lookup"><span data-stu-id="549e8-114">The first parameter is the channel ID which is used to identify the data channel in susequent operations.</span></span> <span data-ttu-id="549e8-115">Вторым параметром является приоритет, указывающий приоритет, с которым данные этого канала передаются на другую сторону.</span><span class="sxs-lookup"><span data-stu-id="549e8-115">The second paramter is the priority which specifies the priority with which data of this channel is transfered to the other side.</span></span> <span data-ttu-id="549e8-116">Допустимый диапазон идентификаторов каналов — от 0 до 63 для стороны узла и 64 вплоть до 127 для стороны проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="549e8-116">The valid range for channel IDs is 0 up to and including 63 for the host side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="549e8-117">Допустимые приоритеты: ```Low```, ```Medium``` или ```High``` (с обеих сторон).</span><span class="sxs-lookup"><span data-stu-id="549e8-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="549e8-118">Чтобы инициировать создание канала данных на стороне **узла** , выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="549e8-118">To initiate the creation of a data channel on the **host** side:</span></span>
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="549e8-119">Чтобы инициировать создание канала данных на стороне **проигрывателя** , сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="549e8-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="549e8-120">Для создания нового пользовательского канала данных только одна сторона (узел или проигрыватель) должна вызывать метод ```CreateDataChannel```.</span><span class="sxs-lookup"><span data-stu-id="549e8-120">To create a new custom data channel, only one side (either host or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="549e8-121">Обработка пользовательских событий канала данных</span><span class="sxs-lookup"><span data-stu-id="549e8-121">Handling custom data channel events</span></span>

<span data-ttu-id="549e8-122">Чтобы установить пользовательский канал данных, необходимо обработать событие ```OnDataChannelCreated``` (как в проигрывателе, так и на стороне главного приложения).</span><span class="sxs-lookup"><span data-stu-id="549e8-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the host side).</span></span> <span data-ttu-id="549e8-123">Он активируется, когда канал данных пользователя создается с помощью одной из сторон и предоставляет объект ```IDataChannel```, который можно использовать для отправки и получения данных по этому каналу.</span><span class="sxs-lookup"><span data-stu-id="549e8-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="549e8-124">Чтобы зарегистрировать прослушиватель в событии ```OnDataChannelCreated```, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="549e8-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="549e8-125">Чтобы получать уведомления о получении данных, зарегистрируйте событие ```OnDataReceived``` в объекте ```IDataChannel```, предоставленном обработчиком ```OnDataChannelCreated```.</span><span class="sxs-lookup"><span data-stu-id="549e8-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="549e8-126">Зарегистрируйте событие ```OnClosed```, чтобы получать уведомления при закрытии канала данных.</span><span class="sxs-lookup"><span data-stu-id="549e8-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a><span data-ttu-id="549e8-127">Отправка данных</span><span class="sxs-lookup"><span data-stu-id="549e8-127">Sending data</span></span>

<span data-ttu-id="549e8-128">Для отправки данных через пользовательский канал данных используйте метод ```IDataChannel::SendData()```.</span><span class="sxs-lookup"><span data-stu-id="549e8-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="549e8-129">Первое значение параметра — это ```winrt::array_view<const uint8_t>``` данных, которые должны быть отправлены.</span><span class="sxs-lookup"><span data-stu-id="549e8-129">The first paramter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="549e8-130">Второй параметр указывает, вхетер ли данные должны быть повторно отправлены, пока другая сторона не подтвердит получение.</span><span class="sxs-lookup"><span data-stu-id="549e8-130">The second parameter specifies wheter the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="549e8-131">В случае неудачных условий сети один и тот же пакет данных может быть доставлен более одного раза.</span><span class="sxs-lookup"><span data-stu-id="549e8-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="549e8-132">Получающий код должен иметь возможность справиться с этой ситуацией.</span><span class="sxs-lookup"><span data-stu-id="549e8-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="549e8-133">Закрытие пользовательского канала данных</span><span class="sxs-lookup"><span data-stu-id="549e8-133">Closing a custom data channel</span></span>

<span data-ttu-id="549e8-134">Чтобы закрыть пользовательский канал данных, используйте метод ```IDataChannel::Close()```.</span><span class="sxs-lookup"><span data-stu-id="549e8-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="549e8-135">После закрытия пользовательского канала данных обе стороны будут уведомлены событием ```OnClosed```.</span><span class="sxs-lookup"><span data-stu-id="549e8-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="549e8-136">См. также</span><span class="sxs-lookup"><span data-stu-id="549e8-136">See Also</span></span>
* [<span data-ttu-id="549e8-137">Создание хост-приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="549e8-137">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="549e8-138">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="549e8-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="549e8-139">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="549e8-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="549e8-140">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="549e8-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="549e8-141">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="549e8-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
