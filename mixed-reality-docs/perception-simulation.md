---
title: Моделирование восприятия
description: Рекомендации по использованию библиотеки моделирования восприятия для автоматизации имитации входных данных для впечатляющих приложений
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, моделирование, тестирование
ms.openlocfilehash: 701fd39490d87b70df9bd68cc99da6482d41b676
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228029"
---
# <a name="perception-simulation"></a><span data-ttu-id="30c60-104">Моделирование восприятия</span><span class="sxs-lookup"><span data-stu-id="30c60-104">Perception simulation</span></span>

<span data-ttu-id="30c60-105">Вы хотите создать автоматический тест для приложения?</span><span class="sxs-lookup"><span data-stu-id="30c60-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="30c60-106">Вы хотите, чтобы тесты переходили за пределы модульного тестирования на уровне компонентов и действительно протестировали свое приложение как можно более полное?</span><span class="sxs-lookup"><span data-stu-id="30c60-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="30c60-107">Имитация восприятия — это то, что вы ищете.</span><span class="sxs-lookup"><span data-stu-id="30c60-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="30c60-108">Библиотека моделирования восприятия отправляет в приложение пользовательские и мировые входные данные, что позволяет автоматизировать тесты.</span><span class="sxs-lookup"><span data-stu-id="30c60-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="30c60-109">Например, можно имитировать входные данные человека, который смотрит в конкретную повторяемую единицу, а затем выполнить жест или использовать контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="30c60-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="30c60-110">Имитация восприятия может отправить смоделированные входные данные на физический HoloLens, эмулятор HoloLens (1 общий), эмулятор HoloLens 2 или компьютер с установленным порталом смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="30c60-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="30c60-111">Имитация восприятия обходит активные датчики на устройстве смешанной реальности и отправляет смоделированные входные данные приложениям, работающим на устройстве.</span><span class="sxs-lookup"><span data-stu-id="30c60-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="30c60-112">Приложения получают эти события ввода через те же API-интерфейсы, которые они всегда используют, и не могут сообщать о различиях между выполнением с реальными датчиками и с имитацией восприятия.</span><span class="sxs-lookup"><span data-stu-id="30c60-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="30c60-113">Имитация восприятия — это та же технология, которая используется эмуляторами HoloLens для отправки смоделированных входных данных на виртуальную машину HoloLens.</span><span class="sxs-lookup"><span data-stu-id="30c60-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="30c60-114">Чтобы приступить к использованию моделирования в коде, начните с создания объекта Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="30c60-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="30c60-115">Из этого объекта можно выдавать команды для управления свойствами имитации «человека», включая позиционирование головной стороны, расположение руки и жесты, а также включать и управлять контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="30c60-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="30c60-116">Настройка проекта Visual Studio для имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="30c60-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="30c60-117">[Установите эмулятор HoloLens](install-the-tools.md) на компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="30c60-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="30c60-118">Эмулятор включает библиотеки, которые будут использоваться для имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="30c60-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="30c60-119">Создайте проект Visual Studio C# для настольных систем (проект консоли прекрасно работает, чтобы начать работу).</span><span class="sxs-lookup"><span data-stu-id="30c60-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="30c60-120">Добавьте в проект следующие двоичные файлы в виде ссылок (проект->добавить >ссылку...). Их можно найти в% ProgramFiles (x86)% \ Microsoft XDE \\ (версия), например **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** для эмулятора HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="30c60-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="30c60-121">(Примечание. Хотя двоичные файлы являются частью эмулятора HoloLens 2, они также работают для Windows Mixed Reality на настольном компьютере.) конкретного.</span><span class="sxs-lookup"><span data-stu-id="30c60-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="30c60-122">Перцептионсимулатионманажер. Interop. dll — управляемая оболочка C# для имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="30c60-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="30c60-123">b.</span><span class="sxs-lookup"><span data-stu-id="30c60-123">b.</span></span> <span data-ttu-id="30c60-124">Перцептионсимулатионрест. DLL — библиотека для настройки канала связи через веб-сокет с HoloLens или Emulator.</span><span class="sxs-lookup"><span data-stu-id="30c60-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="30c60-125">c.</span><span class="sxs-lookup"><span data-stu-id="30c60-125">c.</span></span> <span data-ttu-id="30c60-126">Симулатионстреам. Interop. dll — общие типы для моделирования.</span><span class="sxs-lookup"><span data-stu-id="30c60-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="30c60-127">Добавьте в проект a двоичный файл Перцептионсимулатионманажер. dll реализации.</span><span class="sxs-lookup"><span data-stu-id="30c60-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="30c60-128">Сначала добавьте его в качестве двоичного файла в проект (проект->добавить->существующий элемент...). Сохраните его как ссылку, чтобы он не скопировал его в исходную папку проекта.</span><span class="sxs-lookup"><span data-stu-id="30c60-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="30c60-129">![Добавьте Перцептионсимулатионманажер. dll в проект как ссылку ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="30c60-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="30c60-130">Затем убедитесь, что он скопирован в выходную папку при сборке.</span><span class="sxs-lookup"><span data-stu-id="30c60-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="30c60-131">Он находится на странице свойств двоичного файла.</span><span class="sxs-lookup"><span data-stu-id="30c60-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="30c60-132">![Пометьте Перцептионсимулатионманажер. dll для копирования в выходной каталог](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="30c60-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="30c60-133">Задайте для активной платформы решения x64.</span><span class="sxs-lookup"><span data-stu-id="30c60-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="30c60-134">(Используйте Configuration Manager, чтобы создать запись платформы для x64, если она еще не существует.)</span><span class="sxs-lookup"><span data-stu-id="30c60-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="30c60-135">Создание объекта Иперцептионсимулатион Manager</span><span class="sxs-lookup"><span data-stu-id="30c60-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="30c60-136">Для управления имитацией вы получаете обновления объектов, полученных из объекта Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="30c60-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="30c60-137">Первым шагом является получение этого объекта и его подключение к целевому устройству или эмулятору.</span><span class="sxs-lookup"><span data-stu-id="30c60-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="30c60-138">Вы можете получить IP-адрес эмулятора, нажав кнопку на портале устройства на [панели инструментов](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="30c60-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="30c60-139">![Значок "открыть портал устройств" ](images/emulator-deviceportal.png) **откройте портал**устройств. Откройте портал устройств Windows для ОС HoloLens в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="30c60-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="30c60-140">Для Windows Mixed Reality это можно получить в приложении "Параметры" в разделе "обновление & безопасность", а затем "для разработчиков" в разделе "подключение с помощью:" раздела "Включение портала устройств".</span><span class="sxs-lookup"><span data-stu-id="30c60-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="30c60-141">Обязательно запишите IP-адрес и порт.</span><span class="sxs-lookup"><span data-stu-id="30c60-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="30c60-142">Во-первых, вы вызываете Рестсимулатионстреамсинк. Create для получения объекта Рестсимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="30c60-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="30c60-143">Это целевое устройство или эмулятор, которым будет управлять HTTP-соединением.</span><span class="sxs-lookup"><span data-stu-id="30c60-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="30c60-144">Команды будут переданы и обработаны на [портале устройств Windows](using-the-windows-device-portal.md) , работающем на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="30c60-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="30c60-145">Ниже приведены четыре параметра, которые необходимо создать для объекта.</span><span class="sxs-lookup"><span data-stu-id="30c60-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="30c60-146">URI URI — IP-адрес целевого устройства (например, " https://123.123.123.123 " или " https://123.123.123.123:50080 ").</span><span class="sxs-lookup"><span data-stu-id="30c60-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="30c60-147">System .NET. NetworkCredential Credentials — имя пользователя и пароль для подключения к [порталу устройств Windows](using-the-windows-device-portal.md) на целевом устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="30c60-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="30c60-148">При подключении к эмулятору через его локальный адрес (например, 168.*.*. \*) на том же компьютере будут приниматься любые учетные данные.</span><span class="sxs-lookup"><span data-stu-id="30c60-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="30c60-149">bool обычная — true для обычного приоритета, false для низкого приоритета.</span><span class="sxs-lookup"><span data-stu-id="30c60-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="30c60-150">Обычно необходимо задать для этого параметра значение *true* для тестовых сценариев, что позволяет вашему тесту осуществлять управление.</span><span class="sxs-lookup"><span data-stu-id="30c60-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="30c60-151">Эмулятор и имитация Windows Mixed Reality используют соединения с низким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="30c60-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="30c60-152">Если в тесте также используется подключение с низким приоритетом, то последнее установленное соединение будет управляться.</span><span class="sxs-lookup"><span data-stu-id="30c60-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="30c60-153">Для отмены асинхронной операции маркера токена System. Threading. CancellationToken.</span><span class="sxs-lookup"><span data-stu-id="30c60-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="30c60-154">Во вторых, вы создадите Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="30c60-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="30c60-155">Это объект, используемый для управления имитацией.</span><span class="sxs-lookup"><span data-stu-id="30c60-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="30c60-156">Обратите внимание, что это также необходимо сделать в асинхронном методе.</span><span class="sxs-lookup"><span data-stu-id="30c60-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="30c60-157">Управление имитируемым человеком</span><span class="sxs-lookup"><span data-stu-id="30c60-157">Control the simulated Human</span></span>

<span data-ttu-id="30c60-158">Иперцептионсимулатионманажер имеет свойство человеческого, которое возвращает объект Исимулатедхуман.</span><span class="sxs-lookup"><span data-stu-id="30c60-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="30c60-159">Для управления имитируемым человеком выполните операции с этим объектом.</span><span class="sxs-lookup"><span data-stu-id="30c60-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="30c60-160">Пример:</span><span class="sxs-lookup"><span data-stu-id="30c60-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="30c60-161">Простой пример консольного приложения C#</span><span class="sxs-lookup"><span data-stu-id="30c60-161">Basic Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="30c60-162">Расширенный пример консольного приложения C#</span><span class="sxs-lookup"><span data-stu-id="30c60-162">Extended Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="30c60-163">Примечание о 6-ДОФ контроллерах</span><span class="sxs-lookup"><span data-stu-id="30c60-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="30c60-164">Перед вызовом каких-либо свойств для методов смоделированного 6-ДОФ контроллера необходимо активировать контроллер.</span><span class="sxs-lookup"><span data-stu-id="30c60-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="30c60-165">Это приведет к исключению.</span><span class="sxs-lookup"><span data-stu-id="30c60-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="30c60-166">Начиная с Windows 10 Can 2019 обновление, смоделированные 6-ДОФ контроллеры можно установить и активировать, задав для свойства Status объекта Исимулатедсиксдофконтроллер значение Симулатедсиксдофконтроллерстатус. Active.</span><span class="sxs-lookup"><span data-stu-id="30c60-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="30c60-167">В обновлении Windows 10 октября 2018 и более ранних версиях необходимо отдельно установить смоделированный 6-ДОФ контроллер, вызвав средство Перцептионсимулатиондевице, расположенное в папке \Windows\System32..</span><span class="sxs-lookup"><span data-stu-id="30c60-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="30c60-168">Использование этого средства выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="30c60-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="30c60-169">Например.</span><span class="sxs-lookup"><span data-stu-id="30c60-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="30c60-170">Поддерживаются следующие действия:</span><span class="sxs-lookup"><span data-stu-id="30c60-170">Supported actions are:</span></span>
* <span data-ttu-id="30c60-171">i = установить</span><span class="sxs-lookup"><span data-stu-id="30c60-171">i = install</span></span>
* <span data-ttu-id="30c60-172">q = запрос</span><span class="sxs-lookup"><span data-stu-id="30c60-172">q = query</span></span>
* <span data-ttu-id="30c60-173">r = удалить</span><span class="sxs-lookup"><span data-stu-id="30c60-173">r = remove</span></span>

<span data-ttu-id="30c60-174">Поддерживаются следующие экземпляры:</span><span class="sxs-lookup"><span data-stu-id="30c60-174">Supported instances are:</span></span>
* <span data-ttu-id="30c60-175">1 = левый 6-ДОФ контроллер</span><span class="sxs-lookup"><span data-stu-id="30c60-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="30c60-176">2 = правильный 6-ДОФ контроллер</span><span class="sxs-lookup"><span data-stu-id="30c60-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="30c60-177">Код выхода процесса будет указывать на успех (нулевое возвращаемое значение) или ошибку (ненулевое возвращаемое значение).</span><span class="sxs-lookup"><span data-stu-id="30c60-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="30c60-178">При использовании действия "q" для запроса того, установлен ли контроллер, возвращаемое значение будет равно нулю (0), если контроллер еще не установлен, или один (1), если контроллер установлен.</span><span class="sxs-lookup"><span data-stu-id="30c60-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="30c60-179">При удалении контроллера в Windows 10 октября с обновлением 2018 или более ранней версии установите его состояние в OFF через API, а затем вызовите средство Перцептионсимулатиондевице.</span><span class="sxs-lookup"><span data-stu-id="30c60-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="30c60-180">Обратите внимание, что это средство необходимо запускать от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="30c60-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="30c60-181">Справочник по API</span><span class="sxs-lookup"><span data-stu-id="30c60-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="30c60-182">Microsoft. Перцептионсимулатион. Симулатеддевицетипе</span><span class="sxs-lookup"><span data-stu-id="30c60-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="30c60-183">Описывает тип имитации устройства</span><span class="sxs-lookup"><span data-stu-id="30c60-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="30c60-184">**Microsoft. Перцептионсимулатион. Симулатеддевицетипе. Reference**</span><span class="sxs-lookup"><span data-stu-id="30c60-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="30c60-185">Фиктивное эталонное устройство, используемое по умолчанию для Перцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="30c60-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="30c60-186">Microsoft. Перцептионсимулатион. Хеадтраккермоде</span><span class="sxs-lookup"><span data-stu-id="30c60-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="30c60-187">Описывает режим «головной транспортер»</span><span class="sxs-lookup"><span data-stu-id="30c60-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="30c60-188">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. Default**</span><span class="sxs-lookup"><span data-stu-id="30c60-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="30c60-189">Отслеживание головок по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30c60-189">Default Head Tracking.</span></span> <span data-ttu-id="30c60-190">Это означает, что система может выбрать оптимальный режим отслеживания головной системы на основе условий среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="30c60-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="30c60-191">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. Orientation**</span><span class="sxs-lookup"><span data-stu-id="30c60-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="30c60-192">Только отслеживание головной страницы.</span><span class="sxs-lookup"><span data-stu-id="30c60-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="30c60-193">Это означает, что отслеживающее расположение может быть ненадежным, а некоторые функциональные возможности, зависящие от головного расположения, могут быть недоступны.</span><span class="sxs-lookup"><span data-stu-id="30c60-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="30c60-194">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. положением**</span><span class="sxs-lookup"><span data-stu-id="30c60-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="30c60-195">Отслеживание позиционированных головок.</span><span class="sxs-lookup"><span data-stu-id="30c60-195">Positional Head Tracking.</span></span> <span data-ttu-id="30c60-196">Это означает, что положение и ориентация отслеживающей головки надежны</span><span class="sxs-lookup"><span data-stu-id="30c60-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="30c60-197">Microsoft. Перцептионсимулатион. Симулатеджестуре</span><span class="sxs-lookup"><span data-stu-id="30c60-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="30c60-198">Описывает имитацию жеста</span><span class="sxs-lookup"><span data-stu-id="30c60-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="30c60-199">**Microsoft. Перцептионсимулатион. Симулатеджестуре. None**</span><span class="sxs-lookup"><span data-stu-id="30c60-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="30c60-200">Значение Sentinel, используемое для обозначения отсутствия жестов.</span><span class="sxs-lookup"><span data-stu-id="30c60-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="30c60-201">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Финжерпрессед**</span><span class="sxs-lookup"><span data-stu-id="30c60-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="30c60-202">Жест нажатия пальца.</span><span class="sxs-lookup"><span data-stu-id="30c60-202">A finger pressed gesture.</span></span>

<span data-ttu-id="30c60-203">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Финжеррелеасед**</span><span class="sxs-lookup"><span data-stu-id="30c60-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="30c60-204">Жест отпуска пальца.</span><span class="sxs-lookup"><span data-stu-id="30c60-204">A finger released gesture.</span></span>

<span data-ttu-id="30c60-205">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Home**</span><span class="sxs-lookup"><span data-stu-id="30c60-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="30c60-206">Жест домашнего или системного.</span><span class="sxs-lookup"><span data-stu-id="30c60-206">The home/system gesture.</span></span>

<span data-ttu-id="30c60-207">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Max**</span><span class="sxs-lookup"><span data-stu-id="30c60-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="30c60-208">Максимально допустимый жест.</span><span class="sxs-lookup"><span data-stu-id="30c60-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="30c60-209">Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус</span><span class="sxs-lookup"><span data-stu-id="30c60-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="30c60-210">Возможные состояния имитации 6-ДОФ контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="30c60-211">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Off**</span><span class="sxs-lookup"><span data-stu-id="30c60-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="30c60-212">6-ДОФ контроллер отключен.</span><span class="sxs-lookup"><span data-stu-id="30c60-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="30c60-213">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Active**</span><span class="sxs-lookup"><span data-stu-id="30c60-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="30c60-214">Контроллер ДОФ включается и отключается.</span><span class="sxs-lookup"><span data-stu-id="30c60-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="30c60-215">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Траккинглост**</span><span class="sxs-lookup"><span data-stu-id="30c60-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="30c60-216">6-ДОФ контроллер включен, но не может быть записан.</span><span class="sxs-lookup"><span data-stu-id="30c60-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="30c60-217">Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон</span><span class="sxs-lookup"><span data-stu-id="30c60-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="30c60-218">Поддерживаемые кнопки на имитации 6-ДОФ контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="30c60-219">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. None**</span><span class="sxs-lookup"><span data-stu-id="30c60-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="30c60-220">Значение Sentinel, используемое для отсутствия кнопок.</span><span class="sxs-lookup"><span data-stu-id="30c60-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="30c60-221">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Home**</span><span class="sxs-lookup"><span data-stu-id="30c60-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="30c60-222">Нажата кнопка Главная.</span><span class="sxs-lookup"><span data-stu-id="30c60-222">The Home button is pressed.</span></span>

<span data-ttu-id="30c60-223">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Menu**</span><span class="sxs-lookup"><span data-stu-id="30c60-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="30c60-224">Нажата кнопка меню.</span><span class="sxs-lookup"><span data-stu-id="30c60-224">The Menu button is pressed.</span></span>

<span data-ttu-id="30c60-225">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. захват**</span><span class="sxs-lookup"><span data-stu-id="30c60-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="30c60-226">Нажата кнопка захвата.</span><span class="sxs-lookup"><span data-stu-id="30c60-226">The Grip button is pressed.</span></span>

<span data-ttu-id="30c60-227">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Таучпадпресс**</span><span class="sxs-lookup"><span data-stu-id="30c60-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="30c60-228">Сенсорная панель нажата.</span><span class="sxs-lookup"><span data-stu-id="30c60-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="30c60-229">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Select**</span><span class="sxs-lookup"><span data-stu-id="30c60-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="30c60-230">Нажата кнопка выбрать.</span><span class="sxs-lookup"><span data-stu-id="30c60-230">The Select button is pressed.</span></span>

<span data-ttu-id="30c60-231">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Таучпадтауч**</span><span class="sxs-lookup"><span data-stu-id="30c60-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="30c60-232">Сенсорная панель затронута.</span><span class="sxs-lookup"><span data-stu-id="30c60-232">The TouchPad is touched.</span></span>

<span data-ttu-id="30c60-233">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. аналоговый стик**</span><span class="sxs-lookup"><span data-stu-id="30c60-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="30c60-234">Аналоговый стик нажат.</span><span class="sxs-lookup"><span data-stu-id="30c60-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="30c60-235">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Max**</span><span class="sxs-lookup"><span data-stu-id="30c60-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="30c60-236">Максимальная допустимая кнопка.</span><span class="sxs-lookup"><span data-stu-id="30c60-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="30c60-237">Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате</span><span class="sxs-lookup"><span data-stu-id="30c60-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="30c60-238">Состояние калибровки имитации глаз</span><span class="sxs-lookup"><span data-stu-id="30c60-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="30c60-239">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. недоступно**</span><span class="sxs-lookup"><span data-stu-id="30c60-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="30c60-240">Калибровка глаз недоступна.</span><span class="sxs-lookup"><span data-stu-id="30c60-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="30c60-241">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. ready**</span><span class="sxs-lookup"><span data-stu-id="30c60-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="30c60-242">Эти глаза были откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="30c60-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="30c60-243">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30c60-243">This is the default value.</span></span>

<span data-ttu-id="30c60-244">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. Настройка**</span><span class="sxs-lookup"><span data-stu-id="30c60-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="30c60-245">Эти глаза откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="30c60-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="30c60-246">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. Усеркалибратионнидед**</span><span class="sxs-lookup"><span data-stu-id="30c60-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="30c60-247">Необходимо откалибровать глаза.</span><span class="sxs-lookup"><span data-stu-id="30c60-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="30c60-248">Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци</span><span class="sxs-lookup"><span data-stu-id="30c60-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="30c60-249">Точность отслеживания соединения руки.</span><span class="sxs-lookup"><span data-stu-id="30c60-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="30c60-250">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. недоступно**</span><span class="sxs-lookup"><span data-stu-id="30c60-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="30c60-251">Совместное соединение не производится.</span><span class="sxs-lookup"><span data-stu-id="30c60-251">The joint is not tracked.</span></span>

<span data-ttu-id="30c60-252">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. приблизительный**</span><span class="sxs-lookup"><span data-stu-id="30c60-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="30c60-253">Совместное размещение выводится.</span><span class="sxs-lookup"><span data-stu-id="30c60-253">The joint position is inferred.</span></span>

<span data-ttu-id="30c60-254">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. Visible**</span><span class="sxs-lookup"><span data-stu-id="30c60-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="30c60-255">Совместное соединение полностью отслеживание.</span><span class="sxs-lookup"><span data-stu-id="30c60-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="30c60-256">Microsoft. Перцептионсимулатион. Симулатедхандпосе</span><span class="sxs-lookup"><span data-stu-id="30c60-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="30c60-257">Точность отслеживания соединения руки.</span><span class="sxs-lookup"><span data-stu-id="30c60-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="30c60-258">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Closed**</span><span class="sxs-lookup"><span data-stu-id="30c60-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="30c60-259">Соединения пальца руки настраиваются для отражения закрытого объекта.</span><span class="sxs-lookup"><span data-stu-id="30c60-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="30c60-260">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Open**</span><span class="sxs-lookup"><span data-stu-id="30c60-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="30c60-261">Соединения пальца руки настраиваются для отражения открытой части.</span><span class="sxs-lookup"><span data-stu-id="30c60-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="30c60-262">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Point**</span><span class="sxs-lookup"><span data-stu-id="30c60-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="30c60-263">Соединения пальца руки настраиваются в соответствии с указывающим на себя.</span><span class="sxs-lookup"><span data-stu-id="30c60-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="30c60-264">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. сжатие**</span><span class="sxs-lookup"><span data-stu-id="30c60-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="30c60-265">Соединения пальца руки настраиваются в соответствии с набором сжатия.</span><span class="sxs-lookup"><span data-stu-id="30c60-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="30c60-266">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Max**</span><span class="sxs-lookup"><span data-stu-id="30c60-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="30c60-267">Максимальное допустимое значение для Симулатедхандпосе.</span><span class="sxs-lookup"><span data-stu-id="30c60-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="30c60-268">Microsoft. Перцептионсимулатион. Плайбаккстате</span><span class="sxs-lookup"><span data-stu-id="30c60-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="30c60-269">Описывает состояние воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="30c60-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="30c60-270">**Microsoft. Перцептионсимулатион. Плайбаккстате. Stopped**</span><span class="sxs-lookup"><span data-stu-id="30c60-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="30c60-271">Запись сейчас остановлена и готова к воспроизведению.</span><span class="sxs-lookup"><span data-stu-id="30c60-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="30c60-272">**Microsoft. Перцептионсимулатион. Плайбаккстате. Play**</span><span class="sxs-lookup"><span data-stu-id="30c60-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="30c60-273">Сейчас запись воспроизводится.</span><span class="sxs-lookup"><span data-stu-id="30c60-273">The recording is currently playing.</span></span>

<span data-ttu-id="30c60-274">**Microsoft. Перцептионсимулатион. Плайбаккстате. приостановлено**</span><span class="sxs-lookup"><span data-stu-id="30c60-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="30c60-275">Запись в данный момент приостановлена.</span><span class="sxs-lookup"><span data-stu-id="30c60-275">The recording is currently paused.</span></span>

<span data-ttu-id="30c60-276">**Microsoft. Перцептионсимулатион. Плайбаккстате. end**</span><span class="sxs-lookup"><span data-stu-id="30c60-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="30c60-277">Запись достигла конца.</span><span class="sxs-lookup"><span data-stu-id="30c60-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="30c60-278">Microsoft. Перцептионсимулатион. Vector3</span><span class="sxs-lookup"><span data-stu-id="30c60-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="30c60-279">Описывает вектор 3 компонентов, который может описывать точку или вектор в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="30c60-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="30c60-280">**Microsoft. Перцептионсимулатион. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="30c60-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="30c60-281">Координата X вектора.</span><span class="sxs-lookup"><span data-stu-id="30c60-281">The X component of the vector.</span></span>

<span data-ttu-id="30c60-282">**Microsoft. Перцептионсимулатион. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="30c60-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="30c60-283">Координата Y вектора.</span><span class="sxs-lookup"><span data-stu-id="30c60-283">The Y component of the vector.</span></span>

<span data-ttu-id="30c60-284">**Microsoft. Перцептионсимулатион. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="30c60-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="30c60-285">Координата Z вектора.</span><span class="sxs-lookup"><span data-stu-id="30c60-285">The Z component of the vector.</span></span>

<span data-ttu-id="30c60-286">**Microsoft. Перцептионсимулатион. Vector3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="30c60-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="30c60-287">Создайте новый Vector3.</span><span class="sxs-lookup"><span data-stu-id="30c60-287">Construct a new Vector3.</span></span>

<span data-ttu-id="30c60-288">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-288">Parameters</span></span>
* <span data-ttu-id="30c60-289">x — компонент x вектора.</span><span class="sxs-lookup"><span data-stu-id="30c60-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="30c60-290">y — компонент y вектора.</span><span class="sxs-lookup"><span data-stu-id="30c60-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="30c60-291">z — компонент z вектора.</span><span class="sxs-lookup"><span data-stu-id="30c60-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="30c60-292">Microsoft. Перцептионсимулатион. Rotation3</span><span class="sxs-lookup"><span data-stu-id="30c60-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="30c60-293">Описывает поворот 3 компонентов.</span><span class="sxs-lookup"><span data-stu-id="30c60-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="30c60-294">**Microsoft. Перцептионсимулатион. Rotation3. шаг**</span><span class="sxs-lookup"><span data-stu-id="30c60-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="30c60-295">Компонент шаг поворота вокруг оси X.</span><span class="sxs-lookup"><span data-stu-id="30c60-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="30c60-296">**Microsoft. Перцептионсимулатион. Rotation3. значения нутации**</span><span class="sxs-lookup"><span data-stu-id="30c60-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="30c60-297">Компонент значения нутации вращения, который находится справа вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="30c60-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="30c60-298">**Microsoft. Перцептионсимулатион. Rotation3. рулон**</span><span class="sxs-lookup"><span data-stu-id="30c60-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="30c60-299">Компонент рулона поворота, который находится справа вокруг оси Z.</span><span class="sxs-lookup"><span data-stu-id="30c60-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="30c60-300">**Microsoft. Перцептионсимулатион. Rotation3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="30c60-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="30c60-301">Создайте новый Rotation3.</span><span class="sxs-lookup"><span data-stu-id="30c60-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="30c60-302">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-302">Parameters</span></span>
* <span data-ttu-id="30c60-303">шаг — компонент шага поворота.</span><span class="sxs-lookup"><span data-stu-id="30c60-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="30c60-304">значения нутации — компонент значения нутации вращения.</span><span class="sxs-lookup"><span data-stu-id="30c60-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="30c60-305">рулон — компонент рулона поворота.</span><span class="sxs-lookup"><span data-stu-id="30c60-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="30c60-306">Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион</span><span class="sxs-lookup"><span data-stu-id="30c60-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="30c60-307">Описывает конфигурацию соединения с имитацией руки.</span><span class="sxs-lookup"><span data-stu-id="30c60-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="30c60-308">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. положением**</span><span class="sxs-lookup"><span data-stu-id="30c60-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="30c60-309">Расположение соединения.</span><span class="sxs-lookup"><span data-stu-id="30c60-309">The position of the joint.</span></span>

<span data-ttu-id="30c60-310">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. вращение**</span><span class="sxs-lookup"><span data-stu-id="30c60-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="30c60-311">Поворот соединения.</span><span class="sxs-lookup"><span data-stu-id="30c60-311">The rotation of the joint.</span></span>

<span data-ttu-id="30c60-312">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. Траккингаккураци**</span><span class="sxs-lookup"><span data-stu-id="30c60-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="30c60-313">Точность отслеживания соединения.</span><span class="sxs-lookup"><span data-stu-id="30c60-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="30c60-314">Microsoft. Перцептионсимулатион. Фрустум</span><span class="sxs-lookup"><span data-stu-id="30c60-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="30c60-315">Описывает представление фрустум, как обычно используется камерой.</span><span class="sxs-lookup"><span data-stu-id="30c60-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="30c60-316">**Microsoft. Перцептионсимулатион. Фрустум. Near**</span><span class="sxs-lookup"><span data-stu-id="30c60-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="30c60-317">Минимальное расстояние, которое содержится в фрустум.</span><span class="sxs-lookup"><span data-stu-id="30c60-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="30c60-318">**Microsoft. Перцептионсимулатион. Фрустум. FAR**</span><span class="sxs-lookup"><span data-stu-id="30c60-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="30c60-319">Максимальное расстояние, которое содержится в фрустум.</span><span class="sxs-lookup"><span data-stu-id="30c60-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="30c60-320">**Microsoft. Перцептионсимулатион. Фрустум. Фиелдофвиев**</span><span class="sxs-lookup"><span data-stu-id="30c60-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="30c60-321">Горизонтальное поле представления фрустум в радианах (меньше PI).</span><span class="sxs-lookup"><span data-stu-id="30c60-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="30c60-322">**Microsoft. Перцептионсимулатион. Фрустум. Аспектратио**</span><span class="sxs-lookup"><span data-stu-id="30c60-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="30c60-323">Отношение горизонтального поля представления к вертикальному полю представления.</span><span class="sxs-lookup"><span data-stu-id="30c60-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="30c60-324">Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион</span><span class="sxs-lookup"><span data-stu-id="30c60-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="30c60-325">Описывает конфигурацию экрана имитации гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="30c60-325">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="30c60-326">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Лефтэйепоситион**</span><span class="sxs-lookup"><span data-stu-id="30c60-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="30c60-327">Преобразование из центра заголовка к левому глазу в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="30c60-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="30c60-328">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Лефтэйеротатион**</span><span class="sxs-lookup"><span data-stu-id="30c60-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="30c60-329">Поворот левого глаза в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="30c60-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="30c60-330">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Ригхтэйепоситион**</span><span class="sxs-lookup"><span data-stu-id="30c60-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="30c60-331">Преобразование из центра заголовка к нужному глазу в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="30c60-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="30c60-332">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Ригхтэйеротатион**</span><span class="sxs-lookup"><span data-stu-id="30c60-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="30c60-333">Поворот правильного глаза в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="30c60-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="30c60-334">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. IPD**</span><span class="sxs-lookup"><span data-stu-id="30c60-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="30c60-335">Значение IPD, сообщаемое системой в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="30c60-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="30c60-336">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Апплеетрансформс**</span><span class="sxs-lookup"><span data-stu-id="30c60-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="30c60-337">Указывает, должны ли значения, предоставленные для преобразования влево и вправо, считаться допустимыми и примененными к работающей системе.</span><span class="sxs-lookup"><span data-stu-id="30c60-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="30c60-338">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Апплипд**</span><span class="sxs-lookup"><span data-stu-id="30c60-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="30c60-339">Должно ли значение, указанное для IPD, считаться допустимым и примененным к работающей системе.</span><span class="sxs-lookup"><span data-stu-id="30c60-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="30c60-340">Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="30c60-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="30c60-341">Корень для создания пакетов, используемых для управления устройством.</span><span class="sxs-lookup"><span data-stu-id="30c60-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="30c60-342">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. Device**</span><span class="sxs-lookup"><span data-stu-id="30c60-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="30c60-343">Извлеките объект имитации устройства, который интерпретирует имитацию человека и имитации мира.</span><span class="sxs-lookup"><span data-stu-id="30c60-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="30c60-344">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. человеческий**</span><span class="sxs-lookup"><span data-stu-id="30c60-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="30c60-345">Извлеките объект, управляющий имитацией человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="30c60-346">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. Reset**</span><span class="sxs-lookup"><span data-stu-id="30c60-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="30c60-347">Сбрасывает состояние имитации до состояния по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30c60-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="30c60-348">Microsoft. Перцептионсимулатион. Исимулатеддевице</span><span class="sxs-lookup"><span data-stu-id="30c60-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="30c60-349">Интерфейс, описывающий устройство, которое интерпретирует имитацию мира и имитацию человека</span><span class="sxs-lookup"><span data-stu-id="30c60-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="30c60-350">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Хеадтраккер**</span><span class="sxs-lookup"><span data-stu-id="30c60-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="30c60-351">Извлеките головной датчик из имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="30c60-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="30c60-352">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Хандтраккер**</span><span class="sxs-lookup"><span data-stu-id="30c60-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="30c60-353">Получите датчик руки от имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="30c60-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="30c60-354">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Сетсимулатеддевицетипе (Microsoft. Перцептионсимулатион. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="30c60-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="30c60-355">Задайте свойства виртуального устройства в соответствии с указанным типом устройства.</span><span class="sxs-lookup"><span data-stu-id="30c60-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="30c60-356">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-356">Parameters</span></span>
* <span data-ttu-id="30c60-357">тип — новый тип имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="30c60-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="30c60-358">Microsoft. Перцептионсимулатион. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="30c60-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="30c60-359">Дополнительные свойства доступны путем приведения Исимулатеддевице к ISimulatedDevice2.</span><span class="sxs-lookup"><span data-stu-id="30c60-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="30c60-360">**Microsoft. Перцептионсимулатион. ISimulatedDevice2. Исусерпресент**</span><span class="sxs-lookup"><span data-stu-id="30c60-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="30c60-361">Получение или задание того, активно ли имитация людьмиа на гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="30c60-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="30c60-362">**Microsoft. Перцептионсимулатион. ISimulatedDevice2. Дисплайконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="30c60-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="30c60-363">Получение или установка свойств имитации дисплея.</span><span class="sxs-lookup"><span data-stu-id="30c60-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="30c60-364">Microsoft. Перцептионсимулатион. Исимулатедхеадтраккер</span><span class="sxs-lookup"><span data-stu-id="30c60-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="30c60-365">Интерфейс, описывающий часть имитации устройства, которая отслеживает заголовку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="30c60-366">**Microsoft. Перцептионсимулатион. Исимулатедхеадтраккер. Хеадтраккермоде**</span><span class="sxs-lookup"><span data-stu-id="30c60-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="30c60-367">Извлекает и устанавливает текущий режим трассировки головного подразделения.</span><span class="sxs-lookup"><span data-stu-id="30c60-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="30c60-368">Microsoft. Перцептионсимулатион. Исимулатедхандтраккер</span><span class="sxs-lookup"><span data-stu-id="30c60-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="30c60-369">Интерфейс, описывающий часть имитации устройства, которая отслеживает руки имитации человека</span><span class="sxs-lookup"><span data-stu-id="30c60-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="30c60-370">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="30c60-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="30c60-371">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="30c60-372">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. положением**</span><span class="sxs-lookup"><span data-stu-id="30c60-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="30c60-373">Извлечение и задание положения объекта Tracker для имитации относительно центра головки.</span><span class="sxs-lookup"><span data-stu-id="30c60-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="30c60-374">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. шаг**</span><span class="sxs-lookup"><span data-stu-id="30c60-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="30c60-375">Извлеките и задайте шаг вниз для смоделированного средства записи.</span><span class="sxs-lookup"><span data-stu-id="30c60-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="30c60-376">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Фрустумигноред**</span><span class="sxs-lookup"><span data-stu-id="30c60-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="30c60-377">Получите и задайте значение, определяющее, пропускается ли фрустум транспортера для имитации.</span><span class="sxs-lookup"><span data-stu-id="30c60-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="30c60-378">Если игнорируется, обе руки всегда видимы.</span><span class="sxs-lookup"><span data-stu-id="30c60-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="30c60-379">Если параметр не пропускается (по умолчанию), руки отображаются только в том случае, если они находятся в фрустуме средства записи.</span><span class="sxs-lookup"><span data-stu-id="30c60-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="30c60-380">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Фрустум**</span><span class="sxs-lookup"><span data-stu-id="30c60-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="30c60-381">Получите и задайте свойства фрустум, используемые для определения, видны ли руки для имитации средства записи.</span><span class="sxs-lookup"><span data-stu-id="30c60-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="30c60-382">Microsoft. Перцептионсимулатион. Исимулатедхуман</span><span class="sxs-lookup"><span data-stu-id="30c60-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="30c60-383">Интерфейс верхнего уровня для управления имитируемым человеком.</span><span class="sxs-lookup"><span data-stu-id="30c60-383">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="30c60-384">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="30c60-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="30c60-385">Извлечение и Установка расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="30c60-386">Это расположение соответствует точке в центре метров человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="30c60-387">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Direction**</span><span class="sxs-lookup"><span data-stu-id="30c60-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="30c60-388">Извлеките и задайте направление имитации человеческих лиц в мире.</span><span class="sxs-lookup"><span data-stu-id="30c60-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="30c60-389">0 радианы отменяют отрицательную ось Z.</span><span class="sxs-lookup"><span data-stu-id="30c60-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="30c60-390">Положительные радианы поворачиваются по часовой стрелке относительно оси Y.</span><span class="sxs-lookup"><span data-stu-id="30c60-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="30c60-391">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Height**</span><span class="sxs-lookup"><span data-stu-id="30c60-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="30c60-392">Получение и задание высоты имитации человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="30c60-393">**Microsoft. Перцептионсимулатион. Исимулатедхуман. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="30c60-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="30c60-394">Получите левую руку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="30c60-395">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Ригхсанд**</span><span class="sxs-lookup"><span data-stu-id="30c60-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="30c60-396">Получите правую руку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="30c60-397">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Head**</span><span class="sxs-lookup"><span data-stu-id="30c60-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="30c60-398">Получите заголовок имитации человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="30c60-399">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="30c60-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="30c60-400">Перемещение имитации человека относительно его текущего положения в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="30c60-401">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-401">Parameters</span></span>
* <span data-ttu-id="30c60-402">перевод — перевод, который необходимо переместить, относительно текущего положения.</span><span class="sxs-lookup"><span data-stu-id="30c60-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="30c60-403">**Microsoft. Перцептионсимулатион. Исимулатедхуман. вращение (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="30c60-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="30c60-404">Поворот имитации человека относительно текущего направления по часовой стрелке по оси Y</span><span class="sxs-lookup"><span data-stu-id="30c60-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="30c60-405">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-405">Parameters</span></span>
* <span data-ttu-id="30c60-406">радианы — величина поворота вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="30c60-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="30c60-407">Microsoft. Перцептионсимулатион. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="30c60-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="30c60-408">Дополнительные свойства доступны путем приведения Исимулатедхуман к ISimulatedHuman2.</span><span class="sxs-lookup"><span data-stu-id="30c60-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="30c60-409">**Microsoft. Перцептионсимулатион. ISimulatedHuman2. Лефтконтроллер**</span><span class="sxs-lookup"><span data-stu-id="30c60-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="30c60-410">Получите левый 6-ДОФ контроллер.</span><span class="sxs-lookup"><span data-stu-id="30c60-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="30c60-411">**Microsoft. Перцептионсимулатион. ISimulatedHuman2. Ригхтконтроллер**</span><span class="sxs-lookup"><span data-stu-id="30c60-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="30c60-412">Получите подходящий 6-ДОФ контроллер.</span><span class="sxs-lookup"><span data-stu-id="30c60-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="30c60-413">Microsoft. Перцептионсимулатион. Исимулатедханд</span><span class="sxs-lookup"><span data-stu-id="30c60-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="30c60-414">Интерфейс, описывающий руки имитации человека</span><span class="sxs-lookup"><span data-stu-id="30c60-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="30c60-415">**Microsoft. Перцептионсимулатион. Исимулатедханд. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="30c60-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="30c60-416">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="30c60-417">**Microsoft. Перцептионсимулатион. Исимулатедханд. положением**</span><span class="sxs-lookup"><span data-stu-id="30c60-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="30c60-418">Получение и установка положения смоделированной руки относительно человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="30c60-419">**Microsoft. Перцептионсимулатион. Исимулатедханд. Activated**</span><span class="sxs-lookup"><span data-stu-id="30c60-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="30c60-420">Извлечение и задание того, активирована ли рука в настоящий момент.</span><span class="sxs-lookup"><span data-stu-id="30c60-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="30c60-421">**Microsoft. Перцептионсимулатион. Исимулатедханд. Visible**</span><span class="sxs-lookup"><span data-stu-id="30c60-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="30c60-422">Извлеките, является ли рука в настоящий момент видимой для SimulatedDevice (IE, находится ли она в положении, которое должно быть обнаружено Хандтраккер).</span><span class="sxs-lookup"><span data-stu-id="30c60-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="30c60-423">**Microsoft. Перцептионсимулатион. Исимулатедханд. Енсуревисибле**</span><span class="sxs-lookup"><span data-stu-id="30c60-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="30c60-424">Переместите руку так, чтобы она была видна SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="30c60-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="30c60-425">**Microsoft. Перцептионсимулатион. Исимулатедханд. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="30c60-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="30c60-426">Переместить положение моделируемой руки относительно ее текущей должности в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="30c60-427">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-427">Parameters</span></span>
* <span data-ttu-id="30c60-428">перевод — величина, на которую переводятся смоделированные руки.</span><span class="sxs-lookup"><span data-stu-id="30c60-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="30c60-429">**Microsoft. Перцептионсимулатион. Исимулатедханд. Перформжестуре (Microsoft. Перцептионсимулатион. Симулатеджестуре)**</span><span class="sxs-lookup"><span data-stu-id="30c60-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="30c60-430">Выполните жест, используя имитацию руки.</span><span class="sxs-lookup"><span data-stu-id="30c60-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="30c60-431">Она будет обнаружена системой только в том случае, если она включена.</span><span class="sxs-lookup"><span data-stu-id="30c60-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="30c60-432">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-432">Parameters</span></span>
* <span data-ttu-id="30c60-433">жест — жест, который необходимо выполнить.</span><span class="sxs-lookup"><span data-stu-id="30c60-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="30c60-434">Microsoft. Перцептионсимулатион. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="30c60-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="30c60-435">Дополнительные свойства доступны путем приведения Исимулатедханд к ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="30c60-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="30c60-436">**Microsoft. Перцептионсимулатион. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="30c60-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="30c60-437">Возвращает или задает поворот моделируемой руки.</span><span class="sxs-lookup"><span data-stu-id="30c60-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="30c60-438">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="30c60-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="30c60-439">Microsoft. Перцептионсимулатион. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="30c60-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="30c60-440">Дополнительные свойства доступны путем приведения Исимулатедханд к ISimulatedHand3.</span><span class="sxs-lookup"><span data-stu-id="30c60-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="30c60-441">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Жетжоинтконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="30c60-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="30c60-442">Получение конфигурации соединения для указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="30c60-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="30c60-443">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Сетжоинтконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="30c60-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="30c60-444">Задает конфигурацию соединения для указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="30c60-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="30c60-445">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Сесандпосе**</span><span class="sxs-lookup"><span data-stu-id="30c60-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="30c60-446">Задайте для параметра "рука" известное значение с необязательным флагом для анимации.</span><span class="sxs-lookup"><span data-stu-id="30c60-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="30c60-447">Примечание. анимация не приведет к тому, что присоединения будут немедленно отражены в своих окончательно Объединенных конфигурациях.</span><span class="sxs-lookup"><span data-stu-id="30c60-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="30c60-448">Microsoft. Перцептионсимулатион. Исимулатедхеад</span><span class="sxs-lookup"><span data-stu-id="30c60-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="30c60-449">Интерфейс, описывающий заголовок имитации человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="30c60-450">**Microsoft. Перцептионсимулатион. Исимулатедхеад. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="30c60-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="30c60-451">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="30c60-452">**Microsoft. Перцептионсимулатион. Исимулатедхеад. вращение**</span><span class="sxs-lookup"><span data-stu-id="30c60-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="30c60-453">Извлеките поворот моделируемой головки.</span><span class="sxs-lookup"><span data-stu-id="30c60-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="30c60-454">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="30c60-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="30c60-455">**Microsoft. Перцептионсимулатион. Исимулатедхеад. диаметр**</span><span class="sxs-lookup"><span data-stu-id="30c60-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="30c60-456">Получение диаметра смоделированного головного элемента.</span><span class="sxs-lookup"><span data-stu-id="30c60-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="30c60-457">Это значение используется для определения центра заголовка (точки вращения).</span><span class="sxs-lookup"><span data-stu-id="30c60-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="30c60-458">**Microsoft. Перцептионсимулатион. Исимулатедхеад. вращение (Microsoft. Перцептионсимулатион. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="30c60-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="30c60-459">Поворот смоделированной головки относительно текущего поворота.</span><span class="sxs-lookup"><span data-stu-id="30c60-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="30c60-460">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="30c60-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="30c60-461">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-461">Parameters</span></span>
* <span data-ttu-id="30c60-462">вращение — величина поворота.</span><span class="sxs-lookup"><span data-stu-id="30c60-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="30c60-463">Microsoft. Перцептионсимулатион. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="30c60-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="30c60-464">Дополнительные свойства доступны путем приведения Исимулатедхеад к ISimulatedHead2.</span><span class="sxs-lookup"><span data-stu-id="30c60-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="30c60-465">**Microsoft. Перцептионсимулатион. ISimulatedHead2. глаза**</span><span class="sxs-lookup"><span data-stu-id="30c60-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="30c60-466">Извлеките глаза имитации человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="30c60-467">Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер</span><span class="sxs-lookup"><span data-stu-id="30c60-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="30c60-468">Интерфейс, описывающий ДОФ контроллер, связанный с имитируемым человеком.</span><span class="sxs-lookup"><span data-stu-id="30c60-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="30c60-469">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="30c60-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="30c60-470">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="30c60-471">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. status**</span><span class="sxs-lookup"><span data-stu-id="30c60-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="30c60-472">Возвращает или задает текущее состояние контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="30c60-473">Для состояния контроллера должно быть задано значение, отличное от OFF, прежде чем все вызовы для перемещения, вращения или нажатия кнопки будут выполнены.</span><span class="sxs-lookup"><span data-stu-id="30c60-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="30c60-474">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. положением**</span><span class="sxs-lookup"><span data-stu-id="30c60-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="30c60-475">Получение или установка положения имитации контроллера относительно человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="30c60-476">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Orientation**</span><span class="sxs-lookup"><span data-stu-id="30c60-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="30c60-477">Получение или установка ориентации имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="30c60-478">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="30c60-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="30c60-479">Переместить положение имитации контроллера относительно его текущего положения в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="30c60-480">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-480">Parameters</span></span>
* <span data-ttu-id="30c60-481">перевод — это величина, на которую нужно перевести имитируемый контроллер.</span><span class="sxs-lookup"><span data-stu-id="30c60-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="30c60-482">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Прессбуттон (Симулатедсиксдофконтроллербуттон)**</span><span class="sxs-lookup"><span data-stu-id="30c60-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="30c60-483">Нажмите кнопку на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="30c60-484">Она будет обнаружена системой только в том случае, если контроллер включен.</span><span class="sxs-lookup"><span data-stu-id="30c60-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="30c60-485">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-485">Parameters</span></span>
* <span data-ttu-id="30c60-486">Кнопка для нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="30c60-486">button - The button to press.</span></span>

<span data-ttu-id="30c60-487">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Релеасебуттон (Симулатедсиксдофконтроллербуттон)**</span><span class="sxs-lookup"><span data-stu-id="30c60-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="30c60-488">Выпустите кнопку на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="30c60-489">Она будет обнаружена системой только в том случае, если контроллер включен.</span><span class="sxs-lookup"><span data-stu-id="30c60-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="30c60-490">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-490">Parameters</span></span>
* <span data-ttu-id="30c60-491">Кнопка для выпуска.</span><span class="sxs-lookup"><span data-stu-id="30c60-491">button - The button to release.</span></span>

<span data-ttu-id="30c60-492">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Жеттаучпадпоситион (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="30c60-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="30c60-493">Получить расположение имитации пальца на сенсорной панели имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="30c60-494">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-494">Parameters</span></span>
* <span data-ttu-id="30c60-495">x — горизонтальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="30c60-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="30c60-496">y — вертикальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="30c60-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="30c60-497">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Сеттаучпадпоситион (float, float)**</span><span class="sxs-lookup"><span data-stu-id="30c60-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="30c60-498">Установите расположение имитации пальца на сенсорной панели имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="30c60-499">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-499">Parameters</span></span>
* <span data-ttu-id="30c60-500">x — горизонтальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="30c60-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="30c60-501">y — вертикальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="30c60-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="30c60-502">Microsoft. Перцептионсимулатион. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="30c60-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="30c60-503">Дополнительные свойства и методы доступны путем приведения Исимулатедсиксдофконтроллер к ISimulatedSixDofController2.</span><span class="sxs-lookup"><span data-stu-id="30c60-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="30c60-504">**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Жетсумбстиккпоситион (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="30c60-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="30c60-505">Получение расположения имитации аналогового стика на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="30c60-506">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-506">Parameters</span></span>
* <span data-ttu-id="30c60-507">x — горизонтальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="30c60-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="30c60-508">y — вертикальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="30c60-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="30c60-509">**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Сетсумбстиккпоситион (float, float)**</span><span class="sxs-lookup"><span data-stu-id="30c60-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="30c60-510">Задайте расположение имитации аналогового стика на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="30c60-511">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-511">Parameters</span></span>
* <span data-ttu-id="30c60-512">x — горизонтальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="30c60-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="30c60-513">y — вертикальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="30c60-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="30c60-514">**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Баттерилевел**</span><span class="sxs-lookup"><span data-stu-id="30c60-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="30c60-515">Получение или установка уровня заряда батареи для имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="30c60-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="30c60-516">Значение должно быть больше 0,0 и меньше или равно 100,0.</span><span class="sxs-lookup"><span data-stu-id="30c60-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="30c60-517">Microsoft. Перцептионсимулатион. Исимулатедэйес</span><span class="sxs-lookup"><span data-stu-id="30c60-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="30c60-518">Интерфейс, описывающий глаза имитации человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="30c60-519">**Microsoft. Перцептионсимулатион. Исимулатедэйес. вращение**</span><span class="sxs-lookup"><span data-stu-id="30c60-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="30c60-520">Извлеките поворот имитации глаз.</span><span class="sxs-lookup"><span data-stu-id="30c60-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="30c60-521">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="30c60-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="30c60-522">**Microsoft. Перцептионсимулатион. Исимулатедэйес. вращение (Microsoft. Перцептионсимулатион. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="30c60-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="30c60-523">Поворот имитации глаз относительно текущего вращения.</span><span class="sxs-lookup"><span data-stu-id="30c60-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="30c60-524">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="30c60-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="30c60-525">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-525">Parameters</span></span>
* <span data-ttu-id="30c60-526">вращение — величина поворота.</span><span class="sxs-lookup"><span data-stu-id="30c60-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="30c60-527">**Microsoft. Перцептионсимулатион. Исимулатедэйес. Калибратионстате**</span><span class="sxs-lookup"><span data-stu-id="30c60-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="30c60-528">Возвращает или задает состояние калибровки для имитации глаз.</span><span class="sxs-lookup"><span data-stu-id="30c60-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="30c60-529">**Microsoft. Перцептионсимулатион. Исимулатедэйес. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="30c60-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="30c60-530">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="30c60-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="30c60-531">Microsoft. Перцептионсимулатион. Исимулатионрекординг</span><span class="sxs-lookup"><span data-stu-id="30c60-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="30c60-532">Интерфейс для взаимодействия с одной записью, загруженной для воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="30c60-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="30c60-533">**Типы Microsoft. Перцептионсимулатион. Исимулатионрекординг.**</span><span class="sxs-lookup"><span data-stu-id="30c60-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="30c60-534">Возвращает список типов данных в записи.</span><span class="sxs-lookup"><span data-stu-id="30c60-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="30c60-535">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. State**</span><span class="sxs-lookup"><span data-stu-id="30c60-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="30c60-536">Извлекает текущее состояние записи.</span><span class="sxs-lookup"><span data-stu-id="30c60-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="30c60-537">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Play**</span><span class="sxs-lookup"><span data-stu-id="30c60-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="30c60-538">Запустите воспроизведение.</span><span class="sxs-lookup"><span data-stu-id="30c60-538">Start the playback.</span></span> <span data-ttu-id="30c60-539">Если запись приостановлена, воспроизведение будет возобновлено из приостановленного расположения. При остановке воспроизведение начнется с самого начала.</span><span class="sxs-lookup"><span data-stu-id="30c60-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="30c60-540">Если воспроизведение уже проигрывается, этот вызов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="30c60-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="30c60-541">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Pause**</span><span class="sxs-lookup"><span data-stu-id="30c60-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="30c60-542">Приостанавливает воспроизведение в текущем расположении.</span><span class="sxs-lookup"><span data-stu-id="30c60-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="30c60-543">Если запись остановлена, вызов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="30c60-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="30c60-544">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="30c60-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="30c60-545">Ищет запись в указанное время (в 100 наносекундах с начала) и останавливается в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="30c60-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="30c60-546">Если время превышает окончание записи, оно приостанавливается на последнем кадре.</span><span class="sxs-lookup"><span data-stu-id="30c60-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="30c60-547">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-547">Parameters</span></span>
* <span data-ttu-id="30c60-548">такты — время поиска.</span><span class="sxs-lookup"><span data-stu-id="30c60-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="30c60-549">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. останавливаться**</span><span class="sxs-lookup"><span data-stu-id="30c60-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="30c60-550">Останавливает воспроизведение и сбрасывает текущую точку в начало.</span><span class="sxs-lookup"><span data-stu-id="30c60-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="30c60-551">Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк</span><span class="sxs-lookup"><span data-stu-id="30c60-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="30c60-552">Интерфейс для получения изменений состояния во время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="30c60-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="30c60-553">**Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк. Плайбаккстатечанжед (Microsoft. Перцептионсимулатион. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="30c60-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="30c60-554">Вызывается при изменении состояния воспроизведения Исимулатионрекординг.</span><span class="sxs-lookup"><span data-stu-id="30c60-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="30c60-555">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-555">Parameters</span></span>
* <span data-ttu-id="30c60-556">newState — новое состояние записи.</span><span class="sxs-lookup"><span data-stu-id="30c60-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="30c60-557">Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="30c60-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="30c60-558">Корневой объект для создания объектов имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="30c60-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="30c60-559">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Креатеперцептионсимулатионманажер (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="30c60-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="30c60-560">Создать на объекте для создания смоделированных пакетов и доставки их в предоставленный приемник.</span><span class="sxs-lookup"><span data-stu-id="30c60-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="30c60-561">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-561">Parameters</span></span>
* <span data-ttu-id="30c60-562">приемник — приемник, который будет принимать все созданные пакеты.</span><span class="sxs-lookup"><span data-stu-id="30c60-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="30c60-563">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="30c60-563">Return value</span></span>

<span data-ttu-id="30c60-564">Созданный диспетчер.</span><span class="sxs-lookup"><span data-stu-id="30c60-564">The created Manager.</span></span>

<span data-ttu-id="30c60-565">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Креатеперцептионсимулатионрекординг (System. String)**</span><span class="sxs-lookup"><span data-stu-id="30c60-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="30c60-566">Создание приемника, в котором хранятся все полученные пакеты в файле по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="30c60-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="30c60-567">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-567">Parameters</span></span>
* <span data-ttu-id="30c60-568">путь — путь к создаваемому файлу.</span><span class="sxs-lookup"><span data-stu-id="30c60-568">path - The path of the file to create.</span></span>

<span data-ttu-id="30c60-569">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="30c60-569">Return value</span></span>

<span data-ttu-id="30c60-570">Созданный приемник.</span><span class="sxs-lookup"><span data-stu-id="30c60-570">The created sink.</span></span>

<span data-ttu-id="30c60-571">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Лоадперцептионсимулатионрекординг (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="30c60-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="30c60-572">Загрузка записи из указанного файла.</span><span class="sxs-lookup"><span data-stu-id="30c60-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="30c60-573">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-573">Parameters</span></span>
* <span data-ttu-id="30c60-574">путь — путь к загружаемому файлу.</span><span class="sxs-lookup"><span data-stu-id="30c60-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="30c60-575">Factory — фабрика, используемая записью для создания Исимулатионстреамсинк при необходимости.</span><span class="sxs-lookup"><span data-stu-id="30c60-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="30c60-576">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="30c60-576">Return value</span></span>

<span data-ttu-id="30c60-577">Загруженная запись.</span><span class="sxs-lookup"><span data-stu-id="30c60-577">The loaded recording.</span></span>

<span data-ttu-id="30c60-578">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Лоадперцептионсимулатионрекординг (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="30c60-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="30c60-579">Загрузка записи из указанного файла.</span><span class="sxs-lookup"><span data-stu-id="30c60-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="30c60-580">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-580">Parameters</span></span>
* <span data-ttu-id="30c60-581">путь — путь к загружаемому файлу.</span><span class="sxs-lookup"><span data-stu-id="30c60-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="30c60-582">Factory — фабрика, используемая записью для создания Исимулатионстреамсинк при необходимости.</span><span class="sxs-lookup"><span data-stu-id="30c60-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="30c60-583">Callback — обратный вызов, который получает обновления с пределом состояния записи.</span><span class="sxs-lookup"><span data-stu-id="30c60-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="30c60-584">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="30c60-584">Return value</span></span>

<span data-ttu-id="30c60-585">Загруженная запись.</span><span class="sxs-lookup"><span data-stu-id="30c60-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="30c60-586">Microsoft. Перцептионсимулатион. Стреамдататипес</span><span class="sxs-lookup"><span data-stu-id="30c60-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="30c60-587">Описывает различные типы потоковых данных.</span><span class="sxs-lookup"><span data-stu-id="30c60-587">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="30c60-588">**Microsoft. Перцептионсимулатион. Стреамдататипес. None**</span><span class="sxs-lookup"><span data-stu-id="30c60-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="30c60-589">Значение Sentinel, используемое для обозначения отсутствия типов данных потока.</span><span class="sxs-lookup"><span data-stu-id="30c60-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="30c60-590">**Microsoft. Перцептионсимулатион. Стреамдататипес. Head**</span><span class="sxs-lookup"><span data-stu-id="30c60-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="30c60-591">Поток данных, относящийся к положению и ориентации головного элемента.</span><span class="sxs-lookup"><span data-stu-id="30c60-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="30c60-592">**Microsoft. Перцептионсимулатион. Стреамдататипес. руки**</span><span class="sxs-lookup"><span data-stu-id="30c60-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="30c60-593">Поток данных о положении и жестах руки.</span><span class="sxs-lookup"><span data-stu-id="30c60-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="30c60-594">**Microsoft. Перцептионсимулатион. Стреамдататипес. Спатиалмаппинг**</span><span class="sxs-lookup"><span data-stu-id="30c60-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="30c60-595">Поток данных о пространственном сопоставлении среды.</span><span class="sxs-lookup"><span data-stu-id="30c60-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="30c60-596">**Microsoft. Перцептионсимулатион. Стреамдататипес. Калибровка**</span><span class="sxs-lookup"><span data-stu-id="30c60-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="30c60-597">Поток данных, касающихся калибровки устройства.</span><span class="sxs-lookup"><span data-stu-id="30c60-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="30c60-598">Пакеты калибровки принимаются только системой в удаленном режиме.</span><span class="sxs-lookup"><span data-stu-id="30c60-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="30c60-599">**Microsoft. Перцептионсимулатион. Стреамдататипес. Environment**</span><span class="sxs-lookup"><span data-stu-id="30c60-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="30c60-600">Поток данных о среде устройства.</span><span class="sxs-lookup"><span data-stu-id="30c60-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="30c60-601">**Microsoft. Перцептионсимулатион. Стреамдататипес. Сиксдофконтроллерс**</span><span class="sxs-lookup"><span data-stu-id="30c60-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="30c60-602">Поток данных, касающихся контроллеров движения.</span><span class="sxs-lookup"><span data-stu-id="30c60-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="30c60-603">**Microsoft. Перцептионсимулатион. Стреамдататипес. глаза**</span><span class="sxs-lookup"><span data-stu-id="30c60-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="30c60-604">Поток данных, касающихся глаз имитации человека.</span><span class="sxs-lookup"><span data-stu-id="30c60-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="30c60-605">**Microsoft. Перцептионсимулатион. Стреамдататипес. Дисплайконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="30c60-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="30c60-606">Поток данных, касающихся конфигурации экрана устройства.</span><span class="sxs-lookup"><span data-stu-id="30c60-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="30c60-607">**Microsoft. Перцептионсимулатион. Стреамдататипес. ALL**</span><span class="sxs-lookup"><span data-stu-id="30c60-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="30c60-608">Значение Sentinel, используемое для указания всех записанных типов данных.</span><span class="sxs-lookup"><span data-stu-id="30c60-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="30c60-609">Microsoft. Перцептионсимулатион. Исимулатионстреамсинк</span><span class="sxs-lookup"><span data-stu-id="30c60-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="30c60-610">Объект, получающий пакеты данных из потока имитации.</span><span class="sxs-lookup"><span data-stu-id="30c60-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="30c60-611">**Microsoft. Перцептионсимулатион. Исимулатионстреамсинк. Онпаккетрецеивед (длина uint, Byte [], пакет)**</span><span class="sxs-lookup"><span data-stu-id="30c60-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="30c60-612">Получает один пакет, который внутренне типизирован и имеет версию.</span><span class="sxs-lookup"><span data-stu-id="30c60-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="30c60-613">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c60-613">Parameters</span></span>
* <span data-ttu-id="30c60-614">Длина — Длина пакета.</span><span class="sxs-lookup"><span data-stu-id="30c60-614">length - The length of the packet.</span></span>
* <span data-ttu-id="30c60-615">пакет — данные пакета.</span><span class="sxs-lookup"><span data-stu-id="30c60-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="30c60-616">Microsoft. Перцептионсимулатион. Исимулатионстреамсинкфактори</span><span class="sxs-lookup"><span data-stu-id="30c60-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="30c60-617">Объект, создающий Исимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="30c60-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="30c60-618">**Microsoft. Перцептионсимулатион. Исимулатионстреамсинкфактори. Креатесимулатионстреамсинк ()**</span><span class="sxs-lookup"><span data-stu-id="30c60-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="30c60-619">Создает единственный экземпляр Исимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="30c60-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="30c60-620">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="30c60-620">Return value</span></span>

<span data-ttu-id="30c60-621">Созданный приемник.</span><span class="sxs-lookup"><span data-stu-id="30c60-621">The created sink.</span></span>
