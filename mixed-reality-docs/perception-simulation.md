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
# <a name="perception-simulation"></a><span data-ttu-id="53ce1-104">Моделирование восприятие</span><span class="sxs-lookup"><span data-stu-id="53ce1-104">Perception simulation</span></span>

<span data-ttu-id="53ce1-105">Вы хотите создавать автоматические тесты для своего приложения?</span><span class="sxs-lookup"><span data-stu-id="53ce1-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="53ce1-106">Вы хотите, чтобы тесты выходят за рамки уровня компонента модульное тестирование и действительно производить вашего приложения end-to-end?</span><span class="sxs-lookup"><span data-stu-id="53ce1-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="53ce1-107">Симулятор восприятия —, что вы искали.</span><span class="sxs-lookup"><span data-stu-id="53ce1-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="53ce1-108">В библиотеке имитации восприятие отправляет человека и world входные данные в приложение, чтобы тесты можно автоматизировать.</span><span class="sxs-lookup"><span data-stu-id="53ce1-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="53ce1-109">Например вы можете имитировать входные данные человека поиска в конкретных, повторяемый позицию и затем выполняет жест или с помощью контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="53ce1-110">Моделирование восприятие можно отправлять физических HoloLens, эмулятор HoloLens имитации ввода следующим образом установлен HoloLens 2 эмулятора или ПК с помощью портала смешанной реальности (1-го поколения,).</span><span class="sxs-lookup"><span data-stu-id="53ce1-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="53ce1-111">Восприятие имитации обходит динамической датчиков на устройстве смешанной реальности и отправляет смоделированные входных данных для приложений, выполняющихся на устройстве.</span><span class="sxs-lookup"><span data-stu-id="53ce1-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="53ce1-112">Приложения получают эти события ввода через API-интерфейсы, они всегда использовать и не может определить разницу между запуском с физическими датчиками и при выполнении с моделирования восприятие.</span><span class="sxs-lookup"><span data-stu-id="53ce1-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="53ce1-113">Моделирование восприятие та же технология используется для отправки имитации входных данных к виртуальной машине HoloLens эмуляторы HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53ce1-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="53ce1-114">Чтобы приступить к использованию моделирования в коде, начните с создания объекта IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="53ce1-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="53ce1-115">Из этого объекта можно выполнить команды для управления свойства имитации «человека», включая головной позиции, положение руки и жестов, и можно включить и управлять контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="53ce1-116">Настройка проекта Visual Studio для моделирования восприятие</span><span class="sxs-lookup"><span data-stu-id="53ce1-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="53ce1-117">[Установить эмулятор HoloLens](install-the-tools.md) на Компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="53ce1-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="53ce1-118">Эмулятор включает библиотеки, которая будет использоваться для моделирования восприятие.</span><span class="sxs-lookup"><span data-stu-id="53ce1-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="53ce1-119">Создание новой Visual Studio C# проект для настольной системы (консольный проект прекрасно работает Чтобы приступить к работе).</span><span class="sxs-lookup"><span data-stu-id="53ce1-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="53ce1-120">Добавьте следующие двоичные файлы в проект как ссылки (проект -> Добавить -> ссылка...). Их можно найти в % ProgramFiles (x86) %\Microsoft XDE\\(версия), такие как **% ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** для эмулятора 2 HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53ce1-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="53ce1-121">(Обратите внимание: несмотря на то, что двоичные файлы являются частью эмулятор 2 HoloLens, которые также работают в Windows Mixed Reality на рабочем столе.) .</span><span class="sxs-lookup"><span data-stu-id="53ce1-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="53ce1-122">PerceptionSimulationManager.Interop.dll - управляемых C# программы-оболочки для восприятия моделирования.</span><span class="sxs-lookup"><span data-stu-id="53ce1-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="53ce1-123">2\.</span><span class="sxs-lookup"><span data-stu-id="53ce1-123">b.</span></span> <span data-ttu-id="53ce1-124">PerceptionSimulationRest.dll - библиотеки для настройки веб-сокет коммуникационного канала HoloLens или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="53ce1-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="53ce1-125">В.</span><span class="sxs-lookup"><span data-stu-id="53ce1-125">c.</span></span> <span data-ttu-id="53ce1-126">SimulationStream.Interop.dll - общие типы для моделирования.</span><span class="sxs-lookup"><span data-stu-id="53ce1-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="53ce1-127">Добавьте реализацию двоичный PerceptionSimulationManager.dll в проект.</span><span class="sxs-lookup"><span data-stu-id="53ce1-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="53ce1-128">Сначала добавьте его как двоичный файл в проект (проект -> Добавить -> существующий элемент...). Сохраните его как ссылку, чтобы он не копируются в папку исходного проекта.</span><span class="sxs-lookup"><span data-stu-id="53ce1-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="53ce1-129">![Добавьте в проект как ссылку PerceptionSimulationManager.dll](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="53ce1-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="53ce1-130">Убедитесь, что его получить копируется в папку выходных данных построения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="53ce1-131">Это в окне свойств для двоичного файла.</span><span class="sxs-lookup"><span data-stu-id="53ce1-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="53ce1-132">![Марк PerceptionSimulationManager.dll Копировать в выходной каталог](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="53ce1-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="53ce1-133">Присвоено x64 вашей Активная платформа решения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="53ce1-134">(Используйте Configuration Manager, создайте запись платформы для x64 в том случае, если он еще не существует.)</span><span class="sxs-lookup"><span data-stu-id="53ce1-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="53ce1-135">Создание объекта диспетчера IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="53ce1-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="53ce1-136">Чтобы управлять моделирования, вам отправить обновления в объекты, возвращенные из объекта IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="53ce1-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="53ce1-137">Первым делом для получения этого объекта и подключить его к целевое устройство или эмулятор.</span><span class="sxs-lookup"><span data-stu-id="53ce1-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="53ce1-138">IP-адрес симулятора можно получить, щелкнув кнопку портал устройств в [панели инструментов](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="53ce1-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="53ce1-139">![Значок открытия портал устройств](images/emulator-deviceportal.png) **открыть портал устройства**: Открывает в эмуляторе портал устройств Windows для HoloLens OS.</span><span class="sxs-lookup"><span data-stu-id="53ce1-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="53ce1-140">Для Windows Mixed Reality, это значение можно получить в приложении "Параметры" в разделе «Обновления и безопасность», затем «для разработчиков» в «подключение с использованием:» раздела «Включение портал устройств».</span><span class="sxs-lookup"><span data-stu-id="53ce1-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="53ce1-141">Обязательно запомните IP-адрес и порт.</span><span class="sxs-lookup"><span data-stu-id="53ce1-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="53ce1-142">Во-первых вы вызовете RestSimulationStreamSink.Create для получения объекта RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="53ce1-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="53ce1-143">Это целевое устройство или эмулятор, который будет управлять по протоколу http.</span><span class="sxs-lookup"><span data-stu-id="53ce1-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="53ce1-144">Ваши команды будут передаваться и обрабатываются [Windows Device Portal](using-the-windows-device-portal.md) на устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="53ce1-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="53ce1-145">Ниже приведены четыре параметра, необходимо создать объект.</span><span class="sxs-lookup"><span data-stu-id="53ce1-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="53ce1-146">Uri URI - IP-адрес целевого устройства (например, "http://123.123.123.123 «или» http://123.123.123.123:50080 «)</span><span class="sxs-lookup"><span data-stu-id="53ce1-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="53ce1-147">Учетные данные System.Net.NetworkCredential — имя пользователя и пароль для подключения к [Windows Device Portal](using-the-windows-device-portal.md) на целевом устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="53ce1-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="53ce1-148">При подключении к эмулятору с помощью его локальный адрес (например, 168. *.* . \*) на локальном ПК, будут приняты любые учетные данные.</span><span class="sxs-lookup"><span data-stu-id="53ce1-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="53ce1-149">normal — логическое значение True для нормального приоритета, значение false для с низким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="53ce1-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="53ce1-150">Обычно требуется устанавливать равным *true* для тестовых сценариев, что позволяет контролировать теста.</span><span class="sxs-lookup"><span data-stu-id="53ce1-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="53ce1-151">Эмулятор и моделирование Windows Mixed Reality использовать подключения с низким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="53ce1-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="53ce1-152">Если тест также использует соединение с низким приоритетом, наиболее недавно установлено, что будет использоваться для соединения в элементе управления.</span><span class="sxs-lookup"><span data-stu-id="53ce1-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="53ce1-153">Токен System.Threading.CancellationToken - токен для отмены асинхронной операции.</span><span class="sxs-lookup"><span data-stu-id="53ce1-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="53ce1-154">Во-вторых, вы создадите IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="53ce1-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="53ce1-155">Это объект, который используется для управления моделирования.</span><span class="sxs-lookup"><span data-stu-id="53ce1-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="53ce1-156">Обратите внимание на то, что это необходимо сделать в асинхронном методе.</span><span class="sxs-lookup"><span data-stu-id="53ce1-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="53ce1-157">Элемент управления как имитации человеку</span><span class="sxs-lookup"><span data-stu-id="53ce1-157">Control the simulated Human</span></span>

<span data-ttu-id="53ce1-158">IPerceptionSimulationManager имеет человека свойство, которое возвращает объект ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="53ce1-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="53ce1-159">Для управления как имитации человеку, выполняют операции над объектом.</span><span class="sxs-lookup"><span data-stu-id="53ce1-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="53ce1-160">Пример:</span><span class="sxs-lookup"><span data-stu-id="53ce1-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="53ce1-161">Пример простого C# консольное приложение</span><span class="sxs-lookup"><span data-stu-id="53ce1-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="53ce1-162">Расширенный пример C# консольное приложение</span><span class="sxs-lookup"><span data-stu-id="53ce1-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="53ce1-163">Обратите внимание на контроллерах 6 DOF</span><span class="sxs-lookup"><span data-stu-id="53ce1-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="53ce1-164">Прежде чем выполнять какие-либо свойства на методы в контроллере имитации 6-DOF, необходимо активировать контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="53ce1-165">Не это приведет к возникновению исключения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="53ce1-166">Начиная с Windows 10 может обновлять 2019 г., имитации 6-DOF контроллеры могут устанавливаться и активации, задав свойство Status объекта ISimulatedSixDofController SimulatedSixDofControllerStatus.Active.</span><span class="sxs-lookup"><span data-stu-id="53ce1-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="53ce1-167">В Windows 10 октября 2018 г. обновление и более ранних версиях необходимо отдельно установить контроллер имитации 6-DOF во-первых, вызвав средство PerceptionSimulationDevice, расположенное в папке \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="53ce1-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="53ce1-168">Использование этого средства выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="53ce1-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="53ce1-169">Например</span><span class="sxs-lookup"><span data-stu-id="53ce1-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="53ce1-170">Ниже приведены поддерживаемые действия:</span><span class="sxs-lookup"><span data-stu-id="53ce1-170">Supported actions are:</span></span>
* <span data-ttu-id="53ce1-171">я = install</span><span class="sxs-lookup"><span data-stu-id="53ce1-171">i = install</span></span>
* <span data-ttu-id="53ce1-172">q = запрос</span><span class="sxs-lookup"><span data-stu-id="53ce1-172">q = query</span></span>
* <span data-ttu-id="53ce1-173">r = Удаление</span><span class="sxs-lookup"><span data-stu-id="53ce1-173">r = remove</span></span>

<span data-ttu-id="53ce1-174">Ниже приведены поддерживаемые экземпляры.</span><span class="sxs-lookup"><span data-stu-id="53ce1-174">Supported instances are:</span></span>
* <span data-ttu-id="53ce1-175">1 = слева 6-DOF контроллера</span><span class="sxs-lookup"><span data-stu-id="53ce1-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="53ce1-176">2 = правой 6-DOF контроллера</span><span class="sxs-lookup"><span data-stu-id="53ce1-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="53ce1-177">Код выхода процесса укажет (нулевое возвращаемое значение) успешность (ненулевое возвращаемое значение).</span><span class="sxs-lookup"><span data-stu-id="53ce1-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="53ce1-178">При использовании действия «q» для запроса, установлен ли контроллер, возвращаемое значение будет ноль (0), если контроллер еще не установлен или один (1) Если установлен контроллер.</span><span class="sxs-lookup"><span data-stu-id="53ce1-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="53ce1-179">При удалении контроллера в ОС Windows 10 октября 2018 г. обновление или ранее, задайте его статус на Off через API во-первых, затем вызовите PerceptionSimulationDevice средство.</span><span class="sxs-lookup"><span data-stu-id="53ce1-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="53ce1-180">Обратите внимание, что это средство необходимо запускать от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="53ce1-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="53ce1-181">Справочник по API</span><span class="sxs-lookup"><span data-stu-id="53ce1-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="53ce1-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="53ce1-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="53ce1-183">Описывает тип виртуального устройства</span><span class="sxs-lookup"><span data-stu-id="53ce1-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="53ce1-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="53ce1-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="53ce1-185">Устройство с вымышленными ссылку, по умолчанию для PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="53ce1-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="53ce1-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="53ce1-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="53ce1-187">Описывает режим головной tracker</span><span class="sxs-lookup"><span data-stu-id="53ce1-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="53ce1-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="53ce1-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="53ce1-189">По умолчанию Head отслеживания.</span><span class="sxs-lookup"><span data-stu-id="53ce1-189">Default Head Tracking.</span></span> <span data-ttu-id="53ce1-190">Это означает, что система может выбрать лучший заголовок, режим, в зависимости от условий среды выполнения отслеживания.</span><span class="sxs-lookup"><span data-stu-id="53ce1-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="53ce1-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="53ce1-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="53ce1-192">Ориентация только головные отслеживания.</span><span class="sxs-lookup"><span data-stu-id="53ce1-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="53ce1-193">Это означает, что отслеживаемые положение может быть недостаточно надежен, что некоторые функции зависят от головного позиции не могут быть доступны.</span><span class="sxs-lookup"><span data-stu-id="53ce1-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="53ce1-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="53ce1-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="53ce1-195">Отслеживание позиционные Head.</span><span class="sxs-lookup"><span data-stu-id="53ce1-195">Positional Head Tracking.</span></span> <span data-ttu-id="53ce1-196">Это означает, что отслеживаемые головной положение и ориентацию оба надежных</span><span class="sxs-lookup"><span data-stu-id="53ce1-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="53ce1-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="53ce1-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="53ce1-198">Описание имитации жестов</span><span class="sxs-lookup"><span data-stu-id="53ce1-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="53ce1-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="53ce1-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="53ce1-200">Значение sentinel, используемый для указания никаких жестов.</span><span class="sxs-lookup"><span data-stu-id="53ce1-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="53ce1-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="53ce1-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="53ce1-202">Палец нажата жест.</span><span class="sxs-lookup"><span data-stu-id="53ce1-202">A finger pressed gesture.</span></span>

<span data-ttu-id="53ce1-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="53ce1-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="53ce1-204">Палец выпустила жест.</span><span class="sxs-lookup"><span data-stu-id="53ce1-204">A finger released gesture.</span></span>

<span data-ttu-id="53ce1-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="53ce1-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="53ce1-206">Жест home/system.</span><span class="sxs-lookup"><span data-stu-id="53ce1-206">The home/system gesture.</span></span>

<span data-ttu-id="53ce1-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="53ce1-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="53ce1-208">Максимальный допустимый жест.</span><span class="sxs-lookup"><span data-stu-id="53ce1-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="53ce1-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="53ce1-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="53ce1-210">Возможные состояния контроллера имитации 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="53ce1-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="53ce1-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="53ce1-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="53ce1-212">6-DOF контроллер будет отключено.</span><span class="sxs-lookup"><span data-stu-id="53ce1-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="53ce1-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="53ce1-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="53ce1-214">6-DOF контроллера включается и отслеживаются.</span><span class="sxs-lookup"><span data-stu-id="53ce1-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="53ce1-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="53ce1-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="53ce1-216">6-DOF контроллера включена, но не отслеживается.</span><span class="sxs-lookup"><span data-stu-id="53ce1-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="53ce1-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="53ce1-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="53ce1-218">Поддерживаемые кнопки на контроллере имитации 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="53ce1-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="53ce1-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="53ce1-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="53ce1-220">Значение sentinel, используемый для указания кнопок.</span><span class="sxs-lookup"><span data-stu-id="53ce1-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="53ce1-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="53ce1-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="53ce1-222">Нажата кнопка домашней.</span><span class="sxs-lookup"><span data-stu-id="53ce1-222">The Home button is pressed.</span></span>

<span data-ttu-id="53ce1-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="53ce1-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="53ce1-224">Нажата кнопка меню.</span><span class="sxs-lookup"><span data-stu-id="53ce1-224">The Menu button is pressed.</span></span>

<span data-ttu-id="53ce1-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="53ce1-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="53ce1-226">Нажата кнопка захвата для изменения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-226">The Grip button is pressed.</span></span>

<span data-ttu-id="53ce1-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="53ce1-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="53ce1-228">Нажата сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="53ce1-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="53ce1-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="53ce1-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="53ce1-230">Нажата кнопка "выбрать".</span><span class="sxs-lookup"><span data-stu-id="53ce1-230">The Select button is pressed.</span></span>

<span data-ttu-id="53ce1-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="53ce1-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="53ce1-232">Возникает при просмотре сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="53ce1-232">The TouchPad is touched.</span></span>

<span data-ttu-id="53ce1-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="53ce1-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="53ce1-234">Джойстик нажата.</span><span class="sxs-lookup"><span data-stu-id="53ce1-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="53ce1-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="53ce1-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="53ce1-236">Максимальное число допустимых кнопок.</span><span class="sxs-lookup"><span data-stu-id="53ce1-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="53ce1-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="53ce1-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="53ce1-238">Состояние имитации глаза калибровки</span><span class="sxs-lookup"><span data-stu-id="53ce1-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="53ce1-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="53ce1-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="53ce1-240">Калибровка глаза недоступна.</span><span class="sxs-lookup"><span data-stu-id="53ce1-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="53ce1-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="53ce1-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="53ce1-242">Были калибровки глаза.</span><span class="sxs-lookup"><span data-stu-id="53ce1-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="53ce1-243">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="53ce1-243">This is the default value.</span></span>

<span data-ttu-id="53ce1-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="53ce1-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="53ce1-245">Откалиброваны глаза.</span><span class="sxs-lookup"><span data-stu-id="53ce1-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="53ce1-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="53ce1-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="53ce1-247">Глаза должны можно уточнять.</span><span class="sxs-lookup"><span data-stu-id="53ce1-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="53ce1-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="53ce1-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="53ce1-249">Точность отслеживания соединения вручную.</span><span class="sxs-lookup"><span data-stu-id="53ce1-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="53ce1-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="53ce1-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="53ce1-251">Соединение не отслеживается.</span><span class="sxs-lookup"><span data-stu-id="53ce1-251">The joint is not tracked.</span></span>

<span data-ttu-id="53ce1-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="53ce1-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="53ce1-253">Совместные позиции выводится.</span><span class="sxs-lookup"><span data-stu-id="53ce1-253">The joint position is inferred.</span></span>

<span data-ttu-id="53ce1-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="53ce1-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="53ce1-255">Полностью отслеживается в качестве объединителя.</span><span class="sxs-lookup"><span data-stu-id="53ce1-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="53ce1-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="53ce1-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="53ce1-257">Точность отслеживания соединения вручную.</span><span class="sxs-lookup"><span data-stu-id="53ce1-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="53ce1-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="53ce1-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="53ce1-259">Рука палец соединений были настроены для отражения закрытых позу.</span><span class="sxs-lookup"><span data-stu-id="53ce1-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="53ce1-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="53ce1-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="53ce1-261">Шарнирные соединения вручную палец настраиваются в соответствии с открытым поза.</span><span class="sxs-lookup"><span data-stu-id="53ce1-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="53ce1-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="53ce1-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="53ce1-263">Рука палец соединений были настроены для отражения указывающего позу.</span><span class="sxs-lookup"><span data-stu-id="53ce1-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="53ce1-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="53ce1-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="53ce1-265">Рука палец соединений были настроены для отражения pinching позу.</span><span class="sxs-lookup"><span data-stu-id="53ce1-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="53ce1-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="53ce1-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="53ce1-267">Максимальное допустимое значение для SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="53ce1-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="53ce1-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="53ce1-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="53ce1-269">Описывает состояние воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="53ce1-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="53ce1-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="53ce1-271">Запись в данный момент остановлена и все готово для воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="53ce1-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="53ce1-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="53ce1-273">Запись в настоящее время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-273">The recording is currently playing.</span></span>

<span data-ttu-id="53ce1-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="53ce1-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="53ce1-275">Запись приостановлена.</span><span class="sxs-lookup"><span data-stu-id="53ce1-275">The recording is currently paused.</span></span>

<span data-ttu-id="53ce1-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="53ce1-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="53ce1-277">Запись уже истек.</span><span class="sxs-lookup"><span data-stu-id="53ce1-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="53ce1-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="53ce1-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="53ce1-279">Описывает вектор 3 компонента, который может описывать точку или вектор в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="53ce1-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="53ce1-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="53ce1-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="53ce1-281">Координата X вектора.</span><span class="sxs-lookup"><span data-stu-id="53ce1-281">The X component of the vector.</span></span>

<span data-ttu-id="53ce1-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="53ce1-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="53ce1-283">Компонент Y вектора.</span><span class="sxs-lookup"><span data-stu-id="53ce1-283">The Y component of the vector.</span></span>

<span data-ttu-id="53ce1-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="53ce1-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="53ce1-285">Компонент Z вектора.</span><span class="sxs-lookup"><span data-stu-id="53ce1-285">The Z component of the vector.</span></span>

<span data-ttu-id="53ce1-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="53ce1-287">Создайте новый Vector3.</span><span class="sxs-lookup"><span data-stu-id="53ce1-287">Construct a new Vector3.</span></span>

<span data-ttu-id="53ce1-288">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-288">Parameters</span></span>
* <span data-ttu-id="53ce1-289">x - координату объекта vector.</span><span class="sxs-lookup"><span data-stu-id="53ce1-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="53ce1-290">y - координату объекта vector.</span><span class="sxs-lookup"><span data-stu-id="53ce1-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="53ce1-291">z - компонент z вектора.</span><span class="sxs-lookup"><span data-stu-id="53ce1-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="53ce1-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="53ce1-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="53ce1-293">Описывает поворот 3 компонента.</span><span class="sxs-lookup"><span data-stu-id="53ce1-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="53ce1-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="53ce1-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="53ce1-295">Компонент шаг поворота вокруг оси X вниз.</span><span class="sxs-lookup"><span data-stu-id="53ce1-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="53ce1-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="53ce1-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="53ce1-297">Компонент Нутации поворота вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="53ce1-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="53ce1-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="53ce1-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="53ce1-299">Компонент наката поворота вокруг оси Z.</span><span class="sxs-lookup"><span data-stu-id="53ce1-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="53ce1-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="53ce1-301">Создает новый Rotation3.</span><span class="sxs-lookup"><span data-stu-id="53ce1-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="53ce1-302">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-302">Parameters</span></span>
* <span data-ttu-id="53ce1-303">шаг - компонент шаг поворота.</span><span class="sxs-lookup"><span data-stu-id="53ce1-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="53ce1-304">Поворот - компонент нутации поворота.</span><span class="sxs-lookup"><span data-stu-id="53ce1-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="53ce1-305">Развертывание - наката компонент поворота.</span><span class="sxs-lookup"><span data-stu-id="53ce1-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="53ce1-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="53ce1-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="53ce1-307">Описание настройки соединения с имитации стороны.</span><span class="sxs-lookup"><span data-stu-id="53ce1-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="53ce1-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="53ce1-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="53ce1-309">Позиция соединения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-309">The position of the joint.</span></span>

<span data-ttu-id="53ce1-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="53ce1-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="53ce1-311">Угол поворота соединения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-311">The rotation of the joint.</span></span>

<span data-ttu-id="53ce1-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="53ce1-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="53ce1-313">Точность отслеживания соединения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="53ce1-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="53ce1-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="53ce1-315">Описывает усеченная, как это обычно используется веб-камеры.</span><span class="sxs-lookup"><span data-stu-id="53ce1-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="53ce1-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="53ce1-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="53ce1-317">Минимальное расстояние, которое содержится в панелью видимого пространства.</span><span class="sxs-lookup"><span data-stu-id="53ce1-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="53ce1-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="53ce1-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="53ce1-319">Максимальное расстояние, которое содержится в панелью видимого пространства.</span><span class="sxs-lookup"><span data-stu-id="53ce1-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="53ce1-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="53ce1-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="53ce1-321">Горизонтальное поле представления из пирамиды обзора, в радианах (меньше, чем PI).</span><span class="sxs-lookup"><span data-stu-id="53ce1-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="53ce1-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="53ce1-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="53ce1-323">Отношение количества горизонтальное поле представления для вертикального поля зрения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="53ce1-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="53ce1-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="53ce1-325">Корневой элемент для создания пакетов, которые используются для управления устройством.</span><span class="sxs-lookup"><span data-stu-id="53ce1-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="53ce1-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="53ce1-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="53ce1-327">Получить объект виртуального устройства, который интерпретирует как имитации человеку и мир имитации.</span><span class="sxs-lookup"><span data-stu-id="53ce1-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="53ce1-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="53ce1-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="53ce1-329">Извлечь объект, управляющий имитации отдела.</span><span class="sxs-lookup"><span data-stu-id="53ce1-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="53ce1-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="53ce1-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="53ce1-331">Сбрасывает моделирование в состояние по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="53ce1-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="53ce1-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="53ce1-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="53ce1-333">Интерфейс, описывающий устройства, который интерпретирует виртуального мира и имитации человеком</span><span class="sxs-lookup"><span data-stu-id="53ce1-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="53ce1-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="53ce1-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="53ce1-335">Получить средство отслеживания Head с виртуального устройства.</span><span class="sxs-lookup"><span data-stu-id="53ce1-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="53ce1-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="53ce1-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="53ce1-337">Получить средство отслеживания вручную из имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="53ce1-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="53ce1-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="53ce1-339">Задание свойств виртуального устройства в соответствии с типом предоставленного устройства.</span><span class="sxs-lookup"><span data-stu-id="53ce1-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="53ce1-340">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-340">Parameters</span></span>
* <span data-ttu-id="53ce1-341">Type - новый тип Simulated Device</span><span class="sxs-lookup"><span data-stu-id="53ce1-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="53ce1-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="53ce1-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="53ce1-343">Интерфейс, описывающий часть имитированное устройство, которое отслеживает начало имитации отдела.</span><span class="sxs-lookup"><span data-stu-id="53ce1-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="53ce1-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="53ce1-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="53ce1-345">Получает и задает текущий режим головной tracker.</span><span class="sxs-lookup"><span data-stu-id="53ce1-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="53ce1-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="53ce1-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="53ce1-347">Интерфейс, описывающий часть имитированное устройство, которое отслеживает руки имитации отдела</span><span class="sxs-lookup"><span data-stu-id="53ce1-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="53ce1-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="53ce1-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="53ce1-349">Получите позицию узла по всему миру, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="53ce1-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="53ce1-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="53ce1-351">Получить и задать положение датчик имитации руки, относительно центра элемента head.</span><span class="sxs-lookup"><span data-stu-id="53ce1-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="53ce1-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="53ce1-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="53ce1-353">Получить и задать вниз pitch датчик имитации руки.</span><span class="sxs-lookup"><span data-stu-id="53ce1-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="53ce1-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="53ce1-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="53ce1-355">Получить и задать ли пирамиды обзора средства отслеживания имитации наличии учитывается.</span><span class="sxs-lookup"><span data-stu-id="53ce1-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="53ce1-356">При обоих руки всегда видимы.</span><span class="sxs-lookup"><span data-stu-id="53ce1-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="53ce1-357">Если не учитывается (по умолчанию) руки доступны только внутри пирамиды обзора средства отслеживания вручную.</span><span class="sxs-lookup"><span data-stu-id="53ce1-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="53ce1-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="53ce1-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="53ce1-359">Получить и задать свойства пирамиды обзора, позволяет определить, если руки являются видимыми для датчик имитации руки.</span><span class="sxs-lookup"><span data-stu-id="53ce1-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="53ce1-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="53ce1-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="53ce1-361">Интерфейс верхнего уровня для управления как имитации человеку.</span><span class="sxs-lookup"><span data-stu-id="53ce1-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="53ce1-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="53ce1-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="53ce1-363">Получить и задать положение узла по всему миру, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="53ce1-364">Соответствует позиция точки в центре фута как человеку.</span><span class="sxs-lookup"><span data-stu-id="53ce1-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="53ce1-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="53ce1-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="53ce1-366">Получить и задать направление имитации человеческих лиц в мире.</span><span class="sxs-lookup"><span data-stu-id="53ce1-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="53ce1-367">0 радиан сталкивается вниз отрицательной полуоси Z.</span><span class="sxs-lookup"><span data-stu-id="53ce1-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="53ce1-368">Положительное радианах поворот по часовой стрелке вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="53ce1-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="53ce1-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="53ce1-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="53ce1-370">Получить и задать высоту как имитации человеку в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="53ce1-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="53ce1-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="53ce1-372">Получите левой части имитации отдела.</span><span class="sxs-lookup"><span data-stu-id="53ce1-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="53ce1-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="53ce1-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="53ce1-374">Получите правой стороны из имитации отдела.</span><span class="sxs-lookup"><span data-stu-id="53ce1-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="53ce1-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="53ce1-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="53ce1-376">Получите заголовок как имитации человеку.</span><span class="sxs-lookup"><span data-stu-id="53ce1-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="53ce1-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="53ce1-378">Переместите имитации human относительно текущей позиции, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="53ce1-379">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-379">Parameters</span></span>
* <span data-ttu-id="53ce1-380">Трансляция - перевода для перемещения относительно текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="53ce1-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="53ce1-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="53ce1-382">Поворот имитации человека по отношению к его текущее направление, по часовой стрелке относительно оси Y</span><span class="sxs-lookup"><span data-stu-id="53ce1-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="53ce1-383">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-383">Parameters</span></span>
* <span data-ttu-id="53ce1-384">RADIANS - степень поворота вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="53ce1-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="53ce1-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="53ce1-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="53ce1-386">Доступны дополнительные свойства путем приведения ISimulatedHuman для ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="53ce1-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="53ce1-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="53ce1-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="53ce1-388">Получите левой 6-DOF контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="53ce1-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="53ce1-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="53ce1-390">Получите контроллер правой 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="53ce1-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="53ce1-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="53ce1-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="53ce1-392">Интерфейс, описывающий форму руки имитации отдела</span><span class="sxs-lookup"><span data-stu-id="53ce1-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="53ce1-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="53ce1-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="53ce1-394">Получите позицию узла по всему миру, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="53ce1-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="53ce1-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="53ce1-396">Получить и задать положение имитации Рука относительно как человеку в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="53ce1-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="53ce1-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="53ce1-398">Получить и задать ли Рука, активированного в данный момент.</span><span class="sxs-lookup"><span data-stu-id="53ce1-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="53ce1-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="53ce1-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="53ce1-400">Получите ли Рука видимой в данный момент для SimulatedDevice, (ie, будь то умеющий определяться с помощью HandTracker).</span><span class="sxs-lookup"><span data-stu-id="53ce1-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="53ce1-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="53ce1-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="53ce1-402">Переместите Рука, таким образом, оно становится видимым для SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="53ce1-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="53ce1-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="53ce1-404">Изменить положение имитации Рука относительно текущей позиции, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="53ce1-405">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-405">Parameters</span></span>
* <span data-ttu-id="53ce1-406">Трансляция - трансляции имитации вручную.</span><span class="sxs-lookup"><span data-stu-id="53ce1-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="53ce1-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="53ce1-408">Сделайте жест, с помощью имитации вручную.</span><span class="sxs-lookup"><span data-stu-id="53ce1-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="53ce1-409">Она будет только обнаружена системой при включении Рука.</span><span class="sxs-lookup"><span data-stu-id="53ce1-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="53ce1-410">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-410">Parameters</span></span>
* <span data-ttu-id="53ce1-411">жест - жестов для выполнения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="53ce1-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="53ce1-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="53ce1-413">Путем приведения ISimulatedHand для ISimulatedHand2 доступны дополнительные свойства.</span><span class="sxs-lookup"><span data-stu-id="53ce1-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="53ce1-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="53ce1-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="53ce1-415">Получить или задать угол поворота имитации вручную.</span><span class="sxs-lookup"><span data-stu-id="53ce1-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="53ce1-416">Положительное радианах поворот по часовой стрелке, при взгляде на оси.</span><span class="sxs-lookup"><span data-stu-id="53ce1-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="53ce1-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="53ce1-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="53ce1-418">Доступны дополнительные свойства путем приведения ISimulatedHand для ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="53ce1-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="53ce1-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="53ce1-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="53ce1-420">Получите совместные конфигурацию для указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="53ce1-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="53ce1-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="53ce1-422">Определить совместные конфигурацию для указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="53ce1-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="53ce1-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="53ce1-424">Значение Рука известных поза с необязательный флаг для анимации.</span><span class="sxs-lookup"><span data-stu-id="53ce1-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="53ce1-425">Примечание: анимация не привести соединений, немедленно отражения их окончательной объединенной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="53ce1-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="53ce1-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="53ce1-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="53ce1-427">Интерфейс, описывающий заголовок как имитации человеку.</span><span class="sxs-lookup"><span data-stu-id="53ce1-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="53ce1-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="53ce1-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="53ce1-429">Получите позицию узла по всему миру, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="53ce1-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="53ce1-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="53ce1-431">Получите поворот головы имитации.</span><span class="sxs-lookup"><span data-stu-id="53ce1-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="53ce1-432">Положительное радианах поворот по часовой стрелке, при взгляде на оси.</span><span class="sxs-lookup"><span data-stu-id="53ce1-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="53ce1-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="53ce1-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="53ce1-434">Получите диаметр имитации головного элемента.</span><span class="sxs-lookup"><span data-stu-id="53ce1-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="53ce1-435">Это значение используется для определения center головного элемента (точка вращения).</span><span class="sxs-lookup"><span data-stu-id="53ce1-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="53ce1-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="53ce1-437">Поворот имитации head относительно текущего вращения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="53ce1-438">Положительное радианах поворот по часовой стрелке, при взгляде на оси.</span><span class="sxs-lookup"><span data-stu-id="53ce1-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="53ce1-439">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-439">Parameters</span></span>
* <span data-ttu-id="53ce1-440">Поворот - сумму для поворота.</span><span class="sxs-lookup"><span data-stu-id="53ce1-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="53ce1-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="53ce1-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="53ce1-442">Доступны дополнительные свойства путем приведения ISimulatedHead для ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="53ce1-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="53ce1-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="53ce1-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="53ce1-444">Получите с точки зрения как имитации человеку.</span><span class="sxs-lookup"><span data-stu-id="53ce1-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="53ce1-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="53ce1-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="53ce1-446">Интерфейс, описывающий 6 DOF контроллер, связанный с имитации отдела.</span><span class="sxs-lookup"><span data-stu-id="53ce1-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="53ce1-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="53ce1-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="53ce1-448">Получите позицию узла по всему миру, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="53ce1-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="53ce1-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="53ce1-450">Получить или задать текущее состояние контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="53ce1-451">Состояние контроллера должно быть присвоено значение, отличные от Off перед любым вызовом перемещение, поворот и нажмите кнопки будет выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="53ce1-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="53ce1-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="53ce1-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="53ce1-453">Получить или задать положение виртуального контроллера относительно как человеку в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="53ce1-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="53ce1-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="53ce1-455">Получить или задать ориентацию имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="53ce1-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="53ce1-457">Изменить положение виртуального контроллера относительно текущей позиции, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="53ce1-458">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-458">Parameters</span></span>
* <span data-ttu-id="53ce1-459">Трансляция - трансляции имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="53ce1-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="53ce1-461">Нажмите кнопку имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="53ce1-462">Она будет только обнаружена системой при включении контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="53ce1-463">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-463">Parameters</span></span>
* <span data-ttu-id="53ce1-464">Кнопка - клавиши.</span><span class="sxs-lookup"><span data-stu-id="53ce1-464">button - The button to press.</span></span>

<span data-ttu-id="53ce1-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="53ce1-466">Отпустите кнопку на контроллере имитации.</span><span class="sxs-lookup"><span data-stu-id="53ce1-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="53ce1-467">Она будет только обнаружена системой при включении контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="53ce1-468">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-468">Parameters</span></span>
* <span data-ttu-id="53ce1-469">Кнопка — для освобождения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-469">button - The button to release.</span></span>

<span data-ttu-id="53ce1-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition (out float, float)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="53ce1-471">Получает позицию имитации пальцем на сенсорной панели имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="53ce1-472">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-472">Parameters</span></span>
* <span data-ttu-id="53ce1-473">x - горизонтальное положение пальца.</span><span class="sxs-lookup"><span data-stu-id="53ce1-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="53ce1-474">y - вертикальное положение пальца.</span><span class="sxs-lookup"><span data-stu-id="53ce1-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="53ce1-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="53ce1-476">Установка для позиции имитации палец на сенсорной панели имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="53ce1-477">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-477">Parameters</span></span>
* <span data-ttu-id="53ce1-478">x - горизонтальное положение пальца.</span><span class="sxs-lookup"><span data-stu-id="53ce1-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="53ce1-479">y - вертикальное положение пальца.</span><span class="sxs-lookup"><span data-stu-id="53ce1-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="53ce1-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="53ce1-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="53ce1-481">Дополнительные свойства и методы доступны путем приведения ISimulatedSixDofController для ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="53ce1-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="53ce1-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition (out float, float)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="53ce1-483">Получает позицию имитации джойстик имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="53ce1-484">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-484">Parameters</span></span>
* <span data-ttu-id="53ce1-485">x - горизонтальное положение джойстик.</span><span class="sxs-lookup"><span data-stu-id="53ce1-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="53ce1-486">y - вертикальное положение джойстик.</span><span class="sxs-lookup"><span data-stu-id="53ce1-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="53ce1-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="53ce1-488">Установка для позиции имитации джойстик имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="53ce1-489">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-489">Parameters</span></span>
* <span data-ttu-id="53ce1-490">x - горизонтальное положение джойстик.</span><span class="sxs-lookup"><span data-stu-id="53ce1-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="53ce1-491">y - вертикальное положение джойстик.</span><span class="sxs-lookup"><span data-stu-id="53ce1-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="53ce1-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="53ce1-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="53ce1-493">Извлечение или уровня заряда батареи имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="53ce1-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="53ce1-494">Значение должно быть больше 0,0 и меньше или равна 100,0.</span><span class="sxs-lookup"><span data-stu-id="53ce1-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="53ce1-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="53ce1-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="53ce1-496">Интерфейс, описывающий с точки зрения как имитации человеку.</span><span class="sxs-lookup"><span data-stu-id="53ce1-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="53ce1-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="53ce1-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="53ce1-498">Получите угол поворота имитации глаза.</span><span class="sxs-lookup"><span data-stu-id="53ce1-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="53ce1-499">Положительное радианах поворот по часовой стрелке, при взгляде на оси.</span><span class="sxs-lookup"><span data-stu-id="53ce1-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="53ce1-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="53ce1-501">Поворот имитации глаза относительно текущего вращения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="53ce1-502">Положительное радианах поворот по часовой стрелке, при взгляде на оси.</span><span class="sxs-lookup"><span data-stu-id="53ce1-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="53ce1-503">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-503">Parameters</span></span>
* <span data-ttu-id="53ce1-504">Поворот - сумму для поворота.</span><span class="sxs-lookup"><span data-stu-id="53ce1-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="53ce1-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="53ce1-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="53ce1-506">Получает или задает состояние калибровки имитации глаз.</span><span class="sxs-lookup"><span data-stu-id="53ce1-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="53ce1-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="53ce1-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="53ce1-508">Получите позицию узла по всему миру, в метрах.</span><span class="sxs-lookup"><span data-stu-id="53ce1-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="53ce1-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="53ce1-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="53ce1-510">Для воспроизведения загрузить интерфейс для взаимодействия с одной записью.</span><span class="sxs-lookup"><span data-stu-id="53ce1-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="53ce1-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="53ce1-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="53ce1-512">Извлекает список типов данных в записи.</span><span class="sxs-lookup"><span data-stu-id="53ce1-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="53ce1-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="53ce1-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="53ce1-514">Возвращает текущее состояние записи.</span><span class="sxs-lookup"><span data-stu-id="53ce1-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="53ce1-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="53ce1-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="53ce1-516">Запустите воспроизведение.</span><span class="sxs-lookup"><span data-stu-id="53ce1-516">Start the playback.</span></span> <span data-ttu-id="53ce1-517">Если запись приостановлена, воспроизведение возобновляется из приостановленного расположения; При остановке воспроизведения начнется в начале.</span><span class="sxs-lookup"><span data-stu-id="53ce1-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="53ce1-518">Если уже воспроизведение, этот вызов учитывается.</span><span class="sxs-lookup"><span data-stu-id="53ce1-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="53ce1-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="53ce1-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="53ce1-520">Приостанавливает воспроизведение на текущем месте.</span><span class="sxs-lookup"><span data-stu-id="53ce1-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="53ce1-521">Если запись остановлена, вызов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="53ce1-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="53ce1-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="53ce1-523">Ищет запись в указанное время (в 100 наносекунд интервалов с самого начала) и приостановит выполнение в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="53ce1-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="53ce1-524">Если время выходит за пределы записи, оно было приостановлено в последнем фрейме.</span><span class="sxs-lookup"><span data-stu-id="53ce1-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="53ce1-525">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-525">Parameters</span></span>
* <span data-ttu-id="53ce1-526">такты - время которого осуществляется поиск.</span><span class="sxs-lookup"><span data-stu-id="53ce1-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="53ce1-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="53ce1-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="53ce1-528">Останавливает воспроизведение и сбрасывает позицию в начало.</span><span class="sxs-lookup"><span data-stu-id="53ce1-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="53ce1-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="53ce1-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="53ce1-530">Интерфейс для получения изменений состояния во время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="53ce1-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="53ce1-532">Вызывается, когда изменилось состояние ISimulationRecording воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="53ce1-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="53ce1-533">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-533">Parameters</span></span>
* <span data-ttu-id="53ce1-534">новое состояние - новое состояние записи.</span><span class="sxs-lookup"><span data-stu-id="53ce1-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="53ce1-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="53ce1-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="53ce1-536">Корневой объект для создания объектов восприятие моделирования.</span><span class="sxs-lookup"><span data-stu-id="53ce1-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="53ce1-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="53ce1-538">Создание объекта для создания имитации пакетов и их доставки в указанный приемник.</span><span class="sxs-lookup"><span data-stu-id="53ce1-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="53ce1-539">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-539">Parameters</span></span>
* <span data-ttu-id="53ce1-540">приемник - приемник, который будет получать все созданные пакеты.</span><span class="sxs-lookup"><span data-stu-id="53ce1-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="53ce1-541">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="53ce1-541">Return value</span></span>

<span data-ttu-id="53ce1-542">Созданный диспетчер.</span><span class="sxs-lookup"><span data-stu-id="53ce1-542">The created Manager.</span></span>

<span data-ttu-id="53ce1-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="53ce1-544">Создание приемника, который сохраняет все принимаемые пакеты в файл по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="53ce1-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="53ce1-545">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-545">Parameters</span></span>
* <span data-ttu-id="53ce1-546">Path - путь к файлу для создания.</span><span class="sxs-lookup"><span data-stu-id="53ce1-546">path - The path of the file to create.</span></span>

<span data-ttu-id="53ce1-547">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="53ce1-547">Return value</span></span>

<span data-ttu-id="53ce1-548">Созданный приемник.</span><span class="sxs-lookup"><span data-stu-id="53ce1-548">The created sink.</span></span>

<span data-ttu-id="53ce1-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="53ce1-550">Загрузите записи из указанного файла.</span><span class="sxs-lookup"><span data-stu-id="53ce1-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="53ce1-551">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-551">Parameters</span></span>
* <span data-ttu-id="53ce1-552">Path - путь к загружаемому файлу.</span><span class="sxs-lookup"><span data-stu-id="53ce1-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="53ce1-553">Фабрика - фабрики, используемые записи для создания ISimulationStreamSink при необходимости.</span><span class="sxs-lookup"><span data-stu-id="53ce1-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="53ce1-554">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="53ce1-554">Return value</span></span>

<span data-ttu-id="53ce1-555">Загрузить записи.</span><span class="sxs-lookup"><span data-stu-id="53ce1-555">The loaded recording.</span></span>

<span data-ttu-id="53ce1-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="53ce1-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="53ce1-557">Загрузите записи из указанного файла.</span><span class="sxs-lookup"><span data-stu-id="53ce1-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="53ce1-558">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-558">Parameters</span></span>
* <span data-ttu-id="53ce1-559">Path - путь к загружаемому файлу.</span><span class="sxs-lookup"><span data-stu-id="53ce1-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="53ce1-560">Фабрика - фабрики, используемые записи для создания ISimulationStreamSink при необходимости.</span><span class="sxs-lookup"><span data-stu-id="53ce1-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="53ce1-561">обновляет обратного вызова, который получает обратный вызов - regrading записи состояния.</span><span class="sxs-lookup"><span data-stu-id="53ce1-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="53ce1-562">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="53ce1-562">Return value</span></span>

<span data-ttu-id="53ce1-563">Загрузить записи.</span><span class="sxs-lookup"><span data-stu-id="53ce1-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="53ce1-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="53ce1-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="53ce1-565">Описание различных типов потоковых данных.</span><span class="sxs-lookup"><span data-stu-id="53ce1-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="53ce1-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="53ce1-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="53ce1-567">Значение sentinel, используемый для указания нет типов данных stream.</span><span class="sxs-lookup"><span data-stu-id="53ce1-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="53ce1-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="53ce1-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="53ce1-569">Stream данные, касающиеся положение и ориентацию орла.</span><span class="sxs-lookup"><span data-stu-id="53ce1-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="53ce1-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="53ce1-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="53ce1-571">Stream данные, касающиеся позиции и жесты руки.</span><span class="sxs-lookup"><span data-stu-id="53ce1-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="53ce1-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="53ce1-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="53ce1-573">Stream данные, касающиеся пространственное сопоставление среды.</span><span class="sxs-lookup"><span data-stu-id="53ce1-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="53ce1-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="53ce1-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="53ce1-575">Stream данные, касающиеся калибровки устройства.</span><span class="sxs-lookup"><span data-stu-id="53ce1-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="53ce1-576">Калибровка пакетов принимаются только системой в удаленном режиме.</span><span class="sxs-lookup"><span data-stu-id="53ce1-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="53ce1-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="53ce1-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="53ce1-578">Stream данные о среде устройства.</span><span class="sxs-lookup"><span data-stu-id="53ce1-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="53ce1-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="53ce1-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="53ce1-580">Значение sentinel, используемый для указания всех типов записанные данные.</span><span class="sxs-lookup"><span data-stu-id="53ce1-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="53ce1-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="53ce1-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="53ce1-582">Объект, который получает пакеты данных из потока моделирования.</span><span class="sxs-lookup"><span data-stu-id="53ce1-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="53ce1-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (целое число без знака длиной, пакет byte [])**</span><span class="sxs-lookup"><span data-stu-id="53ce1-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="53ce1-584">Получает один пакет, внутренне типизированных и с контролем версий.</span><span class="sxs-lookup"><span data-stu-id="53ce1-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="53ce1-585">Параметры</span><span class="sxs-lookup"><span data-stu-id="53ce1-585">Parameters</span></span>
* <span data-ttu-id="53ce1-586">Длина — длина пакета.</span><span class="sxs-lookup"><span data-stu-id="53ce1-586">length - The length of the packet.</span></span>
* <span data-ttu-id="53ce1-587">пакет - данные пакета.</span><span class="sxs-lookup"><span data-stu-id="53ce1-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="53ce1-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="53ce1-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="53ce1-589">Объект, который создает ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="53ce1-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="53ce1-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="53ce1-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="53ce1-591">Создает один экземпляр ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="53ce1-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="53ce1-592">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="53ce1-592">Return value</span></span>

<span data-ttu-id="53ce1-593">Созданный приемник.</span><span class="sxs-lookup"><span data-stu-id="53ce1-593">The created sink.</span></span>
