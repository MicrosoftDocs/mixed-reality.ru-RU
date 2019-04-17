---
title: Входные данные MR 211 - жестов
description: Выполнения данного кода пошагового руководства, с помощью Unity, Visual Studio и HoloLens Дополнительные сведения о концепции жест.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, учебник, жестов
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603384"
---
>[!NOTE]
><span data-ttu-id="0cadc-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="0cadc-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0cadc-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="0cadc-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0cadc-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0cadc-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0cadc-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="0cadc-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0cadc-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0cadc-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0cadc-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="0cadc-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="0cadc-110">Входные данные MR 211: Жест</span><span class="sxs-lookup"><span data-stu-id="0cadc-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="0cadc-111">[Жесты](gestures.md) превратить намерение пользователя в действия.</span><span class="sxs-lookup"><span data-stu-id="0cadc-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="0cadc-112">С помощью жестов пользователи могут взаимодействовать с голограммы.</span><span class="sxs-lookup"><span data-stu-id="0cadc-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="0cadc-113">В рамках этого курса вы узнаете как отслеживать руки пользователя, реагировать на ввод данных пользователем и отзывов для пользователя зависимости в наличии, состоянии и расположении.</span><span class="sxs-lookup"><span data-stu-id="0cadc-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="0cadc-114">В [101 основы MR](holograms-101.md), мы использовали жеста простой air касания для взаимодействия с нашей голограммы.</span><span class="sxs-lookup"><span data-stu-id="0cadc-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="0cadc-115">Теперь мы за жест жест касания и изучение новых концепций, чтобы:</span><span class="sxs-lookup"><span data-stu-id="0cadc-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="0cadc-116">Обнаружить при наличии пользователя отслеживается и обеспечивают отзыв для пользователя.</span><span class="sxs-lookup"><span data-stu-id="0cadc-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="0cadc-117">Для изменения наш голограммы выполните жест навигации.</span><span class="sxs-lookup"><span data-stu-id="0cadc-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="0cadc-118">Оставить отзыв, при наличии пользователя выходят за пределы представления.</span><span class="sxs-lookup"><span data-stu-id="0cadc-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="0cadc-119">Позволяет разрешить пользователям перемещать голограммы разработчикам события манипуляции.</span><span class="sxs-lookup"><span data-stu-id="0cadc-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="0cadc-120">В этом курсе мы вернемся к проекта Unity **обозревателя моделей**, который мы создали [210 ввода MR](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="0cadc-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="0cadc-121">Наши friend-космонавты, годится возвращается в том, чтобы помочь нам в наши исследования этих новых концепций жест.</span><span class="sxs-lookup"><span data-stu-id="0cadc-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0cadc-122">Видео, внедренных в каждой главы ниже были записаны с использованием более старой версии Unity и смешанной реальности Toolkit.</span><span class="sxs-lookup"><span data-stu-id="0cadc-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="0cadc-123">Хотя пошаговые инструкции и точной и актуальной, может появиться скрипты и визуальные элементы в соответствующих видео, становятся недействительными.</span><span class="sxs-lookup"><span data-stu-id="0cadc-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="0cadc-124">Видеоролики остаются включены перемешаны и поскольку рассматриваются основные понятия по-прежнему применяются.</span><span class="sxs-lookup"><span data-stu-id="0cadc-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="0cadc-125">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="0cadc-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0cadc-126">Курс</span><span class="sxs-lookup"><span data-stu-id="0cadc-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0cadc-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0cadc-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0cadc-128"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="0cadc-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0cadc-129">Входные данные MR 211: Жест</span><span class="sxs-lookup"><span data-stu-id="0cadc-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="0cadc-130">✔️</span><span class="sxs-lookup"><span data-stu-id="0cadc-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0cadc-131">✔️</span><span class="sxs-lookup"><span data-stu-id="0cadc-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0cadc-132">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="0cadc-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0cadc-133">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="0cadc-133">Prerequisites</span></span>

* <span data-ttu-id="0cadc-134">ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0cadc-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="0cadc-135">Основные C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="0cadc-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="0cadc-136">Необходимо завершить [101 основы MR](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="0cadc-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="0cadc-137">Необходимо завершить [210 ввода MR](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="0cadc-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="0cadc-138">Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="0cadc-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="0cadc-139">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="0cadc-139">Project files</span></span>

* <span data-ttu-id="0cadc-140">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) требуемые для проекта.</span><span class="sxs-lookup"><span data-stu-id="0cadc-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="0cadc-141"> Требуется компонент Unity 2017.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="0cadc-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="0cadc-142">Удаление архива файлы рабочего стола или других легко положения.</span><span class="sxs-lookup"><span data-stu-id="0cadc-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="0cadc-143">Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="0cadc-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="0cadc-144">Список ошибок и примечания</span><span class="sxs-lookup"><span data-stu-id="0cadc-144">Errata and Notes</span></span>

* <span data-ttu-id="0cadc-145">«Включить только мой код» необходимо отключить (*unchecked*) в Visual Studio в разделе Сервис -> Параметры -> Отладка для точки останова в коде.</span><span class="sxs-lookup"><span data-stu-id="0cadc-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="0cadc-146">Глава 0 — Установка Unity</span><span class="sxs-lookup"><span data-stu-id="0cadc-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="0cadc-147">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0cadc-147">Instructions</span></span>

1. <span data-ttu-id="0cadc-148">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="0cadc-148">Start Unity.</span></span>
2. <span data-ttu-id="0cadc-149">Выберите **откройте**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-149">Select **Open**.</span></span>
3. <span data-ttu-id="0cadc-150">Перейдите к **жест** папку вы ранее не архивные.</span><span class="sxs-lookup"><span data-stu-id="0cadc-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="0cadc-151">Найдите и выберите **запуск**/**обозревателя моделей** папки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="0cadc-152">Нажмите кнопку **Выбор папки** кнопки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="0cadc-153">В **проекта** панели, разверните узел **сцены** папки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="0cadc-154">Дважды щелкните **ModelExplorer** сцены, чтобы загрузить его в Unity.</span><span class="sxs-lookup"><span data-stu-id="0cadc-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="0cadc-155">Сборка</span><span class="sxs-lookup"><span data-stu-id="0cadc-155">Building</span></span>

1. <span data-ttu-id="0cadc-156">В Unity, выберите **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="0cadc-157">Если **сцены/ModelExplorer** не указан в **построения кадром**, нажмите кнопку **добавьте откройте сцены** Добавление сцены.</span><span class="sxs-lookup"><span data-stu-id="0cadc-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="0cadc-158">Если вы разрабатываете специально для HoloLens, задайте **целевое устройство** для **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="0cadc-159">В противном случае оставьте его на **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="0cadc-160">Убедитесь, **построение** присваивается **D3D** и **SDK** имеет значение **самую новую установленную** (которое должно быть SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="0cadc-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="0cadc-161">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-161">Click **Build**.</span></span>
6. <span data-ttu-id="0cadc-162">Создание **новую папку** с именем «Приложение».</span><span class="sxs-lookup"><span data-stu-id="0cadc-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="0cadc-163">Одним щелчком мыши **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="0cadc-164">Нажмите клавишу **Выбор папки** и Unity начнется построение проекта для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0cadc-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="0cadc-165">По завершении Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="0cadc-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="0cadc-166">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="0cadc-167">Откройте **решение ModelExplorer в Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="0cadc-168">Если развертывание HoloLens:</span><span class="sxs-lookup"><span data-stu-id="0cadc-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="0cadc-169">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x86**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="0cadc-170">Щелкните стрелку раскрывающегося списка рядом с кнопкой на локальном компьютере и выберите **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="0cadc-171">Введите **IP-адрес устройства HoloLens** и задайте режим проверки подлинности **универсальный (незашифрованный протокол)**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="0cadc-172">Нажмите кнопку **выберите**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-172">Click **Select**.</span></span> <span data-ttu-id="0cadc-173">Если вы не знаете IP-адрес устройства, найдите в **параметры > сеть и Интернет > Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="0cadc-174">В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="0cadc-175">Если это при первом развертывании к устройству, необходимо будет [свяжите его с помощью Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="0cadc-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="0cadc-176">Когда приложение будет развернуто, закрыть **Fitbox** с **выберите жест**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="0cadc-177">Если развертывание иммерсивных гарнитура:</span><span class="sxs-lookup"><span data-stu-id="0cadc-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="0cadc-178">С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x64**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="0cadc-179">Убедитесь, что целевой объект развертывания присваивается **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="0cadc-180">В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="0cadc-181">Когда приложение будет развернуто, закрыть **Fitbox** , потянув триггер на контроллере движения.</span><span class="sxs-lookup"><span data-stu-id="0cadc-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="0cadc-182">Вы можете заметить некоторые ошибки красным на панели ошибок Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0cadc-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="0cadc-183">Можно безопасно пропускать их.</span><span class="sxs-lookup"><span data-stu-id="0cadc-183">It is safe to ignore them.</span></span> <span data-ttu-id="0cadc-184">Переключиться на панели «Вывод», чтобы просмотреть фактический ход выполнения сборки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="0cadc-185">Ошибки в панели «Вывод» потребуется внести исправление (наиболее часто они являются вызвана неправильным действием в скрипте).</span><span class="sxs-lookup"><span data-stu-id="0cadc-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="0cadc-186">Глава 1 - руки обнаружил обратной связи</span><span class="sxs-lookup"><span data-stu-id="0cadc-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="0cadc-187">Цели</span><span class="sxs-lookup"><span data-stu-id="0cadc-187">Objectives</span></span>

* <span data-ttu-id="0cadc-188">Подписка для передачи событий отслеживания.</span><span class="sxs-lookup"><span data-stu-id="0cadc-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="0cadc-189">Использование курсоров отображаются пользователи, при наличии отслеживается.</span><span class="sxs-lookup"><span data-stu-id="0cadc-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cadc-190">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0cadc-190">Instructions</span></span>

* <span data-ttu-id="0cadc-191">В **иерархии** панели, разверните узел **InputManager** объекта.</span><span class="sxs-lookup"><span data-stu-id="0cadc-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="0cadc-192">Найдите и выберите **GesturesInput** объекта.</span><span class="sxs-lookup"><span data-stu-id="0cadc-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="0cadc-193">**InteractionInputSource.cs** скрипт выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="0cadc-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="0cadc-194">Подписывается на события InteractionSourceDetected и InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="0cadc-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="0cadc-195">Задает состояние HandDetected.</span><span class="sxs-lookup"><span data-stu-id="0cadc-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="0cadc-196">Отменяет подписку на события InteractionSourceDetected и InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="0cadc-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="0cadc-197">Далее мы выполним обновление наших курсора из [210 ввода MR](holograms-210.md) в один из них обратной связи в зависимости от действий пользователя.</span><span class="sxs-lookup"><span data-stu-id="0cadc-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="0cadc-198">В **иерархии** панели, выберите **курсор** объекта и удалите его.</span><span class="sxs-lookup"><span data-stu-id="0cadc-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="0cadc-199">В **проекта** панели, поиск **CursorWithFeedback** и перетащите его в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="0cadc-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="0cadc-200">Щелкните **InputManager** в **иерархии** панели, а затем перетащите **CursorWithFeedback** объекта из **иерархии** в В InputManager **SimpleSinglePointerSelector** **курсор** поле в нижней части **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="0cadc-201">Щелкните **CursorWithFeedback** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="0cadc-202">В **инспектор** панели, разверните узел **данные о состоянии курсора** на **объект курсора** скрипта.</span><span class="sxs-lookup"><span data-stu-id="0cadc-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="0cadc-203">**Данные о состоянии курсора** работает следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0cadc-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="0cadc-204">Любой **наблюдения** состояние означает, что обнаружен не вручную пользователь просто всматриваться.</span><span class="sxs-lookup"><span data-stu-id="0cadc-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="0cadc-205">Любой **взаимодействие** состояние означает, что Рука или контроллер обнаружил.</span><span class="sxs-lookup"><span data-stu-id="0cadc-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="0cadc-206">Любой **при наведении указателя мыши** состояние означает, что пользователь просматривает голограмма.</span><span class="sxs-lookup"><span data-stu-id="0cadc-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="0cadc-207">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="0cadc-207">Build and Deploy</span></span>

* <span data-ttu-id="0cadc-208">В Unity, использовать **файл > Параметры сборки** для перестроения приложения.</span><span class="sxs-lookup"><span data-stu-id="0cadc-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="0cadc-209">Откройте **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-209">Open the **App** folder.</span></span>
* <span data-ttu-id="0cadc-210">Если он не открыт, откройте **решение Visual Studio ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="0cadc-211">(Если вы уже сборки и развертывания этого проекта в Visual Studio во время установки, затем можно открыть этот экземпляр VS и нажмите кнопку «Обновить все» при появлении запроса).</span><span class="sxs-lookup"><span data-stu-id="0cadc-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="0cadc-212">В Visual Studio щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0cadc-213">После развертывания приложения для HoloLens, закройте fitbox, с помощью жестов жест касания.</span><span class="sxs-lookup"><span data-stu-id="0cadc-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="0cadc-214">Переместите свои силы в представлении и укажите палец неба, чтобы начать отслеживание вручную.</span><span class="sxs-lookup"><span data-stu-id="0cadc-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="0cadc-215">Переместить свои силы влево, вправо, вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="0cadc-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="0cadc-216">Посмотрите, как изменится курсор, после обнаружения и затем потеряна из представления свои силы.</span><span class="sxs-lookup"><span data-stu-id="0cadc-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="0cadc-217">Если вы используете иммерсивных гарнитура, придется подключаться и отключаться от вашего контроллера.</span><span class="sxs-lookup"><span data-stu-id="0cadc-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="0cadc-218">Ваши отзывы становится менее интересными на устройстве иммерсивных как подключенного контроллера всегда будет «доступно».</span><span class="sxs-lookup"><span data-stu-id="0cadc-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="0cadc-219">Глава 2 - навигации</span><span class="sxs-lookup"><span data-stu-id="0cadc-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="0cadc-220">Цели</span><span class="sxs-lookup"><span data-stu-id="0cadc-220">Objectives</span></span>

* <span data-ttu-id="0cadc-221">Для изменения космонавты выполните жест событий навигации.</span><span class="sxs-lookup"><span data-stu-id="0cadc-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cadc-222">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0cadc-222">Instructions</span></span>

<span data-ttu-id="0cadc-223">Чтобы использовать жесты для навигации в наше приложение, мы собираемся изменить **GestureAction.cs** поворачивают объекты, когда происходит жест навигации.</span><span class="sxs-lookup"><span data-stu-id="0cadc-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="0cadc-224">Кроме того мы добавим отзыв курсор, отображаемый при навигации.</span><span class="sxs-lookup"><span data-stu-id="0cadc-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="0cadc-225">В **иерархии** панели, разверните узел **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="0cadc-226">В **голограммы** папки, найти **ScrollFeedback** активов.</span><span class="sxs-lookup"><span data-stu-id="0cadc-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="0cadc-227">Перетаскивание **ScrollFeedback** prefab на **CursorWithFeedback** GameObject в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="0cadc-228">Щелкните **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="0cadc-229">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="0cadc-230">В меню, введите в поле поиска **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="0cadc-231">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0cadc-231">Select the search result.</span></span>
7. <span data-ttu-id="0cadc-232">Перетаскивание **ScrollFeedback** объекта из **иерархии** на **прокрутки обнаружил игровой объект** свойство в **курсоров**компонент в **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="0cadc-233">В **иерархии** панели, выберите **AstroMan** объекта.</span><span class="sxs-lookup"><span data-stu-id="0cadc-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="0cadc-234">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="0cadc-235">В меню, введите в поле поиска **действие жеста**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="0cadc-236">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0cadc-236">Select the search result.</span></span>

<span data-ttu-id="0cadc-237">Затем откройте **GestureAction.cs** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0cadc-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="0cadc-238">При кодировании Упражнение 2.c, измените сценарий, выполнив следующие действия:</span><span class="sxs-lookup"><span data-stu-id="0cadc-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="0cadc-239">**Поворот AstroMan** при каждом выполнении жеста навигации.</span><span class="sxs-lookup"><span data-stu-id="0cadc-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="0cadc-240">Вычислить **rotationFactor** для управления угол поворота, применяются к объекту.</span><span class="sxs-lookup"><span data-stu-id="0cadc-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="0cadc-241">**Повернуть объект** вокруг оси y, когда пользователь перемещает их наличии влево или вправо.</span><span class="sxs-lookup"><span data-stu-id="0cadc-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="0cadc-242">Полный кода выполняет 2.c в скрипте или замените код готового решения ниже:</span><span class="sxs-lookup"><span data-stu-id="0cadc-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="0cadc-243">Вы заметите, что другие события навигации уже заполнены некоторые сведения.</span><span class="sxs-lookup"><span data-stu-id="0cadc-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="0cadc-244">Мы отправляем GameObject на набора средств в InputSystem модальное стека, так что пользователю не нужно Сконцентрируйтесь на космонавты, после начала поворота.</span><span class="sxs-lookup"><span data-stu-id="0cadc-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="0cadc-245">Соответственно мы pop GameObject из стека, после завершения жест.</span><span class="sxs-lookup"><span data-stu-id="0cadc-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="0cadc-246">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="0cadc-246">Build and Deploy</span></span>

1. <span data-ttu-id="0cadc-247">Перестройте приложение в Unity, построение и развертывание из Visual Studio для запуска в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0cadc-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="0cadc-248">Помощи в космонавты, две стрелки должен появляться в разные стороны от курсора.</span><span class="sxs-lookup"><span data-stu-id="0cadc-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="0cadc-249">Этот новый визуальный элемент указывает, что могут быть повернуты-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="0cadc-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="0cadc-250">Поместить свои силы в готовности место (вытянутым указательным пальцем направлена sky), начнется HoloLens, отслеживания свои силы.</span><span class="sxs-lookup"><span data-stu-id="0cadc-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="0cadc-251">Чтобы повернуть космонавты, снизить палец в позицию жестом сжатия и переместите свои силы влево или вправо, чтобы активировать NavigationX жест.</span><span class="sxs-lookup"><span data-stu-id="0cadc-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="0cadc-252">Глава 3 - инструкции вручную</span><span class="sxs-lookup"><span data-stu-id="0cadc-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="0cadc-253">Цели</span><span class="sxs-lookup"><span data-stu-id="0cadc-253">Objectives</span></span>

* <span data-ttu-id="0cadc-254">Используйте **вручную Оценка рекомендации** для прогнозирования, при наличии отслеживания будут потеряны.</span><span class="sxs-lookup"><span data-stu-id="0cadc-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="0cadc-255">Укажите **отзывы о курсор** для отображения, при наличии пользователя истекает камеры края представления.</span><span class="sxs-lookup"><span data-stu-id="0cadc-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cadc-256">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0cadc-256">Instructions</span></span>

1. <span data-ttu-id="0cadc-257">В **иерархии** панели, выберите **CursorWithFeedback** объекта.</span><span class="sxs-lookup"><span data-stu-id="0cadc-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="0cadc-258">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="0cadc-259">В меню, введите в поле поиска **наличии рекомендации**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="0cadc-260">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0cadc-260">Select the search result.</span></span>
4. <span data-ttu-id="0cadc-261">В **проекта** панели **голограммы** папки, найти **HandGuidanceFeedback** активов.</span><span class="sxs-lookup"><span data-stu-id="0cadc-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="0cadc-262">Перетаскивание **HandGuidanceFeedback** активов на **наличии рекомендации индикатор** свойства в **инспектор** панели.</span><span class="sxs-lookup"><span data-stu-id="0cadc-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="0cadc-263">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="0cadc-263">Build and Deploy</span></span>

* <span data-ttu-id="0cadc-264">Перестройте приложение в Unity, построение и развертывание из Visual Studio, чтобы оценить приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0cadc-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="0cadc-265">Видимым вашей руке и вызывать палец для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="0cadc-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="0cadc-266">Запустить смену-космонавты, годится с жестом навигации (сжатие палец и бегунок друг с другом).</span><span class="sxs-lookup"><span data-stu-id="0cadc-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="0cadc-267">Переместите свои силы далеко влево, вправо, вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="0cadc-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="0cadc-268">Как свои силы незадолго до края рамки жестов, рядом с полем появится стрелка курсора, предупреждающее о том, что Рука отслеживания будут потеряны.</span><span class="sxs-lookup"><span data-stu-id="0cadc-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="0cadc-269">Стрелка указывает направление, в котором для перемещения свои силы во избежание отслеживания Предотвращение потери.</span><span class="sxs-lookup"><span data-stu-id="0cadc-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="0cadc-270">Глава 4 – манипуляции</span><span class="sxs-lookup"><span data-stu-id="0cadc-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="0cadc-271">Цели</span><span class="sxs-lookup"><span data-stu-id="0cadc-271">Objectives</span></span>

* <span data-ttu-id="0cadc-272">Позволяет переносить-космонавты, годится с рук события манипуляции.</span><span class="sxs-lookup"><span data-stu-id="0cadc-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="0cadc-273">Оставить отзыв о курсор, чтобы позволить пользователю узнать, когда манипуляция может использоваться.</span><span class="sxs-lookup"><span data-stu-id="0cadc-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cadc-274">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0cadc-274">Instructions</span></span>

<span data-ttu-id="0cadc-275">GestureManager.cs и AstronautManager.cs позволит нам сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0cadc-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="0cadc-276">Используйте ключевое слово речи "**переместить космонавты**" для включения **манипуляции** жестов и "**повернуть космонавты**" отключить их.</span><span class="sxs-lookup"><span data-stu-id="0cadc-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="0cadc-277">Переключиться в режим реагирование на них **распознаватель жестов манипуляции**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="0cadc-278">Начнем.</span><span class="sxs-lookup"><span data-stu-id="0cadc-278">Let's get started.</span></span>

1. <span data-ttu-id="0cadc-279">В **иерархии** панели, создать новый пустой объект GameObject.</span><span class="sxs-lookup"><span data-stu-id="0cadc-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="0cadc-280">Назовите его "**AstronautManager**«.</span><span class="sxs-lookup"><span data-stu-id="0cadc-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="0cadc-281">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="0cadc-282">В меню, введите в поле поиска **-космонавты, годится Manager**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="0cadc-283">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0cadc-283">Select the search result.</span></span>
4. <span data-ttu-id="0cadc-284">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="0cadc-285">В меню, введите в поле поиска **источника ввода речи**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="0cadc-286">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0cadc-286">Select the search result.</span></span>

<span data-ttu-id="0cadc-287">Теперь мы добавим команды речи, необходимые для управления взаимодействия состоянием-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="0cadc-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="0cadc-288">Разверните **ключевые слова** статьи **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="0cadc-289">Нажмите кнопку **+** на стороне справа, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="0cadc-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="0cadc-290">Введите ключевое слово как **переместить космонавты**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="0cadc-291">Вы можете добавить ярлык ключ, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="0cadc-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="0cadc-292">Нажмите кнопку **+** на стороне справа, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="0cadc-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="0cadc-293">Введите ключевое слово как **повернуть космонавты**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="0cadc-294">Вы можете добавить ярлык ключ, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="0cadc-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="0cadc-295">Соответствующий код обработчика можно найти в **GestureAction.cs**в **ISpeechHandler.OnSpeechKeywordRecognized** обработчика.</span><span class="sxs-lookup"><span data-stu-id="0cadc-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Как настройки источника входных данных речи для главы 4](images/holograms211-speech.png)

<span data-ttu-id="0cadc-297">Далее мы будем Настройка отзыв манипуляции над курсором.</span><span class="sxs-lookup"><span data-stu-id="0cadc-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="0cadc-298">В **проекта** панели **голограммы** папки, найти **PathingFeedback** активов.</span><span class="sxs-lookup"><span data-stu-id="0cadc-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="0cadc-299">Перетаскивание **PathingFeedback** prefab на **CursorWithFeedback** объекта в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="0cadc-300">В **иерархии** панели, щелкнув **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="0cadc-301">Перетаскивание **PathingFeedback** объекта из **иерархии** на **путь обнаружил игровой объект** свойство в **курсоров**компонент в **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="0cadc-302">Теперь нам нужно добавить код, чтобы **GestureAction.cs** возможным следующее:</span><span class="sxs-lookup"><span data-stu-id="0cadc-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="0cadc-303">Добавьте код для **IManipulationHandler.OnManipulationUpdated** функцию, которая будет переместить космонавты при **манипуляции** обнаружении жеста.</span><span class="sxs-lookup"><span data-stu-id="0cadc-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="0cadc-304">Вычислить **вектор перемещения** для определения, где следует перемещать космонавты, в основе стороны позиции.</span><span class="sxs-lookup"><span data-stu-id="0cadc-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="0cadc-305">**Переместить** -космонавты, годится на новое место.</span><span class="sxs-lookup"><span data-stu-id="0cadc-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="0cadc-306">Полный кодирования Упражнение 4.a в **GestureAction.cs**, или используйте наши готового решения ниже:</span><span class="sxs-lookup"><span data-stu-id="0cadc-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="0cadc-307">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="0cadc-307">Build and Deploy</span></span>

* <span data-ttu-id="0cadc-308">Перестроить в Unity, построение и развертывание из Visual Studio, чтобы запустить приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0cadc-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="0cadc-309">Переместите свои силы перед HoloLens и вызывать палец, что его можно отслеживать.</span><span class="sxs-lookup"><span data-stu-id="0cadc-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="0cadc-310">Сосредоточиться курсор над-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="0cadc-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="0cadc-311">Предположим, «Переместить космонавты», чтобы переместить-космонавты, годится с жестом манипуляции.</span><span class="sxs-lookup"><span data-stu-id="0cadc-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="0cadc-312">Четыре стрелки появится этого курсора, чтобы указать, что программа теперь будут отвечать на события манипуляции.</span><span class="sxs-lookup"><span data-stu-id="0cadc-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="0cadc-313">Уменьшите палец вниз, чтобы ваши бегунка и остаться pinched друг с другом.</span><span class="sxs-lookup"><span data-stu-id="0cadc-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="0cadc-314">При перемещении вашей руке вокруг космонавты переместит слишком (это манипуляции).</span><span class="sxs-lookup"><span data-stu-id="0cadc-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="0cadc-315">Вызывать палец для остановки обработки-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="0cadc-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="0cadc-316">Примечание. Если вы не ответите «Переместить космонавты» перед перемещением вашей руке, то жест навигации будет использоваться вместо этого.</span><span class="sxs-lookup"><span data-stu-id="0cadc-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="0cadc-317">Произнесите «Поворот космонавты», чтобы вернуть Поворотный состояние.</span><span class="sxs-lookup"><span data-stu-id="0cadc-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="0cadc-318">Глава 5 - расширение модели</span><span class="sxs-lookup"><span data-stu-id="0cadc-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="0cadc-319">Цели</span><span class="sxs-lookup"><span data-stu-id="0cadc-319">Objectives</span></span>

* <span data-ttu-id="0cadc-320">Разверните модели-космонавты, годится на несколько, более мелкие части, что пользователь может взаимодействовать с.</span><span class="sxs-lookup"><span data-stu-id="0cadc-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="0cadc-321">Переместите каждый фрагмент, по отдельности с помощью жестов перехода и обработки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cadc-322">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0cadc-322">Instructions</span></span>

<span data-ttu-id="0cadc-323">В этом разделе мы предстоит выполнить следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="0cadc-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="0cadc-324">Добавить новое ключевое слово "**разверните модель**" для расширения модели-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="0cadc-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="0cadc-325">Добавить новое ключевое слово "**сброса модели**" для возвращения модели в своем первоначальном виде.</span><span class="sxs-lookup"><span data-stu-id="0cadc-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="0cadc-326">Мы будем сделать, добавив два дополнительных ключевых слова источника входных данных преобразования речи в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="0cadc-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="0cadc-327">Мы также покажем еще один способ обработки события распознавания.</span><span class="sxs-lookup"><span data-stu-id="0cadc-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="0cadc-328">Снова щелкните **AstronautManager** в **инспектор** и разверните **ключевые слова** статьи **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="0cadc-329">Нажмите кнопку **+** на стороне справа, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="0cadc-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="0cadc-330">Введите ключевое слово как **расширяют модель**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="0cadc-331">Вы можете добавить ярлык ключ, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="0cadc-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="0cadc-332">Нажмите кнопку **+** на стороне справа, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="0cadc-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="0cadc-333">Введите ключевое слово как **сброса модели**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="0cadc-334">Вы можете добавить ярлык ключ, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="0cadc-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="0cadc-335">В **инспектор** панели, щелкните **добавить компонент** кнопки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="0cadc-336">В меню, введите в поле поиска **обработчика ввода речи**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="0cadc-337">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="0cadc-337">Select the search result.</span></span>
8. <span data-ttu-id="0cadc-338">Проверьте **является глобальной прослушивателя**, поскольку необходимо, чтобы эти команды заработали независимо от того, GameObject мы сосредоточили.</span><span class="sxs-lookup"><span data-stu-id="0cadc-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="0cadc-339">Нажмите кнопку **+** и выберите **разверните модель** из раскрывающегося списка ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="0cadc-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="0cadc-340">Нажмите кнопку **+** ответа и перетащите **AstronautManager** из **иерархии** в **None (объект)** поле.</span><span class="sxs-lookup"><span data-stu-id="0cadc-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="0cadc-341">Теперь щелкните **функции нет** раскрывающемся списке выберите **AstronautManager**, затем **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="0cadc-342">Нажмите кнопку обработчика ввода речи **+** и выберите **сброса модели** из раскрывающегося списка ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="0cadc-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="0cadc-343">Нажмите кнопку **+** ответа и перетащите **AstronautManager** из **иерархии** в **None (объект)** поле.</span><span class="sxs-lookup"><span data-stu-id="0cadc-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="0cadc-344">Теперь щелкните **функции нет** раскрывающемся списке выберите **AstronautManager**, затем **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Как настроить источник ввода речи и обработчик для главы 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="0cadc-346">Создание и развертывание</span><span class="sxs-lookup"><span data-stu-id="0cadc-346">Build and Deploy</span></span>

* <span data-ttu-id="0cadc-347">Попробуйте!</span><span class="sxs-lookup"><span data-stu-id="0cadc-347">Try it!</span></span> <span data-ttu-id="0cadc-348">Создавайте и развертывайте приложения для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0cadc-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="0cadc-349">Скажем **разверните модель** для космонавты развернутой модели см. в разделе.</span><span class="sxs-lookup"><span data-stu-id="0cadc-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="0cadc-350">Используйте **навигации** для поворота отдельные части масти-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="0cadc-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="0cadc-351">Скажем **переместить космонавты** , а затем использовать **манипуляции** для перемещения отдельных блоков масти-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="0cadc-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="0cadc-352">Сказать **повернуть космонавты** для поворота элементы еще раз.</span><span class="sxs-lookup"><span data-stu-id="0cadc-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="0cadc-353">Скажем **сброса модели** для возврата в исходную форму-космонавты, годится.</span><span class="sxs-lookup"><span data-stu-id="0cadc-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="0cadc-354">Конец</span><span class="sxs-lookup"><span data-stu-id="0cadc-354">The End</span></span>

<span data-ttu-id="0cadc-355">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="0cadc-355">Congratulations!</span></span> <span data-ttu-id="0cadc-356">Вы завершили **211 MR входные данные: Жест**.</span><span class="sxs-lookup"><span data-stu-id="0cadc-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="0cadc-357">Вы знаете, как для обнаружения и реагирования для передачи событий отслеживания, перехода и обработки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="0cadc-358">Необходимо понимать разницу между жесты перехода и обработки.</span><span class="sxs-lookup"><span data-stu-id="0cadc-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="0cadc-359">Вы знаете, как изменить курсор для предоставления визуальной обратной связи при обнаружении руки, при наличии будут потеряны, а если объект поддерживает различные взаимодействия (vs навигации манипуляции).</span><span class="sxs-lookup"><span data-stu-id="0cadc-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
