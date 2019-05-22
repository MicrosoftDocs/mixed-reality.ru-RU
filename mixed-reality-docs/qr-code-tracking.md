---
title: QR-код отслеживания
description: Узнайте, как включить отслеживание в Windows Mixed Reality иммерсивных (VR) гарнитура QR-кода и реализации функции в приложениях виртуальной Реальности.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR lbe, развлечения на основе расположения, vr arcade arcade эффект присутствия, qr, QR-кода
ms.openlocfilehash: e6588552c0cfa8bffa19ac2be5c247c5f73dc19c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974895"
---
# <a name="qr-code-tracking"></a>QR-код отслеживания

QR-код отслеживания реализуется в драйвере Windows Mixed Reality для иммерсивную (VR). Включив модуль отслеживания кода QR в драйвере гарнитуры, гарнитура проверяет наличие QR-коды, и они помечаются для заинтересованных приложений. Эта функция доступна только начиная с версии [10 октября 2018 года Центр обновления Windows (также известный как RS5)](release-notes-october-2018.md).

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Компонент</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> QR-код отслеживания</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Включение и отключение QR код отслеживания для вашей гарнитура
Примечание. В этом разделе допустимо только для [10 октября 2018 года Центр обновления Windows (также известный как RS5)](release-notes-october-2018.md). Из сборок 19h 1 и более поздних версий не имеется для этого.
Вы разрабатываете приложение смешанной реальности, которое будет использовать отслеживание QR-код, или вы являетесь клиентом одного из этих приложений, необходимо вручную включить отслеживания в драйвере вашей гарнитура QR-код.

Чтобы **включите QR-код отслеживания** для вашей иммерсивных Гарнитура (VR):

1. Закройте приложение смешанной реальности портала на вашем Компьютере.
2. Отключите гарнитура с вашего компьютера.
3. Выполните следующий скрипт в командной строке:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Повторное подключение вашего гарнитура на вашем ПК.

Чтобы **отключить QR-код отслеживания** для вашей иммерсивных Гарнитура (VR):

1. Закройте приложение смешанной реальности портала на вашем Компьютере.
2. Отключите гарнитура с вашего компьютера.
3. Выполните следующий скрипт в командной строке:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Повторное подключение вашего гарнитура на вашем ПК. Это сделает все обнаруженные QR-коды «не-может быть найдена.»

## <a name="printing-codes"></a>Коды печати

Прежде всего [спецификаций для QR-коды](https://www.qrcode.com/en/howto/code.html) говорит: «области символ QR-код требует поле или в «тихом зону» вокруг его можно использовать. Поле-это очистить область вокруг символа, где ничего не выводится. QR-код требует четыре модуля предсказанную во все стороны символа». Это нужно имеют ширину, на каждой стороне, четыре раза больше объема модуль — единый черный квадрат в коде. Спецификации страница содержит советы о том, как выполнить печать QR-коды и определить области, который требуется для того, определенные по размеру QR-кода.

В настоящее время качества обнаружения QR-кода делает возможной различными освещения и задника. Для решения этой проблемы Обратите внимание на освещения и печать соответствующий код. В сцене с особенно ярко-освещения напечатать, являющейся черной на сером фоне. В условиях низкой освещенности сцены, черного на белый works. Аналогичным образом Если особенно темно-backdrop к коду, попробуйте черного на серую кода в случае низкой скорости обнаружения. В противном случае если подложки светлее, обычный код должна работать нормально.

## <a name="qrtracking-api"></a>QRTracking API

Подключаемый модуль QRTracking предоставляет интерфейсы API для отслеживания QR-код. Чтобы использовать подключаемый модуль, необходимо использовать следующие типы из *QRCodesTrackerPlugin* пространства имен.

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a>Реализация отслеживания в Unity QR-кода

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Пример Unity сцен в MRTK (смешанной реальности Toolkit)

Пример использования API отслеживания QR в смешанной реальности Toolkit можно найти [сайт GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).

MRTK реализовала необходимые скрипты для simpilify QR, отслеживание использования. Все необходимые ресурсы для разработки QR отслеживания приложений находятся в папке «QRTracker». Существуют двумя сценами: во-первых, пример, чтобы просто отобразить сведения о QR-коды, как их обнаружения, а второй показано, как использовать систему координат, подключенный к QR-код для отображения голограммы.
Нет prefab «QRScanner», добавлены все необходимые скрипты автоматически использовать QRCodes. Сценарий QRCodeManager является singleton-класс, реализующий QRCode API. Это должен быть добавлен в сцену. Сценарий «AttachToQRCode» используется для присоединения голограммы для системы координат QR-код, этот сценарий можно добавить к любому из вашей голограммы. «SpatialGraphCoordinateSystem» показано, как используется система координат QRCode. Эти сценарии можно использовать в качестве-находится в проекте сцен. также можно написать собственный непосредственно с помощью подключаемого модуля как описано выше.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Реализация отслеживания в Unity без MRTK QR-кода

Можно также использовать API отслеживания QR в Unity не полагаться на MRTK. Для использования API, необходимо подготовить проект со следующей инструкцией:

1. Создайте новую папку в папке assets проекта unity с именем: «Подключаемые модули».
2. Скопируйте все необходимые файлы из [эту папку](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) в локальной папке «Подключаемые модули», вы только что создали.
3. Можно использовать QR, отслеживания скрипты в [папке scripts MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) или написать собственный.
Примечание. Они предназначены только для [10 октября 2018 года Центр обновления Windows (также известный как RS5)](release-notes-october-2018.md) сборки. Подключаемые модули будут обновляться в следующем выпуске windows. Текущий подключаемые модули были экспериментальных и не будет работать для будущих версиях windows. Будут опубликованы новые подключаемые модули, который может использоваться в следующем выпуске windows и они не будут обратной предварительными и не будет работать с RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Реализация отслеживания в DirectX QR-кода

Чтобы использовать QRTrackingPlugin в Visual Studio, необходимо добавить ссылку на QRTrackingPlugin .winmd. Можно найти [необходимые файлы для поддерживаемых платформ здесь](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a>Начало системы координат

Мы определяем справа системы координат, выровнены с QR-код в верхнем левом углу квадрата быстрого обнаружения в верхнем левом углу. Ниже приведен систему координат. Указывает оси z в документе (не показан), но в Unity — ось z нет бумаги и для левши.

SpatialCoordinateSystem определяется, выравнивается, как показано. Эту систему координат можно получить из платформы, с помощью API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

Из QRCode ^ объекта кода, приведенный ниже показано, как создать прямоугольник и поместите его в системе координат QR:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

Чтобы создать прямоугольник QR можно использовать физический размер:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

Можно использовать систему координат для рисования QR-код или вложения голограммы расположение:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

В общей сложности вашего *QRCodesTrackerPlugin::QRCodeAddedHandler* может выглядеть следующим образом:

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a>Устранение неполадок и часто задаваемые вопросы

**Устранение общих неполадок**

* — Это ваш ПК под управлением Windows 10 октября 2018 обновление?
* Вы задали ключ реестра? После перезапуска устройства?
* Версия QR код поддерживаемой версии? Текущий API поддерживает до 20 версии QR код. Мы рекомендуем использовать версии 5 для общего использования. 
* Они вам достаточно близко к QR-код? Чем ближе камеры на QR-код, тем выше QR код версии API может поддерживать.  

**Насколько точно нужно быть QR-код для его обнаружения?**

Это будет зависеть от размера QR-код, а также версии это. Для версии 1 QR-код, изменения из сторон 5 cm на 25 cm стороны обнаружение минимальное расстояние в диапазоне от 0,15 метров 0,5 м. Выбирается самый дальний сейчас, они могут быть обнаружены из переходит от около 0,3 счетчики для целевых объектов меньшего размера QR код 1,4 счетчиков для больше. Для QR-коды, больше, чем можно оценить; расстояние обнаружения для размера растет линейно. Наши средства отслеживания не работает с QR-коды с сторон меньше, чем 5 см.

**Сделать QR-коды с работой логотипы?**

QR-коды с логотипами не были протестированы и сейчас не поддерживаются.

**Как очистить QR-коды из моего приложения, они не существуют?**

* QR-коды сохраняются только в рамках сеанса загрузки. После перезагрузки (или перезапустить драйвер), они будут покинут и определяются как новые объекты в следующий раз.
* QR код журнал сохраняется на уровне системы в сеансе драйвер, но можно настроить приложения, чтобы игнорировать QR-коды, которые старше определенной метке времени, если требуется. В настоящее время API-Интерфейс поддерживает журнал Очистка QR код, как несколько приложений могут быть заинтересованы в данных.

**Подключаемые модули для RS5 и будущих версий несовместимы** RS5 версии подключаемый модуль работает только для RS5 и не будет работать для будущих версий. Подключаемый модуль expermental будут заменены на реальных подключаемого модуля и должен быть тем, что вы можете использовать в будущих версиях windows.
