---
title: Ввод в MR 212 — Voice
description: Выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы получить сведения о концепциях голоса.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, Academy, учебник, речь
ms.openlocfilehash: 9db503ea4c7db9a3eb272ad9663024ca3a407dda
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434597"
---
>[!NOTE]
><span data-ttu-id="312d8-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="312d8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="312d8-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="312d8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="312d8-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="312d8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="312d8-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="312d8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="312d8-108">Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="312d8-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="312d8-109">Ввод MR 212: Voice</span><span class="sxs-lookup"><span data-stu-id="312d8-109">MR Input 212: Voice</span></span>

<span data-ttu-id="312d8-110">[Ввод голоса](voice-input.md) дает нам еще один способ взаимодействия с нашими голограммами.</span><span class="sxs-lookup"><span data-stu-id="312d8-110">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="312d8-111">Речевые команды работают очень естественным образом.</span><span class="sxs-lookup"><span data-stu-id="312d8-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="312d8-112">Разработайте свои речевые команды, чтобы они были:</span><span class="sxs-lookup"><span data-stu-id="312d8-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="312d8-113">Логарифм</span><span class="sxs-lookup"><span data-stu-id="312d8-113">Natural</span></span>
* <span data-ttu-id="312d8-114">Легко запомнить</span><span class="sxs-lookup"><span data-stu-id="312d8-114">Easy to remember</span></span>
* <span data-ttu-id="312d8-115">Соответствующий контекст</span><span class="sxs-lookup"><span data-stu-id="312d8-115">Context appropriate</span></span>
* <span data-ttu-id="312d8-116">Достаточно отличается от других параметров в том же контексте</span><span class="sxs-lookup"><span data-stu-id="312d8-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="312d8-117">В статье об основных возможностях [101](holograms-101.md)мы использовали кэйвордрекогнизер для создания двух простых голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="312d8-117">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="312d8-118">В MR input 212 мы подробнее рассмотрим следующие вопросы:</span><span class="sxs-lookup"><span data-stu-id="312d8-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="312d8-119">Разработка голосовых команд, оптимизированных для модуля распознавания речи HoloLens.</span><span class="sxs-lookup"><span data-stu-id="312d8-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="312d8-120">Предоставьте пользователю сведения о том, какие речевые команды доступны.</span><span class="sxs-lookup"><span data-stu-id="312d8-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="312d8-121">Подтвердите, что мы слышали о команде пользователя.</span><span class="sxs-lookup"><span data-stu-id="312d8-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="312d8-122">Сведения о том, что говорят пользователь, с помощью распознавателя диктофона.</span><span class="sxs-lookup"><span data-stu-id="312d8-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="312d8-123">Используйте распознаватель грамматики для прослушивания команд на основе спецификации или грамматики распознавания речи, файла.</span><span class="sxs-lookup"><span data-stu-id="312d8-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="312d8-124">В этом курсе мы перейдем к обозревателю моделей, который мы создали в [MR input 210](holograms-210.md) и [MR input 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="312d8-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="312d8-125">Видеоматериалы, внедренные в каждую из приведенных ниже глав, были записаны с использованием более старой версии Unity и набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="312d8-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="312d8-126">Хотя пошаговые инструкции являются точными и актуальными, в соответствующих видеоматериалах могут отображаться сценарии и визуальные элементы, которые являются неактуальными.</span><span class="sxs-lookup"><span data-stu-id="312d8-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="312d8-127">Видеоматериалы по-прежнему включены в постерити, так как эти концепции все еще применимы.</span><span class="sxs-lookup"><span data-stu-id="312d8-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="312d8-128">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="312d8-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="312d8-129">Хождение</span><span class="sxs-lookup"><span data-stu-id="312d8-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="312d8-130"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="312d8-130"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="312d8-131"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="312d8-131"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="312d8-132">Ввод MR 212: Voice</span><span class="sxs-lookup"><span data-stu-id="312d8-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="312d8-133">✔️</span><span class="sxs-lookup"><span data-stu-id="312d8-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="312d8-134">✔️</span><span class="sxs-lookup"><span data-stu-id="312d8-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="312d8-135">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="312d8-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="312d8-136">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="312d8-136">Prerequisites</span></span>

* <span data-ttu-id="312d8-137">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="312d8-137">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="312d8-138">Некоторые базовые C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="312d8-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="312d8-139">Вы должны были выполнить [Основные сведения о MR 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="312d8-139">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="312d8-140">Необходимо завершить [Ввод MR 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="312d8-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="312d8-141">Необходимо завершить [Ввод MR 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="312d8-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="312d8-142">Устройство HoloLens, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="312d8-142">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="312d8-143">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="312d8-143">Project files</span></span>

* <span data-ttu-id="312d8-144">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="312d8-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="312d8-145">Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="312d8-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="312d8-146">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="312d8-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="312d8-147">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="312d8-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="312d8-148">Ошибки и примечания</span><span class="sxs-lookup"><span data-stu-id="312d8-148">Errata and Notes</span></span>

* <span data-ttu-id="312d8-149">Параметр "Enable Только мой код" должен быть отключен (*снят*) в Visual Studio в разделе "сервис-> Параметры" — > Отладка для попадания в код точек останова в коде.</span><span class="sxs-lookup"><span data-stu-id="312d8-149">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="312d8-150">Установка Unity</span><span class="sxs-lookup"><span data-stu-id="312d8-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="312d8-151">Инструкция</span><span class="sxs-lookup"><span data-stu-id="312d8-151">Instructions</span></span>

1. <span data-ttu-id="312d8-152">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="312d8-152">Start Unity.</span></span>
2. <span data-ttu-id="312d8-153">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="312d8-153">Select **Open**.</span></span>
3. <span data-ttu-id="312d8-154">Перейдите в папку **холографикакадеми-голограмм-212-Voice** , которая была отменена в архиве.</span><span class="sxs-lookup"><span data-stu-id="312d8-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="312d8-155">Найдите и выберите **начальную** папку **обозревателя моделей**/.</span><span class="sxs-lookup"><span data-stu-id="312d8-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="312d8-156">Нажмите кнопку **выбрать папку** .</span><span class="sxs-lookup"><span data-stu-id="312d8-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="312d8-157">На панели **проект** разверните папку **сцены** .</span><span class="sxs-lookup"><span data-stu-id="312d8-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="312d8-158">Дважды щелкните **моделексплорер** сцену, чтобы загрузить его в Unity.</span><span class="sxs-lookup"><span data-stu-id="312d8-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="312d8-159">Создание</span><span class="sxs-lookup"><span data-stu-id="312d8-159">Building</span></span>

1. <span data-ttu-id="312d8-160">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="312d8-160">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="312d8-161">Если « **сцены» или «моделексплорер** » в окне « **Построение**» не отображаются, щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="312d8-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="312d8-162">Если вы специально разрабатываете для HoloLens, задайте для параметра **целевое устройство** значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="312d8-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="312d8-163">В противном случае оставьте его на **любом устройстве**.</span><span class="sxs-lookup"><span data-stu-id="312d8-163">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="312d8-164">Убедитесь, что для **типа сборки** задано значение **D3D** и **пакет SDK** установлен в значение " **Последняя установленная версия** " (это должен быть пакет SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="312d8-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="312d8-165">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="312d8-165">Click **Build**.</span></span>
6. <span data-ttu-id="312d8-166">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="312d8-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="312d8-167">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="312d8-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="312d8-168">Нажмите кнопку **выбрать папку** , и Unity начнет создавать проект для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="312d8-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="312d8-169">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="312d8-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="312d8-170">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="312d8-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="312d8-171">Откройте **решение Моделексплорер Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="312d8-171">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="312d8-172">При развертывании в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="312d8-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="312d8-173">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="312d8-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="312d8-174">Щелкните стрелку раскрывающегося списка рядом с кнопкой локальный компьютер и выберите **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="312d8-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="312d8-175">Введите **IP-адрес устройства HoloLens** и задайте для режима проверки подлинности значение **универсальный (незашифрованный протокол)** .</span><span class="sxs-lookup"><span data-stu-id="312d8-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="312d8-176">Нажмите кнопку **выбрать**.</span><span class="sxs-lookup"><span data-stu-id="312d8-176">Click **Select**.</span></span> <span data-ttu-id="312d8-177">Если вы не узнаете IP-адрес устройства, проверьте **параметры > сеть & интернет > дополнительные параметры**.</span><span class="sxs-lookup"><span data-stu-id="312d8-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="312d8-178">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="312d8-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="312d8-179">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="312d8-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="312d8-180">После развертывания приложения закройте **фитбокс** с помощью **жеста выбора**.</span><span class="sxs-lookup"><span data-stu-id="312d8-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="312d8-181">При развертывании на иммерсивное головной телефон:</span><span class="sxs-lookup"><span data-stu-id="312d8-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="312d8-182">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.</span><span class="sxs-lookup"><span data-stu-id="312d8-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="312d8-183">Убедитесь, что для целевого объекта развертывания задано значение **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="312d8-183">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="312d8-184">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="312d8-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="312d8-185">После развертывания приложения закройте **фитбокс** , изменив триггер на контроллере движения.</span><span class="sxs-lookup"><span data-stu-id="312d8-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="312d8-186">Вы можете заметить некоторые красные ошибки на панели ошибок Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="312d8-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="312d8-187">Их можно спокойно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="312d8-187">It is safe to ignore them.</span></span> <span data-ttu-id="312d8-188">Переключитесь на панель вывода для просмотра фактического хода построения.</span><span class="sxs-lookup"><span data-stu-id="312d8-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="312d8-189">Ошибки на панели вывода потребует внесения исправления (чаще всего они вызваны ошибкой в скрипте).</span><span class="sxs-lookup"><span data-stu-id="312d8-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="312d8-190">Глава 1 — осведомленность</span><span class="sxs-lookup"><span data-stu-id="312d8-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="312d8-191">Задачи</span><span class="sxs-lookup"><span data-stu-id="312d8-191">Objectives</span></span>

* <span data-ttu-id="312d8-192">Узнайте об отделах **и Ототказах** от дизайна речевых команд.</span><span class="sxs-lookup"><span data-stu-id="312d8-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="312d8-193">Используйте **кэйвордрекогнизер** для добавления речевых команд на основе взгляда.</span><span class="sxs-lookup"><span data-stu-id="312d8-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="312d8-194">Предоставление пользователям сведений о голосовых командах с помощью **обратной связи**курсора.</span><span class="sxs-lookup"><span data-stu-id="312d8-194">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="312d8-195">Проектирование команд Voice</span><span class="sxs-lookup"><span data-stu-id="312d8-195">Voice Command Design</span></span>

<span data-ttu-id="312d8-196">В этой главе вы узнаете о проектировании речевых команд.</span><span class="sxs-lookup"><span data-stu-id="312d8-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="312d8-197">При создании команд Voice:</span><span class="sxs-lookup"><span data-stu-id="312d8-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="312d8-198">DO</span><span class="sxs-lookup"><span data-stu-id="312d8-198">DO</span></span>

* <span data-ttu-id="312d8-199">Создание кратких команд.</span><span class="sxs-lookup"><span data-stu-id="312d8-199">Create concise commands.</span></span> <span data-ttu-id="312d8-200">Вы не хотите использовать *"Воспроизвести текущее выбранное видео"* , так как эта команда не является краткой и будет легко забыта пользователем.</span><span class="sxs-lookup"><span data-stu-id="312d8-200">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="312d8-201">Вместо этого следует использовать: *"воспроизвести видео"* , так как он является кратким и имеет несколько слогов.</span><span class="sxs-lookup"><span data-stu-id="312d8-201">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="312d8-202">Используйте простой словарь.</span><span class="sxs-lookup"><span data-stu-id="312d8-202">Use a simple vocabulary.</span></span> <span data-ttu-id="312d8-203">Всегда старайтесь использовать обычные слова и фразы, которые пользователю легко обнаружить и запомнить.</span><span class="sxs-lookup"><span data-stu-id="312d8-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="312d8-204">Например, если в приложении имеется объект Note, который можно было бы отобразить или скрыть в представлении, команда *«Показать*веб-публикацию» не будет использована, так как ««» является редко используемым термином.</span><span class="sxs-lookup"><span data-stu-id="312d8-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="312d8-205">Вместо этого для отображения примечания в приложении следует использовать команду *"Показать Примечание"* .</span><span class="sxs-lookup"><span data-stu-id="312d8-205">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="312d8-206">Соблюдать единообразие.</span><span class="sxs-lookup"><span data-stu-id="312d8-206">Be consistent.</span></span> <span data-ttu-id="312d8-207">Речевые команды должны поддерживать согласованность в приложении.</span><span class="sxs-lookup"><span data-stu-id="312d8-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="312d8-208">Представьте, что у вас есть два сцены в приложении, и в обоих сценах есть кнопка для закрытия приложения.</span><span class="sxs-lookup"><span data-stu-id="312d8-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="312d8-209">Если первая сцена использовала команду *"Exit"* для активации кнопки, но Вторая сцена использовала команду *"закрыть приложение"* , то пользователь будет очень путать.</span><span class="sxs-lookup"><span data-stu-id="312d8-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="312d8-210">Если одна и та же функциональность сохраняется в нескольких сценах, то для ее активации следует использовать одну и ту же голосовую команду.</span><span class="sxs-lookup"><span data-stu-id="312d8-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="312d8-211">Не надо</span><span class="sxs-lookup"><span data-stu-id="312d8-211">DON'T</span></span>

* <span data-ttu-id="312d8-212">Используйте отдельные команды для слогов.</span><span class="sxs-lookup"><span data-stu-id="312d8-212">Use single syllable commands.</span></span> <span data-ttu-id="312d8-213">Например, если вы создавали голосовую команду для воспроизведения видео, следует избегать использования простой команды *«Play»* , так как это лишь один слог, и его легко пропустить в системе.</span><span class="sxs-lookup"><span data-stu-id="312d8-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="312d8-214">Вместо этого следует использовать: *"воспроизвести видео"* , так как он является кратким и имеет несколько слогов.</span><span class="sxs-lookup"><span data-stu-id="312d8-214">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="312d8-215">Используйте системные команды.</span><span class="sxs-lookup"><span data-stu-id="312d8-215">Use system commands.</span></span> <span data-ttu-id="312d8-216">Команда *"Select"* зарезервирована системой для активации события TAP для текущего объекта, на который он нацелен.</span><span class="sxs-lookup"><span data-stu-id="312d8-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="312d8-217">Не используйте повторно команду *"Select"* в ключевом слове или фразе, так как она может не работать должным образом.</span><span class="sxs-lookup"><span data-stu-id="312d8-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="312d8-218">Например, если для выбора куба в приложении выбрано голосовое меню *"выбрать куб"* , но пользователь просматривает сферу при распространеннаяе команды, то вместо этого будет выбрана сфера.</span><span class="sxs-lookup"><span data-stu-id="312d8-218">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="312d8-219">Аналогично, для команд на панели приложений включена поддержка голоса.</span><span class="sxs-lookup"><span data-stu-id="312d8-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="312d8-220">Не используйте следующие голосовые команды в представлении CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="312d8-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="312d8-221">Вернуться</span><span class="sxs-lookup"><span data-stu-id="312d8-221">Go Back</span></span>
    2. <span data-ttu-id="312d8-222">Средство прокрутки</span><span class="sxs-lookup"><span data-stu-id="312d8-222">Scroll Tool</span></span>
    3. <span data-ttu-id="312d8-223">Инструмент масштабирования</span><span class="sxs-lookup"><span data-stu-id="312d8-223">Zoom Tool</span></span>
    4. <span data-ttu-id="312d8-224">Инструмент перетаскивания</span><span class="sxs-lookup"><span data-stu-id="312d8-224">Drag Tool</span></span>
    5. <span data-ttu-id="312d8-225">Регулировка</span><span class="sxs-lookup"><span data-stu-id="312d8-225">Adjust</span></span>
    6. <span data-ttu-id="312d8-226">Remove</span><span class="sxs-lookup"><span data-stu-id="312d8-226">Remove</span></span>
* <span data-ttu-id="312d8-227">Используйте похожие звуки.</span><span class="sxs-lookup"><span data-stu-id="312d8-227">Use similar sounds.</span></span> <span data-ttu-id="312d8-228">Старайтесь не использовать речевые команды, рхиме.</span><span class="sxs-lookup"><span data-stu-id="312d8-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="312d8-229">Если у вас есть приложение для покупок, которое поддерживало *"показывать магазин"* и *"показывать больше"* в качестве голосовых команд, необходимо отключить одну из команд во время использования другой.</span><span class="sxs-lookup"><span data-stu-id="312d8-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="312d8-230">Например, можно использовать кнопку *"Показать магазин"* , чтобы открыть магазин, а затем отключить эту команду при отображении хранилища, чтобы команда *"Показать больше"* могла использоваться для просмотра.</span><span class="sxs-lookup"><span data-stu-id="312d8-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="312d8-231">Инструкция</span><span class="sxs-lookup"><span data-stu-id="312d8-231">Instructions</span></span>

* <span data-ttu-id="312d8-232">На панели **Иерархия** Unity используйте средство поиска для поиска объекта **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="312d8-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="312d8-233">Дважды щелкните объект **holoComm_screen_mesh** , чтобы просмотреть его в **сцене**.</span><span class="sxs-lookup"><span data-stu-id="312d8-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="312d8-234">Это контрольное значение-космонавтам, которое будет отвечать на команды Voice.</span><span class="sxs-lookup"><span data-stu-id="312d8-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="312d8-235">На панели **инспектора** выберите компонент **источник речевого ввода (скрипт)** .</span><span class="sxs-lookup"><span data-stu-id="312d8-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="312d8-236">Разверните раздел **Ключевые слова** , чтобы просмотреть поддерживаемую голосовую команду: **Open Communicator**.</span><span class="sxs-lookup"><span data-stu-id="312d8-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="312d8-237">Щелкните шестеренки справа, а затем выберите **изменить скрипт**.</span><span class="sxs-lookup"><span data-stu-id="312d8-237">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="312d8-238">Изучите **SpeechInputSource.CS** , чтобы понять, как она использует **кэйвордрекогнизер** для добавления речевых команд.</span><span class="sxs-lookup"><span data-stu-id="312d8-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="312d8-239">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="312d8-239">Build and Deploy</span></span>

* <span data-ttu-id="312d8-240">В Unity используйте **параметры сборки File >** для перестроения приложения.</span><span class="sxs-lookup"><span data-stu-id="312d8-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="312d8-241">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="312d8-241">Open the **App** folder.</span></span>
* <span data-ttu-id="312d8-242">Откройте **решение Моделексплорер Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="312d8-242">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="312d8-243">(Если вы уже создали и развернули этот проект в Visual Studio во время настройки, то можете открыть этот экземпляр VS и нажать кнопку "перезагрузить все" при появлении соответствующего запроса).</span><span class="sxs-lookup"><span data-stu-id="312d8-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="312d8-244">В Visual Studio щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="312d8-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="312d8-245">После того как приложение будет развернуто в HoloLens, закройте поле вписать с помощью жеста [касания](gaze-and-commit.md#composite-gestures) .</span><span class="sxs-lookup"><span data-stu-id="312d8-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="312d8-246">Взгляните на контрольное значение-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="312d8-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="312d8-247">Если контрольное значение находится в фокусе, убедитесь, что курсор меняется на микрофон.</span><span class="sxs-lookup"><span data-stu-id="312d8-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="312d8-248">Это дает отзыв о том, что приложение прослушивает голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="312d8-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="312d8-249">Убедитесь, что в контрольном списке отображается подсказка.</span><span class="sxs-lookup"><span data-stu-id="312d8-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="312d8-250">Это помогает пользователям обнаружить команду *Open Communicator* .</span><span class="sxs-lookup"><span data-stu-id="312d8-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="312d8-251">Пока облаками в контрольном списке, скажите *"открыть Communicator"* , чтобы открыть панель Communicator.</span><span class="sxs-lookup"><span data-stu-id="312d8-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="312d8-252">Глава 2. подтверждение</span><span class="sxs-lookup"><span data-stu-id="312d8-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="312d8-253">Задачи</span><span class="sxs-lookup"><span data-stu-id="312d8-253">Objectives</span></span>

* <span data-ttu-id="312d8-254">Запишите сообщение, используя ввод с микрофона.</span><span class="sxs-lookup"><span data-stu-id="312d8-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="312d8-255">Отправьте отзыв пользователю о том, что приложение ожидает передачи голоса.</span><span class="sxs-lookup"><span data-stu-id="312d8-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="312d8-256">Для записи приложения с микрофона необходимо объявить возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="312d8-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="312d8-257">Это делается для тех, у вас уже есть входные данные в MR 212, но не забывайте об этом с учетом собственных проектов.</span><span class="sxs-lookup"><span data-stu-id="312d8-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="312d8-258">В редакторе Unity перейдите к параметрам проигрывателя, перейдя к разделу "изменение параметров проекта > > Player".</span><span class="sxs-lookup"><span data-stu-id="312d8-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="312d8-259">Щелкните вкладку "универсальная платформа Windows".</span><span class="sxs-lookup"><span data-stu-id="312d8-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="312d8-260">В разделе "Параметры публикации > возможности" проверьте возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="312d8-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="312d8-261">Инструкция</span><span class="sxs-lookup"><span data-stu-id="312d8-261">Instructions</span></span>

* <span data-ttu-id="312d8-262">Убедитесь, что на панели **Иерархия** Unity выбран объект **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="312d8-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="312d8-263">На панели **инспектора** найдите компонент **-космонавтам Watch (скрипт)** .</span><span class="sxs-lookup"><span data-stu-id="312d8-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="312d8-264">Щелкните маленький куб, заданный в качестве значения свойства **Communicator prefab** .</span><span class="sxs-lookup"><span data-stu-id="312d8-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="312d8-265">На панели « **проект** » **Communicator** prefab теперь должен иметь фокус.</span><span class="sxs-lookup"><span data-stu-id="312d8-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="312d8-266">Щелкните **Communicator** prefab на панели **проект** , чтобы просмотреть его компоненты в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="312d8-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="312d8-267">Взгляните на компонент **диспетчера микрофонов (script)** . Это позволит нам записывать голоса пользователя.</span><span class="sxs-lookup"><span data-stu-id="312d8-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="312d8-268">Обратите внимание, что объект **Communicator** имеет компонент **обработчика речевого ввода (script)** для ответа на команду **Отправить сообщение** .</span><span class="sxs-lookup"><span data-stu-id="312d8-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="312d8-269">Взгляните на компонент **Communicator (script)** и дважды щелкните сценарий, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="312d8-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="312d8-270">Communicator.cs отвечает за установку соответствующих состояний кнопки на устройстве Communicator.</span><span class="sxs-lookup"><span data-stu-id="312d8-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="312d8-271">Это позволит нашим пользователям записывать сообщение, воспроизводить его и отправить сообщение в-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="312d8-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="312d8-272">Он также запускает и останавливает анимированную волновую форму для подтверждения пользователю о том, что речь заключалась.</span><span class="sxs-lookup"><span data-stu-id="312d8-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="312d8-273">В **Communicator.CS**удалите следующие строки (81 и 82) из метода **Start** .</span><span class="sxs-lookup"><span data-stu-id="312d8-273">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="312d8-274">Это приведет к включению кнопки "запись" в Communicator.</span><span class="sxs-lookup"><span data-stu-id="312d8-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="312d8-275">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="312d8-275">Build and Deploy</span></span>

* <span data-ttu-id="312d8-276">В Visual Studio перестройте приложение и разверните его на устройстве.</span><span class="sxs-lookup"><span data-stu-id="312d8-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="312d8-277">Взгляните на контрольное значение-космонавтам и скажите *"открыть Communicator"* , чтобы отобразить Communicator.</span><span class="sxs-lookup"><span data-stu-id="312d8-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="312d8-278">Нажмите кнопку **записи** (микрофон), чтобы начать запись сообщения текстовом для-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="312d8-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="312d8-279">Начните говорить и убедитесь, что анимация Wave воспроизводится на Communicator, что позволяет отправить отзыв пользователю о том, что речь идет о своей речи.</span><span class="sxs-lookup"><span data-stu-id="312d8-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="312d8-280">Нажмите кнопку **остановить** (левый квадрат) и убедитесь, что анимация Wave не выполняется.</span><span class="sxs-lookup"><span data-stu-id="312d8-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="312d8-281">Нажмите кнопку **воспроизведения** (правый треугольник), чтобы воспроизвести записанное сообщение и услышать его на устройстве.</span><span class="sxs-lookup"><span data-stu-id="312d8-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="312d8-282">Нажмите кнопку " **прерывать** " (правый прямоугольник), чтобы прерывать воспроизведение записанного сообщения.</span><span class="sxs-lookup"><span data-stu-id="312d8-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="312d8-283">Скажите *"отправить сообщение"* , чтобы закрыть Communicator и получить ответ "полученное сообщение" от-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="312d8-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="312d8-284">Глава 3. Основные сведения и распознаватель диктофона</span><span class="sxs-lookup"><span data-stu-id="312d8-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="312d8-285">Задачи</span><span class="sxs-lookup"><span data-stu-id="312d8-285">Objectives</span></span>

* <span data-ttu-id="312d8-286">Используйте распознаватель диктофона для преобразования речи пользователя в текст.</span><span class="sxs-lookup"><span data-stu-id="312d8-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="312d8-287">Отображение гипотетического и окончательного результатов распознавателя диктовки в Communicator.</span><span class="sxs-lookup"><span data-stu-id="312d8-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="312d8-288">В этой главе мы будем использовать распознаватель диктофона для создания сообщения для-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="312d8-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="312d8-289">При использовании распознавателя диктовки Помните, что:</span><span class="sxs-lookup"><span data-stu-id="312d8-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="312d8-290">Для работы распознавателя диктофона необходимо подключение к WiFi.</span><span class="sxs-lookup"><span data-stu-id="312d8-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="312d8-291">Время ожидания происходит по истечении заданного периода времени.</span><span class="sxs-lookup"><span data-stu-id="312d8-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="312d8-292">Существует два времени ожидания, которые следует учитывать:</span><span class="sxs-lookup"><span data-stu-id="312d8-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="312d8-293">Если распознаватель запускается и не слышит звук в течение первых пяти секунд, время ожидания истечет.</span><span class="sxs-lookup"><span data-stu-id="312d8-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="312d8-294">Если распознаватель предоставил результат, а затем слышит бездействия в течение двадцати секунд, время ожидания истечет.</span><span class="sxs-lookup"><span data-stu-id="312d8-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="312d8-295">В каждый момент времени может выполняться только один тип распознавателя (ключевое слово или Диктовка).</span><span class="sxs-lookup"><span data-stu-id="312d8-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="312d8-296">Для записи приложения с микрофона необходимо объявить возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="312d8-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="312d8-297">Это делается для тех, у вас уже есть входные данные в MR 212, но не забывайте об этом с учетом собственных проектов.</span><span class="sxs-lookup"><span data-stu-id="312d8-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="312d8-298">В редакторе Unity перейдите к параметрам проигрывателя, перейдя к разделу "изменение параметров проекта > > Player".</span><span class="sxs-lookup"><span data-stu-id="312d8-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="312d8-299">Щелкните вкладку "универсальная платформа Windows".</span><span class="sxs-lookup"><span data-stu-id="312d8-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="312d8-300">В разделе "Параметры публикации > возможности" проверьте возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="312d8-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="312d8-301">Инструкция</span><span class="sxs-lookup"><span data-stu-id="312d8-301">Instructions</span></span>

<span data-ttu-id="312d8-302">Мы будем изменять **MicrophoneManager.CS** для использования распознавателя диктофона.</span><span class="sxs-lookup"><span data-stu-id="312d8-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="312d8-303">Вот что мы добавим:</span><span class="sxs-lookup"><span data-stu-id="312d8-303">This is what we'll add:</span></span>

1. <span data-ttu-id="312d8-304">При нажатии **кнопки записи** мы начнем **диктатионрекогнизер**.</span><span class="sxs-lookup"><span data-stu-id="312d8-304">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="312d8-305">Показывает **гипотезу** об понятии диктатионрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="312d8-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="312d8-306">Заблокируйте **результаты** того, что диктатионрекогнизер понимает.</span><span class="sxs-lookup"><span data-stu-id="312d8-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="312d8-307">Проверьте время ожидания от Диктатионрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="312d8-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="312d8-308">После нажатия **кнопки "прерывать"** или истечения времени ожидания в сеансе MIC следует **Отключить диктатионрекогнизер**.</span><span class="sxs-lookup"><span data-stu-id="312d8-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="312d8-309">Перезапустите **кэйвордрекогнизер**, который будет прослушивать команду **отправки сообщения** .</span><span class="sxs-lookup"><span data-stu-id="312d8-309">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="312d8-310">Начнем.</span><span class="sxs-lookup"><span data-stu-id="312d8-310">Let's get started.</span></span> <span data-ttu-id="312d8-311">Выполните все упражнения кода для 3. a в **MicrophoneManager.CS**или скопируйте и вставьте готовый код ниже:</span><span class="sxs-lookup"><span data-stu-id="312d8-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="312d8-312">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="312d8-312">Build and Deploy</span></span>

* <span data-ttu-id="312d8-313">Перестройте в Visual Studio и разверните его на устройстве.</span><span class="sxs-lookup"><span data-stu-id="312d8-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="312d8-314">Отклонить поле вписать с помощью жеста касания.</span><span class="sxs-lookup"><span data-stu-id="312d8-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="312d8-315">Взгляните на контрольное значение-космонавтам и скажите *"открыть Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="312d8-315">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="312d8-316">Нажмите кнопку **запись** (микрофон), чтобы записать сообщение.</span><span class="sxs-lookup"><span data-stu-id="312d8-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="312d8-317">Начните говорить.</span><span class="sxs-lookup"><span data-stu-id="312d8-317">Start speaking.</span></span> <span data-ttu-id="312d8-318">**Распознаватель диктовки** будет интерпретировать ваш речевой ввод и показывать гипотетическую текст в Communicator.</span><span class="sxs-lookup"><span data-stu-id="312d8-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="312d8-319">Попробуйте сказать *"отправить сообщение"* во время записи сообщения.</span><span class="sxs-lookup"><span data-stu-id="312d8-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="312d8-320">Обратите внимание, что **распознаватель ключевых слов** не отвечает, так как **распознаватель диктовки** все еще активен.</span><span class="sxs-lookup"><span data-stu-id="312d8-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="312d8-321">Подождите несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="312d8-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="312d8-322">Следите за тем, как распознаватель диктовки завершает свою гипотезу и показывает окончательный результат.</span><span class="sxs-lookup"><span data-stu-id="312d8-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="312d8-323">Начните говорить, а затем приостановитесь на 20 секунд.</span><span class="sxs-lookup"><span data-stu-id="312d8-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="312d8-324">Это приведет к превышению времени ожидания **распознавателя диктофона** .</span><span class="sxs-lookup"><span data-stu-id="312d8-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="312d8-325">Обратите внимание, что после превышения времени ожидания **распознаватель ключевых слов** снова включается.</span><span class="sxs-lookup"><span data-stu-id="312d8-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="312d8-326">Теперь Communicator будет отвечать на команды Voice.</span><span class="sxs-lookup"><span data-stu-id="312d8-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="312d8-327">Скажите *"отправить сообщение"* , чтобы отправить сообщение в-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="312d8-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="312d8-328">Глава 4-распознаватель грамматики</span><span class="sxs-lookup"><span data-stu-id="312d8-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="312d8-329">Задачи</span><span class="sxs-lookup"><span data-stu-id="312d8-329">Objectives</span></span>

* <span data-ttu-id="312d8-330">Используйте распознаватель грамматики для распознавания речи пользователя в соответствии с уточнением или спецификацией распознавания речи, файлом.</span><span class="sxs-lookup"><span data-stu-id="312d8-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="312d8-331">Для записи приложения с микрофона необходимо объявить возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="312d8-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="312d8-332">Это делается для тех, у вас уже есть входные данные в MR 212, но не забывайте об этом с учетом собственных проектов.</span><span class="sxs-lookup"><span data-stu-id="312d8-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="312d8-333">В редакторе Unity перейдите к параметрам проигрывателя, перейдя к разделу "изменение параметров проекта > > Player".</span><span class="sxs-lookup"><span data-stu-id="312d8-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="312d8-334">Щелкните вкладку "универсальная платформа Windows".</span><span class="sxs-lookup"><span data-stu-id="312d8-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="312d8-335">В разделе "Параметры публикации > возможности" проверьте возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="312d8-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="312d8-336">Инструкция</span><span class="sxs-lookup"><span data-stu-id="312d8-336">Instructions</span></span>

1. <span data-ttu-id="312d8-337">На панели **Иерархия** найдите **Jetpack_Center** и выберите его.</span><span class="sxs-lookup"><span data-stu-id="312d8-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="312d8-338">Найдите сценарий **действия тагалонг** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="312d8-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="312d8-339">Щелкните маленький круг справа от **объекта, чтобы добавить тег** в поле.</span><span class="sxs-lookup"><span data-stu-id="312d8-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="312d8-340">В появившемся окне найдите **сргстулбокс** и выберите его из списка.</span><span class="sxs-lookup"><span data-stu-id="312d8-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="312d8-341">Взгляните на файл **сргсколор. XML** в папке **стреамингассетс** .</span><span class="sxs-lookup"><span data-stu-id="312d8-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="312d8-342">Спецификацию модели SRGS можно найти на веб-сайте W3C [здесь](https://www.w3.org/TR/speech-grammar/).</span><span class="sxs-lookup"><span data-stu-id="312d8-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="312d8-343">В нашем файле SRGS есть три типа правил:</span><span class="sxs-lookup"><span data-stu-id="312d8-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="312d8-344">Правило, которое позволяет сказать один цвет из списка из двенадцати цветов.</span><span class="sxs-lookup"><span data-stu-id="312d8-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="312d8-345">Три правила, которые ожидают сочетание правила цвета и одной из трех фигур.</span><span class="sxs-lookup"><span data-stu-id="312d8-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="312d8-346">Корневое правило Колорчусер, которое прослушивает любое сочетание трех правил "цвет + форма".</span><span class="sxs-lookup"><span data-stu-id="312d8-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="312d8-347">Эти фигуры можно сказать в любом порядке и в любой сумме от одного до трех.</span><span class="sxs-lookup"><span data-stu-id="312d8-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="312d8-348">Это единственное правило, которое прослушивается, так как оно указано в качестве корневого правила в начале файла в первом &lt;грамматической&gt; тега.</span><span class="sxs-lookup"><span data-stu-id="312d8-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="312d8-349">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="312d8-349">Build and Deploy</span></span>

* <span data-ttu-id="312d8-350">Перестройте приложение в Unity, а затем выполните сборку и развертывание из Visual Studio, чтобы поработать с приложением в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="312d8-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="312d8-351">Отклонить поле вписать с помощью жеста касания.</span><span class="sxs-lookup"><span data-stu-id="312d8-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="312d8-352">Взгляните на Jetpack-космонавтам и выполните жест касания.</span><span class="sxs-lookup"><span data-stu-id="312d8-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="312d8-353">Начните говорить.</span><span class="sxs-lookup"><span data-stu-id="312d8-353">Start speaking.</span></span> <span data-ttu-id="312d8-354">**Распознаватель грамматики** будет интерпретировать речь и изменить цвета фигур на основе распознавания.</span><span class="sxs-lookup"><span data-stu-id="312d8-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="312d8-355">Пример команды: "синий круг, желтый квадрат".</span><span class="sxs-lookup"><span data-stu-id="312d8-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="312d8-356">Выполните еще один жест касания, чтобы закрыть панель элементов.</span><span class="sxs-lookup"><span data-stu-id="312d8-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="312d8-357">Конец</span><span class="sxs-lookup"><span data-stu-id="312d8-357">The End</span></span>

<span data-ttu-id="312d8-358">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="312d8-358">Congratulations!</span></span> <span data-ttu-id="312d8-359">Теперь вы выполнили **Ввод MR 212: Voice**.</span><span class="sxs-lookup"><span data-stu-id="312d8-359">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="312d8-360">Вы узнаете об отделах речи и запретах на команды Voice.</span><span class="sxs-lookup"><span data-stu-id="312d8-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="312d8-361">Вы узнали, как использовались подсказки, чтобы пользователи могли знать о голосовых командах.</span><span class="sxs-lookup"><span data-stu-id="312d8-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="312d8-362">Вы видели несколько типов отзывов, используемых для подтверждения того, что речь пользователя познакомились.</span><span class="sxs-lookup"><span data-stu-id="312d8-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="312d8-363">Вы знаете, как переключаться между распознавателем ключевых слов и распознавателем диктовки и как эти две функции понимают и обрабатывают ваш речевой ввод.</span><span class="sxs-lookup"><span data-stu-id="312d8-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="312d8-364">Вы узнали, как использовать файл SRGS и распознаватель грамматики для распознавания речи в приложении.</span><span class="sxs-lookup"><span data-stu-id="312d8-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
