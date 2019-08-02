---
title: Написание пользовательского плеера holographic
description: Создав настраиваемое приложение для удаленного взаимодействия holographic, вы можете создать пользовательское приложение, способное отображать содержимое, отображаемое на удаленном компьютере, в HoloLens 2. В этой статье описывается, как это можно сделать.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: fdc3d3bbd72d0812377d6a70c975f2111e1a2224
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718098"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Написание пользовательского приложения для удаленного взаимодействия holographic

>[!IMPORTANT]
>В этом документе описывается создание пользовательского приложения проигрывателя для HoloLens 2. Пользовательские проигрыватели, написанные для HoloLens 2, несовместимы с ведущими приложениями, написанными для HoloLens 1. Это означает, что оба приложения должны использовать пакет NuGet версии **2. x. x**.

Создав настраиваемое приложение для удаленного взаимодействия holographic, вы можете создать пользовательское приложение, способное отображать [иммерсивное представление](app-views.md) с удаленного компьютера в HoloLens 2. В этой статье описывается, как это можно сделать. Весь код на этой странице и рабочих проектах можно найти в репозитории [GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

С помощью плеера holographic в приложении можно отображать holographic-содержимое, [Отображаемое](rendering.md) на настольном компьютере или на устройстве UWP, например Xbox One, что позволяет получить доступ к дополнительным системным ресурсам. Приложение holographic Remoting, которое выполняет потоковую передачу данных, передает входные данные в хост-приложение holographic с удаленным взаимодействием и получает иммерсивное представление в виде видео-и звукового потока. Подключение устанавливается с использованием стандартного Wi-Fi. Чтобы создать приложение проигрывателя, вы будете использовать пакет NuGet для добавления удаленного взаимодействия holographic в ваше приложение UWP и написать код для управления подключением и отображения иммерсивного представления. 

## <a name="prerequisites"></a>предварительные требования

Хорошей отправной точкой является рабочее приложение UWP на основе DirectX, которое уже предназначено для API Windows Mixed Reality. Дополнительные сведения см. в статье [Общие сведения о разработке DirectX](directx-development-overview.md). Если у вас нет существующего приложения и вы хотите начать с самого начала, [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md) является хорошей отправной точкой.

>[!IMPORTANT]
>Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments). Использование однопотокового [аппартмент](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения. При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) по умолчанию используется многопотоковое подразделение.

## <a name="get-the-holographic-remoting-nuget-package"></a>Получение пакета NuGet для удаленного взаимодействия с holographic

Чтобы добавить пакет NuGet в проект в Visual Studio, необходимо выполнить следующие действия.
1. Откройте проект в Visual Studio.
2. Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**
3. На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".
4. Выберите **Microsoft. Holographic. удаленное взаимодействие**, обязательно выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.
5. Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК**.
6. Следующее появившееся диалоговое окно — это лицензионное соглашение. Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.

>[!IMPORTANT]
><a name="idl"></a>В ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` пакете NuGet содержится подробная документация по API, предоставляемому с помощью holographic Remoting.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Изменение Package. appxmanifest приложения

Чтобы приложение было осведомлено о Microsoft. Holographic. Аппремотинг. dll, добавленном пакетом NuGet, необходимо выполнить следующие действия над проектом.

1. В обозреватель решений щелкните правой кнопкой мыши файл **Package. appxmanifest** и выберите **Открыть с помощью...**
2. Выберите **Редактор XML (текстовый)** и нажмите кнопку ОК.
3. Добавьте следующие строки в файл и сохраните
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Создание контекста проигрывателя

В качестве первого шага приложение должно создать контекст проигрывателя.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>Holographic удаленное взаимодействие выполняется путем замены среды выполнения Windows Mixed Reality, которая является частью Windows, на среду выполнения с удаленным взаимодействием. Это делается во время создания контекста проигрывателя. По этой причине любой вызов любого API Windows Mixed Reality перед созданием контекста проигрывателя может привести к непредвиденному поведению. Рекомендуемый подход состоит в том, чтобы создать контекст проигрывателя как можно раньше перед взаимодействием с любым API смешанной реальности. Никогда не смешивать объекты, созданные или полученные через API Windows Mixed Reality до вызова ```PlayerContext::Create()``` с объектами, созданными или полученными позже.

Далее можно создать Холографикспаце, вызвав [холографикспаце. креатефоркоревиндов](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>Подключение к узлу

После того как приложение игрока готово к отрисовке содержимого, можно установить подключение к узлу.

Подключение можно установить одним из входящей способов:
1) Приложение проигрывателя, работающее в HoloLens 2, подключается к ведущему приложению.
2) Ведущее приложение подключается к приложению проигрывателя, работающему в HoloLens 2.

Чтобы подключиться из приложения проигрывателя к узлу, вызовите ```Connect``` метод в контексте проигрывателя, указав имя узла и порт. Порт по умолчанию — **8265**.

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Как и в C++случае любого ```Connect``` API/WinRT, может возникнуть исключение WinRT:: hresult_error, который необходимо обработать.

Прослушивание входящих подключений в приложении проигрывателя можно выполнить, вызвав ```Listen``` метод. Во время этого вызова можно указать как порт подтверждения, так и порт транспорта. Порт подтверждения используется для первоначального подтверждения. Затем данные пересылаются через порт транспорта. По умолчанию используются номер порта **8265** и **8266** .

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Обработка событий, связанных с подключением

```PlayerContext``` Предоставляет три события для отслеживания состояния соединения.
1) Подключено: Активируется при успешном установлении соединения с узлом.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) Отключено: Активируется, если установленное соединение прерывается или не удалось установить подключение.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>Возможные ```ConnectionFailureReason``` значения задокументированы ```Microsoft.Holographic.AppRemoting.idl``` в [файле](#idl).

3) Ожидание: При ожидании запуска входящих подключений.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Кроме того, состояние соединения можно запросить с помощью ```ConnectionState``` свойства в контексте проигрывателя.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Отобразить удаленно визуализированный кадр

Чтобы отобразить удаленно визуализированное содержимое, ```PlayerContext::BlitRemoteFrame()``` вызовите при подготовке к просмотру [холографикфраме](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). 

```BlitRemoteFrame()```требует, чтобы задний буфер для текущего Холографикфраме был привязан как целевой объект рендеринга. Задний буфер можно получить из [холографиккамерарендерингпараметерс](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) с помощью свойства [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .

При вызове ```BlitRemoteFrame()``` копирует последний полученный кадр из ведущего приложения в буфер обмена холографикфраме. Кроме того, устанавливается набор фокусных точек, если удаленное приложение указало фокус-точку во время отрисовки удаленного кадра.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()```потенциально перезаписывает фокусную точку для текущего кадра. 
>- Чтобы задать резервную точку фокусировки, вызовите метод [холографиккамерарендерингпараметерс:: сетфокуспоинт](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame()```. 
>- Чтобы оверрврите удаленную точку фокусировки, вызовите [холографиккамерарендерингпараметерс:: сетфокуспоинт](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) после ```PlayerContext::BlitRemoteFrame()```.

При успешном ```BlitRemoteFrame()``` выполнении ```BlitResult::Success_Color```возвращает. В противном случае возвращается причина сбоя:
- ```BlitResult::Failed_NoRemoteFrameAvailable```. Сбой, так как нет доступных удаленных кадров.
- ```BlitResult::Failed_NoCamera```. Сбой, так как отсутствует камера.

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Дополнительно Получение статистики о последней удаленной рамке

Чтобы диагностировать проблемы с производительностью или сетью, можно получить статистику о последнем удаленном кадре ```PlayerContext::LastFrameStatistics``` с помощью свойства. Статистика обновляется во время вызова [холографикфраме::P ресентусингкуррентпредиктион](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Дополнительные сведения см ```PlayerFrameStatistics``` . в документации ```Microsoft.Holographic.AppRemoting.idl``` в [файле](#idl).

## <a name="optional-custom-data-channels"></a>Дополнительно Пользовательские каналы данных

Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное соединение. Дополнительные сведения см. в разделе [пользовательские каналы данных](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>См. также
* [Создание хост-приложения holographic с удаленным взаимодействием](holographic-remoting-create-host.md)
* [Пользовательские каналы данных с удаленным взаимодействием holographic](holographic-remoting-custom-data-channels.md)
* [Установление безопасного подключения с помощью удаленного взаимодействия с holographic](holographic-remoting-secure-connection.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на программное обеспечение удаленного взаимодействия holographic](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkId=521839)