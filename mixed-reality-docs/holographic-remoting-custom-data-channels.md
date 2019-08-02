---
title: Пользовательские каналы данных с удаленным взаимодействием holographic
description: Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное подключение Holographic.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: 9f7f20023d496412b331606e03d0c5110bb4864f
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718088"
---
# <a name="custom-holographic-remoting-data-channels"></a>Пользовательские каналы данных с удаленным взаимодействием holographic

>[!NOTE]
>Это руководство относится к удаленному взаимодействию с HoloLens 2.

Используйте пользовательские каналы данных для отправки пользовательских данных через установленное удаленное соединение.

>[!IMPORTANT]
>Для пользовательских каналов данных требуется пользовательское ведущее приложение и пользовательское приложение проигрывателя, так как оно обеспечивает взаимодействие между двумя пользовательскими приложениями.

>[!TIP]
>Простой пример для проверки связи можно найти в примерах узлов и проигрывателей в репозитории [GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Раскомментируйте ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` в файлах самплехостмаин. h/самплеплайермаин. h, чтобы включить пример кода.


# <a name="create-a-custom-data-channel"></a>Создание пользовательского канала данных


Для создания пользовательского канала данных требуются следующие поля:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

После успешной установки подключения можно инициировать создание новых каналов данных с помощью узла и (или) стороны проигрывателя. Ремотеконтекст и плайерконтекст предоставляют ```CreateDataChannel()``` метод для этого. Первый параметр — это идентификатор канала, который используется для идентификации канала данных в операциях сусекуент. Вторым параметром является приоритет, указывающий приоритет, с которым данные этого канала передаются на другую сторону. Допустимый диапазон идентификаторов каналов — от 0 до 63 для стороны узла и 64 вплоть до 127 для стороны проигрывателя. Допустимые приоритеты ```Low```: ```Medium``` или ```High``` (на обеих сторонах).

Чтобы инициировать создание канала данных на стороне **узла** , выполните следующие действия.
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Чтобы инициировать создание канала данных на стороне **проигрывателя** , сделайте следующее:
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Для создания нового пользовательского канала данных только одна сторона (узел или проигрыватель) должна вызывать ```CreateDataChannel``` метод.

## <a name="handling-custom-data-channel-events"></a>Обработка пользовательских событий канала данных

Чтобы установить пользовательский канал данных, ```OnDataChannelCreated``` необходимо обработать событие (как на проигрывателе, так и на стороне главного приложения). Он активируется, когда пользовательский канал данных создается с обеих сторон, и предоставляет ```IDataChannel``` объект, который можно использовать для отправки и получения данных по этому каналу.

Чтобы зарегистрировать прослушиватель для события ```OnDataChannelCreated``` , выполните следующие действия.
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Чтобы получать уведомления при получении данных, зарегистрируйтесь в ```OnDataReceived``` событии ```IDataChannel``` для объекта, предоставленного ```OnDataChannelCreated``` обработчиком. Зарегистрируйтесь в ```OnClosed``` событии, чтобы получать уведомления при закрытии канала данных.

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

Чтобы отправить данные через пользовательский канал данных, используйте ```IDataChannel::SendData()``` метод. Первым параметром является ```winrt::array_view<const uint8_t>``` передача данных, которые должны быть отправлены. Второй параметр указывает, вхетер ли данные должны быть повторно отправлены, пока другая сторона не подтвердит получение. 

>[!IMPORTANT]
>В случае неудачных условий сети один и тот же пакет данных может быть доставлен более одного раза. Получающий код должен иметь возможность справиться с этой ситуацией.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Закрытие пользовательского канала данных

Чтобы закрыть пользовательский канал данных, используйте ```IDataChannel::Close()``` метод. Обе стороны будут уведомлены ```OnClosed``` событием после закрытия пользовательского канала данных.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>См. также
* [Создание хост-приложения holographic с удаленным взаимодействием](holographic-remoting-create-host.md)
* [Написание пользовательского приложения для удаленного взаимодействия holographic](holographic-remoting-create-player.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на программное обеспечение удаленного взаимодействия holographic](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkId=521839)