---
title: Входные данные MR 212 - Voice
description: Выполнения данного кода пошагового руководства, с помощью Unity, Visual Studio и HoloLens Дополнительные сведения о концепции голоса.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, учебник, голоса
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598926"
---
>[!NOTE]
><span data-ttu-id="12ee6-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="12ee6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="12ee6-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="12ee6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="12ee6-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="12ee6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="12ee6-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="12ee6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="12ee6-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="12ee6-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="12ee6-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="12ee6-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="12ee6-110">Входные данные MR 212: Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="12ee6-110">MR Input 212: Voice</span></span>

<span data-ttu-id="12ee6-111">[Голоса](voice-input.md) дает нам еще один способ взаимодействия с нашей голограммы.</span><span class="sxs-lookup"><span data-stu-id="12ee6-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="12ee6-112">Голосовые команды работают в это очень естественный и простой способ.</span><span class="sxs-lookup"><span data-stu-id="12ee6-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="12ee6-113">Разработка вашей голосовые команды, чтобы они были.</span><span class="sxs-lookup"><span data-stu-id="12ee6-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="12ee6-114">Естественное</span><span class="sxs-lookup"><span data-stu-id="12ee6-114">Natural</span></span>
* <span data-ttu-id="12ee6-115">Легко запомнить</span><span class="sxs-lookup"><span data-stu-id="12ee6-115">Easy to remember</span></span>
* <span data-ttu-id="12ee6-116">Контекста, соответствующего</span><span class="sxs-lookup"><span data-stu-id="12ee6-116">Context appropriate</span></span>
* <span data-ttu-id="12ee6-117">Достаточной степени отличаются от других параметров, в том же контексте</span><span class="sxs-lookup"><span data-stu-id="12ee6-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="12ee6-118">В [101 основы MR](holograms-101.md), мы использовали KeywordRecognizer создавать две простые голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="12ee6-119">В 212 MR входных данных, мы Погрузитесь глубже и узнайте, как:</span><span class="sxs-lookup"><span data-stu-id="12ee6-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="12ee6-120">Голосовые команды разработки, которые оптимизированы для распознавания речи HoloLens.</span><span class="sxs-lookup"><span data-stu-id="12ee6-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="12ee6-121">Оповестить пользователя голоса, какие команды доступны.</span><span class="sxs-lookup"><span data-stu-id="12ee6-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="12ee6-122">Подтверждаю, что мы слышали пользователя голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="12ee6-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="12ee6-123">Сведения о возможностях, пользователю о том, используя распознаватель диктовки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="12ee6-124">Используйте распознаватель грамматики для прослушивания на основе файла SRGS или спецификации грамматики распознавания речи, команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="12ee6-125">В этом курсе мы вернемся к обозреватель модели, который мы создали в [210 ввода MR](holograms-210.md) и [211 ввода MR](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="12ee6-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="12ee6-126">Видео, внедренных в каждой главы ниже были записаны с использованием более старой версии Unity и смешанной реальности Toolkit.</span><span class="sxs-lookup"><span data-stu-id="12ee6-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="12ee6-127">Хотя пошаговые инструкции и точной и актуальной, может появиться скрипты и визуальные элементы в соответствующих видео, становятся недействительными.</span><span class="sxs-lookup"><span data-stu-id="12ee6-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="12ee6-128">Видеоролики остаются включены перемешаны и поскольку рассматриваются основные понятия по-прежнему применяются.</span><span class="sxs-lookup"><span data-stu-id="12ee6-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="12ee6-129">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="12ee6-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="12ee6-130">Курс</span><span class="sxs-lookup"><span data-stu-id="12ee6-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="12ee6-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="12ee6-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="12ee6-132"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="12ee6-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="12ee6-133">Входные данные MR 212: Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="12ee6-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="12ee6-134">✔️</span><span class="sxs-lookup"><span data-stu-id="12ee6-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="12ee6-135">✔️</span><span class="sxs-lookup"><span data-stu-id="12ee6-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="12ee6-136">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="12ee6-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="12ee6-137">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="12ee6-137">Prerequisites</span></span>

* <span data-ttu-id="12ee6-138">ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="12ee6-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="12ee6-139">Основные C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="12ee6-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="12ee6-140">Необходимо завершить [101 основы MR](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="12ee6-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="12ee6-141">Необходимо завершить [210 ввода MR](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="12ee6-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="12ee6-142">Необходимо завершить [211 ввода MR](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="12ee6-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="12ee6-143">Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="12ee6-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="12ee6-144">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="12ee6-144">Project files</span></span>

* <span data-ttu-id="12ee6-145">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) требуемые для проекта.</span><span class="sxs-lookup"><span data-stu-id="12ee6-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="12ee6-146">Требуется компонент Unity 2017.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="12ee6-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="12ee6-147">Удаление архива файлы рабочего стола или других легко положения.</span><span class="sxs-lookup"><span data-stu-id="12ee6-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="12ee6-148">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="12ee6-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="12ee6-149">Список ошибок и примечания</span><span class="sxs-lookup"><span data-stu-id="12ee6-149">Errata and Notes</span></span>

* <span data-ttu-id="12ee6-150">«Включить только мой код» необходимо отключить (*unchecked*) в Visual Studio в разделе Сервис -> Параметры -> Отладка для точки останова в коде.</span><span class="sxs-lookup"><span data-stu-id="12ee6-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="12ee6-151">Программа установки Unity</span><span class="sxs-lookup"><span data-stu-id="12ee6-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="12ee6-152">Инструкция</span><span class="sxs-lookup"><span data-stu-id="12ee6-152">Instructions</span></span>

1. <span data-ttu-id="12ee6-153">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="12ee6-153">Start Unity.</span></span>
2. <span data-ttu-id="12ee6-154">Выберите **откройте**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-154">Select **Open**.</span></span>
3. <span data-ttu-id="12ee6-155">Перейдите к **HolographicAcademy-голограммы-212-Voice** папку вы ранее не архивные.</span><span class="sxs-lookup"><span data-stu-id="12ee6-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="12ee6-156">Найдите и выберите **запуск**/**обозревателя моделей** папки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="12ee6-157">Нажмите кнопку **Выбор папки** кнопки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="12ee6-158">В **проекта** панели, разверните узел **сцены** папки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="12ee6-159">Дважды щелкните **ModelExplorer** сцены, чтобы загрузить его в Unity.</span><span class="sxs-lookup"><span data-stu-id="12ee6-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="12ee6-160">Сборка</span><span class="sxs-lookup"><span data-stu-id="12ee6-160">Building</span></span>

1. <span data-ttu-id="12ee6-161">В Unity, выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="12ee6-162">Если **сцены/ModelExplorer** не указан в **построения кадром**, нажмите кнопку **добавьте откройте сцены** Добавление сцены.</span><span class="sxs-lookup"><span data-stu-id="12ee6-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="12ee6-163">Если вы разрабатываете специально для HoloLens, задайте **целевое устройство** для **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="12ee6-164">В противном случае оставьте его на **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="12ee6-165">Убедитесь, **построение** присваивается **D3D** и **SDK** имеет значение **самую новую установленную** (которое должно быть SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="12ee6-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="12ee6-166">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-166">Click **Build**.</span></span>
6. <span data-ttu-id="12ee6-167">Создание **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="12ee6-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="12ee6-168">Одним щелчком мыши **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="12ee6-169">Нажмите клавишу **Выбор папки** и Unity начнется построение проекта для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12ee6-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="12ee6-170">По завершении Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="12ee6-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="12ee6-171">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="12ee6-172">Откройте **решение ModelExplorer в Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="12ee6-173">Если развертывание HoloLens:</span><span class="sxs-lookup"><span data-stu-id="12ee6-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="12ee6-174">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x86**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="12ee6-175">Щелкните стрелку раскрывающегося списка рядом с кнопкой на локальном компьютере и выберите **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="12ee6-176">Введите **IP-адрес устройства HoloLens** и задайте режим проверки подлинности **универсальный (незашифрованный протокол)**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="12ee6-177">Нажмите кнопку **выберите**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-177">Click **Select**.</span></span> <span data-ttu-id="12ee6-178">Если вы не знаете IP-адрес устройства, найдите в **параметры > сеть и Интернет > Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="12ee6-179">В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="12ee6-180">Если это при первом развертывании к устройству, необходимо будет [свяжите его с помощью Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="12ee6-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="12ee6-181">Когда приложение будет развернуто, закрыть **Fitbox** с **выберите жест**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="12ee6-182">Если развертывание иммерсивных гарнитура:</span><span class="sxs-lookup"><span data-stu-id="12ee6-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="12ee6-183">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x64**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="12ee6-184">Убедитесь, что целевой объект развертывания присваивается **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="12ee6-185">В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="12ee6-186">Когда приложение будет развернуто, закрыть **Fitbox** , потянув триггер на контроллере движения.</span><span class="sxs-lookup"><span data-stu-id="12ee6-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="12ee6-187">Вы можете заметить некоторые ошибки красным на панели ошибок Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12ee6-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="12ee6-188">Можно безопасно пропускать их.</span><span class="sxs-lookup"><span data-stu-id="12ee6-188">It is safe to ignore them.</span></span> <span data-ttu-id="12ee6-189">Переключиться на панели «Вывод», чтобы просмотреть фактический ход выполнения сборки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="12ee6-190">Ошибки в панели «Вывод» потребуется внести исправление (наиболее часто они являются вызвана неправильным действием в скрипте).</span><span class="sxs-lookup"><span data-stu-id="12ee6-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="12ee6-191">Глава 1 - Awareness</span><span class="sxs-lookup"><span data-stu-id="12ee6-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="12ee6-192">Цели</span><span class="sxs-lookup"><span data-stu-id="12ee6-192">Objectives</span></span>

* <span data-ttu-id="12ee6-193">Узнайте, **и запреты** голосовые команды разработки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="12ee6-194">Используйте **KeywordRecognizer** добавить взглядом на основе голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="12ee6-195">Оповестить пользователей о голосовых команд, с помощью курсора **отзывы**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="12ee6-196">Конструктор голосовых команд</span><span class="sxs-lookup"><span data-stu-id="12ee6-196">Voice Command Design</span></span>

<span data-ttu-id="12ee6-197">В этой главе вы узнаете о разработке голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="12ee6-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="12ee6-198">При создании голосовые команды:</span><span class="sxs-lookup"><span data-stu-id="12ee6-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="12ee6-199">DO</span><span class="sxs-lookup"><span data-stu-id="12ee6-199">DO</span></span>

* <span data-ttu-id="12ee6-200">Создайте краткую команд.</span><span class="sxs-lookup"><span data-stu-id="12ee6-200">Create concise commands.</span></span> <span data-ttu-id="12ee6-201">Вы не хотите использовать *«В этом видео текущего выбранного»*, так как эта команда не является кратким и легко нужно уделять внимание пользователем.</span><span class="sxs-lookup"><span data-stu-id="12ee6-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="12ee6-202">Вместо этого следует использовать: *«Воспроизвести видео»*, так как он очень четкий и имеет несколько слоги.</span><span class="sxs-lookup"><span data-stu-id="12ee6-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="12ee6-203">Используйте простой словаря.</span><span class="sxs-lookup"><span data-stu-id="12ee6-203">Use a simple vocabulary.</span></span> <span data-ttu-id="12ee6-204">Всегда пытаться использовать часто употребляемых слов и фраз, которые просты для пользователя для обнаружения и запомнить.</span><span class="sxs-lookup"><span data-stu-id="12ee6-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="12ee6-205">Например, если приложение должно было объект примечание, который может отобразить или скрыть из представления, не используется команда *«Показать панель»*, так как это редко используемый термин «таблицы».</span><span class="sxs-lookup"><span data-stu-id="12ee6-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="12ee6-206">Вместо этого выполнить команду: *«Показать заметки»*, чтобы отобразить Примечание в приложении.</span><span class="sxs-lookup"><span data-stu-id="12ee6-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="12ee6-207">Соблюдать единообразие.</span><span class="sxs-lookup"><span data-stu-id="12ee6-207">Be consistent.</span></span> <span data-ttu-id="12ee6-208">Голосовые команды должны поддерживать согласованность всего приложения.</span><span class="sxs-lookup"><span data-stu-id="12ee6-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="12ee6-209">Допустим, у вас есть два сцен в приложении и оба сцены быть кнопка для закрытия приложения.</span><span class="sxs-lookup"><span data-stu-id="12ee6-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="12ee6-210">Если первую сцену использовала команду *«Выход»* для активации кнопки, а второй сцены использовала команду *«Закрыть приложение»*, то пользователь будет крайне запутанным.</span><span class="sxs-lookup"><span data-stu-id="12ee6-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="12ee6-211">Если те же функциональные возможности сохраняется между сцены, затем ту же команду голосовой следует использовать для его запуска.</span><span class="sxs-lookup"><span data-stu-id="12ee6-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="12ee6-212">НЕ НАДО</span><span class="sxs-lookup"><span data-stu-id="12ee6-212">DON'T</span></span>

* <span data-ttu-id="12ee6-213">Используйте единый слог команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-213">Use single syllable commands.</span></span> <span data-ttu-id="12ee6-214">Например, при создании голосовых команд для воспроизведения видео, старайтесь не использовать простую команду *«Play»*, так как он является только единый слог и легко могут быть пропущены в системе.</span><span class="sxs-lookup"><span data-stu-id="12ee6-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="12ee6-215">Вместо этого следует использовать: *«Воспроизвести видео»*, так как он очень четкий и имеет несколько слоги.</span><span class="sxs-lookup"><span data-stu-id="12ee6-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="12ee6-216">Команды системы.</span><span class="sxs-lookup"><span data-stu-id="12ee6-216">Use system commands.</span></span> <span data-ttu-id="12ee6-217">*«Select»* команда зарезервировано системой для Активация события касания для выделенного объекта.</span><span class="sxs-lookup"><span data-stu-id="12ee6-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="12ee6-218">Не используйте *«Select»* команда в ключевое слово или фразу, как оно может не работать, как ожидается.</span><span class="sxs-lookup"><span data-stu-id="12ee6-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="12ee6-219">Например, если голосовые команды для выбора куба в приложении была *«Выберите куб»*, но пользователь смотрел сферы при их распространенная команды, то вместо этого будет выбрано сферы.</span><span class="sxs-lookup"><span data-stu-id="12ee6-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="12ee6-220">Кроме того, приложения на панели команд, включена ли голосовая связь.</span><span class="sxs-lookup"><span data-stu-id="12ee6-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="12ee6-221">Не используйте следующие команды речи в представлении CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="12ee6-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="12ee6-222">Вернуться</span><span class="sxs-lookup"><span data-stu-id="12ee6-222">Go Back</span></span>
    2. <span data-ttu-id="12ee6-223">Средство прокрутки</span><span class="sxs-lookup"><span data-stu-id="12ee6-223">Scroll Tool</span></span>
    3. <span data-ttu-id="12ee6-224">Средство масштабирования</span><span class="sxs-lookup"><span data-stu-id="12ee6-224">Zoom Tool</span></span>
    4. <span data-ttu-id="12ee6-225">Инструмент «перетаскивание»</span><span class="sxs-lookup"><span data-stu-id="12ee6-225">Drag Tool</span></span>
    5. <span data-ttu-id="12ee6-226">Регулировка</span><span class="sxs-lookup"><span data-stu-id="12ee6-226">Adjust</span></span>
    6. <span data-ttu-id="12ee6-227">Удалить</span><span class="sxs-lookup"><span data-stu-id="12ee6-227">Remove</span></span>
* <span data-ttu-id="12ee6-228">Используйте аналогичные звуков.</span><span class="sxs-lookup"><span data-stu-id="12ee6-228">Use similar sounds.</span></span> <span data-ttu-id="12ee6-229">Следует избегать использования голосовых команд, взять.</span><span class="sxs-lookup"><span data-stu-id="12ee6-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="12ee6-230">Если у вас есть приложение о покупках поддерживавших *«Показать Store»* и *«Больше»* как голосовые команды, то необходимо отключить одну из команд, пока другой использовался.</span><span class="sxs-lookup"><span data-stu-id="12ee6-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="12ee6-231">Например, можно использовать *«Показать Store»* кнопку для открытия хранилища, а затем отключить этой команды, когда было отображено хранилище, чтобы *«Больше»* команда может быть использована для просмотра.</span><span class="sxs-lookup"><span data-stu-id="12ee6-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="12ee6-232">Инструкция</span><span class="sxs-lookup"><span data-stu-id="12ee6-232">Instructions</span></span>

* <span data-ttu-id="12ee6-233">В Unity **иерархии** панели, воспользуйтесь средством поиска для поиска **holoComm_screen_mesh** объекта.</span><span class="sxs-lookup"><span data-stu-id="12ee6-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="12ee6-234">Дважды щелкните **holoComm_screen_mesh** объект для просмотра его в **сцены**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="12ee6-235">Это watch космонавты, который ответит на наших голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="12ee6-236">В **инспектор** панели, найдите **источника ввода речи (скрипт)** компонента.</span><span class="sxs-lookup"><span data-stu-id="12ee6-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="12ee6-237">Разверните **ключевые слова** раздел, чтобы просмотреть поддерживаемые голосовых команд: **Откройте Communicator**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="12ee6-238">Щелкните значок шестеренки справа, а затем выберите **изменить скрипт**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="12ee6-239">Изучите **SpeechInputSource.cs** чтобы понять, как он использует **KeywordRecognizer** добавить голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="12ee6-240">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="12ee6-240">Build and Deploy</span></span>

* <span data-ttu-id="12ee6-241">В Unity, использовать **файл > Параметры сборки** для перестроения приложения.</span><span class="sxs-lookup"><span data-stu-id="12ee6-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="12ee6-242">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-242">Open the **App** folder.</span></span>
* <span data-ttu-id="12ee6-243">Откройте **решение ModelExplorer в Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="12ee6-244">(Если вы уже сборки и развертывания этого проекта в Visual Studio во время установки, затем можно открыть этот экземпляр VS и нажмите кнопку «Обновить все» при появлении запроса).</span><span class="sxs-lookup"><span data-stu-id="12ee6-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="12ee6-245">В Visual Studio щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="12ee6-246">После развертывания приложения для HoloLens, закрыть окна соответствия с помощью [жест касания](gestures.md#air-tap) жест.</span><span class="sxs-lookup"><span data-stu-id="12ee6-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="12ee6-247">Помощи в космонавты контрольных значений.</span><span class="sxs-lookup"><span data-stu-id="12ee6-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="12ee6-248">Когда часами в фокусе, убедитесь, что вид курсора меняется в микрофон.</span><span class="sxs-lookup"><span data-stu-id="12ee6-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="12ee6-249">Это обеспечивает обратную связь, приложение ожидает передачи данных для голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="12ee6-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="12ee6-250">Убедитесь, что появляется подсказка в watch.</span><span class="sxs-lookup"><span data-stu-id="12ee6-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="12ee6-251">Это позволяет пользователям обнаруживать *«Open Communicator»* команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="12ee6-252">При gazing в часы, скажем *«Откройте Communicator»* Открытие панели communicator.</span><span class="sxs-lookup"><span data-stu-id="12ee6-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="12ee6-253">Глава 2 - подтверждения</span><span class="sxs-lookup"><span data-stu-id="12ee6-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="12ee6-254">Цели</span><span class="sxs-lookup"><span data-stu-id="12ee6-254">Objectives</span></span>

* <span data-ttu-id="12ee6-255">Запишите сообщения с помощью ввода от микрофона.</span><span class="sxs-lookup"><span data-stu-id="12ee6-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="12ee6-256">Отправить отзыв для пользователя, которого приложение ожидает передачи голоса.</span><span class="sxs-lookup"><span data-stu-id="12ee6-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="12ee6-257">**"Микрофон"** возможность должны объявляться для приложения для записи с микрофона.</span><span class="sxs-lookup"><span data-stu-id="12ee6-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="12ee6-258">Для этого вам уже в 212 MR входных данных, но имейте это в виду для ваших собственных проектов.</span><span class="sxs-lookup"><span data-stu-id="12ee6-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="12ee6-259">В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»</span><span class="sxs-lookup"><span data-stu-id="12ee6-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="12ee6-260">Перейдите на вкладку «Универсальной платформы Windows»</span><span class="sxs-lookup"><span data-stu-id="12ee6-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="12ee6-261">В разделе «Возможности публикации > Параметры» установите флажок **"микрофон"** возможностей</span><span class="sxs-lookup"><span data-stu-id="12ee6-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="12ee6-262">Инструкция</span><span class="sxs-lookup"><span data-stu-id="12ee6-262">Instructions</span></span>

* <span data-ttu-id="12ee6-263">В Unity **иерархии** панели, убедитесь, что **holoComm_screen_mesh** выбран объект.</span><span class="sxs-lookup"><span data-stu-id="12ee6-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="12ee6-264">В **инспектор** панели, найти **-космонавты, годится Watch (скрипт)** компонента.</span><span class="sxs-lookup"><span data-stu-id="12ee6-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="12ee6-265">Щелкните Мелкая "," синий куба, который имеет значение для параметра **Communicator Prefab** свойство.</span><span class="sxs-lookup"><span data-stu-id="12ee6-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="12ee6-266">В **проекта** панели **Communicator** prefab теперь должны иметь фокус.</span><span class="sxs-lookup"><span data-stu-id="12ee6-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="12ee6-267">Щелкните **Communicator** prefab в **проекта** панели для просмотра его компонентов в **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="12ee6-268">Рассмотрим **Manager "микрофон" (сценарий)** компонента, это позволит нам записать голос пользователя.</span><span class="sxs-lookup"><span data-stu-id="12ee6-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="12ee6-269">Обратите внимание, что **Communicator** объект имеет **обработчик речи входных данных (скрипт)** компонент за реагирование на **Отправка сообщения** команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="12ee6-270">Рассмотрим **Communicator (скрипт)** компонента и дважды щелкните его, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12ee6-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="12ee6-271">Communicator.cs отвечает за настройку состояния соответствующие кнопки, communicator устройства.</span><span class="sxs-lookup"><span data-stu-id="12ee6-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="12ee6-272">Это позволит пользователям записывать сообщения, воспроизведите его и отправить сообщение-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="12ee6-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="12ee6-273">Он также будет запускать и останавливать форму анимированных wave для подтверждения для пользователя, их мнение.</span><span class="sxs-lookup"><span data-stu-id="12ee6-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="12ee6-274">В **Communicator.cs**, удалите следующие строки (81 и 82) из **запустить** метод.</span><span class="sxs-lookup"><span data-stu-id="12ee6-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="12ee6-275">Это позволит кнопки «Запись» на communicator.</span><span class="sxs-lookup"><span data-stu-id="12ee6-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="12ee6-276">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="12ee6-276">Build and Deploy</span></span>

* <span data-ttu-id="12ee6-277">В Visual Studio перестройте свое приложение и развернуть на устройстве.</span><span class="sxs-lookup"><span data-stu-id="12ee6-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="12ee6-278">Помощи в космонавты контрольных значений и сказать *«Open Communicator»* Показать communicator.</span><span class="sxs-lookup"><span data-stu-id="12ee6-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="12ee6-279">Нажмите клавишу **записи** кнопку (микрофон) для начала записи устные сообщение для-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="12ee6-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="12ee6-280">Начните говорить и убедитесь, что волна анимация воспроизводится на communicator, который предоставляет отзывы пользователю их мнение.</span><span class="sxs-lookup"><span data-stu-id="12ee6-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="12ee6-281">Нажмите клавишу **остановить** (левый квадрат) и убедитесь, что анимация wave останавливается.</span><span class="sxs-lookup"><span data-stu-id="12ee6-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="12ee6-282">Нажмите клавишу **воспроизведение** кнопку (Прямоугольный треугольник), чтобы воспроизвести записанные сообщения и получить ваш отзыв на устройстве.</span><span class="sxs-lookup"><span data-stu-id="12ee6-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="12ee6-283">Нажмите клавишу **остановить** кнопку (правом квадрат), чтобы остановить воспроизведение записанных сообщения.</span><span class="sxs-lookup"><span data-stu-id="12ee6-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="12ee6-284">Скажем *«Отправить сообщение»* закрыть communicator и получать ответ сообщение получено от-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="12ee6-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="12ee6-285">Глава 3 - основные сведения о и распознаватель диктовки</span><span class="sxs-lookup"><span data-stu-id="12ee6-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="12ee6-286">Цели</span><span class="sxs-lookup"><span data-stu-id="12ee6-286">Objectives</span></span>

* <span data-ttu-id="12ee6-287">Используйте распознаватель диктовки для преобразования пользователя речи в текст.</span><span class="sxs-lookup"><span data-stu-id="12ee6-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="12ee6-288">Показать распознаватель диктовки нулевой гипотезы и конечный результаты в communicator.</span><span class="sxs-lookup"><span data-stu-id="12ee6-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="12ee6-289">В этой главе мы будем использовать распознаватель диктовки для создания сообщения для-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="12ee6-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="12ee6-290">При использовании распознавателя диктовки, имейте в виду, что:</span><span class="sxs-lookup"><span data-stu-id="12ee6-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="12ee6-291">Вы должны быть подключены к Wi-Fi для распознавателя диктовки для работы.</span><span class="sxs-lookup"><span data-stu-id="12ee6-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="12ee6-292">Истекает время ожидания после заданного периода времени.</span><span class="sxs-lookup"><span data-stu-id="12ee6-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="12ee6-293">Существует два времени ожидания, которые следует учитывать:</span><span class="sxs-lookup"><span data-stu-id="12ee6-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="12ee6-294">Если распознаватель запускается не слышит аудио для первых пяти секунд, истечет.</span><span class="sxs-lookup"><span data-stu-id="12ee6-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="12ee6-295">Если распознаватель дала результат, но затем слышит бездействия в течение 20 секунд, время ожидания истекает.</span><span class="sxs-lookup"><span data-stu-id="12ee6-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="12ee6-296">Одновременно можно запустить только один тип распознавателя (ключевое слово или речевые сообщения).</span><span class="sxs-lookup"><span data-stu-id="12ee6-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="12ee6-297">**"Микрофон"** возможность должны объявляться для приложения для записи с микрофона.</span><span class="sxs-lookup"><span data-stu-id="12ee6-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="12ee6-298">Для этого вам уже в 212 MR входных данных, но имейте это в виду для ваших собственных проектов.</span><span class="sxs-lookup"><span data-stu-id="12ee6-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="12ee6-299">В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»</span><span class="sxs-lookup"><span data-stu-id="12ee6-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="12ee6-300">Перейдите на вкладку «Универсальной платформы Windows»</span><span class="sxs-lookup"><span data-stu-id="12ee6-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="12ee6-301">В разделе «Возможности публикации > Параметры» установите флажок **"микрофон"** возможностей</span><span class="sxs-lookup"><span data-stu-id="12ee6-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="12ee6-302">Инструкция</span><span class="sxs-lookup"><span data-stu-id="12ee6-302">Instructions</span></span>

<span data-ttu-id="12ee6-303">Мы собираемся изменить **MicrophoneManager.cs** использовать распознаватель диктовки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="12ee6-304">Это, мы добавим:</span><span class="sxs-lookup"><span data-stu-id="12ee6-304">This is what we'll add:</span></span>

1. <span data-ttu-id="12ee6-305">Когда **кнопку записи** является нажата, мы будем **запустить DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="12ee6-306">Показать **гипотезы** из DictationRecognizer понятны.</span><span class="sxs-lookup"><span data-stu-id="12ee6-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="12ee6-307">Блокировка в **результаты** из DictationRecognizer понятны.</span><span class="sxs-lookup"><span data-stu-id="12ee6-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="12ee6-308">Проверьте наличие времени ожидания из DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="12ee6-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="12ee6-309">Когда **"Остановить"** нажата, или время ожидания, сеанса mic **остановить DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="12ee6-310">Перезапустите **KeywordRecognizer**, который будет прослушивать **Отправка сообщения** команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="12ee6-311">Начнем.</span><span class="sxs-lookup"><span data-stu-id="12ee6-311">Let's get started.</span></span> <span data-ttu-id="12ee6-312">Завершить все упражнений по кодированию для 3.a в **MicrophoneManager.cs**, или скопируйте и вставьте код завершения, найти ниже:</span><span class="sxs-lookup"><span data-stu-id="12ee6-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="12ee6-313">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="12ee6-313">Build and Deploy</span></span>

* <span data-ttu-id="12ee6-314">В Visual Studio и разверните на ваше устройство.</span><span class="sxs-lookup"><span data-stu-id="12ee6-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="12ee6-315">Закройте окно соответствия с помощью жеста жест касания.</span><span class="sxs-lookup"><span data-stu-id="12ee6-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="12ee6-316">Помощи в космонавты контрольных значений и сказать *«Open Communicator»*.</span><span class="sxs-lookup"><span data-stu-id="12ee6-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="12ee6-317">Выберите **записи** кнопки (микрофон) для записи сообщения.</span><span class="sxs-lookup"><span data-stu-id="12ee6-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="12ee6-318">Начните говорить.</span><span class="sxs-lookup"><span data-stu-id="12ee6-318">Start speaking.</span></span> <span data-ttu-id="12ee6-319">**Распознаватель диктовки** будет интерпретировать речи и отображать текст нулевой гипотезы в communicator.</span><span class="sxs-lookup"><span data-stu-id="12ee6-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="12ee6-320">Попробуйте указать *«Отправить сообщение»* при записи сообщения.</span><span class="sxs-lookup"><span data-stu-id="12ee6-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="12ee6-321">Обратите внимание, что **распознаватель ключевое слово** не отвечает, так как **распознаватель диктовки** по-прежнему активна.</span><span class="sxs-lookup"><span data-stu-id="12ee6-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="12ee6-322">Остановите проговаривание на несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="12ee6-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="12ee6-323">Следите за диктовки распознаватель завершает его гипотезы и показан окончательный результат.</span><span class="sxs-lookup"><span data-stu-id="12ee6-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="12ee6-324">Начать разговор, а затем сделать паузу на 20 секунд.</span><span class="sxs-lookup"><span data-stu-id="12ee6-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="12ee6-325">Это приведет к **распознаватель диктовки** истечение времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="12ee6-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="12ee6-326">Обратите внимание, что **распознаватель ключевое слово** будет снова включена после выше времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="12ee6-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="12ee6-327">Communicator теперь будет отвечать на голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="12ee6-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="12ee6-328">Скажем *«Отправить сообщение»* для отправки сообщения-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="12ee6-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="12ee6-329">Глава 4 – грамматики распознавания</span><span class="sxs-lookup"><span data-stu-id="12ee6-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="12ee6-330">Цели</span><span class="sxs-lookup"><span data-stu-id="12ee6-330">Objectives</span></span>

* <span data-ttu-id="12ee6-331">Используйте распознаватель грамматику для распознавания речи пользователя в соответствии с файла SRGS или спецификации грамматики распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="12ee6-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="12ee6-332">**"Микрофон"** возможность должны объявляться для приложения для записи с микрофона.</span><span class="sxs-lookup"><span data-stu-id="12ee6-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="12ee6-333">Для этого вам уже в 212 MR входных данных, но имейте это в виду для ваших собственных проектов.</span><span class="sxs-lookup"><span data-stu-id="12ee6-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="12ee6-334">В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»</span><span class="sxs-lookup"><span data-stu-id="12ee6-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="12ee6-335">Перейдите на вкладку «Универсальной платформы Windows»</span><span class="sxs-lookup"><span data-stu-id="12ee6-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="12ee6-336">В разделе «Возможности публикации > Параметры» установите флажок **"микрофон"** возможностей</span><span class="sxs-lookup"><span data-stu-id="12ee6-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="12ee6-337">Инструкция</span><span class="sxs-lookup"><span data-stu-id="12ee6-337">Instructions</span></span>

1. <span data-ttu-id="12ee6-338">В **иерархии** панели, поиск **Jetpack_Center** и выберите его.</span><span class="sxs-lookup"><span data-stu-id="12ee6-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="12ee6-339">Найдите **свои действия** скрипта в **инспектор** панели.</span><span class="sxs-lookup"><span data-stu-id="12ee6-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="12ee6-340">Щелкните маленький кружок в правой части **объекта в тег вдоль** поля.</span><span class="sxs-lookup"><span data-stu-id="12ee6-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="12ee6-341">В открывшемся окне Поиск **SRGSToolbox** и выберите его из списка.</span><span class="sxs-lookup"><span data-stu-id="12ee6-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="12ee6-342">Взгляните на **SRGSColor.xml** файл **StreamingAssets** папки.</span><span class="sxs-lookup"><span data-stu-id="12ee6-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="12ee6-343">Спецификации SRGS разработки можно найти на веб-сайте W3C [здесь](https://www.w3.org/TR/speech-grammar/).</span><span class="sxs-lookup"><span data-stu-id="12ee6-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="12ee6-344">В наш файл SRGS у нас есть три типа правил:</span><span class="sxs-lookup"><span data-stu-id="12ee6-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="12ee6-345">Правило, которое позволяет вам сказать один цвет из списка двенадцать цветов.</span><span class="sxs-lookup"><span data-stu-id="12ee6-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="12ee6-346">Три правила, которые прослушивают сочетание правила цвета и одну из трех фигур.</span><span class="sxs-lookup"><span data-stu-id="12ee6-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="12ee6-347">Корневое правило colorChooser, который ожидает передачи любое сочетание трех правил «цвет + фигуры».</span><span class="sxs-lookup"><span data-stu-id="12ee6-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="12ee6-348">Фигуры можно сказать, что в любом порядке и в любой суммы от лишь одна всем трем.</span><span class="sxs-lookup"><span data-stu-id="12ee6-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="12ee6-349">Это единственное правило, которое будет отслеживаться, как оно указано в качестве корневого правила в верхней части файла исходную &lt;грамматики&gt; тега.</span><span class="sxs-lookup"><span data-stu-id="12ee6-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="12ee6-350">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="12ee6-350">Build and Deploy</span></span>

* <span data-ttu-id="12ee6-351">Перестройте приложение в Unity, а затем построить и развернуть из Visual Studio, чтобы оценить приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="12ee6-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="12ee6-352">Закройте окно соответствия с помощью жеста жест касания.</span><span class="sxs-lookup"><span data-stu-id="12ee6-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="12ee6-353">Помощи в jetpack космонавты и сделайте жест жест касания.</span><span class="sxs-lookup"><span data-stu-id="12ee6-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="12ee6-354">Начните говорить.</span><span class="sxs-lookup"><span data-stu-id="12ee6-354">Start speaking.</span></span> <span data-ttu-id="12ee6-355">**Грамматики распознавания** будет интерпретировать речи и изменить цвета фигуры, основаны на предположении.</span><span class="sxs-lookup"><span data-stu-id="12ee6-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="12ee6-356">Пример команды — «синий круг, Желтый квадрат».</span><span class="sxs-lookup"><span data-stu-id="12ee6-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="12ee6-357">Сделайте другой жест жест касания для закрытия панели элементов.</span><span class="sxs-lookup"><span data-stu-id="12ee6-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="12ee6-358">Конец</span><span class="sxs-lookup"><span data-stu-id="12ee6-358">The End</span></span>

<span data-ttu-id="12ee6-359">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="12ee6-359">Congratulations!</span></span> <span data-ttu-id="12ee6-360">Вы завершили **212 MR входные данные: Голосовые**.</span><span class="sxs-lookup"><span data-stu-id="12ee6-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="12ee6-361">Вы знаете, рекомендации и запреты голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="12ee6-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="12ee6-362">Вы узнали, как всплывающие подсказки были, применяемых в информировании пользователей голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="12ee6-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="12ee6-363">Вы видели несколько видов обратной связи, используется для подтверждения, что голос пользователя был слышали.</span><span class="sxs-lookup"><span data-stu-id="12ee6-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="12ee6-364">Вы знаете, как переключиться между распознаватель ключевое слово и распознаватель диктовки, а также как эти две возможности понимать и интерпретировать ваш голос.</span><span class="sxs-lookup"><span data-stu-id="12ee6-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="12ee6-365">Вы узнали, как использовать файл SRGS и распознаватель грамматику для распознавания речи в приложении.</span><span class="sxs-lookup"><span data-stu-id="12ee6-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
