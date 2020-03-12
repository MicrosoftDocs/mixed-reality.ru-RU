---
title: Написание пользовательского плеера holographic
description: Создав настраиваемое приложение для удаленного взаимодействия holographic, вы можете создать пользовательское приложение, способное отображать содержимое, отображаемое на удаленном компьютере, в HoloLens 2. В этой статье описывается, как это можно сделать.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: eaa6549eb34d3a37c21b3decb348bf43594a110f
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092413"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Написание пользовательского приложения для удаленного взаимодействия holographic

>[!IMPORTANT]
>В этом документе описывается создание пользовательского приложения проигрывателя для HoloLens 2. Пользовательские проигрыватели, написанные для HoloLens 2, несовместимы с удаленными приложениями, написанными для HoloLens 1. Это означает, что оба приложения должны использовать пакет NuGet версии **2. x. x**.

Создав настраиваемое приложение для удаленного взаимодействия holographic, вы можете создать пользовательское приложение, способное отображать [иммерсивное представление](app-views.md) с удаленного компьютера в HoloLens 2. В этой статье описывается, как это можно сделать. Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

С помощью плеера holographic в приложении можно отображать holographic-содержимое, [Отображаемое](rendering.md) на настольном компьютере или на устройстве UWP, например Xbox One, что позволяет получить доступ к дополнительным системным ресурсам. Приложение с удаленным проигрывателем holographic передает входные данные удаленному приложению holographic Remoting и получает иммерсивное представление в виде видео-и звукового потока. Подключение устанавливается с использованием стандартного Wi-Fi. Чтобы создать приложение проигрывателя, вы будете использовать пакет NuGet для добавления удаленного взаимодействия holographic в ваше приложение UWP и написать код для управления подключением и отображения иммерсивного представления. 

## <a name="prerequisites"></a>Предварительные требования

Хорошей отправной точкой является рабочее приложение UWP на основе DirectX, которое уже предназначено для API Windows Mixed Reality. Дополнительные сведения см. в статье [Общие сведения о разработке DirectX](directx-development-overview.md). Если у вас нет существующего приложения и вы хотите начать с самого начала, [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md) является хорошей отправной точкой.

>[!IMPORTANT]
>Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments). Использование [однопотокового аппартмент](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения. При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) многопотоковое подразделение является значением по умолчанию.

## <a name="get-the-holographic-remoting-nuget-package"></a>Получение пакета NuGet для удаленного взаимодействия с holographic

Чтобы добавить пакет NuGet в проект в Visual Studio, необходимо выполнить следующие действия.
1. Откройте проект в Visual Studio.
2. Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**
3. На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".
4. Выберите **Microsoft. Holographic. удаленное взаимодействие**, обязательно выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.
5. Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК**.
6. Следующее появившееся диалоговое окно — это лицензионное соглашение. Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.

>[!IMPORTANT]
><a name="idl"></a>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` в пакете NuGet содержит подробную документацию по API, предоставляемому с помощью holographic Remoting.

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
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>Holographic удаленное взаимодействие выполняется путем замены среды выполнения Windows Mixed Reality, которая является частью Windows, на среду выполнения с удаленным взаимодействием. Это делается во время создания контекста проигрывателя. По этой причине любой вызов любого API Windows Mixed Reality перед созданием контекста проигрывателя может привести к непредвиденному поведению. Рекомендуемый подход состоит в том, чтобы создать контекст проигрывателя как можно раньше перед взаимодействием с любым API смешанной реальности. Никогда не смешивать объекты, созданные или полученные через API Windows Mixed Reality до вызова ```PlayerContext::Create``` с объектами, созданными или полученными позже.

Далее можно создать Холографикспаце, вызвав [холографикспаце. креатефоркоревиндов](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Подключение к удаленному приложению

После того как приложение игрока готово к отрисовке содержимого, можно установить подключение к удаленному приложению.

Соединение может быть установлено одним из следующих способов:
1) Приложение проигрывателя, работающее в HoloLens 2, подключается к удаленному приложению.
2) Удаленное приложение подключается к приложению проигрывателя, работающему в HoloLens 2.

Чтобы подключиться из приложения проигрывателя к удаленному приложению, вызовите метод ```Connect``` в контексте проигрывателя, указав имя узла и порт. Порт по умолчанию — **8265**.

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
>Как и в C++случае любого API/WinRT, ```Connect``` может вызывать исключение WinRT:: hresult_error, которое необходимо обработать.

Прослушивание входящих подключений в приложении проигрывателя можно выполнить, вызвав метод ```Listen```. Во время этого вызова можно указать как порт подтверждения, так и порт транспорта. Порт подтверждения используется для первоначального подтверждения. Затем данные пересылаются через порт транспорта. По умолчанию используются номер порта **8265** и **8266** .

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

```PlayerContext``` предоставляет три события для отслеживания состояния соединения.
1) Подключено: активируется при успешном установлении подключения к удаленному приложению.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) Ondisconnectо: активируется, если установленное соединение прерывается или не удалось установить подключение.
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
>Возможные значения ```ConnectionFailureReason``` задокументированы в [файле](#idl)```Microsoft.Holographic.AppRemoting.idl```.

3) Идет ожидание: при прослушивании входящих подключений начинается.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Кроме того, состояние соединения можно запросить с помощью свойства ```ConnectionState``` в контексте проигрывателя.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Отобразить удаленно визуализированный кадр

Чтобы отобразить удаленно визуализированное содержимое, вызовите ```PlayerContext::BlitRemoteFrame``` при подготовке к просмотру [холографикфраме](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe). 

```BlitRemoteFrame``` требует, чтобы задний буфер для текущего Холографикфраме был привязан как целевой объект рендеринга. Задний буфер можно получить из [холографиккамерарендерингпараметерс](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) с помощью свойства [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .

При вызове ```BlitRemoteFrame``` копирует последний полученный кадр из удаленного приложения в буфер обмена Холографикфраме. Кроме того, устанавливается набор фокусных точек, если удаленное приложение указало фокус-точку во время отрисовки удаленного кадра.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` потенциально перезаписывает фокусную точку для текущего кадра. 
>- Чтобы указать резервную точку фокусировки, вызовите метод [холографиккамерарендерингпараметерс:: сетфокуспоинт](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) перед ```PlayerContext::BlitRemoteFrame```. 
>- Чтобы перезаписать удаленную точку фокусировки, вызовите [холографиккамерарендерингпараметерс:: сетфокуспоинт](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) после ```PlayerContext::BlitRemoteFrame```.

При успешном выполнении ```BlitRemoteFrame``` возвращает ```BlitResult::Success_Color```. В противном случае возвращается причина сбоя:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: сбой, так как нет доступных удаленных кадров.
- ```BlitResult::Failed_NoCamera```: сбой, так как отсутствует камера.
- ```BlitResult::Failed_RemoteFrameTooOld```: не выполнено, так как удаленная рамка устарела (см. свойство Плайерконтекст:: Блитремотефраметимеаут).

>[!IMPORTANT]
> Начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0) , с помощью пользовательского проигрывателя можно использовать репроектную перепроекцию с помощью удаленного взаимодействия с Holographic.

```BlitResult``` также могут возвращать ```BlitResult::Success_Color_Depth``` в следующих случаях.

- Удаленное приложение зафиксировало буфер глубины через [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).
- Пользовательское приложение проигрывателя привязывает допустимый буфер глубины перед вызовом ```BlitRemoteFrame```.

Если эти условия выполнены, ```BlitRemoteFrame``` Блит удаленную глубину в локальный буфер глубины, привязанный к текущему объекту. Затем можно отобразить дополнительное локальное содержимое, которое будет иметь более глубокое пересечение с удаленно подготовленным содержимым. Кроме того, можно зафиксировать локальный буфер глубины с помощью [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) в пользовательском проигрывателе, чтобы настроить глубину РЕПРОЕКЦИИ удаленного и локального отображаемого содержимого. Дополнительные сведения см. в разделе [глубина РЕПРОЕКЦИИ](hologram-stability.md#reprojection) .

### <a name="projection-transform-mode"></a>Режим преобразования проекции

Одна из проблем, выводимых при использовании РЕПРОЕКЦИИ с глубиной в holographic Remoting, заключается в том, что удаленное содержимое можно визуализировать с другим преобразованием проекции, чем локальное содержимое, непосредственно отображаемое пользовательским приложением проигрывателя. Распространенным вариантом использования является указание различных значений для ближайших и дальнеих плоскостей (через [холографиккамера:: сетнеарпланедистанце](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) и [Холографиккамера:: сетфарпланедистанце](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) на стороне проигрывателя и на удаленной стороне. В этом случае неясно, если преобразование проекции на стороне игрока должно отражать удаленные расстояния на уровне вблизи или на расстоянии от локальной плоскости.

Начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0) можно управлять режимом преобразования проекции с помощью ```PlayerContext::ProjectionTransformConfig```. Поддерживаются следующие значения:

- ```Local``` - [холографиккамерапосе::P рожектионтрансформ](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) Возвращает преобразование проекции, отражающее расстояния близкого и дальнего плоскости, заданное пользовательским приложением проигрывателя в холографиккамера.
- ```Remote```-преобразование — это расстояния близкого и дальнего плоскостей, заданные удаленным приложением.
- ```Merged``` — расстояния на расстоянии от удаленного приложения до ближайшего или далекого, а пользовательское приложение проигрывателя объединяется. По умолчанию это достигается за счет минимального расстояния между близкими плоскостями и максимальным расстоянием на расстоянии плоскости. Если удаленная или локальная сторона перевернута, скажем, далеко < вблизи, то на удаленных расстояниях вблизи и дальней плоскости происходит зеркальное отображение.

## Необязательно: Set Блитремотефраметимеаут<a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9). 

Свойство ```PlayerContext::BlitRemoteFrameTimeout``` указывает промежуток времени, в течение которого удаленная рамка повторно используется, если не получена новая Удаленная рамка. 

Типичный вариант использования заключается в том, чтобы включить время ожидания Блитремотефраме для отображения пустого экрана, если новые кадры не будут получены в течение определенного промежутка времени. Если параметр включен, можно также использовать тип возвращаемого значения метода ```BlitRemoteFrame```, чтобы переключиться на локально визуализированное резервное содержимое. 

Чтобы включить время ожидания, задайте для свойства значение длительности, равное или больше 100 мс. Чтобы отключить время ожидания, присвойте свойству нулевую длительность. Если время ожидания включено и в течение заданного периода не получена Удаленная рамка, Блитремотефраме завершается ошибкой и возвращает ```Failed_RemoteFrameTooOld``` до тех пор, пока не будет получена новая Удаленная рамка.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Необязательно: получение статистики о последней удаленной рамке

Чтобы диагностировать проблемы с производительностью или сетью, можно получить статистику о последнем удаленном кадре с помощью свойства ```PlayerContext::LastFrameStatistics```. Статистика обновляется во время вызова [холографикфраме::P ресентусингкуррентпредиктион](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Дополнительные сведения см. в документации по ```PlayerFrameStatistics``` в [файле](#idl)```Microsoft.Holographic.AppRemoting.idl```.

## <a name="optional-custom-data-channels"></a>Необязательно: пользовательские каналы данных

Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное соединение. Дополнительные сведения см. в разделе [пользовательские каналы данных](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>См. также
* [Создание удаленного приложения holographic с удаленным взаимодействием](holographic-remoting-create-host.md)
* [Пользовательские каналы данных с голографическим удаленным взаимодействием](holographic-remoting-custom-data-channels.md)
* [Установление безопасного подключения с помощью удаленного взаимодействия с holographic](holographic-remoting-secure-connection.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkId=521839)
