---
title: Пользовательские каналы данных с удаленным взаимодействием holographic
description: Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное подключение Holographic.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: 12fa47b6b3a46521a9e6029cab61fa1c628c06e9
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278102"
---
# <a name="custom-holographic-remoting-data-channels"></a>Пользовательские каналы данных с удаленным взаимодействием holographic

>[!NOTE]
>Это руководство относится к удаленному взаимодействию с HoloLens 2.

Используйте пользовательские каналы данных для отправки пользовательских данных через установленное удаленное соединение.

>[!IMPORTANT]
>Для пользовательских каналов данных требуется пользовательское удаленное приложение и пользовательское приложение проигрывателя, так как оно обеспечивает взаимодействие между двумя пользовательскими приложениями.

>[!TIP]
>Простой пример для проверки связи можно найти в примерах для удаленного доступа и проигрывателя в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Раскомментируйте ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` в файлах Самплеремотемаин. h/Самплеплайермаин. h, чтобы включить пример кода.


## <a name="create-a-custom-data-channel"></a>Создание пользовательского канала данных


Для создания пользовательского канала данных требуются следующие поля:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

После успешной установки подключения можно инициировать создание новых каналов данных с удаленной стороны или с стороны проигрывателя. Ремотеконтекст и Плайерконтекст предоставляют для этого метод ```CreateDataChannel()```. Первый параметр — это идентификатор канала, который используется для идентификации канала данных в последующих операциях. Второй параметр — приоритет, указывающий приоритет, с которым данные этого канала передаются на другую сторону. Допустимый диапазон идентификаторов каналов — от 0 до 63 для удаленной стороны, а 64 — до 127 для стороны проигрывателя. Допустимые приоритеты: ```Low```, ```Medium``` или ```High``` (с обеих сторон).

Чтобы инициировать создание канала данных на **удаленной** стороне, выполните следующие действия.
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Чтобы инициировать создание канала данных на стороне **проигрывателя** , сделайте следующее:
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Чтобы создать новый пользовательский канал данных, необходимо вызвать метод ```CreateDataChannel``` только одной стороне (удаленно или с помощью проигрывателя).

## <a name="handling-custom-data-channel-events"></a>Обработка пользовательских событий канала данных

Чтобы установить пользовательский канал данных, необходимо обработать событие ```OnDataChannelCreated``` (как на проигрывателе, так и на удаленной стороне). Он активируется, когда канал данных пользователя создается с помощью одной из сторон и предоставляет объект ```IDataChannel```, который можно использовать для отправки и получения данных по этому каналу.

Чтобы зарегистрировать прослушиватель в событии ```OnDataChannelCreated```, выполните следующие действия.
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Чтобы получать уведомления о получении данных, зарегистрируйте событие ```OnDataReceived``` в объекте ```IDataChannel```, предоставленном обработчиком ```OnDataChannelCreated```. Зарегистрируйте событие ```OnClosed```, чтобы получать уведомления при закрытии канала данных.

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

## <a name="sending-data"></a>Отправка данных

Для отправки данных через пользовательский канал данных используйте метод ```IDataChannel::SendData()```. Первый параметр — это ```winrt::array_view<const uint8_t>``` данных, которые должны быть отправлены. Второй параметр указывает, куда следует повторно отправить данные, пока другая сторона не подтвердит получение. 

>[!IMPORTANT]
>В случае неудачных условий сети один и тот же пакет данных может быть доставлен более одного раза. Получающий код должен иметь возможность справиться с этой ситуацией.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Закрытие пользовательского канала данных

Чтобы закрыть пользовательский канал данных, используйте метод ```IDataChannel::Close()```. После закрытия пользовательского канала данных обе стороны будут уведомлены событием ```OnClosed```.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>См. также
* [Создание удаленного приложения holographic с удаленным взаимодействием](holographic-remoting-create-host.md)
* [Написание пользовательского приложения для удаленного взаимодействия holographic](holographic-remoting-create-player.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkId=521839)
