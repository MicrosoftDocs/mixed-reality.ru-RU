---
title: Имитация восприятия
description: Рекомендации по использованию библиотеки моделирования восприятия для автоматизации имитации входных данных для впечатляющих приложений
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
# <a name="perception-simulation"></a><span data-ttu-id="68e0c-104">Имитация восприятия</span><span class="sxs-lookup"><span data-stu-id="68e0c-104">Perception simulation</span></span>

<span data-ttu-id="68e0c-105">Вы хотите создать автоматический тест для приложения?</span><span class="sxs-lookup"><span data-stu-id="68e0c-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="68e0c-106">Вы хотите, чтобы тесты переходили за пределы модульного тестирования на уровне компонентов и действительно протестировали свое приложение как можно более полное?</span><span class="sxs-lookup"><span data-stu-id="68e0c-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="68e0c-107">Имитация восприятия — это то, что вы ищете.</span><span class="sxs-lookup"><span data-stu-id="68e0c-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="68e0c-108">Библиотека моделирования восприятия отправляет в приложение пользовательские и мировые входные данные, что позволяет автоматизировать тесты.</span><span class="sxs-lookup"><span data-stu-id="68e0c-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="68e0c-109">Например, можно имитировать входные данные человека, который смотрит в конкретную повторяемую единицу, а затем выполнить жест или использовать контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="68e0c-110">Имитация восприятия может отправить смоделированные входные данные на физический HoloLens, эмулятор HoloLens (1 общий), эмулятор HoloLens 2 или компьютер с установленным порталом смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="68e0c-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="68e0c-111">Имитация восприятия обходит активные датчики на устройстве смешанной реальности и отправляет смоделированные входные данные приложениям, работающим на устройстве.</span><span class="sxs-lookup"><span data-stu-id="68e0c-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="68e0c-112">Приложения получают эти события ввода через те же API-интерфейсы, которые они всегда используют, и не могут сообщать о различиях между выполнением с реальными датчиками и с имитацией восприятия.</span><span class="sxs-lookup"><span data-stu-id="68e0c-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="68e0c-113">Имитация восприятия — это та же технология, которая используется эмуляторами HoloLens для отправки смоделированных входных данных на виртуальную машину HoloLens.</span><span class="sxs-lookup"><span data-stu-id="68e0c-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="68e0c-114">Чтобы приступить к использованию моделирования в коде, начните с создания объекта Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="68e0c-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="68e0c-115">Из этого объекта можно выдавать команды для управления свойствами имитации «человека», включая позиционирование головной стороны, расположение руки и жесты, а также включать и управлять контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="68e0c-116">Настройка проекта Visual Studio для имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="68e0c-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="68e0c-117">[Установите эмулятор HoloLens](install-the-tools.md) на компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="68e0c-118">Эмулятор включает библиотеки, которые будут использоваться для имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="68e0c-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="68e0c-119">Создайте проект Visual Studio C# для настольных систем (проект консоли прекрасно работает, чтобы начать работу).</span><span class="sxs-lookup"><span data-stu-id="68e0c-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="68e0c-120">Добавьте в проект следующие двоичные файлы в виде ссылок (проект-> Добавить > ссылку...). Их можно найти в% ProgramFiles (x86)% \ Microsoft XDE\\(версия), например **% ProgramFiles (x86)% \ Microsoft XDE\\10.0.18362.0** для эмулятора HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="68e0c-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="68e0c-121">(Примечание. Хотя двоичные файлы являются частью эмулятора HoloLens 2, они также работают для Windows Mixed Reality на настольном компьютере.) конкретного.</span><span class="sxs-lookup"><span data-stu-id="68e0c-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="68e0c-122">Перцептионсимулатионманажер. Interop. dll — управляемая C# оболочка для имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="68e0c-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="68e0c-123">2\.</span><span class="sxs-lookup"><span data-stu-id="68e0c-123">b.</span></span> <span data-ttu-id="68e0c-124">Перцептионсимулатионрест. DLL — библиотека для настройки канала связи через веб-сокет с HoloLens или Emulator.</span><span class="sxs-lookup"><span data-stu-id="68e0c-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="68e0c-125">В.</span><span class="sxs-lookup"><span data-stu-id="68e0c-125">c.</span></span> <span data-ttu-id="68e0c-126">Симулатионстреам. Interop. dll — общие типы для моделирования.</span><span class="sxs-lookup"><span data-stu-id="68e0c-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="68e0c-127">Добавьте в проект a двоичный файл Перцептионсимулатионманажер. dll реализации.</span><span class="sxs-lookup"><span data-stu-id="68e0c-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="68e0c-128">Сначала добавьте его в качестве двоичного файла в проект (проект-> Добавить-> существующий элемент...). Сохраните его как ссылку, чтобы он не скопировал его в исходную папку проекта.</span><span class="sxs-lookup"><span data-stu-id="68e0c-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="68e0c-129">![Добавьте перцептионсимулатионманажер. dll в проект как ссылку](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="68e0c-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="68e0c-130">Затем убедитесь, что он скопирован в выходную папку при сборке.</span><span class="sxs-lookup"><span data-stu-id="68e0c-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="68e0c-131">Он находится на странице свойств двоичного файла.</span><span class="sxs-lookup"><span data-stu-id="68e0c-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="68e0c-132">![Пометьте Перцептионсимулатионманажер. dll для копирования в выходной каталог](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="68e0c-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="68e0c-133">Задайте для активной платформы решения x64.</span><span class="sxs-lookup"><span data-stu-id="68e0c-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="68e0c-134">(Используйте Configuration Manager, чтобы создать запись платформы для x64, если она еще не существует.)</span><span class="sxs-lookup"><span data-stu-id="68e0c-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="68e0c-135">Создание объекта Иперцептионсимулатион Manager</span><span class="sxs-lookup"><span data-stu-id="68e0c-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="68e0c-136">Для управления имитацией вы получаете обновления объектов, полученных из объекта Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="68e0c-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="68e0c-137">Первым шагом является получение этого объекта и его подключение к целевому устройству или эмулятору.</span><span class="sxs-lookup"><span data-stu-id="68e0c-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="68e0c-138">Вы можете получить IP-адрес эмулятора, нажав кнопку на портале устройства на [панели инструментов](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="68e0c-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="68e0c-139">![Значок](images/emulator-deviceportal.png) "открыть портал устройств" **откройте портал устройств**: Открывает в эмуляторе портал устройств Windows для HoloLens OS.</span><span class="sxs-lookup"><span data-stu-id="68e0c-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="68e0c-140">Для Windows Mixed Reality это можно получить в приложении "Параметры" в разделе "Обновление & безопасность", а затем "для разработчиков" в разделе "подключение с помощью:" раздела "Включение портала устройств".</span><span class="sxs-lookup"><span data-stu-id="68e0c-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="68e0c-141">Обязательно запишите IP-адрес и порт.</span><span class="sxs-lookup"><span data-stu-id="68e0c-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="68e0c-142">Во-первых, вы вызываете Рестсимулатионстреамсинк. Create для получения объекта Рестсимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="68e0c-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="68e0c-143">Это целевое устройство или эмулятор, которым будет управлять HTTP-соединением.</span><span class="sxs-lookup"><span data-stu-id="68e0c-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="68e0c-144">Команды будут переданы и обработаны на [портале устройств Windows](using-the-windows-device-portal.md) , работающем на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="68e0c-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="68e0c-145">Ниже приведены четыре параметра, которые необходимо создать для объекта.</span><span class="sxs-lookup"><span data-stu-id="68e0c-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="68e0c-146">URI URI — IP-адрес целевого устройства (например, "http://123.123.123.123" или "http://123.123.123.123:50080").</span><span class="sxs-lookup"><span data-stu-id="68e0c-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="68e0c-147">System .NET. NetworkCredential Credentials — имя пользователя и пароль для подключения к [порталу устройств Windows](using-the-windows-device-portal.md) на целевом устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="68e0c-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="68e0c-148">При подключении к эмулятору через его локальный адрес (например, 168. *.* . \*) на том же компьютере будут приниматься любые учетные данные.</span><span class="sxs-lookup"><span data-stu-id="68e0c-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="68e0c-149">bool обычная — true для обычного приоритета, false для низкого приоритета.</span><span class="sxs-lookup"><span data-stu-id="68e0c-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="68e0c-150">Обычно необходимо задать для этого параметра значение *true* для тестовых сценариев, что позволяет вашему тесту осуществлять управление.</span><span class="sxs-lookup"><span data-stu-id="68e0c-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="68e0c-151">Эмулятор и имитация Windows Mixed Reality используют соединения с низким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="68e0c-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="68e0c-152">Если в тесте также используется подключение с низким приоритетом, то последнее установленное соединение будет управляться.</span><span class="sxs-lookup"><span data-stu-id="68e0c-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="68e0c-153">Для отмены асинхронной операции маркера токена System. Threading. CancellationToken.</span><span class="sxs-lookup"><span data-stu-id="68e0c-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="68e0c-154">Во вторых, вы создадите Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="68e0c-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="68e0c-155">Это объект, используемый для управления имитацией.</span><span class="sxs-lookup"><span data-stu-id="68e0c-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="68e0c-156">Обратите внимание, что это также необходимо сделать в асинхронном методе.</span><span class="sxs-lookup"><span data-stu-id="68e0c-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="68e0c-157">Управление имитируемым человеком</span><span class="sxs-lookup"><span data-stu-id="68e0c-157">Control the simulated Human</span></span>

<span data-ttu-id="68e0c-158">Иперцептионсимулатионманажер имеет свойство человеческого, которое возвращает объект Исимулатедхуман.</span><span class="sxs-lookup"><span data-stu-id="68e0c-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="68e0c-159">Для управления имитируемым человеком выполните операции с этим объектом.</span><span class="sxs-lookup"><span data-stu-id="68e0c-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="68e0c-160">Пример:</span><span class="sxs-lookup"><span data-stu-id="68e0c-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="68e0c-161">Простой пример C# консольного приложения</span><span class="sxs-lookup"><span data-stu-id="68e0c-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="68e0c-162">Расширенный пример C# консольного приложения</span><span class="sxs-lookup"><span data-stu-id="68e0c-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="68e0c-163">Примечание о 6-ДОФ контроллерах</span><span class="sxs-lookup"><span data-stu-id="68e0c-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="68e0c-164">Перед вызовом каких-либо свойств для методов смоделированного 6-ДОФ контроллера необходимо активировать контроллер.</span><span class="sxs-lookup"><span data-stu-id="68e0c-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="68e0c-165">Это приведет к исключению.</span><span class="sxs-lookup"><span data-stu-id="68e0c-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="68e0c-166">Начиная с Windows 10 Can 2019 обновление, смоделированные 6-ДОФ контроллеры можно установить и активировать, задав для свойства Status объекта Исимулатедсиксдофконтроллер значение Симулатедсиксдофконтроллерстатус. Active.</span><span class="sxs-lookup"><span data-stu-id="68e0c-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="68e0c-167">В обновлении Windows 10 октября 2018 и более ранних версиях необходимо отдельно установить смоделированный 6-ДОФ контроллер, вызвав средство Перцептионсимулатиондевице, расположенное в папке \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="68e0c-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="68e0c-168">Использование этого средства выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="68e0c-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="68e0c-169">Например</span><span class="sxs-lookup"><span data-stu-id="68e0c-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="68e0c-170">Поддерживаются следующие действия:</span><span class="sxs-lookup"><span data-stu-id="68e0c-170">Supported actions are:</span></span>
* <span data-ttu-id="68e0c-171">i = установить</span><span class="sxs-lookup"><span data-stu-id="68e0c-171">i = install</span></span>
* <span data-ttu-id="68e0c-172">q = запрос</span><span class="sxs-lookup"><span data-stu-id="68e0c-172">q = query</span></span>
* <span data-ttu-id="68e0c-173">r = удалить</span><span class="sxs-lookup"><span data-stu-id="68e0c-173">r = remove</span></span>

<span data-ttu-id="68e0c-174">Поддерживаются следующие экземпляры:</span><span class="sxs-lookup"><span data-stu-id="68e0c-174">Supported instances are:</span></span>
* <span data-ttu-id="68e0c-175">1 = левый 6-ДОФ контроллер</span><span class="sxs-lookup"><span data-stu-id="68e0c-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="68e0c-176">2 = правильный 6-ДОФ контроллер</span><span class="sxs-lookup"><span data-stu-id="68e0c-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="68e0c-177">Код выхода процесса будет указывать на успех (нулевое возвращаемое значение) или ошибку (ненулевое возвращаемое значение).</span><span class="sxs-lookup"><span data-stu-id="68e0c-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="68e0c-178">При использовании действия "q" для запроса того, установлен ли контроллер, возвращаемое значение будет равно нулю (0), если контроллер еще не установлен, или один (1), если контроллер установлен.</span><span class="sxs-lookup"><span data-stu-id="68e0c-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="68e0c-179">При удалении контроллера в Windows 10 октября с обновлением 2018 или более ранней версии установите его состояние в OFF через API, а затем вызовите средство Перцептионсимулатиондевице.</span><span class="sxs-lookup"><span data-stu-id="68e0c-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="68e0c-180">Обратите внимание, что это средство необходимо запускать от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="68e0c-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="68e0c-181">Справочник по API</span><span class="sxs-lookup"><span data-stu-id="68e0c-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="68e0c-182">Microsoft. Перцептионсимулатион. Симулатеддевицетипе</span><span class="sxs-lookup"><span data-stu-id="68e0c-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="68e0c-183">Описывает тип имитации устройства</span><span class="sxs-lookup"><span data-stu-id="68e0c-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="68e0c-184">**Microsoft. Перцептионсимулатион. Симулатеддевицетипе. Reference**</span><span class="sxs-lookup"><span data-stu-id="68e0c-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="68e0c-185">Фиктивное эталонное устройство, используемое по умолчанию для Перцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="68e0c-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="68e0c-186">Microsoft. Перцептионсимулатион. Хеадтраккермоде</span><span class="sxs-lookup"><span data-stu-id="68e0c-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="68e0c-187">Описывает режим «головной транспортер»</span><span class="sxs-lookup"><span data-stu-id="68e0c-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="68e0c-188">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. Default**</span><span class="sxs-lookup"><span data-stu-id="68e0c-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="68e0c-189">Отслеживание головок по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="68e0c-189">Default Head Tracking.</span></span> <span data-ttu-id="68e0c-190">Это означает, что система может выбрать оптимальный режим отслеживания головной системы на основе условий среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="68e0c-191">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. Orientation**</span><span class="sxs-lookup"><span data-stu-id="68e0c-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="68e0c-192">Только отслеживание головной страницы.</span><span class="sxs-lookup"><span data-stu-id="68e0c-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="68e0c-193">Это означает, что отслеживающее расположение может быть ненадежным, а некоторые функциональные возможности, зависящие от головного расположения, могут быть недоступны.</span><span class="sxs-lookup"><span data-stu-id="68e0c-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="68e0c-194">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. положением**</span><span class="sxs-lookup"><span data-stu-id="68e0c-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="68e0c-195">Отслеживание позиционированных головок.</span><span class="sxs-lookup"><span data-stu-id="68e0c-195">Positional Head Tracking.</span></span> <span data-ttu-id="68e0c-196">Это означает, что положение и ориентация отслеживающей головки надежны</span><span class="sxs-lookup"><span data-stu-id="68e0c-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="68e0c-197">Microsoft. Перцептионсимулатион. Симулатеджестуре</span><span class="sxs-lookup"><span data-stu-id="68e0c-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="68e0c-198">Описывает имитацию жеста</span><span class="sxs-lookup"><span data-stu-id="68e0c-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="68e0c-199">**Microsoft. Перцептионсимулатион. Симулатеджестуре. None**</span><span class="sxs-lookup"><span data-stu-id="68e0c-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="68e0c-200">Значение Sentinel, используемое для обозначения отсутствия жестов.</span><span class="sxs-lookup"><span data-stu-id="68e0c-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="68e0c-201">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Финжерпрессед**</span><span class="sxs-lookup"><span data-stu-id="68e0c-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="68e0c-202">Жест нажатия пальца.</span><span class="sxs-lookup"><span data-stu-id="68e0c-202">A finger pressed gesture.</span></span>

<span data-ttu-id="68e0c-203">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Финжеррелеасед**</span><span class="sxs-lookup"><span data-stu-id="68e0c-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="68e0c-204">Жест отпуска пальца.</span><span class="sxs-lookup"><span data-stu-id="68e0c-204">A finger released gesture.</span></span>

<span data-ttu-id="68e0c-205">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Home**</span><span class="sxs-lookup"><span data-stu-id="68e0c-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="68e0c-206">Жест домашнего или системного.</span><span class="sxs-lookup"><span data-stu-id="68e0c-206">The home/system gesture.</span></span>

<span data-ttu-id="68e0c-207">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Max**</span><span class="sxs-lookup"><span data-stu-id="68e0c-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="68e0c-208">Максимально допустимый жест.</span><span class="sxs-lookup"><span data-stu-id="68e0c-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="68e0c-209">Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус</span><span class="sxs-lookup"><span data-stu-id="68e0c-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="68e0c-210">Возможные состояния имитации 6-ДОФ контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="68e0c-211">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Off**</span><span class="sxs-lookup"><span data-stu-id="68e0c-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="68e0c-212">6-ДОФ контроллер отключен.</span><span class="sxs-lookup"><span data-stu-id="68e0c-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="68e0c-213">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Active**</span><span class="sxs-lookup"><span data-stu-id="68e0c-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="68e0c-214">Контроллер ДОФ включается и отключается.</span><span class="sxs-lookup"><span data-stu-id="68e0c-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="68e0c-215">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Траккинглост**</span><span class="sxs-lookup"><span data-stu-id="68e0c-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="68e0c-216">6-ДОФ контроллер включен, но не может быть записан.</span><span class="sxs-lookup"><span data-stu-id="68e0c-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="68e0c-217">Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон</span><span class="sxs-lookup"><span data-stu-id="68e0c-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="68e0c-218">Поддерживаемые кнопки на имитации 6-ДОФ контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="68e0c-219">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. None**</span><span class="sxs-lookup"><span data-stu-id="68e0c-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="68e0c-220">Значение Sentinel, используемое для отсутствия кнопок.</span><span class="sxs-lookup"><span data-stu-id="68e0c-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="68e0c-221">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Home**</span><span class="sxs-lookup"><span data-stu-id="68e0c-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="68e0c-222">Нажата кнопка Главная.</span><span class="sxs-lookup"><span data-stu-id="68e0c-222">The Home button is pressed.</span></span>

<span data-ttu-id="68e0c-223">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Menu**</span><span class="sxs-lookup"><span data-stu-id="68e0c-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="68e0c-224">Нажата кнопка меню.</span><span class="sxs-lookup"><span data-stu-id="68e0c-224">The Menu button is pressed.</span></span>

<span data-ttu-id="68e0c-225">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. захват**</span><span class="sxs-lookup"><span data-stu-id="68e0c-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="68e0c-226">Нажата кнопка захвата.</span><span class="sxs-lookup"><span data-stu-id="68e0c-226">The Grip button is pressed.</span></span>

<span data-ttu-id="68e0c-227">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Таучпадпресс**</span><span class="sxs-lookup"><span data-stu-id="68e0c-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="68e0c-228">Сенсорная панель нажата.</span><span class="sxs-lookup"><span data-stu-id="68e0c-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="68e0c-229">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Select**</span><span class="sxs-lookup"><span data-stu-id="68e0c-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="68e0c-230">Нажата кнопка выбрать.</span><span class="sxs-lookup"><span data-stu-id="68e0c-230">The Select button is pressed.</span></span>

<span data-ttu-id="68e0c-231">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Таучпадтауч**</span><span class="sxs-lookup"><span data-stu-id="68e0c-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="68e0c-232">Сенсорная панель затронута.</span><span class="sxs-lookup"><span data-stu-id="68e0c-232">The TouchPad is touched.</span></span>

<span data-ttu-id="68e0c-233">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. аналоговый стик**</span><span class="sxs-lookup"><span data-stu-id="68e0c-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="68e0c-234">Аналоговый стик нажат.</span><span class="sxs-lookup"><span data-stu-id="68e0c-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="68e0c-235">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Max**</span><span class="sxs-lookup"><span data-stu-id="68e0c-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="68e0c-236">Максимальная допустимая кнопка.</span><span class="sxs-lookup"><span data-stu-id="68e0c-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="68e0c-237">Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате</span><span class="sxs-lookup"><span data-stu-id="68e0c-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="68e0c-238">Состояние калибровки имитации глаз</span><span class="sxs-lookup"><span data-stu-id="68e0c-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="68e0c-239">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. недоступно**</span><span class="sxs-lookup"><span data-stu-id="68e0c-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="68e0c-240">Калибровка глаз недоступна.</span><span class="sxs-lookup"><span data-stu-id="68e0c-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="68e0c-241">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. ready**</span><span class="sxs-lookup"><span data-stu-id="68e0c-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="68e0c-242">Эти глаза были откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="68e0c-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="68e0c-243">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="68e0c-243">This is the default value.</span></span>

<span data-ttu-id="68e0c-244">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. Настройка**</span><span class="sxs-lookup"><span data-stu-id="68e0c-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="68e0c-245">Эти глаза откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="68e0c-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="68e0c-246">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. Усеркалибратионнидед**</span><span class="sxs-lookup"><span data-stu-id="68e0c-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="68e0c-247">Необходимо откалибровать глаза.</span><span class="sxs-lookup"><span data-stu-id="68e0c-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="68e0c-248">Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци</span><span class="sxs-lookup"><span data-stu-id="68e0c-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="68e0c-249">Точность отслеживания соединения руки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="68e0c-250">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. недоступно**</span><span class="sxs-lookup"><span data-stu-id="68e0c-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="68e0c-251">Совместное соединение не производится.</span><span class="sxs-lookup"><span data-stu-id="68e0c-251">The joint is not tracked.</span></span>

<span data-ttu-id="68e0c-252">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. приблизительный**</span><span class="sxs-lookup"><span data-stu-id="68e0c-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="68e0c-253">Совместное размещение выводится.</span><span class="sxs-lookup"><span data-stu-id="68e0c-253">The joint position is inferred.</span></span>

<span data-ttu-id="68e0c-254">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. Visible**</span><span class="sxs-lookup"><span data-stu-id="68e0c-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="68e0c-255">Совместное соединение полностью отслеживание.</span><span class="sxs-lookup"><span data-stu-id="68e0c-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="68e0c-256">Microsoft. Перцептионсимулатион. Симулатедхандпосе</span><span class="sxs-lookup"><span data-stu-id="68e0c-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="68e0c-257">Точность отслеживания соединения руки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="68e0c-258">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Closed**</span><span class="sxs-lookup"><span data-stu-id="68e0c-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="68e0c-259">Соединения пальца руки настраиваются для отражения закрытого объекта.</span><span class="sxs-lookup"><span data-stu-id="68e0c-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="68e0c-260">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Open**</span><span class="sxs-lookup"><span data-stu-id="68e0c-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="68e0c-261">Соединения пальца руки настраиваются для отражения открытой части.</span><span class="sxs-lookup"><span data-stu-id="68e0c-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="68e0c-262">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Point**</span><span class="sxs-lookup"><span data-stu-id="68e0c-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="68e0c-263">Соединения пальца руки настраиваются в соответствии с указывающим на себя.</span><span class="sxs-lookup"><span data-stu-id="68e0c-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="68e0c-264">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. сжатие**</span><span class="sxs-lookup"><span data-stu-id="68e0c-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="68e0c-265">Соединения пальца руки настраиваются в соответствии с набором сжатия.</span><span class="sxs-lookup"><span data-stu-id="68e0c-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="68e0c-266">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Max**</span><span class="sxs-lookup"><span data-stu-id="68e0c-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="68e0c-267">Максимальное допустимое значение для Симулатедхандпосе.</span><span class="sxs-lookup"><span data-stu-id="68e0c-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="68e0c-268">Microsoft. Перцептионсимулатион. Плайбаккстате</span><span class="sxs-lookup"><span data-stu-id="68e0c-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="68e0c-269">Описывает состояние воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="68e0c-270">**Microsoft. Перцептионсимулатион. Плайбаккстате. Stopped**</span><span class="sxs-lookup"><span data-stu-id="68e0c-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="68e0c-271">Запись сейчас остановлена и готова к воспроизведению.</span><span class="sxs-lookup"><span data-stu-id="68e0c-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="68e0c-272">**Microsoft. Перцептионсимулатион. Плайбаккстате. Play**</span><span class="sxs-lookup"><span data-stu-id="68e0c-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="68e0c-273">Сейчас запись воспроизводится.</span><span class="sxs-lookup"><span data-stu-id="68e0c-273">The recording is currently playing.</span></span>

<span data-ttu-id="68e0c-274">**Microsoft. Перцептионсимулатион. Плайбаккстате. приостановлено**</span><span class="sxs-lookup"><span data-stu-id="68e0c-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="68e0c-275">Запись в данный момент приостановлена.</span><span class="sxs-lookup"><span data-stu-id="68e0c-275">The recording is currently paused.</span></span>

<span data-ttu-id="68e0c-276">**Microsoft. Перцептионсимулатион. Плайбаккстате. end**</span><span class="sxs-lookup"><span data-stu-id="68e0c-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="68e0c-277">Запись достигла конца.</span><span class="sxs-lookup"><span data-stu-id="68e0c-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="68e0c-278">Microsoft. Перцептионсимулатион. Vector3</span><span class="sxs-lookup"><span data-stu-id="68e0c-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="68e0c-279">Описывает вектор 3 компонентов, который может описывать точку или вектор в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="68e0c-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="68e0c-280">**Microsoft. Перцептионсимулатион. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="68e0c-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="68e0c-281">Компонент X вектора.</span><span class="sxs-lookup"><span data-stu-id="68e0c-281">The X component of the vector.</span></span>

<span data-ttu-id="68e0c-282">**Microsoft. Перцептионсимулатион. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="68e0c-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="68e0c-283">Компонент Y вектора.</span><span class="sxs-lookup"><span data-stu-id="68e0c-283">The Y component of the vector.</span></span>

<span data-ttu-id="68e0c-284">**Microsoft. Перцептионсимулатион. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="68e0c-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="68e0c-285">Компонент Z вектора.</span><span class="sxs-lookup"><span data-stu-id="68e0c-285">The Z component of the vector.</span></span>

<span data-ttu-id="68e0c-286">**Microsoft. Перцептионсимулатион. Vector3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="68e0c-287">Создайте новый Vector3.</span><span class="sxs-lookup"><span data-stu-id="68e0c-287">Construct a new Vector3.</span></span>

<span data-ttu-id="68e0c-288">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-288">Parameters</span></span>
* <span data-ttu-id="68e0c-289">x — компонент x вектора.</span><span class="sxs-lookup"><span data-stu-id="68e0c-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="68e0c-290">y — компонент y вектора.</span><span class="sxs-lookup"><span data-stu-id="68e0c-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="68e0c-291">z — компонент z вектора.</span><span class="sxs-lookup"><span data-stu-id="68e0c-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="68e0c-292">Microsoft. Перцептионсимулатион. Rotation3</span><span class="sxs-lookup"><span data-stu-id="68e0c-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="68e0c-293">Описывает поворот 3 компонентов.</span><span class="sxs-lookup"><span data-stu-id="68e0c-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="68e0c-294">**Microsoft. Перцептионсимулатион. Rotation3. шаг**</span><span class="sxs-lookup"><span data-stu-id="68e0c-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="68e0c-295">Компонент шаг поворота вокруг оси X.</span><span class="sxs-lookup"><span data-stu-id="68e0c-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="68e0c-296">**Microsoft. Перцептионсимулатион. Rotation3. значения нутации**</span><span class="sxs-lookup"><span data-stu-id="68e0c-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="68e0c-297">Компонент значения нутации вращения, который находится справа вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="68e0c-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="68e0c-298">**Microsoft. Перцептионсимулатион. Rotation3. рулон**</span><span class="sxs-lookup"><span data-stu-id="68e0c-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="68e0c-299">Компонент рулона поворота, который находится справа вокруг оси Z.</span><span class="sxs-lookup"><span data-stu-id="68e0c-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="68e0c-300">**Microsoft. Перцептионсимулатион. Rotation3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="68e0c-301">Создайте новый Rotation3.</span><span class="sxs-lookup"><span data-stu-id="68e0c-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="68e0c-302">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-302">Parameters</span></span>
* <span data-ttu-id="68e0c-303">шаг — компонент шага поворота.</span><span class="sxs-lookup"><span data-stu-id="68e0c-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="68e0c-304">значения нутации — компонент значения нутации вращения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="68e0c-305">рулон — компонент рулона поворота.</span><span class="sxs-lookup"><span data-stu-id="68e0c-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="68e0c-306">Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион</span><span class="sxs-lookup"><span data-stu-id="68e0c-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="68e0c-307">Описывает конфигурацию соединения с имитацией руки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="68e0c-308">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. положением**</span><span class="sxs-lookup"><span data-stu-id="68e0c-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="68e0c-309">Расположение соединения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-309">The position of the joint.</span></span>

<span data-ttu-id="68e0c-310">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. вращение**</span><span class="sxs-lookup"><span data-stu-id="68e0c-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="68e0c-311">Поворот соединения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-311">The rotation of the joint.</span></span>

<span data-ttu-id="68e0c-312">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. Траккингаккураци**</span><span class="sxs-lookup"><span data-stu-id="68e0c-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="68e0c-313">Точность отслеживания соединения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="68e0c-314">Microsoft. Перцептионсимулатион. Фрустум</span><span class="sxs-lookup"><span data-stu-id="68e0c-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="68e0c-315">Описывает представление фрустум, как обычно используется камерой.</span><span class="sxs-lookup"><span data-stu-id="68e0c-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="68e0c-316">**Microsoft. Перцептионсимулатион. Фрустум. Near**</span><span class="sxs-lookup"><span data-stu-id="68e0c-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="68e0c-317">Минимальное расстояние, которое содержится в фрустум.</span><span class="sxs-lookup"><span data-stu-id="68e0c-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="68e0c-318">**Microsoft. Перцептионсимулатион. Фрустум. FAR**</span><span class="sxs-lookup"><span data-stu-id="68e0c-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="68e0c-319">Максимальное расстояние, которое содержится в фрустум.</span><span class="sxs-lookup"><span data-stu-id="68e0c-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="68e0c-320">**Microsoft. Перцептионсимулатион. Фрустум. Фиелдофвиев**</span><span class="sxs-lookup"><span data-stu-id="68e0c-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="68e0c-321">Горизонтальное поле представления фрустум в радианах (меньше PI).</span><span class="sxs-lookup"><span data-stu-id="68e0c-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="68e0c-322">**Microsoft. Перцептионсимулатион. Фрустум. Аспектратио**</span><span class="sxs-lookup"><span data-stu-id="68e0c-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="68e0c-323">Отношение горизонтального поля представления к вертикальному полю представления.</span><span class="sxs-lookup"><span data-stu-id="68e0c-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="68e0c-324">Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="68e0c-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="68e0c-325">Корень для создания пакетов, используемых для управления устройством.</span><span class="sxs-lookup"><span data-stu-id="68e0c-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="68e0c-326">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. Device**</span><span class="sxs-lookup"><span data-stu-id="68e0c-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="68e0c-327">Извлеките объект имитации устройства, который интерпретирует имитацию человека и имитации мира.</span><span class="sxs-lookup"><span data-stu-id="68e0c-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="68e0c-328">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. человеческий**</span><span class="sxs-lookup"><span data-stu-id="68e0c-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="68e0c-329">Извлеките объект, управляющий имитацией человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="68e0c-330">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. Reset**</span><span class="sxs-lookup"><span data-stu-id="68e0c-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="68e0c-331">Сбрасывает состояние имитации до состояния по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="68e0c-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="68e0c-332">Microsoft. Перцептионсимулатион. Исимулатеддевице</span><span class="sxs-lookup"><span data-stu-id="68e0c-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="68e0c-333">Интерфейс, описывающий устройство, которое интерпретирует имитацию мира и имитацию человека</span><span class="sxs-lookup"><span data-stu-id="68e0c-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="68e0c-334">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Хеадтраккер**</span><span class="sxs-lookup"><span data-stu-id="68e0c-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="68e0c-335">Извлеките головной датчик из имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="68e0c-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="68e0c-336">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Хандтраккер**</span><span class="sxs-lookup"><span data-stu-id="68e0c-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="68e0c-337">Получите датчик руки от имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="68e0c-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="68e0c-338">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Сетсимулатеддевицетипе (Microsoft. Перцептионсимулатион. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="68e0c-339">Задайте свойства виртуального устройства в соответствии с указанным типом устройства.</span><span class="sxs-lookup"><span data-stu-id="68e0c-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="68e0c-340">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-340">Parameters</span></span>
* <span data-ttu-id="68e0c-341">тип — новый тип имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="68e0c-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="68e0c-342">Microsoft. Перцептионсимулатион. Исимулатедхеадтраккер</span><span class="sxs-lookup"><span data-stu-id="68e0c-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="68e0c-343">Интерфейс, описывающий часть имитации устройства, которая отслеживает заголовку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="68e0c-344">**Microsoft. Перцептионсимулатион. Исимулатедхеадтраккер. Хеадтраккермоде**</span><span class="sxs-lookup"><span data-stu-id="68e0c-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="68e0c-345">Извлекает и устанавливает текущий режим трассировки головного подразделения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="68e0c-346">Microsoft. Перцептионсимулатион. Исимулатедхандтраккер</span><span class="sxs-lookup"><span data-stu-id="68e0c-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="68e0c-347">Интерфейс, описывающий часть имитации устройства, которая отслеживает руки имитации человека</span><span class="sxs-lookup"><span data-stu-id="68e0c-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="68e0c-348">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="68e0c-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="68e0c-349">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="68e0c-350">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. положением**</span><span class="sxs-lookup"><span data-stu-id="68e0c-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="68e0c-351">Извлечение и задание положения объекта Tracker для имитации относительно центра головки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="68e0c-352">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. шаг**</span><span class="sxs-lookup"><span data-stu-id="68e0c-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="68e0c-353">Извлеките и задайте шаг вниз для смоделированного средства записи.</span><span class="sxs-lookup"><span data-stu-id="68e0c-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="68e0c-354">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Фрустумигноред**</span><span class="sxs-lookup"><span data-stu-id="68e0c-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="68e0c-355">Получите и задайте значение, определяющее, пропускается ли фрустум транспортера для имитации.</span><span class="sxs-lookup"><span data-stu-id="68e0c-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="68e0c-356">Если игнорируется, обе руки всегда видимы.</span><span class="sxs-lookup"><span data-stu-id="68e0c-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="68e0c-357">Если параметр не пропускается (по умолчанию), руки отображаются только в том случае, если они находятся в фрустуме средства записи.</span><span class="sxs-lookup"><span data-stu-id="68e0c-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="68e0c-358">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Фрустум**</span><span class="sxs-lookup"><span data-stu-id="68e0c-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="68e0c-359">Получите и задайте свойства фрустум, используемые для определения, видны ли руки для имитации средства записи.</span><span class="sxs-lookup"><span data-stu-id="68e0c-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="68e0c-360">Microsoft. Перцептионсимулатион. Исимулатедхуман</span><span class="sxs-lookup"><span data-stu-id="68e0c-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="68e0c-361">Интерфейс верхнего уровня для управления имитируемым человеком.</span><span class="sxs-lookup"><span data-stu-id="68e0c-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="68e0c-362">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="68e0c-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="68e0c-363">Извлечение и Установка расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="68e0c-364">Это расположение соответствует точке в центре метров человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="68e0c-365">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Direction**</span><span class="sxs-lookup"><span data-stu-id="68e0c-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="68e0c-366">Извлеките и задайте направление имитации человеческих лиц в мире.</span><span class="sxs-lookup"><span data-stu-id="68e0c-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="68e0c-367">0 радианы отменяют отрицательную ось Z.</span><span class="sxs-lookup"><span data-stu-id="68e0c-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="68e0c-368">Положительные радианы поворачиваются по часовой стрелке относительно оси Y.</span><span class="sxs-lookup"><span data-stu-id="68e0c-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="68e0c-369">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Height**</span><span class="sxs-lookup"><span data-stu-id="68e0c-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="68e0c-370">Получение и задание высоты имитации человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="68e0c-371">**Microsoft. Перцептионсимулатион. Исимулатедхуман. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="68e0c-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="68e0c-372">Получите левую руку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="68e0c-373">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Ригхсанд**</span><span class="sxs-lookup"><span data-stu-id="68e0c-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="68e0c-374">Получите правую руку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="68e0c-375">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Head**</span><span class="sxs-lookup"><span data-stu-id="68e0c-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="68e0c-376">Получите заголовок имитации человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="68e0c-377">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="68e0c-378">Перемещение имитации человека относительно его текущего положения в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="68e0c-379">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-379">Parameters</span></span>
* <span data-ttu-id="68e0c-380">перевод — перевод, который необходимо переместить, относительно текущего положения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="68e0c-381">**Microsoft. Перцептионсимулатион. Исимулатедхуман. вращение (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="68e0c-382">Поворот имитации человека относительно текущего направления по часовой стрелке по оси Y</span><span class="sxs-lookup"><span data-stu-id="68e0c-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="68e0c-383">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-383">Parameters</span></span>
* <span data-ttu-id="68e0c-384">радианы — величина поворота вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="68e0c-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="68e0c-385">Microsoft. Перцептионсимулатион. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="68e0c-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="68e0c-386">Дополнительные свойства доступны путем приведения Исимулатедхуман к ISimulatedHuman2.</span><span class="sxs-lookup"><span data-stu-id="68e0c-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="68e0c-387">**Microsoft. Перцептионсимулатион. ISimulatedHuman2. Лефтконтроллер**</span><span class="sxs-lookup"><span data-stu-id="68e0c-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="68e0c-388">Получите левый 6-ДОФ контроллер.</span><span class="sxs-lookup"><span data-stu-id="68e0c-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="68e0c-389">**Microsoft. Перцептионсимулатион. ISimulatedHuman2. Ригхтконтроллер**</span><span class="sxs-lookup"><span data-stu-id="68e0c-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="68e0c-390">Получите подходящий 6-ДОФ контроллер.</span><span class="sxs-lookup"><span data-stu-id="68e0c-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="68e0c-391">Microsoft. Перцептионсимулатион. Исимулатедханд</span><span class="sxs-lookup"><span data-stu-id="68e0c-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="68e0c-392">Интерфейс, описывающий руки имитации человека</span><span class="sxs-lookup"><span data-stu-id="68e0c-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="68e0c-393">**Microsoft. Перцептионсимулатион. Исимулатедханд. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="68e0c-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="68e0c-394">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="68e0c-395">**Microsoft. Перцептионсимулатион. Исимулатедханд. положением**</span><span class="sxs-lookup"><span data-stu-id="68e0c-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="68e0c-396">Получение и установка положения смоделированной руки относительно человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="68e0c-397">**Microsoft. Перцептионсимулатион. Исимулатедханд. Activated**</span><span class="sxs-lookup"><span data-stu-id="68e0c-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="68e0c-398">Извлечение и задание того, активирована ли рука в настоящий момент.</span><span class="sxs-lookup"><span data-stu-id="68e0c-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="68e0c-399">**Microsoft. Перцептионсимулатион. Исимулатедханд. Visible**</span><span class="sxs-lookup"><span data-stu-id="68e0c-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="68e0c-400">Извлеките, является ли рука в настоящий момент видимой для SimulatedDevice (IE, находится ли она в положении, которое должно быть обнаружено Хандтраккер).</span><span class="sxs-lookup"><span data-stu-id="68e0c-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="68e0c-401">**Microsoft. Перцептионсимулатион. Исимулатедханд. Енсуревисибле**</span><span class="sxs-lookup"><span data-stu-id="68e0c-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="68e0c-402">Переместите руку так, чтобы она была видна SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="68e0c-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="68e0c-403">**Microsoft. Перцептионсимулатион. Исимулатедханд. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="68e0c-404">Переместить положение моделируемой руки относительно ее текущей должности в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="68e0c-405">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-405">Parameters</span></span>
* <span data-ttu-id="68e0c-406">перевод — величина, на которую переводятся смоделированные руки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="68e0c-407">**Microsoft. Перцептионсимулатион. Исимулатедханд. Перформжестуре (Microsoft. Перцептионсимулатион. Симулатеджестуре)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="68e0c-408">Выполните жест, используя имитацию руки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="68e0c-409">Она будет обнаружена системой только в том случае, если она включена.</span><span class="sxs-lookup"><span data-stu-id="68e0c-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="68e0c-410">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-410">Parameters</span></span>
* <span data-ttu-id="68e0c-411">жест — жест, который необходимо выполнить.</span><span class="sxs-lookup"><span data-stu-id="68e0c-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="68e0c-412">Microsoft. Перцептионсимулатион. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="68e0c-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="68e0c-413">Дополнительные свойства доступны путем приведения Исимулатедханд к ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="68e0c-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="68e0c-414">**Microsoft. Перцептионсимулатион. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="68e0c-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="68e0c-415">Возвращает или задает поворот моделируемой руки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="68e0c-416">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="68e0c-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="68e0c-417">Microsoft. Перцептионсимулатион. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="68e0c-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="68e0c-418">Дополнительные свойства доступны путем приведения Исимулатедханд к ISimulatedHand3.</span><span class="sxs-lookup"><span data-stu-id="68e0c-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="68e0c-419">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Жетжоинтконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="68e0c-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="68e0c-420">Получение конфигурации соединения для указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="68e0c-421">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Сетжоинтконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="68e0c-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="68e0c-422">Задает конфигурацию соединения для указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="68e0c-423">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Сесандпосе**</span><span class="sxs-lookup"><span data-stu-id="68e0c-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="68e0c-424">Задайте для параметра "рука" известное значение с необязательным флагом для анимации.</span><span class="sxs-lookup"><span data-stu-id="68e0c-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="68e0c-425">Примечание. анимация не приведет к тому, что присоединения будут немедленно отражены в своих окончательно Объединенных конфигурациях.</span><span class="sxs-lookup"><span data-stu-id="68e0c-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="68e0c-426">Microsoft. Перцептионсимулатион. Исимулатедхеад</span><span class="sxs-lookup"><span data-stu-id="68e0c-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="68e0c-427">Интерфейс, описывающий заголовок имитации человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="68e0c-428">**Microsoft. Перцептионсимулатион. Исимулатедхеад. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="68e0c-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="68e0c-429">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="68e0c-430">**Microsoft. Перцептионсимулатион. Исимулатедхеад. вращение**</span><span class="sxs-lookup"><span data-stu-id="68e0c-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="68e0c-431">Извлеките поворот моделируемой головки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="68e0c-432">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="68e0c-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="68e0c-433">**Microsoft. Перцептионсимулатион. Исимулатедхеад. диаметр**</span><span class="sxs-lookup"><span data-stu-id="68e0c-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="68e0c-434">Получение диаметра смоделированного головного элемента.</span><span class="sxs-lookup"><span data-stu-id="68e0c-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="68e0c-435">Это значение используется для определения центра заголовка (точки вращения).</span><span class="sxs-lookup"><span data-stu-id="68e0c-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="68e0c-436">**Microsoft. Перцептионсимулатион. Исимулатедхеад. вращение (Microsoft. Перцептионсимулатион. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="68e0c-437">Поворот смоделированной головки относительно текущего поворота.</span><span class="sxs-lookup"><span data-stu-id="68e0c-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="68e0c-438">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="68e0c-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="68e0c-439">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-439">Parameters</span></span>
* <span data-ttu-id="68e0c-440">вращение — величина поворота.</span><span class="sxs-lookup"><span data-stu-id="68e0c-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="68e0c-441">Microsoft. Перцептионсимулатион. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="68e0c-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="68e0c-442">Дополнительные свойства доступны путем приведения Исимулатедхеад к ISimulatedHead2.</span><span class="sxs-lookup"><span data-stu-id="68e0c-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="68e0c-443">**Microsoft. Перцептионсимулатион. ISimulatedHead2. глаза**</span><span class="sxs-lookup"><span data-stu-id="68e0c-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="68e0c-444">Извлеките глаза имитации человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="68e0c-445">Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер</span><span class="sxs-lookup"><span data-stu-id="68e0c-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="68e0c-446">Интерфейс, описывающий ДОФ контроллер, связанный с имитируемым человеком.</span><span class="sxs-lookup"><span data-stu-id="68e0c-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="68e0c-447">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="68e0c-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="68e0c-448">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="68e0c-449">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. status**</span><span class="sxs-lookup"><span data-stu-id="68e0c-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="68e0c-450">Возвращает или задает текущее состояние контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="68e0c-451">Для состояния контроллера должно быть задано значение, отличное от OFF, прежде чем все вызовы для перемещения, вращения или нажатия кнопки будут выполнены.</span><span class="sxs-lookup"><span data-stu-id="68e0c-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="68e0c-452">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. положением**</span><span class="sxs-lookup"><span data-stu-id="68e0c-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="68e0c-453">Получение или установка положения имитации контроллера относительно человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="68e0c-454">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Orientation**</span><span class="sxs-lookup"><span data-stu-id="68e0c-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="68e0c-455">Получение или установка ориентации имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="68e0c-456">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="68e0c-457">Переместить положение имитации контроллера относительно его текущего положения в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="68e0c-458">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-458">Parameters</span></span>
* <span data-ttu-id="68e0c-459">перевод — это величина, на которую нужно перевести имитируемый контроллер.</span><span class="sxs-lookup"><span data-stu-id="68e0c-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="68e0c-460">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Прессбуттон (Симулатедсиксдофконтроллербуттон)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="68e0c-461">Нажмите кнопку на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="68e0c-462">Она будет обнаружена системой только в том случае, если контроллер включен.</span><span class="sxs-lookup"><span data-stu-id="68e0c-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="68e0c-463">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-463">Parameters</span></span>
* <span data-ttu-id="68e0c-464">Кнопка для нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-464">button - The button to press.</span></span>

<span data-ttu-id="68e0c-465">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Релеасебуттон (Симулатедсиксдофконтроллербуттон)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="68e0c-466">Выпустите кнопку на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="68e0c-467">Она будет обнаружена системой только в том случае, если контроллер включен.</span><span class="sxs-lookup"><span data-stu-id="68e0c-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="68e0c-468">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-468">Parameters</span></span>
* <span data-ttu-id="68e0c-469">Кнопка для выпуска.</span><span class="sxs-lookup"><span data-stu-id="68e0c-469">button - The button to release.</span></span>

<span data-ttu-id="68e0c-470">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Жеттаучпадпоситион (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="68e0c-471">Получить расположение имитации пальца на сенсорной панели имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="68e0c-472">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-472">Parameters</span></span>
* <span data-ttu-id="68e0c-473">x — горизонтальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="68e0c-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="68e0c-474">y — вертикальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="68e0c-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="68e0c-475">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Сеттаучпадпоситион (float, float)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="68e0c-476">Установите расположение имитации пальца на сенсорной панели имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="68e0c-477">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-477">Parameters</span></span>
* <span data-ttu-id="68e0c-478">x — горизонтальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="68e0c-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="68e0c-479">y — вертикальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="68e0c-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="68e0c-480">Microsoft. Перцептионсимулатион. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="68e0c-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="68e0c-481">Дополнительные свойства и методы доступны путем приведения Исимулатедсиксдофконтроллер к ISimulatedSixDofController2.</span><span class="sxs-lookup"><span data-stu-id="68e0c-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="68e0c-482">**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Жетсумбстиккпоситион (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="68e0c-483">Получение расположения имитации аналогового стика на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="68e0c-484">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-484">Parameters</span></span>
* <span data-ttu-id="68e0c-485">x — горизонтальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="68e0c-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="68e0c-486">y — вертикальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="68e0c-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="68e0c-487">**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Сетсумбстиккпоситион (float, float)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="68e0c-488">Задайте расположение имитации аналогового стика на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="68e0c-489">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-489">Parameters</span></span>
* <span data-ttu-id="68e0c-490">x — горизонтальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="68e0c-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="68e0c-491">y — вертикальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="68e0c-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="68e0c-492">**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Баттерилевел**</span><span class="sxs-lookup"><span data-stu-id="68e0c-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="68e0c-493">Получение или установка уровня заряда батареи для имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="68e0c-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="68e0c-494">Значение должно быть больше 0,0 и меньше или равно 100,0.</span><span class="sxs-lookup"><span data-stu-id="68e0c-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="68e0c-495">Microsoft. Перцептионсимулатион. Исимулатедэйес</span><span class="sxs-lookup"><span data-stu-id="68e0c-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="68e0c-496">Интерфейс, описывающий глаза имитации человека.</span><span class="sxs-lookup"><span data-stu-id="68e0c-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="68e0c-497">**Microsoft. Перцептионсимулатион. Исимулатедэйес. вращение**</span><span class="sxs-lookup"><span data-stu-id="68e0c-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="68e0c-498">Извлеките поворот имитации глаз.</span><span class="sxs-lookup"><span data-stu-id="68e0c-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="68e0c-499">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="68e0c-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="68e0c-500">**Microsoft. Перцептионсимулатион. Исимулатедэйес. вращение (Microsoft. Перцептионсимулатион. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="68e0c-501">Поворот имитации глаз относительно текущего вращения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="68e0c-502">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="68e0c-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="68e0c-503">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-503">Parameters</span></span>
* <span data-ttu-id="68e0c-504">вращение — величина поворота.</span><span class="sxs-lookup"><span data-stu-id="68e0c-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="68e0c-505">**Microsoft. Перцептионсимулатион. Исимулатедэйес. Калибратионстате**</span><span class="sxs-lookup"><span data-stu-id="68e0c-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="68e0c-506">Возвращает или задает состояние калибровки для имитации глаз.</span><span class="sxs-lookup"><span data-stu-id="68e0c-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="68e0c-507">**Microsoft. Перцептионсимулатион. Исимулатедэйес. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="68e0c-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="68e0c-508">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="68e0c-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="68e0c-509">Microsoft. Перцептионсимулатион. Исимулатионрекординг</span><span class="sxs-lookup"><span data-stu-id="68e0c-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="68e0c-510">Интерфейс для взаимодействия с одной записью, загруженной для воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="68e0c-511">**Типы Microsoft. Перцептионсимулатион. Исимулатионрекординг.**</span><span class="sxs-lookup"><span data-stu-id="68e0c-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="68e0c-512">Возвращает список типов данных в записи.</span><span class="sxs-lookup"><span data-stu-id="68e0c-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="68e0c-513">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. State**</span><span class="sxs-lookup"><span data-stu-id="68e0c-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="68e0c-514">Извлекает текущее состояние записи.</span><span class="sxs-lookup"><span data-stu-id="68e0c-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="68e0c-515">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Play**</span><span class="sxs-lookup"><span data-stu-id="68e0c-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="68e0c-516">Запустите воспроизведение.</span><span class="sxs-lookup"><span data-stu-id="68e0c-516">Start the playback.</span></span> <span data-ttu-id="68e0c-517">Если запись приостановлена, воспроизведение будет возобновлено из приостановленного расположения. При остановке воспроизведение начнется с самого начала.</span><span class="sxs-lookup"><span data-stu-id="68e0c-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="68e0c-518">Если воспроизведение уже проигрывается, этот вызов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="68e0c-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="68e0c-519">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Pause**</span><span class="sxs-lookup"><span data-stu-id="68e0c-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="68e0c-520">Приостанавливает воспроизведение в текущем расположении.</span><span class="sxs-lookup"><span data-stu-id="68e0c-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="68e0c-521">Если запись остановлена, вызов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="68e0c-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="68e0c-522">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="68e0c-523">Ищет запись в указанное время (в 100 наносекундах с начала) и останавливается в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="68e0c-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="68e0c-524">Если время превышает окончание записи, оно приостанавливается на последнем кадре.</span><span class="sxs-lookup"><span data-stu-id="68e0c-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="68e0c-525">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-525">Parameters</span></span>
* <span data-ttu-id="68e0c-526">такты — время поиска.</span><span class="sxs-lookup"><span data-stu-id="68e0c-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="68e0c-527">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. останавливаться**</span><span class="sxs-lookup"><span data-stu-id="68e0c-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="68e0c-528">Останавливает воспроизведение и сбрасывает текущую точку в начало.</span><span class="sxs-lookup"><span data-stu-id="68e0c-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="68e0c-529">Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк</span><span class="sxs-lookup"><span data-stu-id="68e0c-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="68e0c-530">Интерфейс для получения изменений состояния во время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="68e0c-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="68e0c-531">**Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк. Плайбаккстатечанжед (Microsoft. Перцептионсимулатион. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="68e0c-532">Вызывается при изменении состояния воспроизведения Исимулатионрекординг.</span><span class="sxs-lookup"><span data-stu-id="68e0c-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="68e0c-533">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-533">Parameters</span></span>
* <span data-ttu-id="68e0c-534">newState — новое состояние записи.</span><span class="sxs-lookup"><span data-stu-id="68e0c-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="68e0c-535">Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="68e0c-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="68e0c-536">Корневой объект для создания объектов имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="68e0c-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="68e0c-537">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Креатеперцептионсимулатионманажер (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="68e0c-538">Создать на объекте для создания смоделированных пакетов и доставки их в предоставленный приемник.</span><span class="sxs-lookup"><span data-stu-id="68e0c-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="68e0c-539">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-539">Parameters</span></span>
* <span data-ttu-id="68e0c-540">приемник — приемник, который будет принимать все созданные пакеты.</span><span class="sxs-lookup"><span data-stu-id="68e0c-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="68e0c-541">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="68e0c-541">Return value</span></span>

<span data-ttu-id="68e0c-542">Созданный диспетчер.</span><span class="sxs-lookup"><span data-stu-id="68e0c-542">The created Manager.</span></span>

<span data-ttu-id="68e0c-543">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Креатеперцептионсимулатионрекординг (System. String)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="68e0c-544">Создание приемника, в котором хранятся все полученные пакеты в файле по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="68e0c-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="68e0c-545">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-545">Parameters</span></span>
* <span data-ttu-id="68e0c-546">путь — путь к создаваемому файлу.</span><span class="sxs-lookup"><span data-stu-id="68e0c-546">path - The path of the file to create.</span></span>

<span data-ttu-id="68e0c-547">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="68e0c-547">Return value</span></span>

<span data-ttu-id="68e0c-548">Созданный приемник.</span><span class="sxs-lookup"><span data-stu-id="68e0c-548">The created sink.</span></span>

<span data-ttu-id="68e0c-549">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Лоадперцептионсимулатионрекординг (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="68e0c-550">Загрузка записи из указанного файла.</span><span class="sxs-lookup"><span data-stu-id="68e0c-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="68e0c-551">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-551">Parameters</span></span>
* <span data-ttu-id="68e0c-552">путь — путь к загружаемому файлу.</span><span class="sxs-lookup"><span data-stu-id="68e0c-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="68e0c-553">Factory — фабрика, используемая записью для создания Исимулатионстреамсинк при необходимости.</span><span class="sxs-lookup"><span data-stu-id="68e0c-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="68e0c-554">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="68e0c-554">Return value</span></span>

<span data-ttu-id="68e0c-555">Загруженная запись.</span><span class="sxs-lookup"><span data-stu-id="68e0c-555">The loaded recording.</span></span>

<span data-ttu-id="68e0c-556">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Лоадперцептионсимулатионрекординг (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="68e0c-557">Загрузка записи из указанного файла.</span><span class="sxs-lookup"><span data-stu-id="68e0c-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="68e0c-558">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-558">Parameters</span></span>
* <span data-ttu-id="68e0c-559">путь — путь к загружаемому файлу.</span><span class="sxs-lookup"><span data-stu-id="68e0c-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="68e0c-560">Factory — фабрика, используемая записью для создания Исимулатионстреамсинк при необходимости.</span><span class="sxs-lookup"><span data-stu-id="68e0c-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="68e0c-561">Callback — обратный вызов, который получает обновления с пределом состояния записи.</span><span class="sxs-lookup"><span data-stu-id="68e0c-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="68e0c-562">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="68e0c-562">Return value</span></span>

<span data-ttu-id="68e0c-563">Загруженная запись.</span><span class="sxs-lookup"><span data-stu-id="68e0c-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="68e0c-564">Microsoft. Перцептионсимулатион. Стреамдататипес</span><span class="sxs-lookup"><span data-stu-id="68e0c-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="68e0c-565">Описывает различные типы потоковых данных.</span><span class="sxs-lookup"><span data-stu-id="68e0c-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="68e0c-566">**Microsoft. Перцептионсимулатион. Стреамдататипес. None**</span><span class="sxs-lookup"><span data-stu-id="68e0c-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="68e0c-567">Значение Sentinel, используемое для обозначения отсутствия типов данных потока.</span><span class="sxs-lookup"><span data-stu-id="68e0c-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="68e0c-568">**Microsoft. Перцептионсимулатион. Стреамдататипес. Head**</span><span class="sxs-lookup"><span data-stu-id="68e0c-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="68e0c-569">Поток данных, относящийся к положению и ориентации головного элемента.</span><span class="sxs-lookup"><span data-stu-id="68e0c-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="68e0c-570">**Microsoft. Перцептионсимулатион. Стреамдататипес. руки**</span><span class="sxs-lookup"><span data-stu-id="68e0c-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="68e0c-571">Поток данных о положении и жестах руки.</span><span class="sxs-lookup"><span data-stu-id="68e0c-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="68e0c-572">**Microsoft. Перцептионсимулатион. Стреамдататипес. Спатиалмаппинг**</span><span class="sxs-lookup"><span data-stu-id="68e0c-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="68e0c-573">Поток данных о пространственном сопоставлении среды.</span><span class="sxs-lookup"><span data-stu-id="68e0c-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="68e0c-574">**Microsoft. Перцептионсимулатион. Стреамдататипес. Калибровка**</span><span class="sxs-lookup"><span data-stu-id="68e0c-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="68e0c-575">Поток данных, касающихся калибровки устройства.</span><span class="sxs-lookup"><span data-stu-id="68e0c-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="68e0c-576">Пакеты калибровки принимаются только системой в удаленном режиме.</span><span class="sxs-lookup"><span data-stu-id="68e0c-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="68e0c-577">**Microsoft. Перцептионсимулатион. Стреамдататипес. Environment**</span><span class="sxs-lookup"><span data-stu-id="68e0c-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="68e0c-578">Поток данных о среде устройства.</span><span class="sxs-lookup"><span data-stu-id="68e0c-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="68e0c-579">**Microsoft. Перцептионсимулатион. Стреамдататипес. ALL**</span><span class="sxs-lookup"><span data-stu-id="68e0c-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="68e0c-580">Значение Sentinel, используемое для указания всех записанных типов данных.</span><span class="sxs-lookup"><span data-stu-id="68e0c-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="68e0c-581">Microsoft. Перцептионсимулатион. Исимулатионстреамсинк</span><span class="sxs-lookup"><span data-stu-id="68e0c-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="68e0c-582">Объект, получающий пакеты данных из потока имитации.</span><span class="sxs-lookup"><span data-stu-id="68e0c-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="68e0c-583">**Microsoft. Перцептионсимулатион. Исимулатионстреамсинк. Онпаккетрецеивед (длина uint, Byte [], пакет)**</span><span class="sxs-lookup"><span data-stu-id="68e0c-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="68e0c-584">Получает один пакет, который внутренне типизирован и имеет версию.</span><span class="sxs-lookup"><span data-stu-id="68e0c-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="68e0c-585">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e0c-585">Parameters</span></span>
* <span data-ttu-id="68e0c-586">Длина — Длина пакета.</span><span class="sxs-lookup"><span data-stu-id="68e0c-586">length - The length of the packet.</span></span>
* <span data-ttu-id="68e0c-587">пакет — данные пакета.</span><span class="sxs-lookup"><span data-stu-id="68e0c-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="68e0c-588">Microsoft. Перцептионсимулатион. Исимулатионстреамсинкфактори</span><span class="sxs-lookup"><span data-stu-id="68e0c-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="68e0c-589">Объект, создающий Исимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="68e0c-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="68e0c-590">**Microsoft. Перцептионсимулатион. Исимулатионстреамсинкфактори. Креатесимулатионстреамсинк ()**</span><span class="sxs-lookup"><span data-stu-id="68e0c-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="68e0c-591">Создает единственный экземпляр Исимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="68e0c-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="68e0c-592">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="68e0c-592">Return value</span></span>

<span data-ttu-id="68e0c-593">Созданный приемник.</span><span class="sxs-lookup"><span data-stu-id="68e0c-593">The created sink.</span></span>
