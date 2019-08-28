---
title: MR и Azure 310 — обнаружение объектов
description: Пройдите этот курс, чтобы научиться обучить модель машинного обучения, а затем использовать обученную модель для распознавания похожих объектов и их позиций в реальном мире из приложения смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, пользовательское видение, обнаружение объектов, Смешанная реальность, Academy, Unity, учебник, API, hololens
ms.openlocfilehash: 71370db84a9b90b017e8d5fac0799a862883d046
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047219"
---
>[!NOTE]
><span data-ttu-id="0ae15-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="0ae15-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0ae15-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="0ae15-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0ae15-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0ae15-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0ae15-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="0ae15-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0ae15-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0ae15-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0ae15-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="0ae15-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="0ae15-110">MR и Azure 310: Обнаружение объектов</span><span class="sxs-lookup"><span data-stu-id="0ae15-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="0ae15-111">В этом курсе вы узнаете, как распознать пользовательское визуальное содержимое и его пространственное расположение в предоставленном образе, используя возможности Azure Пользовательское визуальное распознавание "обнаружение объектов" в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="0ae15-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="0ae15-112">Эта служба позволит обучить модель машинного обучения с помощью образов объектов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="0ae15-113">Затем вы будете использовать обученную модель для распознавания похожих объектов и приближения их расположения в реальном мире, как это обеспечивается видеозаписью камеры Microsoft HoloLens или камера подключается к ПК для использования в режиме погружения (VR).</span><span class="sxs-lookup"><span data-stu-id="0ae15-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![результат курса](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="0ae15-115">**Пользовательское визуальное распознавание Azure, обнаружение объектов** — это служба Майкрософт, которая позволяет разработчикам создавать пользовательские классификаторы изображений.</span><span class="sxs-lookup"><span data-stu-id="0ae15-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="0ae15-116">Эти классификаторы можно использовать с новыми образами для обнаружения объектов внутри этого нового изображения, предоставляя **границы рамки** в самом образе.</span><span class="sxs-lookup"><span data-stu-id="0ae15-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="0ae15-117">Служба предоставляет простой, простой в использовании веб-портал для упрощения этого процесса.</span><span class="sxs-lookup"><span data-stu-id="0ae15-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="0ae15-118">Дополнительные сведения см. по следующим ссылкам:</span><span class="sxs-lookup"><span data-stu-id="0ae15-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="0ae15-119">Страница Пользовательское визуальное распознавание Azure</span><span class="sxs-lookup"><span data-stu-id="0ae15-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="0ae15-120">Ограничения и квоты</span><span class="sxs-lookup"><span data-stu-id="0ae15-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="0ae15-121">После завершения этого курса у вас будет приложение смешанной реальности, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="0ae15-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="0ae15-122">Пользователь сможет Взгляните на объект , с которым они обучены с помощью пользовательская служба визуального распознавания Azure, обнаружения объектов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="0ae15-123">Пользователь будет использовать жест *касания* для записи изображения того, что они видят.</span><span class="sxs-lookup"><span data-stu-id="0ae15-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="0ae15-124">Приложение будет отправит образ в Пользовательская служба визуального распознавания Azure.</span><span class="sxs-lookup"><span data-stu-id="0ae15-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="0ae15-125">Будет получен ответ от службы, который будет отображать результат распознавания как текст в виде текста в мировом пространстве.</span><span class="sxs-lookup"><span data-stu-id="0ae15-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="0ae15-126">Это будет выполнено с помощью пространственного отслеживания Microsoft HoloLens, чтобы понять расположение распознанного объекта в мире, а затем использовать *тег* , связанный с тем, что обнаруживается на изображении, чтобы предоставить текст метки.</span><span class="sxs-lookup"><span data-stu-id="0ae15-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="0ae15-127">Курс также охватывает ручную загрузку изображений, Создание тегов и обучение службы, чтобы распознать различные объекты (в предоставленном примере — чашку), установив *границу* в рамках отправляемого изображения.</span><span class="sxs-lookup"><span data-stu-id="0ae15-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="0ae15-128">После создания и использования приложения разработчик должен вернуться к Пользовательская служба визуального распознавания Azure и определить прогнозы, выполненные службой, и определить, были ли они верными (с помощью тегов все пропущенные службы и Настройка *ограничивающих прямоугольников*).</span><span class="sxs-lookup"><span data-stu-id="0ae15-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="0ae15-129">Затем служба может быть переучена, что увеличит вероятность того, что она будет распознать реальные объекты мира.</span><span class="sxs-lookup"><span data-stu-id="0ae15-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="0ae15-130">В этом курсе вы узнаете, как получить результаты из Пользовательская служба визуального распознавания Azure, обнаружения объектов, в примере приложения на основе Unity.</span><span class="sxs-lookup"><span data-stu-id="0ae15-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="0ae15-131">Вы сможете применить эти понятия к настраиваемому приложению, которое вы можете собрать.</span><span class="sxs-lookup"><span data-stu-id="0ae15-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="0ae15-132">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="0ae15-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0ae15-133">Хождение</span><span class="sxs-lookup"><span data-stu-id="0ae15-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0ae15-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0ae15-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0ae15-135"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="0ae15-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0ae15-136">MR и Azure 310: Обнаружение объектов</span><span class="sxs-lookup"><span data-stu-id="0ae15-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="0ae15-137">✔️</span><span class="sxs-lookup"><span data-stu-id="0ae15-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="0ae15-138">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="0ae15-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0ae15-139">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="0ae15-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0ae15-140">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018).</span><span class="sxs-lookup"><span data-stu-id="0ae15-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="0ae15-141">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="0ae15-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="0ae15-142">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="0ae15-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0ae15-143">ПК для разработки</span><span class="sxs-lookup"><span data-stu-id="0ae15-143">A development PC</span></span>
- [<span data-ttu-id="0ae15-144">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="0ae15-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0ae15-145">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="0ae15-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0ae15-146">Unity 2017,4 LTS</span><span class="sxs-lookup"><span data-stu-id="0ae15-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0ae15-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0ae15-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="0ae15-148">[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="0ae15-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="0ae15-149">Доступ к Интернету для установки Azure и извлечения Пользовательская служба визуального распознавания</span><span class="sxs-lookup"><span data-stu-id="0ae15-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="0ae15-150">Для каждого объекта, который необходимо распознать Пользовательское визуальное распознавание, требуется ряд по крайней мере пятнадцати (15) образов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="0ae15-151">При желании вы можете использовать образы, которые уже предоставлены в этом курсе, [серии – CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="0ae15-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0ae15-152">Перед началом</span><span class="sxs-lookup"><span data-stu-id="0ae15-152">Before you start</span></span>

1.  <span data-ttu-id="0ae15-153">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="0ae15-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="0ae15-154">Настройка и тестирование HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ae15-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="0ae15-155">Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="0ae15-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="0ae15-156">Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="0ae15-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="0ae15-157">Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="0ae15-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="0ae15-158">Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="0ae15-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="0ae15-159">Глава 1. портал Пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="0ae15-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="0ae15-160">Чтобы использовать **Пользовательская служба визуального распознавания Azure**, необходимо настроить его экземпляр, чтобы сделать его доступным для приложения.</span><span class="sxs-lookup"><span data-stu-id="0ae15-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="0ae15-161">Перейдите [на главную страницу **Пользовательская служба визуального распознавания** ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="0ae15-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="0ae15-162">Щелкните **Начало работы**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="0ae15-163">Войдите на портал Пользовательское визуальное распознавание.</span><span class="sxs-lookup"><span data-stu-id="0ae15-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="0ae15-164">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="0ae15-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0ae15-165">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="0ae15-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="0ae15-166">После первого входа в систему вам будет предложено ввести *условия использования панели Сервис* .</span><span class="sxs-lookup"><span data-stu-id="0ae15-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="0ae15-167">Установите флажок, чтобы *принять условия*.</span><span class="sxs-lookup"><span data-stu-id="0ae15-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="0ae15-168">Затем нажмитекнопку Принимаю.</span><span class="sxs-lookup"><span data-stu-id="0ae15-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="0ae15-169">Принимаю условия, вы теперь в разделе *Мои проекты* .</span><span class="sxs-lookup"><span data-stu-id="0ae15-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="0ae15-170">Щелкните **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="0ae15-171">На правой стороне появится вкладка, в которой будет предложено указать некоторые поля для проекта.</span><span class="sxs-lookup"><span data-stu-id="0ae15-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="0ae15-172">Вставка имени проекта</span><span class="sxs-lookup"><span data-stu-id="0ae15-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="0ae15-173">Вставка описания проекта (необязательно)</span><span class="sxs-lookup"><span data-stu-id="0ae15-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="0ae15-174">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="0ae15-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0ae15-175">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="0ae15-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0ae15-176">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="0ae15-177">Если вы хотите [ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите к соответствующему документу](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) .</span><span class="sxs-lookup"><span data-stu-id="0ae15-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="0ae15-178">Задайте **типы проектов** как **Обнаружение объектов (Предварительная версия)** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="0ae15-179">После завершения нажмите кнопку **создать проект**, и вы будете перенаправлены на страницу проекта пользовательская служба визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="0ae15-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="0ae15-180">Глава 2. обучение проекта Пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="0ae15-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="0ae15-181">На портале Пользовательское визуальное распознавание основной целью является обучение проекта для распознавания конкретных объектов в изображениях.</span><span class="sxs-lookup"><span data-stu-id="0ae15-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="0ae15-182">Для каждого объекта, который должен распознать ваше приложение, требуется по крайней мере пятнадцать (15) образов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="0ae15-183">Вы можете использовать образы, предоставленные в этом курсе ([серия – CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="0ae15-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="0ae15-184">Обучение проекта Пользовательское визуальное распознавание:</span><span class="sxs-lookup"><span data-stu-id="0ae15-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="0ae15-185">Нажмите кнопку рядом с пунктом **теги.** **+**</span><span class="sxs-lookup"><span data-stu-id="0ae15-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="0ae15-186">Добавьте **имя** тега, который будет использоваться для связывания изображений с.</span><span class="sxs-lookup"><span data-stu-id="0ae15-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="0ae15-187">В этом примере мы используем образы – CUPS для распознавания, так что им присвоено имя Tag.</span><span class="sxs-lookup"><span data-stu-id="0ae15-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="0ae15-188">По завершении нажмите кнопку **сохранить** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="0ae15-189">Обратите внимание, что добавлен **тег** (может потребоваться перезагрузить страницу, чтобы она отображалась).</span><span class="sxs-lookup"><span data-stu-id="0ae15-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="0ae15-190">Щелкните **Добавить изображения** в центре страницы.</span><span class="sxs-lookup"><span data-stu-id="0ae15-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="0ae15-191">Щелкните **Обзор локальные файлы**и перейдите к изображениям, которые вы хотите передать для одного объекта, с минимальным числом пятнадцати (15).</span><span class="sxs-lookup"><span data-stu-id="0ae15-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="0ae15-192">Для отправки можно выбрать несколько образов за раз.</span><span class="sxs-lookup"><span data-stu-id="0ae15-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="0ae15-193">После выбора всех образов, с которыми вы хотите обучить проект, нажмите кнопку **отправить файлы** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="0ae15-194">Файлы начнут отправляться.</span><span class="sxs-lookup"><span data-stu-id="0ae15-194">The files will begin uploading.</span></span> <span data-ttu-id="0ae15-195">Получив подтверждение отправки, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="0ae15-196">На этом этапе образы передаются, но не помечаются тегами.</span><span class="sxs-lookup"><span data-stu-id="0ae15-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="0ae15-197">Чтобы пометить изображения, используйте мышь.</span><span class="sxs-lookup"><span data-stu-id="0ae15-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="0ae15-198">При наведении указателя мыши на изображение выделенный фрагмент поможет вам автоматически рисовать выделенный фрагмент вокруг объекта.</span><span class="sxs-lookup"><span data-stu-id="0ae15-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="0ae15-199">Если он неточен, можно нарисовать собственный.</span><span class="sxs-lookup"><span data-stu-id="0ae15-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="0ae15-200">Это достигается путем нажатия левой кнопки мыши и перетаскивания области выделения, чтобы охватить объект.</span><span class="sxs-lookup"><span data-stu-id="0ae15-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="0ae15-201">После выбора объекта в изображении появляется небольшой запрос на *Добавление тега Region*.</span><span class="sxs-lookup"><span data-stu-id="0ae15-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="0ae15-202">Выберите ранее созданный тег ("чашка" в приведенном выше примере) или, если вы добавляете дополнительные теги, введите его в и нажмите кнопку **+ (плюс)** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="0ae15-203">Чтобы добавить тег к следующему изображению, можно щелкнуть стрелку справа от колонки или закрыть колонку тега (щелкнув значок **X** в правом верхнем углу колонки), а затем щелкнув следующее изображение.</span><span class="sxs-lookup"><span data-stu-id="0ae15-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="0ae15-204">После подготовки следующего образа Повторите ту же процедуру.</span><span class="sxs-lookup"><span data-stu-id="0ae15-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="0ae15-205">Сделайте это для всех отправленных образов, пока они не помечаются тегами.</span><span class="sxs-lookup"><span data-stu-id="0ae15-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="0ae15-206">Можно выбрать несколько объектов в одном изображении, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="0ae15-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="0ae15-207">Получив все теги, нажмите кнопку с **тегами** в левой части экрана, чтобы отобразить изображения с тегами.</span><span class="sxs-lookup"><span data-stu-id="0ae15-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="0ae15-208">Теперь все готово для обучения службы.</span><span class="sxs-lookup"><span data-stu-id="0ae15-208">You are now ready to train your Service.</span></span> <span data-ttu-id="0ae15-209">Нажмите кнопку **обучение** , и начнется первая итерация для обучения.</span><span class="sxs-lookup"><span data-stu-id="0ae15-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="0ae15-210">После завершения сборки вы увидите две кнопки с именем сделать **URL-адрес** **по умолчанию** и прогноз.</span><span class="sxs-lookup"><span data-stu-id="0ae15-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="0ae15-211">Щелкните сначала **создать значение по умолчанию** , а затем щелкните **URL-адрес прогноза**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="0ae15-212">Конечной точке, предоставляемой из этого, присваивается любая *Итерация* , помеченная как используемая по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0ae15-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="0ae15-213">Таким образом, если позднее вы выполните новую *итерацию* и обновите ее по умолчанию, вам не потребуется изменять код.</span><span class="sxs-lookup"><span data-stu-id="0ae15-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="0ae15-214">После того как вы щелкнули **URL-адрес прогноза**, откройте *Блокнот*и скопируйте и вставьте **URL-адрес** (также называемый прогнозной **конечной точкой**) и **ключ прогноза службы**, чтобы его можно было извлечь, когда он понадобится позже в коде.</span><span class="sxs-lookup"><span data-stu-id="0ae15-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="0ae15-215">Глава 3. Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="0ae15-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="0ae15-216">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="0ae15-217">Откройте **Unity** и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="0ae15-218">Теперь необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="0ae15-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="0ae15-219">Вставьте **кустомвисионобждетектион**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="0ae15-220">Убедитесь, что для типа проекта задано значение **3D**, и задайте для **расположения** нужное значение (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="0ae15-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0ae15-221">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="0ae15-222">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0ae15-223">Перейдите к разделу **изменение* > *настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0ae15-224">Измените **Редактор внешних скриптов** на **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="0ae15-225">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="0ae15-226">Затем перейдите в раздел **файл > параметры сборки** и переключите **платформу** на *универсальная платформа Windows*, а затем нажмите кнопку **коммутатора платформы** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="0ae15-227">В том же окне **параметров сборки** убедитесь, что установлены следующие значения:</span><span class="sxs-lookup"><span data-stu-id="0ae15-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="0ae15-228">**Целевое устройство** имеет значение **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="0ae15-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="0ae15-229">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="0ae15-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="0ae15-230">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="0ae15-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="0ae15-231">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="0ae15-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="0ae15-232">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="0ae15-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="0ae15-233">Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0ae15-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="0ae15-234">В том же окне **параметров сборки** нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится **инспектор** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="0ae15-235">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="0ae15-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="0ae15-236">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="0ae15-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="0ae15-237">**Версия среды выполнения сценариев** должна быть **экспериментальной** (эквивалент .NET 4,6), что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="0ae15-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="0ae15-238">**Серверная часть сценариев** должна быть **.NET**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="0ae15-239">**Уровень совместимости API** должен быть **.NET 4,6**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="0ae15-240">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="0ae15-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="0ae15-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0ae15-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="0ae15-242">**Бесед**</span><span class="sxs-lookup"><span data-stu-id="0ae15-242">**Webcam**</span></span>

        3. <span data-ttu-id="0ae15-243">**спатиалперцептион**</span><span class="sxs-lookup"><span data-stu-id="0ae15-243">**SpatialPerception**</span></span>

            <span data-ttu-id="0ae15-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="0ae15-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="0ae15-245">На панели в **параметрах XR** (см. ниже **Параметры публикации**), поддерживаемая **Виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="0ae15-246">Назад в **параметрах сборки** *проекты Unity\# C* больше не заключаются: установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="0ae15-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="0ae15-247">Закройте окно **параметры сборки** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="0ae15-248">В **редакторе**щелкните **изменить** > **проект параметры** > **графика**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="0ae15-249">На **панели инспектора** будут открыты *параметры графики* .</span><span class="sxs-lookup"><span data-stu-id="0ae15-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="0ae15-250">Прокрутите вниз до тех пор, пока не появится массив с именем **всегда содержать шейдеры**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="0ae15-251">Добавьте слот, увеличив переменную **размера** на единицу (в этом примере она была 8, поэтому мы сделали это 9).</span><span class="sxs-lookup"><span data-stu-id="0ae15-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="0ae15-252">В последней позиции массива появится новый слот, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="0ae15-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="0ae15-253">В области щелкните маленький целевой круг рядом с слотом, чтобы открыть список шейдеров.</span><span class="sxs-lookup"><span data-stu-id="0ae15-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="0ae15-254">Найдите устаревшие шейдеры, **прозрачный** и диффузный, а затем дважды щелкните его.</span><span class="sxs-lookup"><span data-stu-id="0ae15-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="0ae15-255">Глава 4. Импорт пакета Unity Кустомвисионобждетектион</span><span class="sxs-lookup"><span data-stu-id="0ae15-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="0ae15-256">Для этого курса вы предоставляете пакет ресурса Unity с именем **Azure-MR-310. пакет unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="0ae15-257">Советы Все объекты, поддерживаемые Unity, включая все сцены, можно упаковать в файл **пакет unitypackage** , а затем экспортировать или импортировать в другие проекты.</span><span class="sxs-lookup"><span data-stu-id="0ae15-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="0ae15-258">Это самый надежный и эффективный способ перемещения ресурсов между различными **проектами Unity**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="0ae15-259">[Пакет Azure-MR-310, который нужно скачать здесь,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)можно найти здесь.</span><span class="sxs-lookup"><span data-stu-id="0ae15-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="0ae15-260">Теперь, когда панель мониторинга Unity находится перед вами, щелкните **ресурсы** в меню в верхней части экрана, а затем щелкните **Импорт пакета > настраиваемый пакет**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="0ae15-261">С помощью средства выбора файлов выберите пакет **Azure-MR-310. пакет unitypackage** и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="0ae15-262">Отобразится список компонентов для этого актива.</span><span class="sxs-lookup"><span data-stu-id="0ae15-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="0ae15-263">Подтвердите импорт, нажав кнопку " **Импорт** ".</span><span class="sxs-lookup"><span data-stu-id="0ae15-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="0ae15-264">После завершения импорта вы заметите, что папки пакета теперь добавлены в папку **Assets** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="0ae15-265">Такой тип структуры папок является типичным для проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="0ae15-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="0ae15-266">В папке « **материалы** » содержится материал, используемый **курсором «взгляд**».</span><span class="sxs-lookup"><span data-stu-id="0ae15-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="0ae15-267">Папка **plugins** содержит библиотеку DLL Newtonsoft, используемую кодом для десериализации веб-ответа службы.</span><span class="sxs-lookup"><span data-stu-id="0ae15-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="0ae15-268">Две (2) версии, содержащиеся в папке и вложенной папке, необходимы для того, чтобы библиотека была использована и построена как в редакторе Unity, так и в сборке UWP.</span><span class="sxs-lookup"><span data-stu-id="0ae15-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="0ae15-269">Папка **Prefabs** содержит Prefabs, содержащийся в сцене.</span><span class="sxs-lookup"><span data-stu-id="0ae15-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="0ae15-270">Это:</span><span class="sxs-lookup"><span data-stu-id="0ae15-270">Those are:</span></span>

        1.  <span data-ttu-id="0ae15-271">**Газекурсор**, курсор, используемый в приложении.</span><span class="sxs-lookup"><span data-stu-id="0ae15-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="0ae15-272">Будет работать вместе с Спатиалмаппинг prefab, чтобы их можно было разместить в сцене поверх физических объектов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="0ae15-273">**Метка**, которая является объектом пользовательского интерфейса, используемым для вывода тега объекта в сцене при необходимости.</span><span class="sxs-lookup"><span data-stu-id="0ae15-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="0ae15-274">**Спатиалмаппинг**— это объект, который позволяет приложению использовать создание виртуальной схемы с помощью пространственного отслеживания Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ae15-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="0ae15-275">Папка « **сцены** », в которой в настоящее время находится предварительно построенная сцена для этого курса.</span><span class="sxs-lookup"><span data-stu-id="0ae15-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="0ae15-276">Откройте папку « **сцены** » на **панели «проект**» и дважды щелкните **обждетектионсцене**, чтобы загрузить сцену, которая будет использоваться для этого курса.</span><span class="sxs-lookup"><span data-stu-id="0ae15-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="0ae15-277">**Код не включается**, вы пишете код, следуя этому курсу.</span><span class="sxs-lookup"><span data-stu-id="0ae15-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="0ae15-278">Глава 5. Создание класса Кустомвисионаналисер.</span><span class="sxs-lookup"><span data-stu-id="0ae15-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="0ae15-279">На этом этапе вы готовы написать некоторый код.</span><span class="sxs-lookup"><span data-stu-id="0ae15-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="0ae15-280">Вы начнете с класса **кустомвисионаналисер** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="0ae15-281">Вызовы **Пользовательская служба визуального распознавания**, выполненные в приведенном ниже коде, выполняются с помощью **REST API пользовательское визуальное распознавание**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="0ae15-282">С помощью этой функции вы узнаете, как реализовать этот API и использовать его (это полезно для понимания того, как реализовать что-то подобное).</span><span class="sxs-lookup"><span data-stu-id="0ae15-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="0ae15-283">Имейте в виду, что корпорация Майкрософт предлагает **пакет SDK для пользовательское визуальное распознавание** , который также можно использовать для вызова службы.</span><span class="sxs-lookup"><span data-stu-id="0ae15-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="0ae15-284">Дополнительные сведения см. в [статье пользовательское ВИЗУАЛЬНОЕ распознавание SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="0ae15-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="0ae15-285">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="0ae15-285">This class is responsible for:</span></span>

- <span data-ttu-id="0ae15-286">Загрузка последнего образа, записанного в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="0ae15-287">Отправка массива байтов в экземпляр **Пользовательская служба визуального распознавания** Azure для анализа.</span><span class="sxs-lookup"><span data-stu-id="0ae15-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="0ae15-288">Получение ответа в виде строки JSON.</span><span class="sxs-lookup"><span data-stu-id="0ae15-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="0ae15-289">Десериализация ответа и передача полученного **прогноза** классу **сценеорганисер** , который будет позаботиться о том, как должен отображаться ответ.</span><span class="sxs-lookup"><span data-stu-id="0ae15-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="0ae15-290">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0ae15-290">To create this class:</span></span>

1.  <span data-ttu-id="0ae15-291">Щелкните правой кнопкой мыши **папку Asset**, расположенную на **панели проект**, и выберите команду **создать** > **папку**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="0ae15-292">Вызовите **скрипты**папки.</span><span class="sxs-lookup"><span data-stu-id="0ae15-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="0ae15-293">Дважды щелкните только что созданную папку, чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="0ae15-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="0ae15-294">Щелкните правой кнопкой мыши внутри папки и выберите команду **создать** > **сценарий\# C**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0ae15-295">Назовите сценарий **кустомвисионаналисер.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="0ae15-296">Дважды щелкните новый скрипт **кустомвисионаналисер** , чтобы открыть его в **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="0ae15-297">Убедитесь, что в верхней части файла есть ссылки на следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="0ae15-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="0ae15-298">В классе **кустомвисионаналисер** добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="0ae15-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="0ae15-299">Убедитесь, что вы вставили **ключ прогноза службы** в переменную **Предиктионкэй** , а **Прогноз-конечную точку —** в переменную **предиктионендпоинт** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="0ae15-300">Вы скопировали их в [Блокнот ранее, в главе 2, на шаге 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="0ae15-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="0ae15-301">Необходимо добавить код для "спящего" **()** , чтобы инициализировать переменную экземпляра:</span><span class="sxs-lookup"><span data-stu-id="0ae15-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="0ae15-302">Добавьте соподпрограмму (с помощью статического метода **жетимажеасбитеаррай ()** ниже), который будет получать результаты анализа изображения, захваченного классом **имажекаптуре** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0ae15-303">В соподпрограмме **аналисеимажекаптуре** есть вызов класса **сценеорганисер** , который вы еще создали.</span><span class="sxs-lookup"><span data-stu-id="0ae15-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="0ae15-304">Поэтому **оставьте эти строки комментариями в настоящий момент**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. <span data-ttu-id="0ae15-305">Удалите методы **Start ()** и **Update ()** , так как они не будут использоваться.</span><span class="sxs-lookup"><span data-stu-id="0ae15-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="0ae15-306">Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ae15-307">Как упоминалось ранее, не беспокойтесь о коде, который может показаться ошибочным, так как в ближайшее время будут предоставлены дальнейшие занятия, которые будут устранены.</span><span class="sxs-lookup"><span data-stu-id="0ae15-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="0ae15-308">Глава 6. Создание класса Кустомвисионобжектс</span><span class="sxs-lookup"><span data-stu-id="0ae15-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="0ae15-309">Класс, который вы создадите, теперь является классом **кустомвисионобжектс** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="0ae15-310">Этот скрипт содержит несколько объектов, используемых другими классами для сериализации и десериализации вызовов, выполненных в Пользовательская служба визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="0ae15-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="0ae15-311">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0ae15-311">To create this class:</span></span>

1.  <span data-ttu-id="0ae15-312">Щелкните правой кнопкой мыши в папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0ae15-313">Вызовите скрипт **кустомвисионобжектс.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="0ae15-314">Дважды щелкните новый скрипт **кустомвисионобжектс** , чтобы открыть его в **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0ae15-315">Убедитесь, что в верхней части файла есть ссылки на следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="0ae15-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="0ae15-316">Удалите методы **Start ()** и **Update ()** внутри класса **кустомвисионобжектс** . Теперь этот класс должен быть пустым.</span><span class="sxs-lookup"><span data-stu-id="0ae15-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="0ae15-317">Важно внимательно следовать следующей инструкции.</span><span class="sxs-lookup"><span data-stu-id="0ae15-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="0ae15-318">Если поместить объявления нового класса в класс **кустомвисионобжектс** , в [главе 10](#chapter-10---create-the-imagecapture-class)будут возникнет ошибки компиляции, в которых говорится, что **аналисисрутобжект** и **BoundingBox** не найдены.</span><span class="sxs-lookup"><span data-stu-id="0ae15-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="0ae15-319">Добавьте следующие классы *за* пределами класса **кустомвисионобжектс** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="0ae15-320">Эти объекты используются библиотекой **Newtonsoft** для сериализации и десериализации данных ответа:</span><span class="sxs-lookup"><span data-stu-id="0ae15-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="0ae15-321">Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="0ae15-322">Глава 7. Создание класса Спатиалмаппинг</span><span class="sxs-lookup"><span data-stu-id="0ae15-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="0ae15-323">Этот класс настроит средство обнаружения для **пространственного сопоставления** в сцене, чтобы иметь возможность обнаруживать конфликты между виртуальными объектами и реальными объектами.</span><span class="sxs-lookup"><span data-stu-id="0ae15-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="0ae15-324">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0ae15-324">To create this class:</span></span>

1.  <span data-ttu-id="0ae15-325">Щелкните правой кнопкой мыши в папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0ae15-326">Вызовите скрипт **спатиалмаппинг.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="0ae15-327">Дважды щелкните новый скрипт **спатиалмаппинг** , чтобы открыть его в **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0ae15-328">Убедитесь, что имеются следующие пространства имен, на которые ссылается класс **спатиалмаппинг** :</span><span class="sxs-lookup"><span data-stu-id="0ae15-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="0ae15-329">Затем добавьте следующие переменные в класс **спатиалмаппинг** над методом **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="0ae15-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="0ae15-330">Добавьте параметр " **спящий ()** " и " **Начало" ()** :</span><span class="sxs-lookup"><span data-stu-id="0ae15-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="0ae15-331">Удалите метод **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="0ae15-332">Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="0ae15-333">Глава 8. Создание класса Газекурсор</span><span class="sxs-lookup"><span data-stu-id="0ae15-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="0ae15-334">Этот класс отвечает за настройку курсора в правильном расположении в реальном пространстве путем использования **спатиалмаппингколлидер**, созданного в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="0ae15-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="0ae15-335">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0ae15-335">To create this class:</span></span>

1.  <span data-ttu-id="0ae15-336">Щелкните правой кнопкой мыши в папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0ae15-337">Вызов скрипта **газекурсор**</span><span class="sxs-lookup"><span data-stu-id="0ae15-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="0ae15-338">Дважды щелкните новый скрипт **газекурсор** , чтобы открыть его в **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0ae15-339">Убедитесь, что у вас есть следующее пространство имен, указанное выше класса **газекурсор** :</span><span class="sxs-lookup"><span data-stu-id="0ae15-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="0ae15-340">Затем добавьте следующую переменную в класс **газекурсор** выше метода **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="0ae15-341">Обновите метод **Start ()** следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="0ae15-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="0ae15-342">Обновите метод **Update ()** , используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="0ae15-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="0ae15-343">Не беспокойтесь об ошибке, когда класс **сценеорганисер** не найден, он будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="0ae15-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="0ae15-344">Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="0ae15-345">Глава 9. Создание класса Сценеорганисер</span><span class="sxs-lookup"><span data-stu-id="0ae15-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="0ae15-346">Этот класс будет:</span><span class="sxs-lookup"><span data-stu-id="0ae15-346">This class will:</span></span>

-   <span data-ttu-id="0ae15-347">Настройте *основную камеру* , присоединив к ней соответствующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="0ae15-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="0ae15-348">При обнаружении объекта он отвечает за вычисление его позиции в реальном мире и помещает **метку тега** рядом с соответствующим **именем тега**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="0ae15-349">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0ae15-349">To create this class:</span></span>

1.  <span data-ttu-id="0ae15-350">Щелкните правой кнопкой мыши в папке Scripts, а затем выберите команду **создать** > **Сценарий C\#** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0ae15-351">Назовите сценарий **сценеорганисер**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="0ae15-352">Дважды щелкните новый скрипт **сценеорганисер** , чтобы открыть его в **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0ae15-353">Убедитесь, что имеются следующие пространства имен, на которые ссылается класс **сценеорганисер** :</span><span class="sxs-lookup"><span data-stu-id="0ae15-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="0ae15-354">Затем добавьте следующие переменные в класс **сценеорганисер** над методом **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="0ae15-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="0ae15-355">Удалите методы **Start ()** и **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="0ae15-356">Под переменными добавьте метод " **спящий ()** ", который будет инициализировать класс и настроить сцену.</span><span class="sxs-lookup"><span data-stu-id="0ae15-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="0ae15-357">Добавьте метод **плацеаналисислабел ()** , который будет *создавать экземпляр* метки в сцене (которая на данный момент невидима для пользователя).</span><span class="sxs-lookup"><span data-stu-id="0ae15-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="0ae15-358">Он также помещает четыре (невидимые) места размещения образа и пересекается с реальным миром.</span><span class="sxs-lookup"><span data-stu-id="0ae15-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="0ae15-359">Это важно, поскольку координаты Box, полученные от службы после анализа, отправляются обратно в эту Quad, чтобы определить приблизительное расположение объекта в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="0ae15-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="0ae15-360">Добавьте метод **финалиселабел ()** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="0ae15-361">Он отвечает за следующее:</span><span class="sxs-lookup"><span data-stu-id="0ae15-361">It is responsible for:</span></span>

    *   <span data-ttu-id="0ae15-362">Установка для текста *метки* *тега* прогноза с наибольшей достоверностью.</span><span class="sxs-lookup"><span data-stu-id="0ae15-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="0ae15-363">Вызов вычисления *ограничивающего прямоугольника* для объекта Quad, расположенного ранее, и размещение метки в сцене.</span><span class="sxs-lookup"><span data-stu-id="0ae15-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="0ae15-364">Настройка глубины метки с помощью Райкаст к *ограничивающему прямоугольнику*, который должен конфликтовать с объектом в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="0ae15-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="0ae15-365">Сброс процесса отслеживания, позволяющий пользователю записать другой образ.</span><span class="sxs-lookup"><span data-stu-id="0ae15-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="0ae15-366">Добавьте метод **калкулатебаундингбокспоситион ()** , который содержит ряд вычислений, необходимых для преобразования координат ограничивающего *прямоугольника* , полученных из службы, и повторного создания их пропорционально четырем.</span><span class="sxs-lookup"><span data-stu-id="0ae15-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="0ae15-367">Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0ae15-368">Прежде чем продолжить, откройте класс **кустомвисионаналисер** и в методе **аналиселастимажекаптуред ()** раскомментируйте следующие строки:</span><span class="sxs-lookup"><span data-stu-id="0ae15-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="0ae15-369">Не беспокойтесь о сообщении о том, что класс **имажекаптуре** не найден, вы создадите его в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="0ae15-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="0ae15-370">Глава 10. Создание класса Имажекаптуре</span><span class="sxs-lookup"><span data-stu-id="0ae15-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="0ae15-371">Следующий класс, который предстоит создать, — это класс **имажекаптуре** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="0ae15-372">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="0ae15-372">This class is responsible for:</span></span>

*   <span data-ttu-id="0ae15-373">Запись изображения с помощью камеры HoloLens и сохранение его в папке *приложения* .</span><span class="sxs-lookup"><span data-stu-id="0ae15-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="0ae15-374">Обработка жестов касания от пользователя.</span><span class="sxs-lookup"><span data-stu-id="0ae15-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="0ae15-375">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0ae15-375">To create this class:</span></span>

1.  <span data-ttu-id="0ae15-376">Перейдите к созданной ранее папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="0ae15-377">Щелкните правой кнопкой мыши внутри папки и выберите команду **создать** > **сценарий\# C**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0ae15-378">Назовите сценарий **имажекаптуре**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="0ae15-379">Дважды щелкните новый скрипт **имажекаптуре** , чтобы открыть его в **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="0ae15-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="0ae15-380">Замените пространства имен в верхней части файла следующим:</span><span class="sxs-lookup"><span data-stu-id="0ae15-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="0ae15-381">Затем добавьте следующие переменные в класс **имажекаптуре** над методом **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="0ae15-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="0ae15-382">Теперь необходимо добавить код для методов **"спящий" ()** и **"начало" ()** :</span><span class="sxs-lookup"><span data-stu-id="0ae15-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="0ae15-383">Реализуйте обработчик, который будет вызываться при возникновении жеста касания:</span><span class="sxs-lookup"><span data-stu-id="0ae15-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="0ae15-384">Когда курсор **горит зеленым**, это означает, что Камера доступна для получения образа.</span><span class="sxs-lookup"><span data-stu-id="0ae15-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="0ae15-385">**Красный цвет**курсора означает, что камера занята.</span><span class="sxs-lookup"><span data-stu-id="0ae15-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="0ae15-386">Добавьте метод, используемый приложением для запуска процесса записи образа, и сохраните образ:</span><span class="sxs-lookup"><span data-stu-id="0ae15-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  <span data-ttu-id="0ae15-387">Добавьте обработчики, которые будут вызываться при записи фотографии и при ее готовности к анализу.</span><span class="sxs-lookup"><span data-stu-id="0ae15-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="0ae15-388">Затем результат передается в **кустомвисионаналисер** для анализа.</span><span class="sxs-lookup"><span data-stu-id="0ae15-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="0ae15-389">Не забудьте сохранить изменения в **Visual Studio**перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="0ae15-390">Глава 11. Настройка сценариев в сцене</span><span class="sxs-lookup"><span data-stu-id="0ae15-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="0ae15-391">Теперь, когда вы написали весь код, необходимый для этого проекта, пора настроить скрипты в сцене и на Prefabs, чтобы они правильно ведут себя.</span><span class="sxs-lookup"><span data-stu-id="0ae15-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="0ae15-392">В **редакторе Unity**на **панели Иерархия**выберите **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="0ae15-393">На **панели инспектора**с выбранной **основной камерой** щелкните **Добавить компонент**, найдите скрипт **сценеорганисер** и дважды щелкните, чтобы добавить его.</span><span class="sxs-lookup"><span data-stu-id="0ae15-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="0ae15-394">На **панели проект**откройте **папку Prefabs**, перетащите **метку** prefab в область входные данные целевого объекта *метки* пусто, в скрипте **Сценеорганисер** , который вы только что добавили к *основной камере*, как показано на изображение ниже:</span><span class="sxs-lookup"><span data-stu-id="0ae15-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="0ae15-395">На **панели Иерархия**выберите дочерний элемент **газекурсор** **основной камеры**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="0ae15-396">На **панели инспектора**с выбранным **Газекурсор** щелкните **Добавить компонент**, затем найдите скрипт **газекурсор** и дважды щелкните, чтобы добавить его.</span><span class="sxs-lookup"><span data-stu-id="0ae15-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="0ae15-397">Опять же, на **панели Иерархия**выберите дочерний элемент **спатиалмаппинг** **основной камеры**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="0ae15-398">На **панели инспектора**с выбранным **Спатиалмаппинг** щелкните **Добавить компонент**, затем найдите скрипт **спатиалмаппинг** и дважды щелкните, чтобы добавить его.</span><span class="sxs-lookup"><span data-stu-id="0ae15-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="0ae15-399">Остальные скрипты, которые не были заданы, будут добавляться кодом в скрипте **сценеорганисер** во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0ae15-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="0ae15-400">Глава 12-перед сборкой</span><span class="sxs-lookup"><span data-stu-id="0ae15-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="0ae15-401">Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ae15-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="0ae15-402">Перед этим убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="0ae15-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="0ae15-403">Все параметры, упомянутые в [главе 3](#chapter-3---set-up-the-unity-project) , заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="0ae15-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="0ae15-404">**Сценеорганисер** скрипта прикреплен к главному объекту **Camera** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="0ae15-405">**Газекурсор** скрипта присоединен к объекту **газекурсор** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="0ae15-406">**Спатиалмаппинг** скрипта присоединен к объекту **спатиалмаппинг** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="0ae15-407">В [главе 5](#chapter-5---create-the-customvisionanalyser-class)шаг 6.</span><span class="sxs-lookup"><span data-stu-id="0ae15-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="0ae15-408">Убедитесь, что вы вставили **ключ прогноза службы** в переменную **предиктионкэй** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="0ae15-409">Вы вставили **конечную точку прогнозирования** в класс **предиктионендпоинт** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="0ae15-410">Глава 13. Создание решения UWP и загружать неопубликованные приложения</span><span class="sxs-lookup"><span data-stu-id="0ae15-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="0ae15-411">Теперь вы готовы к созданию приложения в качестве решения UWP, которое можно будет развернуть на Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ae15-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="0ae15-412">Чтобы начать процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="0ae15-412">To begin the build process:</span></span>

1.  <span data-ttu-id="0ae15-413">Выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="0ae15-414">**Проекты тактов Unity\# C**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="0ae15-415">Щелкните **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="0ae15-416">При этом в сборку будет добавлена открытая сцена.</span><span class="sxs-lookup"><span data-stu-id="0ae15-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="0ae15-417">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-417">Click **Build**.</span></span> <span data-ttu-id="0ae15-418">Unity запустит окно *проводника* , в котором необходимо создать, а затем выбрать папку для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="0ae15-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="0ae15-419">Создайте эту папку сейчас и назовите ее **app**Name.</span><span class="sxs-lookup"><span data-stu-id="0ae15-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="0ae15-420">Затем выберите папку **приложения** и щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="0ae15-421">Unity начнет сборку проекта в папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="0ae15-422">После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).</span><span class="sxs-lookup"><span data-stu-id="0ae15-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="0ae15-423">Чтобы выполнить развертывание в Microsoft HoloLens, вам потребуется IP-адрес этого устройства (для удаленного развертывания) и убедиться, что в нем также установлен **режим разработчика** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="0ae15-424">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="0ae15-424">To do this:</span></span>

    1.  <span data-ttu-id="0ae15-425">Людьми HoloLens, откройте **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="0ae15-426">Выберите сетевые &**Дополнительные параметры** **сети Интернет** > **Wi-Fi** > </span><span class="sxs-lookup"><span data-stu-id="0ae15-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="0ae15-427">Запишите **IPv4** -адрес.</span><span class="sxs-lookup"><span data-stu-id="0ae15-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="0ae15-428">Затем вернитесь к параметрами **Обновите & безопасности** > **для разработчиков** .</span><span class="sxs-lookup"><span data-stu-id="0ae15-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="0ae15-429">Задайте **режим разработчика** *на*.</span><span class="sxs-lookup"><span data-stu-id="0ae15-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="0ae15-430">Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="0ae15-431">В конфигурации решения выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="0ae15-432">На платформе решения выберите **x86, удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="0ae15-433">Вам будет предложено вставить **IP-адрес** удаленного устройства (в данном случае — Microsoft HoloLens, который вы заметили).</span><span class="sxs-lookup"><span data-stu-id="0ae15-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="0ae15-434">Перейдите в меню " **Сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ae15-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="0ae15-435">Теперь приложение должно появиться в списке установленных приложений в Microsoft HoloLens, готовом к запуску.</span><span class="sxs-lookup"><span data-stu-id="0ae15-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="0ae15-436">Чтобы использовать приложение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="0ae15-436">To use the application:</span></span>

* <span data-ttu-id="0ae15-437">Взгляните на объект, который вы обучили **Пользовательская служба визуального распознавания Azure, обнаружение объектов**и используйте **жест касания**.</span><span class="sxs-lookup"><span data-stu-id="0ae15-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="0ae15-438">Если объект успешно обнаружен, *текст метки* в мировом пространстве будет отображаться с именем тега.</span><span class="sxs-lookup"><span data-stu-id="0ae15-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ae15-439">Каждый раз, когда вы записываете фотографию и отправляете ее в службу, вы можете вернуться на страницу службы и переучить службу с новыми записанными образами.</span><span class="sxs-lookup"><span data-stu-id="0ae15-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="0ae15-440">В начале вам, возможно, придется исправить *ограничивающие рамки* , чтобы они были более точными и переучить службу.</span><span class="sxs-lookup"><span data-stu-id="0ae15-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="0ae15-441">Размещенный текст метки может не располагаться рядом с объектом, когда датчики Microsoft HoloLens и (или) Спатиалтраккингкомпонент в Unity не могут поместить соответствующие конфликты, связанные с реальными объектами мира.</span><span class="sxs-lookup"><span data-stu-id="0ae15-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="0ae15-442">Если это так, попробуйте использовать приложение на другой поверхности.</span><span class="sxs-lookup"><span data-stu-id="0ae15-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="0ae15-443">Пользовательское визуальное распознавание, приложение обнаружения объектов</span><span class="sxs-lookup"><span data-stu-id="0ae15-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="0ae15-444">Поздравляем! вы создали приложение смешанной реальности, которое использует Пользовательское визуальное распознавание Azure, API обнаружения объектов, который может распознать объект из изображения, а затем выдать приблизительное место для этого объекта в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="0ae15-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0ae15-445">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="0ae15-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0ae15-446">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="0ae15-446">Exercise 1</span></span>

<span data-ttu-id="0ae15-447">При добавлении к текстовой метке используйте полупрозрачный куб, чтобы обернуть реальный объект в трехмерный *ограничивающий прямоугольник*.</span><span class="sxs-lookup"><span data-stu-id="0ae15-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0ae15-448">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="0ae15-448">Exercise 2</span></span>

<span data-ttu-id="0ae15-449">Обучить Пользовательская служба визуального распознавания для распознавания большего числа объектов.</span><span class="sxs-lookup"><span data-stu-id="0ae15-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="0ae15-450">Упражнение 3</span><span class="sxs-lookup"><span data-stu-id="0ae15-450">Exercise 3</span></span>

<span data-ttu-id="0ae15-451">Подавать звуковой сигнал при распознавании объекта.</span><span class="sxs-lookup"><span data-stu-id="0ae15-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="0ae15-452">Упражнение 4</span><span class="sxs-lookup"><span data-stu-id="0ae15-452">Exercise 4</span></span>

<span data-ttu-id="0ae15-453">Используйте API для переобучения службы с теми же изображениями, которые анализирует приложение, чтобы сделать службу более точной (одновременное прогнозирование и обучение).</span><span class="sxs-lookup"><span data-stu-id="0ae15-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
