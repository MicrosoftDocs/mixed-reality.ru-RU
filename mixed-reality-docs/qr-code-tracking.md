---
title: Отслеживание QR-кода
description: Узнайте, как включить отслеживание QR-кода для головной гарнитуры Windows Mixed Reality (VR) и реализовать эту функцию в приложениях VR.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, лбе, развлечения на основе расположения, VR Аркадные, Аркадные, иммерсивное, QR, QR-код
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829985"
---
# <a name="qr-code-tracking"></a>Отслеживание QR-кода

Отслеживание QR-кода реализуется в драйвере Windows Mixed Reality для головных телефонов (VR). Включив средство трассировки QR-кода в драйвере гарнитуры, гарнитура сканирует QR-коды и сообщает заинтересованным приложениям о них. Эта функция доступна только в [Windows 10 октября с обновлением 2018 (также известное как RS5)](release-notes-october-2018.md).

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

## <a name="device-support"></a>Поддержка устройств

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Возможность</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></td>
    </tr>
     <tr>
        <td>Отслеживание QR-кода</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Включение и отключение отслеживания QR-кода для гарнитуры
Примечание. Этот раздел действителен только для [Windows 10 октября 2018 с обновлением (также известное как RS5)](release-notes-october-2018.md). Из сборок 19h1, начиная с версии, это не потребуется делать.
Независимо от того, разрабатывается ли приложение для смешанной реальности, которое будет использовать отслеживание QR-кода, или вы являетесь клиентом одного из этих приложений, вам потребуется вручную включить отслеживание QR-кода в драйвере гарнитуры.

Чтобы **включить отслеживание QR-кода** для головной гарнитуры (VR), сделайте следующее:

1. Закройте приложение портала Mixed Reality на компьютере.
2. Отсоедините гарнитуру от компьютера.
3. В командной строке выполните следующий скрипт:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Повторно подключите гарнитуру к компьютеру.

Чтобы **отключить отслеживание QR-кода** для головной гарнитуры (VR), выполните следующие действия.

1. Закройте приложение портала Mixed Reality на компьютере.
2. Отсоедините гарнитуру от компьютера.
3. В командной строке выполните следующий скрипт:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Повторно подключите гарнитуру к компьютеру. Это сделает все обнаруженные QR-коды "не размещаемые".

## <a name="printing-codes"></a>Печать кодов

В первой и самой самой [спецификации QR-кодов](https://www.qrcode.com/en/howto/code.html) указано "область символов QR-кода требует наличия поля или" скрытой зоны ", которую он будет использовать. Поле является четкой областью вокруг символа, где ничего не печатается. QR-коду требуется четыре модуля на всех сторонах символа. " Она должна иметь ширину на каждой стороне в четыре раза больше размера модуля — единичного Черного квадрата в коде. На странице спецификации содержатся советы по печати QR-кодов и определению области, необходимой для создания QR-кода определенного размера.

В настоящее время качество обнаружения QR-кодов является уязвимым для различных освещения и подложки. Чтобы бороться с этим, обратите внимание на освещения и распечатайте соответствующий код. В сцене с особенно ярким освещением распечатайте черный цвет на сером фоне. При низких сценах черный цвет на белом фоне работает. Аналогично, если фон для кода является особенно темным, попробуйте использовать черный цвет в сером коде, если частота обнаружения мала. В противном случае, если заднися светлее, обычный код должен работать нормально.

## <a name="qrtracking-api"></a>API Кртраккинг

Подключаемый модуль Кртраккинг предоставляет интерфейсы API для отслеживания QR-кода. Чтобы использовать подключаемый модуль, необходимо использовать следующие типы из пространства имен *кркодестраккерплугин* .

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Реализация отслеживания QR-кода в Unity

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Пример сцен Unity в МРТК (набор средств для смешанной реальности)

Пример использования API отслеживания QR-кодов можно найти на [сайте GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)для набора средств Mixed Reality.

МРТК реализовала необходимые сценарии для симпилифи использования отслеживания QR-кодов. Все необходимые активы для разработки приложений для отслеживания QR-файлов находятся в папке "Кртраккер". Существует два монтажных фрагмента: первый — пример для простого отображения сведений о QR-кодах при их обнаружении, а во втором демонстрируется использование системы координат, прикрепленной к QR-коду, для отображения голограмм.
Существует prefab "Крсканнер", который добавил все необходимые сценарии в сцен для использования Кркодес. Кркодеманажер сценария — это одноэлементный класс, реализующий API Кркоде. Его необходимо добавить в сцену. Сценарий «Аттачтокркоде» используется для прикрепления голограмм к системам координат QR-кода. Этот сценарий можно добавить к любой из ваших голограмм. В "Спатиалграфкурдинатесистем" показано, как использовать систему координат Кркоде. Эти скрипты можно использовать как есть в сценах проекта, или вы можете написать собственный объект непосредственно с помощью подключаемого модуля, как описано выше.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Реализация отслеживания QR-кода в Unity без МРТК

Вы также можете использовать API отслеживания QR в Unity, не принимая во внимание зависимость от МРТК. Чтобы использовать API, необходимо подготовить проект с помощью следующей инструкции:

1. Создайте новую папку в папке Assets проекта Unity с именем: "Подключаемые модули".
2. Скопируйте все необходимые файлы из [этой папки](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) в локальную папку "Plugins", которая была только что создана.
3. Вы можете использовать скрипты отслеживания QR в [папке сценариев мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) или написать собственный.
Примечание. Эти подключаемые модули предназначены только для сборок [Windows 10 октябрь 2018 с обновлением (также известных как RS5)](release-notes-october-2018.md) . Подключаемые модули будут обновлены в следующем выпуске Windows. Текущие подключаемые модули были экспериментальными и не будут работать в будущих версиях Windows. Будут опубликованы новые подключаемые модули, которые можно использовать в следующем выпуске Windows, и они не будут поддерживать обратную совместимость и не будут работать с RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Реализация отслеживания QR-кода в DirectX

Чтобы использовать Кртраккингплугин в Visual Studio, необходимо добавить ссылку на Кртраккингплугин в WINMD-файла. [Необходимые файлы для поддерживаемых платформ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)можно найти здесь.

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

## <a name="getting-a-coordinate-system"></a>Получение системы координат

Мы определим правую систему координат, согласованную с QR-кодом в левом верхнем углу квадрата быстрого обнаружения в левом верху. Ниже показана система координат. Ось Z указывает на бумагу (не показано), но в Unity ось z находится за пределами бумаги и левши.

Определяется Спатиалкурдинатесистем, который выводится по отображаемому рассогласованию. Эта система координат может быть получена с платформы с помощью окон API *::P ерцептион:: spatial::P проверка:: спатиалграфинтероппревиев:: креатекурдинатесистемфорноде*.

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

В следующем коде из объекта Кркоде ^ Code показано, как создать прямоугольник и разместить его в системе координат QR:

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

Для создания QR-прямоугольника можно использовать физический размер:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

Систему координат можно использовать для рисования QR-кода или прикрепления голограмм к расположению:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

В целом, *кркодестраккерплугин:: кркодеаддедхандлер* может выглядеть примерно так:

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

**Общие сведения об устранении неполадок**

* Ваш ПК работает под управлением Windows 10 октября с обновлением 2018?
* Вы установили ключ reg? После этого устройство перезагружено?
* Поддерживается ли версия QR-кода поддерживаемой версией? Текущий API поддерживает до версии 20 с кодом QR. Мы рекомендуем использовать версию 5 для общего использования. 
* Достаточно близко к QR-коду? Чем ближе камера к QR-коду, тем выше эта версия может поддерживаться API.  

**Как это должно быть в QR-коде для его обнаружения?**

Это будет зависеть от размера QR-кода, а также от его версии. Для QR-кода версии 1, наличного от 5 сторон cm до 25 Сторон cm, минимальное расстояние обнаружения составляет от 0,15 метров до 0,5 метров. Самое далекое из них можно обнаружить, отказаться от приблизительно 0,3 метров для меньших объемов QR-кода до 1,4 метров. Для больших QR-кодов, которые больше этого размера, можно оценить. Расстояние обнаружения для размера увеличивается линейно. Наш датчик не работает с QR-кодами с сторонами, размер которых меньше 5 см.

**Работают ли QR-коды с логотипами?**

QR-коды с логотипами не тестировались и в настоящее время не поддерживаются.

**Разделы справки удалить QR-коды из моего приложения, чтобы они не сохранялись?**

* QR-коды сохраняются только в сеансе загрузки. После перезагрузки (или перезапуска драйвера) они будут пропала и обнаружены как новые объекты в следующий раз.
* Журнал QR-кодов сохраняется на уровне системы в сеансе драйвера, но вы можете настроить приложение таким же, чтобы при необходимости игнорировать QR-коды старше определенной метки времени. В настоящее время API поддерживает очистку журнала QR-кода, так как данные могут заинтересовать несколько приложений.

**Подключаемые модули для RS5 и будущих версий не поддерживают совместимость** RS5 версия подключаемого модуля работает только для RS5 и не будет работать в будущих версиях. Подключаемый модуль експерментал будет заменен реальным подключаемым модулем и должен быть тем, который можно использовать в будущих версиях Windows.
