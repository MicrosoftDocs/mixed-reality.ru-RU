---
title: Моделирование восприятие
description: Руководство по использованию библиотеки восприятие моделирования для автоматизации имитации ввода для иммерсивных приложений
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, моделирование, тестирование
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602206"
---
# <a name="perception-simulation"></a><span data-ttu-id="22741-104">Моделирование восприятие</span><span class="sxs-lookup"><span data-stu-id="22741-104">Perception simulation</span></span>

<span data-ttu-id="22741-105">Вы хотите создавать автоматические тесты для своего приложения?</span><span class="sxs-lookup"><span data-stu-id="22741-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="22741-106">Вы хотите, чтобы тесты выходят за рамки уровня компонента модульное тестирование и действительно производить вашего приложения end-to-end?</span><span class="sxs-lookup"><span data-stu-id="22741-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="22741-107">Симулятор восприятия —, что вы искали.</span><span class="sxs-lookup"><span data-stu-id="22741-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="22741-108">В библиотеке имитации восприятие отправляет фальшивые человека, так и входных данных по всему миру в приложение, для автоматизации тестов.</span><span class="sxs-lookup"><span data-stu-id="22741-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="22741-109">Например вы можете имитировать ввод человека поиска левого, правого и затем выполняет жест.</span><span class="sxs-lookup"><span data-stu-id="22741-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="22741-110">Моделирование восприятия можно отправить имитации ввода следующим образом физических HoloLens, эмулятор HoloLens или ПК с смешанной реальности портал.</span><span class="sxs-lookup"><span data-stu-id="22741-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="22741-111">Восприятие имитации обходит динамической датчиков на устройстве смешанной реальности и отправляет смоделированные входных данных для приложений, выполняющихся на устройстве.</span><span class="sxs-lookup"><span data-stu-id="22741-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="22741-112">Приложения получают эти фальшивые входных событий через API-интерфейсы, они всегда использовать и не может определить разницу между запуском с физическими датчиками и при выполнении с моделирования восприятие.</span><span class="sxs-lookup"><span data-stu-id="22741-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="22741-113">Моделирование восприятие та же технология, используемой эмулятором HoloLens отправлять имитации входные данные для виртуальной машины HoloLens.</span><span class="sxs-lookup"><span data-stu-id="22741-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="22741-114">Имитация начинается с создания объекта IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="22741-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="22741-115">Из этого объекта можно выполнить команды для управления свойства имитации «человека», включая головной позиции, положение руки и жесты.</span><span class="sxs-lookup"><span data-stu-id="22741-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="22741-116">Настройка проекта Visual Studio для моделирования восприятие</span><span class="sxs-lookup"><span data-stu-id="22741-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="22741-117">[Установить эмулятор HoloLens](install-the-tools.md) на Компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="22741-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="22741-118">Эмулятор включает библиотеки, которая будет использоваться для моделирования восприятие.</span><span class="sxs-lookup"><span data-stu-id="22741-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="22741-119">Создание новой Visual Studio C# проект для настольной системы (консольный проект прекрасно работает Чтобы приступить к работе).</span><span class="sxs-lookup"><span data-stu-id="22741-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="22741-120">Добавьте следующие двоичные файлы в проект как ссылки (проект -> Добавить -> ссылка...). Вы можете найти их в **% ProgramFiles (x86) %\Microsoft XDE\10.0.11082.0** .</span><span class="sxs-lookup"><span data-stu-id="22741-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="22741-121">PerceptionSimulationManager.Interop.dll - управляемых C# программы-оболочки для восприятия моделирования.</span><span class="sxs-lookup"><span data-stu-id="22741-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="22741-122">2.</span><span class="sxs-lookup"><span data-stu-id="22741-122">b.</span></span> <span data-ttu-id="22741-123">PerceptionSimulationRest.dll - библиотеки для настройки веб-сокет коммуникационного канала HoloLens или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="22741-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="22741-124">В.</span><span class="sxs-lookup"><span data-stu-id="22741-124">c.</span></span> <span data-ttu-id="22741-125">SimulationStream.Interop.dll - общие типы для моделирования.</span><span class="sxs-lookup"><span data-stu-id="22741-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="22741-126">Добавьте реализацию двоичный PerceptionSimulationManager.dll в проект.</span><span class="sxs-lookup"><span data-stu-id="22741-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="22741-127">Сначала добавьте его как двоичный файл в проект (проект -> Добавить -> существующий элемент...). Сохраните его как ссылку, чтобы он не копируются в папку исходного проекта.</span><span class="sxs-lookup"><span data-stu-id="22741-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="22741-128">![Добавьте в проект как ссылку PerceptionSimulationManager.dll](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="22741-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="22741-129">Убедитесь, что его получить копируется в папку выходных данных построения.</span><span class="sxs-lookup"><span data-stu-id="22741-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="22741-130">Это в окне свойств для двоичного файла.</span><span class="sxs-lookup"><span data-stu-id="22741-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="22741-131">![Марк PerceptionSimulationManager.dll Копировать в выходной каталог](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="22741-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="22741-132">Создание объекта диспетчера IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="22741-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="22741-133">Чтобы управлять моделирования, вам отправить обновления в объекты, возвращенные из объекта IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="22741-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="22741-134">Первым делом для получения этого объекта и подключить его к целевое устройство или эмулятор.</span><span class="sxs-lookup"><span data-stu-id="22741-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="22741-135">IP-адрес симулятора можно получить, щелкнув кнопку портал устройств в [панели инструментов](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="22741-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="22741-136">![Значок открытия портал устройств](images/emulator-deviceportal.png) **открыть портал устройства**: Откройте Windows Device Portal для HoloLens операционной системы в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="22741-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="22741-137">Во-первых вы вызовете RestSimulationStreamSink.Create для получения объекта RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="22741-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="22741-138">Это целевое устройство или эмулятор, который будет управлять по протоколу http.</span><span class="sxs-lookup"><span data-stu-id="22741-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="22741-139">Ваши команды будут передаваться и обрабатываются [Windows Device Portal](using-the-windows-device-portal.md) на устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="22741-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="22741-140">Ниже приведены четыре параметра, необходимо создать объект.</span><span class="sxs-lookup"><span data-stu-id="22741-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="22741-141">Uri URI - IP-адрес целевого устройства (например, "http://123.123.123.123«)</span><span class="sxs-lookup"><span data-stu-id="22741-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="22741-142">Учетные данные System.Net.NetworkCredential — имя пользователя и пароль для подключения к [Windows Device Portal](using-the-windows-device-portal.md) на целевом устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="22741-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="22741-143">При подключении к эмулятору с помощью его локальной 168. *.* . \* адрес на тот же ПК будут приняты любые учетные данные.</span><span class="sxs-lookup"><span data-stu-id="22741-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="22741-144">normal — логическое значение True для нормального приоритета, значение false для с низким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="22741-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="22741-145">Обычно требуется устанавливать равным *true* для тестовых сценариев.</span><span class="sxs-lookup"><span data-stu-id="22741-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="22741-146">Токен System.Threading.CancellationToken - токен для отмены асинхронной операции.</span><span class="sxs-lookup"><span data-stu-id="22741-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="22741-147">Во-вторых, вы создадите IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="22741-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="22741-148">Это объект, который используется для управления моделирования.</span><span class="sxs-lookup"><span data-stu-id="22741-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="22741-149">Обратите внимание на то, что это необходимо сделать в асинхронном методе.</span><span class="sxs-lookup"><span data-stu-id="22741-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="22741-150">Элемент управления как имитации человеку</span><span class="sxs-lookup"><span data-stu-id="22741-150">Control the simulated Human</span></span>

<span data-ttu-id="22741-151">IPerceptionSimulationManager имеет человека свойство, которое возвращает объект ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="22741-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="22741-152">Для управления как имитации человеку, выполняют операции над объектом.</span><span class="sxs-lookup"><span data-stu-id="22741-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="22741-153">Пример:</span><span class="sxs-lookup"><span data-stu-id="22741-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="22741-154">Пример простого C# консольное приложение</span><span class="sxs-lookup"><span data-stu-id="22741-154">Basic Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="22741-155">Расширенный пример C# консольное приложение</span><span class="sxs-lookup"><span data-stu-id="22741-155">Extended Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

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
        }
    }
}
```

## <a name="api-reference"></a><span data-ttu-id="22741-156">Справочник по API</span><span class="sxs-lookup"><span data-stu-id="22741-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="22741-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="22741-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="22741-158">Описывает тип виртуального устройства</span><span class="sxs-lookup"><span data-stu-id="22741-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="22741-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="22741-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="22741-160">Устройство с вымышленными ссылку, по умолчанию для PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="22741-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="22741-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="22741-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="22741-162">Описывает режим головной tracker</span><span class="sxs-lookup"><span data-stu-id="22741-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="22741-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="22741-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="22741-164">По умолчанию Head отслеживания.</span><span class="sxs-lookup"><span data-stu-id="22741-164">Default Head Tracking.</span></span> <span data-ttu-id="22741-165">Это означает, что система может выбрать лучший заголовок, режим, в зависимости от условий среды выполнения отслеживания.</span><span class="sxs-lookup"><span data-stu-id="22741-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="22741-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="22741-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="22741-167">Ориентация только головные отслеживания.</span><span class="sxs-lookup"><span data-stu-id="22741-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="22741-168">Это означает, что отслеживаемые положение может быть недостаточно надежен, что некоторые функции зависят от головного позиции не могут быть доступны.</span><span class="sxs-lookup"><span data-stu-id="22741-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="22741-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="22741-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="22741-170">Отслеживание позиционные Head.</span><span class="sxs-lookup"><span data-stu-id="22741-170">Positional Head Tracking.</span></span> <span data-ttu-id="22741-171">Это означает, что отслеживаемые головной положение и ориентацию оба надежных</span><span class="sxs-lookup"><span data-stu-id="22741-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="22741-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="22741-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="22741-173">Описание имитации жестов</span><span class="sxs-lookup"><span data-stu-id="22741-173">Describes a simulated gesture</span></span>

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

<span data-ttu-id="22741-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="22741-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="22741-175">Значение-метку, используемый для указания никаких жестов</span><span class="sxs-lookup"><span data-stu-id="22741-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="22741-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="22741-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="22741-177">Нажата жест пальцем</span><span class="sxs-lookup"><span data-stu-id="22741-177">A finger pressed gesture</span></span>

<span data-ttu-id="22741-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="22741-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="22741-179">Жест пальцем выпуска</span><span class="sxs-lookup"><span data-stu-id="22741-179">A finger released gesture</span></span>

<span data-ttu-id="22741-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="22741-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="22741-181">Домашний жестов</span><span class="sxs-lookup"><span data-stu-id="22741-181">The home gesture</span></span>

<span data-ttu-id="22741-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="22741-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="22741-183">Максимальный допустимый жестов</span><span class="sxs-lookup"><span data-stu-id="22741-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="22741-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="22741-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="22741-185">Описывает состояние воспроизведения</span><span class="sxs-lookup"><span data-stu-id="22741-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="22741-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="22741-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="22741-187">Запись в настоящее время остановлены, а все готово для воспроизведения</span><span class="sxs-lookup"><span data-stu-id="22741-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="22741-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="22741-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="22741-189">Запись воспроизводится</span><span class="sxs-lookup"><span data-stu-id="22741-189">The recording is currently playing</span></span>

<span data-ttu-id="22741-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="22741-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="22741-191">Запись приостановлена</span><span class="sxs-lookup"><span data-stu-id="22741-191">The recording is currently paused</span></span>

<span data-ttu-id="22741-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="22741-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="22741-193">Запись уже истек</span><span class="sxs-lookup"><span data-stu-id="22741-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="22741-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="22741-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="22741-195">Описывает вектор 3 компонента, который может описывать точку или вектор в трехмерном пространстве</span><span class="sxs-lookup"><span data-stu-id="22741-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="22741-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="22741-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="22741-197">Компонент X вектора</span><span class="sxs-lookup"><span data-stu-id="22741-197">The X component of the vector</span></span>

<span data-ttu-id="22741-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="22741-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="22741-199">Координата Y вектора</span><span class="sxs-lookup"><span data-stu-id="22741-199">The Y component of the vector</span></span>

<span data-ttu-id="22741-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="22741-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="22741-201">Компонент Z вектора</span><span class="sxs-lookup"><span data-stu-id="22741-201">The Z component of the vector</span></span>

<span data-ttu-id="22741-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="22741-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="22741-203">Создать новый Vector3</span><span class="sxs-lookup"><span data-stu-id="22741-203">Construct a new Vector3</span></span>

<span data-ttu-id="22741-204">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-204">Parameters</span></span>
* <span data-ttu-id="22741-205">x - координату объекта vector</span><span class="sxs-lookup"><span data-stu-id="22741-205">x - The x component of the vector</span></span>
* <span data-ttu-id="22741-206">y - Координата y вектора</span><span class="sxs-lookup"><span data-stu-id="22741-206">y - The y component of the vector</span></span>
* <span data-ttu-id="22741-207">z - компонент z вектора</span><span class="sxs-lookup"><span data-stu-id="22741-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="22741-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="22741-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="22741-209">Описывает поворот 3 компонента</span><span class="sxs-lookup"><span data-stu-id="22741-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="22741-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="22741-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="22741-211">Компонент шаг поворота вокруг оси X вниз</span><span class="sxs-lookup"><span data-stu-id="22741-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="22741-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="22741-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="22741-213">Компонент Нутации поворота вокруг оси Y</span><span class="sxs-lookup"><span data-stu-id="22741-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="22741-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="22741-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="22741-215">Компонент наката поворота вокруг оси Z</span><span class="sxs-lookup"><span data-stu-id="22741-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="22741-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="22741-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="22741-217">Создать новый Rotation3</span><span class="sxs-lookup"><span data-stu-id="22741-217">Construct a new Rotation3</span></span>

<span data-ttu-id="22741-218">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-218">Parameters</span></span>
* <span data-ttu-id="22741-219">шаг - компонент шаг поворота</span><span class="sxs-lookup"><span data-stu-id="22741-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="22741-220">Поворот - компонент нутации поворота</span><span class="sxs-lookup"><span data-stu-id="22741-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="22741-221">Сводный - наката компонент поворота</span><span class="sxs-lookup"><span data-stu-id="22741-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="22741-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="22741-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="22741-223">Описывает усеченная, как это обычно используется веб-камеры</span><span class="sxs-lookup"><span data-stu-id="22741-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="22741-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="22741-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="22741-225">Минимальное расстояние, которое содержится в пирамиды обзора</span><span class="sxs-lookup"><span data-stu-id="22741-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="22741-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="22741-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="22741-227">Максимальное расстояние, которое содержится в пирамиды обзора</span><span class="sxs-lookup"><span data-stu-id="22741-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="22741-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="22741-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="22741-229">Горизонтальное поле представления из пирамиды обзора, в радианах (меньше, чем PI)</span><span class="sxs-lookup"><span data-stu-id="22741-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="22741-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="22741-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="22741-231">Доля горизонтальное поле представления для вертикального поля зрения</span><span class="sxs-lookup"><span data-stu-id="22741-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="22741-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="22741-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="22741-233">Корневой элемент для создания пакетов, которые используются для управления устройством</span><span class="sxs-lookup"><span data-stu-id="22741-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="22741-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="22741-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="22741-235">Получить объект виртуального устройства, который интерпретирует как имитации человеку и мир имитации.</span><span class="sxs-lookup"><span data-stu-id="22741-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="22741-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="22741-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="22741-237">Извлечь объект, управляющий имитации отдела.</span><span class="sxs-lookup"><span data-stu-id="22741-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="22741-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="22741-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="22741-239">Сбрасывает моделирование в состояние по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="22741-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="22741-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="22741-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="22741-241">Интерфейс, описывающий устройства, который интерпретирует виртуального мира и имитации человеком</span><span class="sxs-lookup"><span data-stu-id="22741-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="22741-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="22741-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="22741-243">Получить средство отслеживания Head с виртуального устройства.</span><span class="sxs-lookup"><span data-stu-id="22741-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="22741-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="22741-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="22741-245">Получить средство отслеживания вручную из имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="22741-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="22741-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="22741-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="22741-247">Задание свойств виртуального устройства в соответствии с типом предоставленного устройства.</span><span class="sxs-lookup"><span data-stu-id="22741-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="22741-248">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-248">Parameters</span></span>
* <span data-ttu-id="22741-249">Type - новый тип Simulated Device</span><span class="sxs-lookup"><span data-stu-id="22741-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="22741-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="22741-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="22741-251">Интерфейс, описывающий часть имитированное устройство, которое отслеживает заголовок как имитации человеку</span><span class="sxs-lookup"><span data-stu-id="22741-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="22741-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="22741-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="22741-253">Получает и задает текущий режим головной tracker.</span><span class="sxs-lookup"><span data-stu-id="22741-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="22741-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="22741-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="22741-255">Интерфейс, описывающий часть имитированное устройство, которое отслеживает руки имитации отдела</span><span class="sxs-lookup"><span data-stu-id="22741-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="22741-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="22741-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="22741-257">Получить позицию узла по всему миру, в метрах</span><span class="sxs-lookup"><span data-stu-id="22741-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="22741-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="22741-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="22741-259">Получить и задать положение датчик имитации руки, относительно центра элемента head.</span><span class="sxs-lookup"><span data-stu-id="22741-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="22741-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="22741-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="22741-261">Получить и задать вниз pitch датчик имитации руки</span><span class="sxs-lookup"><span data-stu-id="22741-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="22741-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="22741-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="22741-263">Получить и задать ли пирамиды обзора средства отслеживания имитации наличии учитывается.</span><span class="sxs-lookup"><span data-stu-id="22741-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="22741-264">При обоих руки всегда видимы.</span><span class="sxs-lookup"><span data-stu-id="22741-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="22741-265">Если не учитывается (по умолчанию) руки доступны только внутри пирамиды обзора средства отслеживания вручную.</span><span class="sxs-lookup"><span data-stu-id="22741-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="22741-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="22741-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="22741-267">Получить и задать свойства пирамиды обзора, позволяет определить, если руки являются видимыми для датчик имитации руки.</span><span class="sxs-lookup"><span data-stu-id="22741-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="22741-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="22741-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="22741-269">Интерфейс верхнего уровня для управления как имитации человеку</span><span class="sxs-lookup"><span data-stu-id="22741-269">Top level interface for controlling the simulated human</span></span>

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

<span data-ttu-id="22741-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="22741-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="22741-271">Получить и задать положение узла по всему миру, в метрах.</span><span class="sxs-lookup"><span data-stu-id="22741-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="22741-272">Соответствует позиция точки в центре фута как человеку.</span><span class="sxs-lookup"><span data-stu-id="22741-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="22741-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="22741-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="22741-274">Получить и задать направление имитации человеческих лиц в мире.</span><span class="sxs-lookup"><span data-stu-id="22741-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="22741-275">0 радиан сталкивается вниз отрицательной полуоси Z.</span><span class="sxs-lookup"><span data-stu-id="22741-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="22741-276">Положительное радианах поворот по часовой стрелке вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="22741-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="22741-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="22741-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="22741-278">Получить и задать высоту как имитации человеку в метрах</span><span class="sxs-lookup"><span data-stu-id="22741-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="22741-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="22741-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="22741-280">Получить левой части имитации отдела</span><span class="sxs-lookup"><span data-stu-id="22741-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="22741-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="22741-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="22741-282">Получить правой стороны из имитации отдела</span><span class="sxs-lookup"><span data-stu-id="22741-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="22741-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="22741-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="22741-284">Получить заголовок как имитации человеку</span><span class="sxs-lookup"><span data-stu-id="22741-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="22741-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="22741-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="22741-286">Переместить имитации human относительно текущей позиции, в метрах</span><span class="sxs-lookup"><span data-stu-id="22741-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="22741-287">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-287">Parameters</span></span>
* <span data-ttu-id="22741-288">Трансляция - перевода для перемещения относительно текущей позиции</span><span class="sxs-lookup"><span data-stu-id="22741-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="22741-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="22741-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="22741-290">Поворот имитации человека по отношению к его текущее направление, по часовой стрелке относительно оси Y</span><span class="sxs-lookup"><span data-stu-id="22741-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="22741-291">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-291">Parameters</span></span>
* <span data-ttu-id="22741-292">RADIANS - степень поворота вокруг оси Y</span><span class="sxs-lookup"><span data-stu-id="22741-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="22741-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="22741-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="22741-294">Интерфейс, описывающий форму руки имитации отдела</span><span class="sxs-lookup"><span data-stu-id="22741-294">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="22741-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="22741-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="22741-296">Получить позицию узла по всему миру, в метрах</span><span class="sxs-lookup"><span data-stu-id="22741-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="22741-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="22741-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="22741-298">Получить и задать положение имитации Рука относительно как человеку в метрах.</span><span class="sxs-lookup"><span data-stu-id="22741-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="22741-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="22741-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="22741-300">Получить и задать ли Рука, активированного в данный момент.</span><span class="sxs-lookup"><span data-stu-id="22741-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="22741-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="22741-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="22741-302">Получите ли Рука видимой в данный момент для SimulatedDevice, (ie, будь то умеющий определяться с помощью HandTracker).</span><span class="sxs-lookup"><span data-stu-id="22741-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="22741-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="22741-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="22741-304">Переместите Рука, таким образом, оно становится видимым для SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="22741-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="22741-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="22741-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="22741-306">Изменить положение имитации Рука относительно текущей позиции, в метрах.</span><span class="sxs-lookup"><span data-stu-id="22741-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="22741-307">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-307">Parameters</span></span>
* <span data-ttu-id="22741-308">Трансляция - трансляции имитации Рука</span><span class="sxs-lookup"><span data-stu-id="22741-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="22741-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="22741-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="22741-310">Сделайте жест, с помощью имитации Рука (она будет только обнаружена системой при включении Рука).</span><span class="sxs-lookup"><span data-stu-id="22741-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="22741-311">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-311">Parameters</span></span>
* <span data-ttu-id="22741-312">жест - жестов для выполнения</span><span class="sxs-lookup"><span data-stu-id="22741-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="22741-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="22741-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="22741-314">Интерфейс, описывающий заголовок как имитации человеку</span><span class="sxs-lookup"><span data-stu-id="22741-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="22741-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="22741-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="22741-316">Получить позицию узла по всему миру, в метрах</span><span class="sxs-lookup"><span data-stu-id="22741-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="22741-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="22741-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="22741-318">Получите поворот головы имитации.</span><span class="sxs-lookup"><span data-stu-id="22741-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="22741-319">Положительное радианах поворот по часовой стрелке, при взгляде на оси.</span><span class="sxs-lookup"><span data-stu-id="22741-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="22741-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="22741-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="22741-321">Получите диаметр имитации головного элемента.</span><span class="sxs-lookup"><span data-stu-id="22741-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="22741-322">Это значение используется для определения center головного элемента (точка вращения).</span><span class="sxs-lookup"><span data-stu-id="22741-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="22741-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="22741-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="22741-324">Поворот имитации head относительно текущего вращения.</span><span class="sxs-lookup"><span data-stu-id="22741-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="22741-325">Положительное радианах поворот по часовой стрелке, при взгляде на оси.</span><span class="sxs-lookup"><span data-stu-id="22741-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="22741-326">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-326">Parameters</span></span>
* <span data-ttu-id="22741-327">Поворот - сумму для поворота</span><span class="sxs-lookup"><span data-stu-id="22741-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="22741-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="22741-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="22741-329">Для воспроизведения загрузить интерфейс для взаимодействия с одной записью.</span><span class="sxs-lookup"><span data-stu-id="22741-329">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="22741-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="22741-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="22741-331">Извлекает список типов данных в записи.</span><span class="sxs-lookup"><span data-stu-id="22741-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="22741-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="22741-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="22741-333">Возвращает текущее состояние записи.</span><span class="sxs-lookup"><span data-stu-id="22741-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="22741-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="22741-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="22741-335">Запустите воспроизведение.</span><span class="sxs-lookup"><span data-stu-id="22741-335">Start the playback.</span></span> <span data-ttu-id="22741-336">Если запись приостановлена, воспроизведение возобновляется из приостановленного расположения; При остановке воспроизведения начнется в начале.</span><span class="sxs-lookup"><span data-stu-id="22741-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="22741-337">Если уже воспроизведение, этот вызов учитывается.</span><span class="sxs-lookup"><span data-stu-id="22741-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="22741-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="22741-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="22741-339">Приостанавливает воспроизведение на текущем месте.</span><span class="sxs-lookup"><span data-stu-id="22741-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="22741-340">Если запись остановлена, вызов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="22741-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="22741-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="22741-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="22741-342">Ищет запись в указанное время (в 100 наносекунд интервалов с самого начала) и приостановит выполнение в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="22741-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="22741-343">Если время выходит за пределы записи, оно было приостановлено в последнем фрейме.</span><span class="sxs-lookup"><span data-stu-id="22741-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="22741-344">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-344">Parameters</span></span>
* <span data-ttu-id="22741-345">такты - время которого осуществляется поиск</span><span class="sxs-lookup"><span data-stu-id="22741-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="22741-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="22741-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="22741-347">Останавливает воспроизведение и сбрасывает позицию в начало</span><span class="sxs-lookup"><span data-stu-id="22741-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="22741-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="22741-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="22741-349">Интерфейс для получения изменений состояния во время воспроизведения</span><span class="sxs-lookup"><span data-stu-id="22741-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="22741-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="22741-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="22741-351">Вызывается при изменении состояния ISimulationRecording воспроизведения</span><span class="sxs-lookup"><span data-stu-id="22741-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="22741-352">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-352">Parameters</span></span>
* <span data-ttu-id="22741-353">новое состояние - новое состояние записи</span><span class="sxs-lookup"><span data-stu-id="22741-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="22741-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="22741-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="22741-355">Корневой объект для создания объектов восприятие моделирования</span><span class="sxs-lookup"><span data-stu-id="22741-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="22741-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="22741-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="22741-357">Создание объекта для создания имитации пакетов и их доставки в указанный приемник.</span><span class="sxs-lookup"><span data-stu-id="22741-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="22741-358">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-358">Parameters</span></span>
* <span data-ttu-id="22741-359">приемник - приемник, который будет получать все созданные пакеты</span><span class="sxs-lookup"><span data-stu-id="22741-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="22741-360">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="22741-360">Return value</span></span>

<span data-ttu-id="22741-361">Созданный диспетчер</span><span class="sxs-lookup"><span data-stu-id="22741-361">The created Manager</span></span>

<span data-ttu-id="22741-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="22741-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="22741-363">Создание приемника, который сохраняет все принимаемые пакеты в файл по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="22741-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="22741-364">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-364">Parameters</span></span>
* <span data-ttu-id="22741-365">Path - путь к файлу для создания</span><span class="sxs-lookup"><span data-stu-id="22741-365">path - The path of the file to create</span></span>

<span data-ttu-id="22741-366">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="22741-366">Return value</span></span>

<span data-ttu-id="22741-367">Созданный приемника</span><span class="sxs-lookup"><span data-stu-id="22741-367">The created sink</span></span>

<span data-ttu-id="22741-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="22741-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="22741-369">Загрузить записи из указанного файла</span><span class="sxs-lookup"><span data-stu-id="22741-369">Load a recording from the specified file</span></span>

<span data-ttu-id="22741-370">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-370">Parameters</span></span>
* <span data-ttu-id="22741-371">Path - путь к файлу для загрузки</span><span class="sxs-lookup"><span data-stu-id="22741-371">path - The path of the file to load</span></span>
* <span data-ttu-id="22741-372">Фабрика — фабрику, используемые записи для создания ISimulationStreamSink при необходимости</span><span class="sxs-lookup"><span data-stu-id="22741-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="22741-373">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="22741-373">Return value</span></span>

<span data-ttu-id="22741-374">Загрузить записи</span><span class="sxs-lookup"><span data-stu-id="22741-374">The loaded recording</span></span>

<span data-ttu-id="22741-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="22741-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="22741-376">Загрузить записи из указанного файла</span><span class="sxs-lookup"><span data-stu-id="22741-376">Load a recording from the specified file</span></span>

<span data-ttu-id="22741-377">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-377">Parameters</span></span>
* <span data-ttu-id="22741-378">Path - путь к файлу для загрузки</span><span class="sxs-lookup"><span data-stu-id="22741-378">path - The path of the file to load</span></span>
* <span data-ttu-id="22741-379">Фабрика — фабрику, используемые записи для создания ISimulationStreamSink при необходимости</span><span class="sxs-lookup"><span data-stu-id="22741-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="22741-380">обновляет обратного вызова, который получает обратный вызов - regrading записи состояния</span><span class="sxs-lookup"><span data-stu-id="22741-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="22741-381">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="22741-381">Return value</span></span>

<span data-ttu-id="22741-382">Загрузить записи</span><span class="sxs-lookup"><span data-stu-id="22741-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="22741-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="22741-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="22741-384">Описание различных типов потоковых данных</span><span class="sxs-lookup"><span data-stu-id="22741-384">Describes the different types of stream data</span></span>

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

<span data-ttu-id="22741-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="22741-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="22741-386">Значение-метку, используемый для указания типов данных нет потоков</span><span class="sxs-lookup"><span data-stu-id="22741-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="22741-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="22741-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="22741-388">Stream данных относительно положение и ориентацию орла</span><span class="sxs-lookup"><span data-stu-id="22741-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="22741-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="22741-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="22741-390">Stream данных относительно позиции и жесты руки</span><span class="sxs-lookup"><span data-stu-id="22741-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="22741-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="22741-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="22741-392">Stream данных относительно пространственное сопоставление среды</span><span class="sxs-lookup"><span data-stu-id="22741-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="22741-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="22741-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="22741-394">Stream данные, касающиеся калибровки устройства.</span><span class="sxs-lookup"><span data-stu-id="22741-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="22741-395">Калибровка пакетов принимаются только системой в удаленном режиме.</span><span class="sxs-lookup"><span data-stu-id="22741-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="22741-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="22741-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="22741-397">Stream данных о среде устройства</span><span class="sxs-lookup"><span data-stu-id="22741-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="22741-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="22741-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="22741-399">Значение-метку, используемый для указания всех типов записанные данные</span><span class="sxs-lookup"><span data-stu-id="22741-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="22741-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="22741-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="22741-401">Объект, который получает пакеты данных из потока моделирования</span><span class="sxs-lookup"><span data-stu-id="22741-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="22741-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (целое число без знака длиной, пакет byte [])**</span><span class="sxs-lookup"><span data-stu-id="22741-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="22741-403">Получает один пакет, внутренне типизированных и с контролем версий</span><span class="sxs-lookup"><span data-stu-id="22741-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="22741-404">Параметры</span><span class="sxs-lookup"><span data-stu-id="22741-404">Parameters</span></span>
* <span data-ttu-id="22741-405">Длина — длина пакета</span><span class="sxs-lookup"><span data-stu-id="22741-405">length - The length of the packet</span></span>
* <span data-ttu-id="22741-406">пакетов, данные пакета</span><span class="sxs-lookup"><span data-stu-id="22741-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="22741-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="22741-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="22741-408">Объект, который создает ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="22741-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="22741-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="22741-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="22741-410">Создает один экземпляр ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="22741-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="22741-411">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="22741-411">Return value</span></span>

<span data-ttu-id="22741-412">Созданный приемника</span><span class="sxs-lookup"><span data-stu-id="22741-412">The created sink</span></span>
