---
title: Отслеживание QR-кода
description: Узнайте, как обнаруживать QR-коды в HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, лбе, развлечения на основе расположения, VR Аркадные, Аркадные, иммерсивное, QR, QR-код, hololens2
ms.openlocfilehash: d51da88aa7bff1dc5c6d3068cb31793891c71e61
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2019
ms.locfileid: "69565997"
---
# <a name="qr-code-tracking"></a>Отслеживание QR-кода

HoloLens 2 может обнаруживать QR-коды в окружении, окружающем гарнитуру, устанавливая систему координат в реальном расположении всего кода.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Компонент</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1-го поколения)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> Обнаружение QR-кода</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">См. Примечание</td>
</tr>
</table>

>[!NOTE]
>Поддержка впечатляющих головных телефонов Windows Mixed Reality на настольных ПК в настоящее время не поддерживается в пакете NuGet ниже.  Следите за дальнейшими обновлениями в службе поддержки настольных систем.

## <a name="getting-the-qr-package"></a>Получение QR-пакета
Пакет NuGet для обнаружения QR-кода можно скачать [здесь](https://github.com/dorreneb/mixed-reality/releases).

Будущие версии этого пакета будут доступны в общедоступном репозитории пакетов NuGet.

## <a name="detecting-qr-codes"></a>Обнаружение QR-кодов

### <a name="adding-the-webcam-capability"></a>Добавление возможности веб-камеры
Для обнаружения QR-кодов необходимо добавить `webcam` в манифест возможность. Эта возможность необходима, так как данные в обнаруженных кодах в пользовательской среде могут содержать конфиденциальные сведения.

Разрешение можно запросить, вызвав `QRCodeWatcher.RequestAccessAsync()`:

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

Разрешение должно быть запрошено до создания объекта Кркодеватчер.

Хотя для `webcam` обнаружения QR-кодов требуется возможность, обнаружение осуществляется с помощью камер отслеживания устройства. Это обеспечивает более широкое ФОВное обнаружение и повышает время работы аккумулятора по сравнению с обнаружением с помощью камеры устройства и видео (ПС).

### <a name="detecting-qr-codes-in-unity"></a>Обнаружение QR-кодов в Unity

Вы можете использовать API обнаружения QR-кода в Unity, не принимая зависимость от МРТК. Для этого необходимо выполнить следующие действия.

1. Создайте новую папку в папке Assets проекта Unity с подключаемыми модулями имен.
2. Скопируйте все необходимые файлы из этой папки в локальную папку "Plugins", которая была только что создана.

Существует пример приложения Unity, которое отображает holographic-квадрат над QR-кодами вместе со связанными данными, такими как GUID, физический размер, метка времени и декодированные данные. Это приложение можно найти по адресу https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.

### <a name="detecting-qr-codes-in-c"></a>Обнаружение QR-кодов вC++

>[!NOTE]
>Фрагменты C++ кода в этой статье в настоящее время демонстрируют использование языка C++/CX вместо C + +17, соответствующего C++/WinRT, как используется в шаблоне [ C++ проекта holographic](creating-a-holographic-directx-project.md). Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Получение системы координат для QR-кода

Каждый обнаруженный QR-код предоставляет [систему пространственных координат](coordinate-systems.md) , выравниваемая по левому краю в верхнем левом углу квадрата быстрого обнаружения, как показано ниже.  При непосредственном использовании QR-пакета SDK ось Z указывает на бумагу (не показано) — при преобразовании в координаты Unity точки оси Z находятся за пределами бумаги и остаются в левой части.

Выводятся Спатиалкурдинатесистеми для рассогласований QR-кода. Эта система координат может быть получена из платформы путем вызова <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">спатиалграфинтероппревиев:: креатекурдинатесистемфорноде</a> и передачи спатиалграфнодеид кода.

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

Для объекта Кркоде в следующем C++коде/CX показано, как создать прямоугольник и разместить его с помощью системы координат QR-кода:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

Для создания QR-прямоугольника можно использовать физический размер:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

Систему координат можно использовать для рисования QR-кода или прикрепления голограмм к расположению:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

В целом, *кркодеватчер:: кркодеаддедхандлер* может выглядеть примерно так:

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
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

## <a name="best-practices-for-qr-code-detection"></a>Рекомендации по обнаружению QR-кода

### <a name="quiet-zones-around-qr-codes"></a>Зоны без кавычек вокруг QR-кодов

Для правильного чтения QR-коды занимают поля вокруг всех сторон кода. Это поле не должно содержать ни одного печатного содержимого и должно состоять из четырех модулей (один черный квадрат в коде). 

[QR-спецификация](https://www.qrcode.com/en/howto/code.html) содержит дополнительные сведения о зонах «тихий».

### <a name="lighting-and-backdrop"></a>Освещение и подложка
Качество обнаружения QR-кодов является уязвимым для различных освещения и подложки. 

В сцене с особенно ярким освещением распечатайте черный цвет на сером фоне. В противном случае распечатайте черный QR-код на белом фоне.

Если фон кода является особенно темным, попробуйте использовать черный цвет в сером коде, если частота обнаружения мала. Если подложка относительно легкая, то обычный код должен работать нормально.

### <a name="size-of-qr-codes"></a>Размер QR-кодов
Устройства Windows Mixed Reality не работают с QR-кодами с сторонами, меньшими 5 cm.

Для QR-кодов, которые находятся в диапазоне от 5 до 10 cm, вы должны быть достаточно близки для обнаружения кода. Для обнаружения кодов с таким размером также потребуется больше времени. 

Точное время на обнаружение кодов зависит не только от размера QR-кодов, но от того, на каком расстоянии у вас нет кода. Переход ближе к коду поможет в смещении проблем с размером.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Расстояние и угловое расположение из QR-кода
Отслеживающие камеры могут обнаруживать только определенный уровень детализации. Для действительно небольших кодов — < 10cm вдоль сторон, вы должны быть достаточно близки. Для QR-кода версии 1, наличного от 10 до 25 сантиметров, минимальное расстояние обнаружения составляет от 0,15 метров до 0,5 метров. 

Расстояние обнаружения для размера увеличивается линейно. 

Обнаружение QR работает с диапазоном углов + = 45deg. Это необходимо для того, чтобы убедиться, что у нас есть правильное разрешение для обнаружения кода.

### <a name="qr-codes-with-logos"></a>QR-коды с логотипами
QR-коды с логотипами не тестировались и в настоящее время не поддерживаются.

### <a name="managing-qr-code-data"></a>Управление данными QR-кода
Устройства Windows Mixed Reality обнаруживают QR-коды на уровне системы в драйвере. При перезагрузке устройства обнаруженные QR-коды исчезают и будут повторно обнаружены как новые объекты в следующий раз.

Рекомендуется настроить приложение так, чтобы оно игнорировало QR-коды старше определенной метки времени. В настоящее время API не поддерживает очистку журнала QR-кода.

## <a name="qr-api-reference"></a>Справочник по QR-API

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>См. также
* [Системы координат](coordinate-systems.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a>