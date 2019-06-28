---
title: Моделирование восприятие
description: Руководство по использованию библиотеки восприятие моделирования для автоматизации имитации ввода для иммерсивных приложений
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, моделирование, тестирование
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414530"
---
# <a name="perception-simulation"></a>Моделирование восприятие

Вы хотите создавать автоматические тесты для своего приложения? Вы хотите, чтобы тесты выходят за рамки уровня компонента модульное тестирование и действительно производить вашего приложения end-to-end? Симулятор восприятия —, что вы искали. В библиотеке имитации восприятие отправляет человека и world входные данные в приложение, чтобы тесты можно автоматизировать. Например вы можете имитировать входные данные человека поиска в конкретных, повторяемый позицию и затем выполняет жест или с помощью контроллера движения.

Моделирование восприятие можно отправлять физических HoloLens, эмулятор HoloLens имитации ввода следующим образом установлен HoloLens 2 эмулятора или ПК с помощью портала смешанной реальности (1-го поколения,). Восприятие имитации обходит динамической датчиков на устройстве смешанной реальности и отправляет смоделированные входных данных для приложений, выполняющихся на устройстве. Приложения получают эти события ввода через API-интерфейсы, они всегда использовать и не может определить разницу между запуском с физическими датчиками и при выполнении с моделирования восприятие. Моделирование восприятие та же технология используется для отправки имитации входных данных к виртуальной машине HoloLens эмуляторы HoloLens.

Чтобы приступить к использованию моделирования в коде, начните с создания объекта IPerceptionSimulationManager. Из этого объекта можно выполнить команды для управления свойства имитации «человека», включая головной позиции, положение руки и жестов, и можно включить и управлять контроллерами движения.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Настройка проекта Visual Studio для моделирования восприятие
1. [Установить эмулятор HoloLens](install-the-tools.md) на Компьютере разработки. Эмулятор включает библиотеки, которая будет использоваться для моделирования восприятие.
2. Создание новой Visual Studio C# проект для настольной системы (консольный проект прекрасно работает Чтобы приступить к работе).
3. Добавьте следующие двоичные файлы в проект как ссылки (проект -> Добавить -> ссылка...). Их можно найти в % ProgramFiles (x86) %\Microsoft XDE\\(версия), такие как **% ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** для эмулятора 2 HoloLens.  (Обратите внимание: несмотря на то, что двоичные файлы являются частью эмулятор 2 HoloLens, которые также работают в Windows Mixed Reality на рабочем столе.) . PerceptionSimulationManager.Interop.dll - управляемых C# программы-оболочки для восприятия моделирования.
    2\. PerceptionSimulationRest.dll - библиотеки для настройки веб-сокет коммуникационного канала HoloLens или эмуляторе.
    В. SimulationStream.Interop.dll - общие типы для моделирования.
4. Добавьте реализацию двоичный PerceptionSimulationManager.dll в проект. Сначала добавьте его как двоичный файл в проект (проект -> Добавить -> существующий элемент...). Сохраните его как ссылку, чтобы он не копируются в папку исходного проекта. ![Добавьте в проект как ссылку PerceptionSimulationManager.dll](images/saveaslink.png) b. Убедитесь, что его получить копируется в папку выходных данных построения. Это в окне свойств для двоичного файла. ![Марк PerceptionSimulationManager.dll Копировать в выходной каталог](images/copyalways.png)
5. Присвоено x64 вашей Активная платформа решения.  (Используйте Configuration Manager, создайте запись платформы для x64 в том случае, если он еще не существует.)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Создание объекта диспетчера IPerceptionSimulation

Чтобы управлять моделирования, вам отправить обновления в объекты, возвращенные из объекта IPerceptionSimulationManager. Первым делом для получения этого объекта и подключить его к целевое устройство или эмулятор. IP-адрес симулятора можно получить, щелкнув кнопку портал устройств в [панели инструментов](using-the-hololens-emulator.md)

![Значок открытия портал устройств](images/emulator-deviceportal.png) **открыть портал устройства**: Открывает в эмуляторе портал устройств Windows для HoloLens OS.  Для Windows Mixed Reality, это значение можно получить в приложении "Параметры" в разделе «Обновления и безопасность», затем «для разработчиков» в «подключение с использованием:» раздела «Включение портал устройств».  Обязательно запомните IP-адрес и порт.

Во-первых вы вызовете RestSimulationStreamSink.Create для получения объекта RestSimulationStreamSink. Это целевое устройство или эмулятор, который будет управлять по протоколу http. Ваши команды будут передаваться и обрабатываются [Windows Device Portal](using-the-windows-device-portal.md) на устройстве или эмуляторе. Ниже приведены четыре параметра, необходимо создать объект.
* Uri URI - IP-адрес целевого устройства (например, "http://123.123.123.123 «или» http://123.123.123.123:50080 «)
* Учетные данные System.Net.NetworkCredential — имя пользователя и пароль для подключения к [Windows Device Portal](using-the-windows-device-portal.md) на целевом устройстве или эмуляторе. При подключении к эмулятору с помощью его локальный адрес (например, 168. *.* . *) на локальном ПК, будут приняты любые учетные данные.
* normal — логическое значение True для нормального приоритета, значение false для с низким приоритетом. Обычно требуется устанавливать равным *true* для тестовых сценариев, что позволяет контролировать теста.  Эмулятор и моделирование Windows Mixed Reality использовать подключения с низким приоритетом.  Если тест также использует соединение с низким приоритетом, наиболее недавно установлено, что будет использоваться для соединения в элементе управления.
* Токен System.Threading.CancellationToken - токен для отмены асинхронной операции.

Во-вторых, вы создадите IPerceptionSimulationManager. Это объект, который используется для управления моделирования. Обратите внимание на то, что это необходимо сделать в асинхронном методе.

## <a name="control-the-simulated-human"></a>Элемент управления как имитации человеку

IPerceptionSimulationManager имеет человека свойство, которое возвращает объект ISimulatedHuman. Для управления как имитации человеку, выполняют операции над объектом. Пример:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Пример простого C# консольное приложение

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>Расширенный пример C# консольное приложение

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>Обратите внимание на контроллерах 6 DOF

Прежде чем выполнять какие-либо свойства на методы в контроллере имитации 6-DOF, необходимо активировать контроллера.  Не это приведет к возникновению исключения.  Начиная с Windows 10 может обновлять 2019 г., имитации 6-DOF контроллеры могут устанавливаться и активации, задав свойство Status объекта ISimulatedSixDofController SimulatedSixDofControllerStatus.Active.
В Windows 10 октября 2018 г. обновление и более ранних версиях необходимо отдельно установить контроллер имитации 6-DOF во-первых, вызвав средство PerceptionSimulationDevice, расположенное в папке \Windows\System32.  Использование этого средства выглядит следующим образом:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Например

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Ниже приведены поддерживаемые действия:
* я = install
* q = запрос
* r = Удаление

Ниже приведены поддерживаемые экземпляры.
* 1 = слева 6-DOF контроллера
* 2 = правой 6-DOF контроллера

Код выхода процесса укажет (нулевое возвращаемое значение) успешность (ненулевое возвращаемое значение).  При использовании действия «q» для запроса, установлен ли контроллер, возвращаемое значение будет ноль (0), если контроллер еще не установлен или один (1) Если установлен контроллер.

При удалении контроллера в ОС Windows 10 октября 2018 г. обновление или ранее, задайте его статус на Off через API во-первых, затем вызовите PerceptionSimulationDevice средство.

Обратите внимание, что это средство необходимо запускать от имени администратора.




## <a name="api-reference"></a>Справочник по API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

Описывает тип виртуального устройства

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

Устройство с вымышленными ссылку, по умолчанию для PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

Описывает режим головной tracker

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

По умолчанию Head отслеживания. Это означает, что система может выбрать лучший заголовок, режим, в зависимости от условий среды выполнения отслеживания.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

Ориентация только головные отслеживания. Это означает, что отслеживаемые положение может быть недостаточно надежен, что некоторые функции зависят от головного позиции не могут быть доступны.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

Отслеживание позиционные Head. Это означает, что отслеживаемые головной положение и ориентацию оба надежных

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

Описание имитации жестов

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

Значение sentinel, используемый для указания никаких жестов.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Палец нажата жест.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Палец выпустила жест.

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

Жест home/system.

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

Максимальный допустимый жест.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

Возможные состояния контроллера имитации 6-DOF.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

6-DOF контроллер будет отключено.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

6-DOF контроллера включается и отслеживаются.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

6-DOF контроллера включена, но не отслеживается.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

Поддерживаемые кнопки на контроллере имитации 6-DOF.

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

Значение sentinel, используемый для указания кнопок.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

Нажата кнопка домашней.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

Нажата кнопка меню.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

Нажата кнопка захвата для изменения.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

Нажата сенсорной панели.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

Нажата кнопка "выбрать".

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

Возникает при просмотре сенсорной панели.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

Джойстик нажата.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

Максимальное число допустимых кнопок.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

Состояние имитации глаза калибровки

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

Калибровка глаза недоступна.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

Были калибровки глаза.  Это значение по умолчанию.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

Откалиброваны глаза.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

Глаза должны можно уточнять.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

Точность отслеживания соединения вручную.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

Соединение не отслеживается.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

Совместные позиции выводится.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

Полностью отслеживается в качестве объединителя.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

Точность отслеживания соединения вручную.

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

Рука палец соединений были настроены для отражения закрытых позу.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

Шарнирные соединения вручную палец настраиваются в соответствии с открытым поза.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

Рука палец соединений были настроены для отражения указывающего позу.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

Рука палец соединений были настроены для отражения pinching позу.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

Максимальное допустимое значение для SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Описывает состояние воспроизведения.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

Запись в данный момент остановлена и все готово для воспроизведения.

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

Запись в настоящее время воспроизведения.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

Запись приостановлена.

**Microsoft.PerceptionSimulation.PlaybackState.End**

Запись уже истек.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Описывает вектор 3 компонента, который может описывать точку или вектор в трехмерном пространстве.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

Координата X вектора.

**Microsoft.PerceptionSimulation.Vector3.Y**

Компонент Y вектора.

**Microsoft.PerceptionSimulation.Vector3.Z**

Компонент Z вектора.

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

Создайте новый Vector3.

Параметры
* x - координату объекта vector.
* y - координату объекта vector.
* z - компонент z вектора.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Описывает поворот 3 компонента.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

Компонент шаг поворота вокруг оси X вниз.

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Компонент Нутации поворота вокруг оси Y.

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Компонент наката поворота вокруг оси Z.

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

Создает новый Rotation3.

Параметры
* шаг - компонент шаг поворота.
* Поворот - компонент нутации поворота.
* Развертывание - наката компонент поворота.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

Описание настройки соединения с имитации стороны.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

Позиция соединения.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

Угол поворота соединения.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

Точность отслеживания соединения.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Описывает усеченная, как это обычно используется веб-камеры.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

Минимальное расстояние, которое содержится в панелью видимого пространства.

**Microsoft.PerceptionSimulation.Frustum.Far**

Максимальное расстояние, которое содержится в панелью видимого пространства.

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

Горизонтальное поле представления из пирамиды обзора, в радианах (меньше, чем PI).

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

Отношение количества горизонтальное поле представления для вертикального поля зрения.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Корневой элемент для создания пакетов, которые используются для управления устройством.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

Получить объект виртуального устройства, который интерпретирует как имитации человеку и мир имитации.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

Извлечь объект, управляющий имитации отдела.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

Сбрасывает моделирование в состояние по умолчанию.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

Интерфейс, описывающий устройства, который интерпретирует виртуального мира и имитации человеком

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

Получить средство отслеживания Head с виртуального устройства.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

Получить средство отслеживания вручную из имитации устройства.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

Задание свойств виртуального устройства в соответствии с типом предоставленного устройства.

Параметры
* Type - новый тип Simulated Device

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

Интерфейс, описывающий часть имитированное устройство, которое отслеживает начало имитации отдела.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

Получает и задает текущий режим головной tracker.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

Интерфейс, описывающий часть имитированное устройство, которое отслеживает руки имитации отдела

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

Получите позицию узла по всему миру, в метрах.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Получить и задать положение датчик имитации руки, относительно центра элемента head.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Получить и задать вниз pitch датчик имитации руки.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Получить и задать ли пирамиды обзора средства отслеживания имитации наличии учитывается. При обоих руки всегда видимы. Если не учитывается (по умолчанию) руки доступны только внутри пирамиды обзора средства отслеживания вручную.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Получить и задать свойства пирамиды обзора, позволяет определить, если руки являются видимыми для датчик имитации руки.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

Интерфейс верхнего уровня для управления как имитации человеку.

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

Получить и задать положение узла по всему миру, в метрах. Соответствует позиция точки в центре фута как человеку.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

Получить и задать направление имитации человеческих лиц в мире. 0 радиан сталкивается вниз отрицательной полуоси Z. Положительное радианах поворот по часовой стрелке вокруг оси Y.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

Получить и задать высоту как имитации человеку в метрах.

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

Получите левой части имитации отдела.

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

Получите правой стороны из имитации отдела.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

Получите заголовок как имитации человеку.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

Переместите имитации human относительно текущей позиции, в метрах.

Параметры
* Трансляция - перевода для перемещения относительно текущей позиции.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Поворот имитации человека по отношению к его текущее направление, по часовой стрелке относительно оси Y

Параметры
* RADIANS - степень поворота вокруг оси Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedHuman2

Доступны дополнительные свойства путем приведения ISimulatedHuman для ISimulatedHuman2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**

Получите левой 6-DOF контроллера.

**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**

Получите контроллер правой 6-DOF.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

Интерфейс, описывающий форму руки имитации отдела

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

Получите позицию узла по всему миру, в метрах.

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

Получить и задать положение имитации Рука относительно как человеку в метрах.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

Получить и задать ли Рука, активированного в данный момент.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

Получите ли Рука видимой в данный момент для SimulatedDevice, (ie, будь то умеющий определяться с помощью HandTracker).

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

Переместите Рука, таким образом, оно становится видимым для SimulatedDevice.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

Изменить положение имитации Рука относительно текущей позиции, в метрах.

Параметры
* Трансляция - трансляции имитации вручную.

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Сделайте жест, с помощью имитации вручную.  Она будет только обнаружена системой при включении Рука.

Параметры
* жест - жестов для выполнения.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

Путем приведения ISimulatedHand для ISimulatedHand2 доступны дополнительные свойства.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

Получить или задать угол поворота имитации вручную.  Положительное радианах поворот по часовой стрелке, при взгляде на оси.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

Доступны дополнительные свойства путем приведения ISimulatedHand для ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

Получите совместные конфигурацию для указанного соединения.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

Определить совместные конфигурацию для указанного соединения.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

Значение Рука известных поза с необязательный флаг для анимации.  Примечание: анимация не привести соединений, немедленно отражения их окончательной объединенной конфигурации.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Интерфейс, описывающий заголовок как имитации человеку.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

Получите позицию узла по всему миру, в метрах.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Получите поворот головы имитации. Положительное радианах поворот по часовой стрелке, при взгляде на оси.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Получите диаметр имитации головного элемента. Это значение используется для определения center головного элемента (точка вращения).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Поворот имитации head относительно текущего вращения. Положительное радианах поворот по часовой стрелке, при взгляде на оси.

Параметры
* Поворот - сумму для поворота.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

Доступны дополнительные свойства путем приведения ISimulatedHead для ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

Получите с точки зрения как имитации человеку.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

Интерфейс, описывающий 6 DOF контроллер, связанный с имитации отдела.

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

Получите позицию узла по всему миру, в метрах.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

Получить или задать текущее состояние контроллера.  Состояние контроллера должно быть присвоено значение, отличные от Off перед любым вызовом перемещение, поворот и нажмите кнопки будет выполнена успешно.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

Получить или задать положение виртуального контроллера относительно как человеку в метрах.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

Получить или задать ориентацию имитации контроллера.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

Изменить положение виртуального контроллера относительно текущей позиции, в метрах.

Параметры
* Трансляция - трансляции имитации контроллера.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

Нажмите кнопку имитации контроллера.  Она будет только обнаружена системой при включении контроллера.

Параметры
* Кнопка - клавиши.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

Отпустите кнопку на контроллере имитации.  Она будет только обнаружена системой при включении контроллера.

Параметры
* Кнопка — для освобождения.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition (out float, float)**

Получает позицию имитации пальцем на сенсорной панели имитации контроллера.

Параметры
* x - горизонтальное положение пальца.
* y - вертикальное положение пальца.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition (float, float)**

Установка для позиции имитации палец на сенсорной панели имитации контроллера.

Параметры
* x - горизонтальное положение пальца.
* y - вертикальное положение пальца.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

Дополнительные свойства и методы доступны путем приведения ISimulatedSixDofController для ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition (out float, float)**

Получает позицию имитации джойстик имитации контроллера.

Параметры
* x - горизонтальное положение джойстик.
* y - вертикальное положение джойстик.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition (float, float)**

Установка для позиции имитации джойстик имитации контроллера.

Параметры
* x - горизонтальное положение джойстик.
* y - вертикальное положение джойстик.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

Извлечение или уровня заряда батареи имитации контроллера.  Значение должно быть больше 0,0 и меньше или равна 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

Интерфейс, описывающий с точки зрения как имитации человеку.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

Получите угол поворота имитации глаза. Положительное радианах поворот по часовой стрелке, при взгляде на оси.

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Поворот имитации глаза относительно текущего вращения. Положительное радианах поворот по часовой стрелке, при взгляде на оси.

Параметры
* Поворот - сумму для поворота.

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

Получает или задает состояние калибровки имитации глаз.

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

Получите позицию узла по всему миру, в метрах.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

Для воспроизведения загрузить интерфейс для взаимодействия с одной записью.

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

Извлекает список типов данных в записи.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

Возвращает текущее состояние записи.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

Запустите воспроизведение. Если запись приостановлена, воспроизведение возобновляется из приостановленного расположения; При остановке воспроизведения начнется в начале. Если уже воспроизведение, этот вызов учитывается.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

Приостанавливает воспроизведение на текущем месте. Если запись остановлена, вызов игнорируется.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

Ищет запись в указанное время (в 100 наносекунд интервалов с самого начала) и приостановит выполнение в этом расположении. Если время выходит за пределы записи, оно было приостановлено в последнем фрейме.

Параметры
* такты - время которого осуществляется поиск.

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Останавливает воспроизведение и сбрасывает позицию в начало.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Интерфейс для получения изменений состояния во время воспроизведения.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Вызывается, когда изменилось состояние ISimulationRecording воспроизведения.

Параметры
* новое состояние - новое состояние записи.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Корневой объект для создания объектов восприятие моделирования.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

Создание объекта для создания имитации пакетов и их доставки в указанный приемник.

Параметры
* приемник - приемник, который будет получать все созданные пакеты.

Возвращаемое значение

Созданный диспетчер.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Создание приемника, который сохраняет все принимаемые пакеты в файл по указанному пути.

Параметры
* Path - путь к файлу для создания.

Возвращаемое значение

Созданный приемник.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Загрузите записи из указанного файла.

Параметры
* Path - путь к загружаемому файлу.
* Фабрика - фабрики, используемые записи для создания ISimulationStreamSink при необходимости.

Возвращаемое значение

Загрузить записи.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Загрузите записи из указанного файла.

Параметры
* Path - путь к загружаемому файлу.
* Фабрика - фабрики, используемые записи для создания ISimulationStreamSink при необходимости.
* обновляет обратного вызова, который получает обратный вызов - regrading записи состояния.

Возвращаемое значение

Загрузить записи.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Описание различных типов потоковых данных.

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

Значение sentinel, используемый для указания нет типов данных stream.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Stream данные, касающиеся положение и ориентацию орла.

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Stream данные, касающиеся позиции и жесты руки.

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Stream данные, касающиеся пространственное сопоставление среды.

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Stream данные, касающиеся калибровки устройства. Калибровка пакетов принимаются только системой в удаленном режиме.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Stream данные о среде устройства.

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Значение sentinel, используемый для указания всех типов записанные данные.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Объект, который получает пакеты данных из потока моделирования.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (целое число без знака длиной, пакет byte [])**

Получает один пакет, внутренне типизированных и с контролем версий.

Параметры
* Длина — длина пакета.
* пакет - данные пакета.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Объект, который создает ISimulationStreamSink.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Создает один экземпляр ISimulationStreamSink.

Возвращаемое значение

Созданный приемник.
