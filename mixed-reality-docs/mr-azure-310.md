---
title: Г-н и 310 Azure — обнаружение объектов
description: Выполните этот курс, чтобы узнать, как обучить модель машинного обучения, а затем используйте обученной модели для распознавания схожие объекты и их положение в реальном мире из приложения смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, пользовательской службе визуального распознавания, объект обнаружения, смешанный реальность, academy, unity, учебник, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597649"
---
>[!NOTE]
><span data-ttu-id="b64b1-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="b64b1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b64b1-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="b64b1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b64b1-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b64b1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b64b1-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="b64b1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b64b1-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b64b1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b64b1-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="b64b1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="b64b1-110">Г-н и Azure 310: Обнаружение объектов</span><span class="sxs-lookup"><span data-stu-id="b64b1-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="b64b1-111">В рамках этого курса вы узнаете, как для распознавания пользовательского визуального содержимого и его пространственных место в указанное изображение, с помощью пользовательской службе визуального распознавания Azure «объект» возможности приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b64b1-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="b64b1-112">Эта служба позволит вам для обучения модели машинного обучения с использованием объекта изображения.</span><span class="sxs-lookup"><span data-stu-id="b64b1-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="b64b1-113">Затем понадобится обученной модели для распознавания схожие объекты и приблизительное их расположение в реальном мире, предоставленный камеры из Microsoft HoloLens или веб-камеры подключиться к компьютеру для иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="b64b1-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![результат курс](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="b64b1-115">**Azure пользовательской службе визуального распознавания, обнаружение объекта** — это служба Майкрософт, что позволяет разработчикам создавать пользовательский образ классификаторов.</span><span class="sxs-lookup"><span data-stu-id="b64b1-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="b64b1-116">Эти классификаторы затем можно с помощью новых образов для обнаружения объектов в рамках этого нового образа, предоставляя **границы рамки** в самом образе.</span><span class="sxs-lookup"><span data-stu-id="b64b1-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="b64b1-117">Служба предоставляет простой, удобный, online портал для упрощения этого процесса.</span><span class="sxs-lookup"><span data-stu-id="b64b1-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="b64b1-118">Дополнительные сведения по следующим ссылкам:</span><span class="sxs-lookup"><span data-stu-id="b64b1-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="b64b1-119">Custom Vision страница в Azure</span><span class="sxs-lookup"><span data-stu-id="b64b1-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="b64b1-120">Ограничения и квоты</span><span class="sxs-lookup"><span data-stu-id="b64b1-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="b64b1-121">По завершении этого курса вы получите с приложением смешанной реальности, которое будет осуществлять следующее:</span><span class="sxs-lookup"><span data-stu-id="b64b1-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="b64b1-122">Пользователь будет иметь возможность *помощи* в объект, который они обучения с помощью пользовательской концепции службы Azure, объект обнаружения.</span><span class="sxs-lookup"><span data-stu-id="b64b1-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="b64b1-123">Пользователь будет использовать *коснитесь* жест быстрого проведения нужной информации на создание образа.</span><span class="sxs-lookup"><span data-stu-id="b64b1-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="b64b1-124">Приложение отправляет изображение пользовательской службы визуального распознавания Azure.</span><span class="sxs-lookup"><span data-stu-id="b64b1-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="b64b1-125">Будет существовать ответа от службы, который будет отображать результат распознавания как текст в абсолютном пространстве.</span><span class="sxs-lookup"><span data-stu-id="b64b1-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="b64b1-126">Это будет выполняться через использование Microsoft HoloLens пространственных отслеживания, как способ основные сведения о распознанных объекта положение в мировых координатах, а затем использовать *тега* сопоставленный обнаруженных в образе, до Введите текст метки.</span><span class="sxs-lookup"><span data-stu-id="b64b1-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="b64b1-127">Курс также рассматривается вручную загрузки изображений, создание тегов, и обучение для распознавания различных службой объекты (в предоставленном примере чашку), по параметр *границ поле* в образе, отправке.</span><span class="sxs-lookup"><span data-stu-id="b64b1-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="b64b1-128">После создания и использования приложения, разработчику необходимо перейти обратно к пользовательской концепции службы Azure и определить прогноза, выполненных службой и определить, были ли правильно или нет (посредством добавления тегов, что-либо службы пропустили, и Настройка *ограничивающий поля*).</span><span class="sxs-lookup"><span data-stu-id="b64b1-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="b64b1-129">Службу можно затем повторно обучить, которой будет увеличить вероятность его распознавание объектов реального мира.</span><span class="sxs-lookup"><span data-stu-id="b64b1-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="b64b1-130">Этот курс ознакомят вас для получения результатов из пользовательской концепции службы Azure, определение объекта, в основе Unity примера приложения.</span><span class="sxs-lookup"><span data-stu-id="b64b1-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="b64b1-131">Это будет необходимо применение этих понятий в пользовательское приложение, возможно, вы разрабатываете.</span><span class="sxs-lookup"><span data-stu-id="b64b1-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="b64b1-132">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="b64b1-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b64b1-133">Курс</span><span class="sxs-lookup"><span data-stu-id="b64b1-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b64b1-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b64b1-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b64b1-135"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="b64b1-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b64b1-136">Г-н и Azure 310: Обнаружение объектов</span><span class="sxs-lookup"><span data-stu-id="b64b1-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="b64b1-137">✔️</span><span class="sxs-lookup"><span data-stu-id="b64b1-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="b64b1-138">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b64b1-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b64b1-139">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="b64b1-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b64b1-140">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="b64b1-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="b64b1-141">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="b64b1-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="b64b1-142">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b64b1-143">Компьютере разработки</span><span class="sxs-lookup"><span data-stu-id="b64b1-143">A development PC</span></span>
- [<span data-ttu-id="b64b1-144">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="b64b1-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="b64b1-145">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="b64b1-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="b64b1-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="b64b1-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="b64b1-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b64b1-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="b64b1-148">Объект [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="b64b1-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="b64b1-149">Доступ к Интернету для настройки Azure и извлечения пользовательской службы визуального распознавания</span><span class="sxs-lookup"><span data-stu-id="b64b1-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="b64b1-150">Ряд образов по крайней мере пятнадцать (15) являются обязательными) для каждого объекта, хотелось бы концепции Custom для распознавания.</span><span class="sxs-lookup"><span data-stu-id="b64b1-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="b64b1-151">Если вы хотите, можно использовать образы, представленных в этом курсе [ряд пользовательских политик,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="b64b1-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b64b1-152">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="b64b1-152">Before you start</span></span>

1.  <span data-ttu-id="b64b1-153">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="b64b1-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="b64b1-154">Настроить и проверить ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b64b1-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="b64b1-155">Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="b64b1-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="b64b1-156">Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="b64b1-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="b64b1-157">Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="b64b1-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="b64b1-158">Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="b64b1-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="b64b1-159">Глава 1 - портале пользовательской службе визуального распознавания</span><span class="sxs-lookup"><span data-stu-id="b64b1-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="b64b1-160">Чтобы использовать **пользовательская служба визуального распознавания Azure**, необходимо настроить экземпляр его, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="b64b1-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="b64b1-161">Перейдите [для **пользовательская служба визуального распознавания** главной странице](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="b64b1-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="b64b1-162">Щелкните **Приступая к работе**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="b64b1-163">Войдите на портал пользовательской службе визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="b64b1-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="b64b1-164">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="b64b1-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b64b1-165">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="b64b1-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="b64b1-166">После входа в первый раз, вам будет предложено с *условиями* панели.</span><span class="sxs-lookup"><span data-stu-id="b64b1-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="b64b1-167">Установите флажок, чтобы *согласны с условиями*.</span><span class="sxs-lookup"><span data-stu-id="b64b1-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="b64b1-168">Нажмите кнопку **принимаю**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="b64b1-169">Согласии с условиями, теперь вы находитесь в *Мои проекты* раздел.</span><span class="sxs-lookup"><span data-stu-id="b64b1-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="b64b1-170">Щелкните **новый проект**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="b64b1-171">Будет отображаться в области справа, который предложит задать некоторые поля для проекта.</span><span class="sxs-lookup"><span data-stu-id="b64b1-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="b64b1-172">Вставить имя проекта</span><span class="sxs-lookup"><span data-stu-id="b64b1-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="b64b1-173">Введите описание для проекта (**необязательно**)</span><span class="sxs-lookup"><span data-stu-id="b64b1-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="b64b1-174">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="b64b1-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b64b1-175">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="b64b1-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b64b1-176">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="b64b1-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="b64b1-177">Если вы хотите [Дополнительные сведения о группах ресурсов Azure, перейдите к связанные документы](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="b64b1-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="b64b1-178">Задайте **типы проектов** как **обнаружение объектов (Предварительная версия)**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="b64b1-179">Когда вы закончите, нажмите кнопку **создать проект**, и вы будете перенаправлены на страницу проекта пользовательской службы визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="b64b1-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="b64b1-180">Глава 2 - обучение Custom Vision проекта</span><span class="sxs-lookup"><span data-stu-id="b64b1-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="b64b1-181">Один раз на портале Custom Vision, ваша основная задача заключается для обучения проекта распознавать определенные объекты на изображениях.</span><span class="sxs-lookup"><span data-stu-id="b64b1-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="b64b1-182">Необходимо по крайней мере 15 (15) образы для каждого объекта, которые требуется приложение для распознавания.</span><span class="sxs-lookup"><span data-stu-id="b64b1-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="b64b1-183">Можно использовать образы, предоставленные в этом курсе ([ряд пользовательских политик,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="b64b1-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="b64b1-184">Для обучения Custom Vision проекта:</span><span class="sxs-lookup"><span data-stu-id="b64b1-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="b64b1-185">Щелкните **+** рядом с пунктом **теги**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="b64b1-186">Добавить **имя** для тега, который будет использоваться для связи изображений.</span><span class="sxs-lookup"><span data-stu-id="b64b1-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="b64b1-187">В этом примере мы используем образы пользовательских политик, для распознавания, поэтому тега с именем, для этого **Cup**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="b64b1-188">Нажмите кнопку **Сохранить** после завершения.</span><span class="sxs-lookup"><span data-stu-id="b64b1-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="b64b1-189">Обратите внимание на **тега** был добавлен (может потребоваться перезагрузить страницу, чтобы он появился).</span><span class="sxs-lookup"><span data-stu-id="b64b1-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="b64b1-190">Щелкните **Добавление изображений** в центре страницы.</span><span class="sxs-lookup"><span data-stu-id="b64b1-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="b64b1-191">Щелкните **Обзор локальных файлов**и перейдите к изображениям, вы бы хотели отправить один объект, с минимальным благосостояние пятнадцать (15).</span><span class="sxs-lookup"><span data-stu-id="b64b1-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="b64b1-192">Можно выбрать несколько изображений одновременно, для отправки.</span><span class="sxs-lookup"><span data-stu-id="b64b1-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="b64b1-193">Нажмите клавишу **передача файлов** после выбора всех образов, вы бы хотели обучения проекта.</span><span class="sxs-lookup"><span data-stu-id="b64b1-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="b64b1-194">Файлы начнется передача.</span><span class="sxs-lookup"><span data-stu-id="b64b1-194">The files will begin uploading.</span></span> <span data-ttu-id="b64b1-195">Получив подтверждение отправки, нажмите кнопку **сделать**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="b64b1-196">На этом этапе образы отправлен, но не добавлены проектные теги.</span><span class="sxs-lookup"><span data-stu-id="b64b1-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="b64b1-197">Добавить тег изображения, с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="b64b1-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="b64b1-198">При наведении указателя мыши на изображение, выделение поможет нарисовав выбора вокруг вашего объекта автоматически.</span><span class="sxs-lookup"><span data-stu-id="b64b1-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="b64b1-199">Если это не точное, можно создать собственные.</span><span class="sxs-lookup"><span data-stu-id="b64b1-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="b64b1-200">Это достигается путем хранения щелкните левой кнопкой мыши и перетащив области выделения вплоть до охватывающих объекта.</span><span class="sxs-lookup"><span data-stu-id="b64b1-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="b64b1-201">После выделенного объекта на изображении небольшой запрос запросит для *добавьте тег Region*.</span><span class="sxs-lookup"><span data-stu-id="b64b1-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="b64b1-202">Выберите ранее созданный тег («Cup», в приведенном выше примере) или если вы добавляете дополнительные теги, введите в и нажмите кнопку **+ (плюс)** кнопки.</span><span class="sxs-lookup"><span data-stu-id="b64b1-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="b64b1-203">Для пометки Далее образа, можно щелкните стрелку справа от колонки или закройте колонку тега (щелкнув **X** в правом верхнем углу колонки) и нажмите кнопку Далее.</span><span class="sxs-lookup"><span data-stu-id="b64b1-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="b64b1-204">Получив Далее готов, повторите ту же процедуру.</span><span class="sxs-lookup"><span data-stu-id="b64b1-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="b64b1-205">Это необходимо сделайте для всех образов, которые вы отправили, пока они все помечаются.</span><span class="sxs-lookup"><span data-stu-id="b64b1-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="b64b1-206">Можно выбрать несколько объектов в одном образе, как на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="b64b1-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="b64b1-207">После пометки их все, щелкните на **с тегами** кнопки в левой части экрана, чтобы отобразить теги образов.</span><span class="sxs-lookup"><span data-stu-id="b64b1-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="b64b1-208">Теперь вы готовы для обучения службы.</span><span class="sxs-lookup"><span data-stu-id="b64b1-208">You are now ready to train your Service.</span></span> <span data-ttu-id="b64b1-209">Нажмите кнопку **Train** начнется кнопку и первой итерации обучения.</span><span class="sxs-lookup"><span data-stu-id="b64b1-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="b64b1-210">После построения, можно увидеть две кнопки с именем **сделать значением по умолчанию** и **прогноза URL-адрес**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="b64b1-211">Щелкните **сделать значением по умолчанию** сначала, затем щелкните **прогноза URL-адрес**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="b64b1-212">Какое значение присваивается конечную точку, которая предоставляется из этого, *итерации* был помечен как по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b64b1-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="b64b1-213">Таким образом, если вы позднее сделать новый *итерации* и обновить его по умолчанию, не потребуется изменять код.</span><span class="sxs-lookup"><span data-stu-id="b64b1-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="b64b1-214">Когда вы перейдете на **URL-адрес прогноза**откройте *Блокнот*, скопируйте и вставьте **URL-адрес** (также называется вашей **конечной точки прогноза**) и **прогноза-ключ службы**, так что его можно получить, когда это потребуется далее в коде.</span><span class="sxs-lookup"><span data-stu-id="b64b1-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="b64b1-215">Глава 3 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="b64b1-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="b64b1-216">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="b64b1-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b64b1-217">Откройте **Unity** и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="b64b1-218">Теперь необходимо будет указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="b64b1-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="b64b1-219">Вставить **CustomVisionObjDetection**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="b64b1-220">Убедитесь, что тип проекта присваивается **3D**и задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="b64b1-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b64b1-221">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="b64b1-222">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b64b1-223">Перейдите к **изменить* > *предпочтения** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b64b1-224">Изменение **внешнего редактора скриптов** для **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="b64b1-225">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="b64b1-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="b64b1-226">Перейдите к **файл > Параметры сборки** и переключаться **платформы** для *универсальной платформы Windows*и затем щелкнув **переключения платформы** кнопки.</span><span class="sxs-lookup"><span data-stu-id="b64b1-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="b64b1-227">В том же **параметры построения** окна, задайте следующее:</span><span class="sxs-lookup"><span data-stu-id="b64b1-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="b64b1-228">**Целевое устройство** присваивается **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b64b1-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="b64b1-229">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="b64b1-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="b64b1-230">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="b64b1-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="b64b1-231">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="b64b1-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="b64b1-232">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="b64b1-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="b64b1-233">Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="b64b1-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="b64b1-234">В том же **параметры построения** щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где **инспектор** находится.</span><span class="sxs-lookup"><span data-stu-id="b64b1-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="b64b1-235">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="b64b1-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="b64b1-236">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="b64b1-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="b64b1-237">**Сценарии версии среды выполнения** должно быть **экспериментальный** (.NET 4.6 эквивалент), что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="b64b1-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="b64b1-238">**Создание сценариев серверной части** должно быть **.NET**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="b64b1-239">**Уровень совместимости API** должно быть **.NET 4.6**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="b64b1-240">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="b64b1-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="b64b1-241">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="b64b1-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="b64b1-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="b64b1-242">**Webcam**</span></span>

        3. <span data-ttu-id="b64b1-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="b64b1-243">**SpatialPerception**</span></span>

            <span data-ttu-id="b64b1-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="b64b1-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="b64b1-245">Последующих частях панели **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанный Windows Реальность SDK** добавляется.</span><span class="sxs-lookup"><span data-stu-id="b64b1-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="b64b1-246">Вернитесь в **параметры построения**, *Unity C\# проекты* больше не отображается серым: установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="b64b1-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="b64b1-247">Закрыть **параметры построения** окна.</span><span class="sxs-lookup"><span data-stu-id="b64b1-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="b64b1-248">В **редактор**, щелкните **изменить** > **параметры проекта** > **графики**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="b64b1-249">В **панели Инспектора** *параметры графики* будут открыты.</span><span class="sxs-lookup"><span data-stu-id="b64b1-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="b64b1-250">Прокрутите вниз, пока не увидите массив с именем **всегда включать шейдеры**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="b64b1-251">Добавление слота, увеличив **размер** переменную на единицу (в данном случае оно имело значение 8, мы сделали 9).</span><span class="sxs-lookup"><span data-stu-id="b64b1-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="b64b1-252">Новый слот будет отображаться, в последней позиции массива, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b64b1-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="b64b1-253">В области щелкните маленьких целевых круг рядом с слот, чтобы просмотреть список построителей текстур.</span><span class="sxs-lookup"><span data-stu-id="b64b1-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="b64b1-254">Найдите **прежних версий шейдеры/Transparent/Диффузия** шейдера и дважды щелкните его.</span><span class="sxs-lookup"><span data-stu-id="b64b1-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="b64b1-255">Глава 4 — Импорт пакета CustomVisionObjDetection Unity</span><span class="sxs-lookup"><span data-stu-id="b64b1-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="b64b1-256">Для этого курса, вам будет предоставлен пакет средств Unity, которые называются **Azure-MR-310.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="b64b1-257">[СОВЕТ] Любые объекты, поддерживаемые Unity, включая целые сцены можно упаковать в **.unitypackage** файл и экспорта / импорта в других проектах.</span><span class="sxs-lookup"><span data-stu-id="b64b1-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="b64b1-258">Это максимально эффективным и безопасным способом, перемещать между различными **проектов Unity**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="b64b1-259">Можно найти [Azure MR-310 пакет, который можно загрузить здесь](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="b64b1-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="b64b1-260">С помощью панели мониторинга Unity перед глазами, щелкните **активы** в меню в верхней части экрана, нажмите кнопку **Импорт пакета > пользовательского пакета**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="b64b1-261">Используйте средство выбора файлов для выбора **Azure-MR-310.unitypackage** пакета и нажмите кнопку **откройте**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="b64b1-262">Список компонентов для этого ресурса будет отображаться пользователю.</span><span class="sxs-lookup"><span data-stu-id="b64b1-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="b64b1-263">Подтверждение импорта, щелкнув **импорта** кнопки.</span><span class="sxs-lookup"><span data-stu-id="b64b1-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="b64b1-264">После завершения импорта, можно заметить, что папки из пакета теперь были добавлены к **активы** папки.</span><span class="sxs-lookup"><span data-stu-id="b64b1-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="b64b1-265">Такого рода структуру папок является типичным для проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="b64b1-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="b64b1-266">**Материалы** папка содержит материал, используемый **помощи курсора**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="b64b1-267">**Подключаемые модули** папка содержит Библиотеку Newtonsoft, используемых в коде для десериализации веб-ответа службы.</span><span class="sxs-lookup"><span data-stu-id="b64b1-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="b64b1-268">Два (2) разных версий содержащихся в папке, а также вложенную папку, необходимые для поддержки библиотеки с возможностью использования созданные редактора Unity и построения универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="b64b1-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="b64b1-269">**Prefabs** папка содержит prefabs, содержащихся в сцене.</span><span class="sxs-lookup"><span data-stu-id="b64b1-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="b64b1-270">Таковы:</span><span class="sxs-lookup"><span data-stu-id="b64b1-270">Those are:</span></span>

        1.  <span data-ttu-id="b64b1-271">**GazeCursor**, курсор, используемый в приложении.</span><span class="sxs-lookup"><span data-stu-id="b64b1-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="b64b1-272">Будет работать вместе с prefab SpatialMapping, чтобы иметь возможность разместить в сцене поверх физических объектов.</span><span class="sxs-lookup"><span data-stu-id="b64b1-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="b64b1-273">**Метка**, который является объектом пользовательского интерфейса, используемый для отображения тега объекта в сцену, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="b64b1-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="b64b1-274">**SpatialMapping**, который является объект, который позволяет приложению использовать Создание виртуальной схемы, использование пространственных отслеживания Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b64b1-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="b64b1-275">**Сцены** папке, которая в настоящее время содержит предварительно созданные сцены курс с демороликами.</span><span class="sxs-lookup"><span data-stu-id="b64b1-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="b64b1-276">Откройте **сцены** папку в **панель проекта**и дважды щелкните **ObjDetectionScene**, чтобы загрузить сцены, который будет использоваться для этого курса.</span><span class="sxs-lookup"><span data-stu-id="b64b1-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="b64b1-277">**Включено без кода**, вы напишете код, выполнив этот курс.</span><span class="sxs-lookup"><span data-stu-id="b64b1-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="b64b1-278">Глава 5 - создание класса CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="b64b1-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="b64b1-279">На этом этапе вы готовы написать код.</span><span class="sxs-lookup"><span data-stu-id="b64b1-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="b64b1-280">Вы начнете с **CustomVisionAnalyser** класса.</span><span class="sxs-lookup"><span data-stu-id="b64b1-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="b64b1-281">Вызовы **пользовательская служба визуального распознавания**, внесенных в код, показанный ниже, с помощью **Custom Vision REST API**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="b64b1-282">С помощью это, вы увидите, как реализовать и использовать этот API (полезно для понимания того, как выполнить что-то подобное самостоятельно).</span><span class="sxs-lookup"><span data-stu-id="b64b1-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="b64b1-283">Имейте в виду, что корпорация Майкрософт предлагает **Custom Vision SDK** , может также использоваться для выполнения вызовов к службе.</span><span class="sxs-lookup"><span data-stu-id="b64b1-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="b64b1-284">Дополнительные сведения см. в статье [статьи пакет SDK для компьютерного зрения Custom](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="b64b1-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="b64b1-285">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="b64b1-285">This class is responsible for:</span></span>

- <span data-ttu-id="b64b1-286">Загрузка последней версии образа, записано в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="b64b1-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="b64b1-287">Отправка массива байтов подписки Azure **пользовательская служба визуального распознавания** экземпляра для анализа.</span><span class="sxs-lookup"><span data-stu-id="b64b1-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="b64b1-288">Получение ответа как строку JSON.</span><span class="sxs-lookup"><span data-stu-id="b64b1-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="b64b1-289">Десериализации ответа и передачи итоговый **прогноза** для **SceneOrganiser** класс, который берет на себя отображения ответа.</span><span class="sxs-lookup"><span data-stu-id="b64b1-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="b64b1-290">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-290">To create this class:</span></span>

1.  <span data-ttu-id="b64b1-291">Щелкните правой кнопкой мыши в **папке Asset**, который находится в **панель проекта**, затем нажмите кнопку **создать** > **папку**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="b64b1-292">Вызовите папке **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="b64b1-293">Дважды щелкните новую папку, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="b64b1-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="b64b1-294">Щелкните правой кнопкой мыши внутри папки, а затем щелкните **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b64b1-295">Назовите сценарий **CustomVisionAnalyser.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="b64b1-296">Дважды щелкните новый **CustomVisionAnalyser** скрипт, чтобы открыть его с **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="b64b1-297">Убедитесь, что у вас есть следующие пространства имен, в верхней части файла:</span><span class="sxs-lookup"><span data-stu-id="b64b1-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="b64b1-298">В **CustomVisionAnalyser** добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="b64b1-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

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
    > <span data-ttu-id="b64b1-299">Убедитесь, что вы вставляете вашей **прогноза-ключ службы** в **predictionKey** переменной и **конечной точки прогноза** в **predictionEndpoint**  переменной.</span><span class="sxs-lookup"><span data-stu-id="b64b1-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="b64b1-300">Вы скопировали их [Блокнот ранее, в главе 2, шаге 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="b64b1-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="b64b1-301">Код для **Awake()** теперь должен быть добавлен для инициализации переменной экземпляра:</span><span class="sxs-lookup"><span data-stu-id="b64b1-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="b64b1-302">Добавить соподпрограмме (с помощью статического **GetImageAsByteArray()** метод под ним), которой будет получать результаты анализа, изображения, охватываемым **ImageCapture** класс.</span><span class="sxs-lookup"><span data-stu-id="b64b1-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b64b1-303">В **AnalyseImageCapture** соподпрограмме, имеется вызов **SceneOrganiser** класс, который вы еще для создания.</span><span class="sxs-lookup"><span data-stu-id="b64b1-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="b64b1-304">Таким образом **оставлю их строк закомментирована сейчас**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-304">Therefore, **leave those lines commented for now**.</span></span>

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

9. <span data-ttu-id="b64b1-305">Удалить **Start()** и **Update()** методы, так как они не будут использоваться.</span><span class="sxs-lookup"><span data-stu-id="b64b1-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="b64b1-306">Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b64b1-307">Как упоминалось ранее, не беспокоясь о коде, который может появиться ошибка, как вы будете обеспечивать дополнительные классы в ближайшее время, которые будет устранить их.</span><span class="sxs-lookup"><span data-stu-id="b64b1-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="b64b1-308">Глава 6 - создание класса CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="b64b1-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="b64b1-309">Класс, вы создадите теперь является **CustomVisionObjects** класса.</span><span class="sxs-lookup"><span data-stu-id="b64b1-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="b64b1-310">Этот скрипт содержит несколько объектов, используемых другими классами для сериализации и десериализации вызовы к пользовательской службы визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="b64b1-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="b64b1-311">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-311">To create this class:</span></span>

1.  <span data-ttu-id="b64b1-312">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b64b1-313">Вызовите сценарий **CustomVisionObjects.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="b64b1-314">Дважды щелкните новый **CustomVisionObjects** скрипт, чтобы открыть его с **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="b64b1-315">Убедитесь, что у вас есть следующие пространства имен, в верхней части файла:</span><span class="sxs-lookup"><span data-stu-id="b64b1-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="b64b1-316">Удалить **Start()** и **Update()** методов внутри **CustomVisionObjects** класса, этот класс будет очищен.</span><span class="sxs-lookup"><span data-stu-id="b64b1-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="b64b1-317">Очень важно, что вы внимательно выполните следующую инструкцию.</span><span class="sxs-lookup"><span data-stu-id="b64b1-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="b64b1-318">Если поместить новый объявления классов внутри **CustomVisionObjects** класс, вы получите ошибки компиляции [Глава 10](#chapter-10---create-the-imagecapture-class), содержащее сведения о, **AnalysisRootObject** и  **BoundingBox** не найдены.</span><span class="sxs-lookup"><span data-stu-id="b64b1-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="b64b1-319">Добавьте следующие классы *за пределами* **CustomVisionObjects** класса.</span><span class="sxs-lookup"><span data-stu-id="b64b1-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="b64b1-320">Эти объекты используются **Newtonsoft** библиотеки для сериализации и десериализации данных ответа:</span><span class="sxs-lookup"><span data-stu-id="b64b1-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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

6.  <span data-ttu-id="b64b1-321">Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="b64b1-322">Глава 7 - создание класса SpatialMapping</span><span class="sxs-lookup"><span data-stu-id="b64b1-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="b64b1-323">Задаст этот класс **пространственных сопоставление Collider** в сцене таким образом, чтобы иметь возможность обнаруживать конфликты между виртуальных объектах и реальными объектами.</span><span class="sxs-lookup"><span data-stu-id="b64b1-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="b64b1-324">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-324">To create this class:</span></span>

1.  <span data-ttu-id="b64b1-325">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b64b1-326">Вызовите сценарий **SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="b64b1-327">Дважды щелкните новый **SpatialMapping** скрипт, чтобы открыть его с **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="b64b1-328">Убедитесь, что у вас есть следующие пространства имен, упоминавшиеся **SpatialMapping** класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="b64b1-329">Затем добавьте следующие переменные внутри **SpatialMapping** класса выше **Start()** метод:</span><span class="sxs-lookup"><span data-stu-id="b64b1-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="b64b1-330">Добавить **Awake()** и **Start()**:</span><span class="sxs-lookup"><span data-stu-id="b64b1-330">Add the **Awake()** and **Start()**:</span></span>

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

6.  <span data-ttu-id="b64b1-331">Удалить **Update()** метод.</span><span class="sxs-lookup"><span data-stu-id="b64b1-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="b64b1-332">Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="b64b1-333">Глава 8 - создать класс GazeCursor</span><span class="sxs-lookup"><span data-stu-id="b64b1-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="b64b1-334">Этот класс отвечает за Настройка курсора в нужное место в реальных пространстве с помощью **SpatialMappingCollider**, созданный в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="b64b1-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="b64b1-335">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-335">To create this class:</span></span>

1.  <span data-ttu-id="b64b1-336">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b64b1-337">Вызовите сценарий **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="b64b1-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="b64b1-338">Дважды щелкните новый **GazeCursor** скрипт, чтобы открыть его с **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="b64b1-339">Убедитесь, что у вас есть следующее пространство имен, указанное выше **GazeCursor** класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="b64b1-340">Затем добавьте следующую переменную внутри **GazeCursor** класса выше **Start()** метод.</span><span class="sxs-lookup"><span data-stu-id="b64b1-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="b64b1-341">Обновление **Start()** метод следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="b64b1-341">Update the **Start()** method with the following code:</span></span>

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

6.  <span data-ttu-id="b64b1-342">Обновление **Update()** метод следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="b64b1-342">Update the **Update()** method with the following code:</span></span>

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
    > <span data-ttu-id="b64b1-343">Не волнуйтесь об ошибке для **SceneOrganiser** класс не найден, он будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="b64b1-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="b64b1-344">Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="b64b1-345">Глава 9 — создать класс SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="b64b1-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="b64b1-346">Этот класс выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="b64b1-346">This class will:</span></span>

-   <span data-ttu-id="b64b1-347">Настройка *Main Camera* путем присоединения к нему соответствующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="b64b1-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="b64b1-348">При обнаружении объекта, он будет отвечать за вычисление его позиции в реальном мире и место **тега метки** его рядом с соответствующим **имя тега**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="b64b1-349">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-349">To create this class:</span></span>

1.  <span data-ttu-id="b64b1-350">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b64b1-351">Назовите сценарий **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="b64b1-352">Дважды щелкните новый **SceneOrganiser** скрипт, чтобы открыть его с **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="b64b1-353">Убедитесь, что у вас есть следующие пространства имен, упоминавшиеся **SceneOrganiser** класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="b64b1-354">Затем добавьте следующие переменные внутри **SceneOrganiser** класса выше **Start()** метод:</span><span class="sxs-lookup"><span data-stu-id="b64b1-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="b64b1-355">Удалить **Start()** и **Update()** методы.</span><span class="sxs-lookup"><span data-stu-id="b64b1-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="b64b1-356">Под переменные, добавить **Awake()** метод, который будет инициализировать класс и подготовить сцены.</span><span class="sxs-lookup"><span data-stu-id="b64b1-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="b64b1-357">Добавить **PlaceAnalysisLabel()** метод, который будет *создание их экземпляров* метки в сцене (который теперь является невидимой для пользователя).</span><span class="sxs-lookup"><span data-stu-id="b64b1-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="b64b1-358">Он также помещает (также невидимый) quad где изображение размещается и перекрывается с реальным миром.</span><span class="sxs-lookup"><span data-stu-id="b64b1-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="b64b1-359">Это важно, так как поле координаты получить от службы после анализа трассируются обратно в этом quad определить Приблизительное расположение объекта в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="b64b1-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

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

8.  <span data-ttu-id="b64b1-360">Добавить **FinaliseLabel()** метод.</span><span class="sxs-lookup"><span data-stu-id="b64b1-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="b64b1-361">Он отвечает за:</span><span class="sxs-lookup"><span data-stu-id="b64b1-361">It is responsible for:</span></span>

    *   <span data-ttu-id="b64b1-362">Установка *метка* текст с *тега* прогноза, будучи уверенными самый высокий.</span><span class="sxs-lookup"><span data-stu-id="b64b1-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="b64b1-363">Вызов расчет *ограничивающий прямоугольник* четыре объекта, расположенный ранее, и перемещение метки в сцене.</span><span class="sxs-lookup"><span data-stu-id="b64b1-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="b64b1-364">Настройка метки глубины с помощью Raycast к *ограничивающий прямоугольник*, которого следует конфликтуют с объектом в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="b64b1-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="b64b1-365">Сброс процесс отслеживания, чтобы разрешить пользователю записывать другое изображение.</span><span class="sxs-lookup"><span data-stu-id="b64b1-365">Resetting the capture process to allow the user to capture another image.</span></span>

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

9.  <span data-ttu-id="b64b1-366">Добавить **CalculateBoundingBoxPosition()** метод, который включает ряд вычислений, необходимых для перевода *ограничивающий прямоугольник* координатах, полученных от службы и воссоздать их пропорционально на четыре.</span><span class="sxs-lookup"><span data-stu-id="b64b1-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

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

10. <span data-ttu-id="b64b1-367">Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b64b1-368">Прежде чем продолжить, откройте **CustomVisionAnalyser** класса и в **AnalyseLastImageCaptured()** метод, *раскомментируйте* следующие строки:</span><span class="sxs-lookup"><span data-stu-id="b64b1-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
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
> <span data-ttu-id="b64b1-369">Не волнуйтесь о **ImageCapture** класса сообщение «не удалось найти», он будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="b64b1-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="b64b1-370">Глава 10 — создать класс ImageCapture</span><span class="sxs-lookup"><span data-stu-id="b64b1-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="b64b1-371">Далее нужно создать класс является **ImageCapture** класса.</span><span class="sxs-lookup"><span data-stu-id="b64b1-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="b64b1-372">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="b64b1-372">This class is responsible for:</span></span>

*   <span data-ttu-id="b64b1-373">Создание образа с помощью камеры HoloLens и сохранить его в *приложения* папки.</span><span class="sxs-lookup"><span data-stu-id="b64b1-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="b64b1-374">Обработка *коснитесь* жесты пользователя.</span><span class="sxs-lookup"><span data-stu-id="b64b1-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="b64b1-375">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="b64b1-375">To create this class:</span></span>

1.  <span data-ttu-id="b64b1-376">Перейдите к **сценариев** папку, созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="b64b1-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="b64b1-377">Щелкните правой кнопкой мыши внутри папки, а затем щелкните **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b64b1-378">Назовите сценарий **ImageCapture**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="b64b1-379">Дважды щелкните новый **ImageCapture** скрипт, чтобы открыть его с **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b64b1-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="b64b1-380">Замените следующие пространства имен в верхней части файла:</span><span class="sxs-lookup"><span data-stu-id="b64b1-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="b64b1-381">Затем добавьте следующие переменные внутри **ImageCapture** класса выше **Start()** метод:</span><span class="sxs-lookup"><span data-stu-id="b64b1-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="b64b1-382">Код для **Awake()** и **Start()** теперь необходимо добавить методы:</span><span class="sxs-lookup"><span data-stu-id="b64b1-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="b64b1-383">Реализация обработчика, который будет вызываться при возникновении жеста касания:</span><span class="sxs-lookup"><span data-stu-id="b64b1-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

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
    > <span data-ttu-id="b64b1-384">Если курсор находится **зеленый**, это означает, что камера находится на изображение.</span><span class="sxs-lookup"><span data-stu-id="b64b1-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="b64b1-385">Если курсор находится **red**, это означает, что камера занят.</span><span class="sxs-lookup"><span data-stu-id="b64b1-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="b64b1-386">Добавьте метод, который приложение использует для запуска процесса захвата образа и сохранения образа:</span><span class="sxs-lookup"><span data-stu-id="b64b1-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

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

9.  <span data-ttu-id="b64b1-387">Добавление обработчиков, которые будут вызываться захваченный фотографии и когда он будет готов для анализа.</span><span class="sxs-lookup"><span data-stu-id="b64b1-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="b64b1-388">Результат затем передается **CustomVisionAnalyser** для анализа.</span><span class="sxs-lookup"><span data-stu-id="b64b1-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

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

10. <span data-ttu-id="b64b1-389">Не забудьте сохранить изменения в **Visual Studio**, перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="b64b1-390">Глава 11 - Настройка сценариев в сцене</span><span class="sxs-lookup"><span data-stu-id="b64b1-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="b64b1-391">Теперь, когда вы написали весь код, необходимые для этого проекта, пора установить сценарии в сцене, а также на prefabs, для их правильной.</span><span class="sxs-lookup"><span data-stu-id="b64b1-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="b64b1-392">В рамках **редактора Unity**в **панели иерархии**выберите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="b64b1-393">В **панели Инспектора**, с **Main Camera** , щелкните на **добавить компонент**, а затем найдите **SceneOrganiser** скрипт и Дважды щелкните, чтобы добавить его.</span><span class="sxs-lookup"><span data-stu-id="b64b1-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="b64b1-394">В **панель проекта**откройте **папку Prefabs**, перетащите **метка** prefab в *метка* пустой ссылочную целевую область, хранения в **SceneOrganiser** сценарий, который вы только что добавили к *Main Camera*, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="b64b1-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="b64b1-395">В **панели иерархии**выберите **GazeCursor** потомком **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="b64b1-396">В **панели Инспектора**, с **GazeCursor** , щелкните на **добавить компонент**, а затем найдите **GazeCursor** скрипт и Дважды щелкните, чтобы добавить его.</span><span class="sxs-lookup"><span data-stu-id="b64b1-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="b64b1-397">Опять же, в **панели иерархии**выберите **SpatialMapping** потомком **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="b64b1-398">В **панели Инспектора**, с **SpatialMapping** , щелкните на **добавить компонент**, а затем найдите **SpatialMapping** скрипт и дважды щелкните, чтобы добавить его.</span><span class="sxs-lookup"><span data-stu-id="b64b1-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="b64b1-399">Оставшиеся сценарии, которые вы еще не будет добавлен в коде в **SceneOrganiser** сценария во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="b64b1-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="b64b1-400">Глава 12 - перед сборкой</span><span class="sxs-lookup"><span data-stu-id="b64b1-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="b64b1-401">Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b64b1-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="b64b1-402">Прежде чем сделать, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="b64b1-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="b64b1-403">Все параметры, упомянутые в [Глава 3](#chapter-3---set-up-the-unity-project) заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="b64b1-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="b64b1-404">Сценарий **SceneOrganiser** присоединяется к **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="b64b1-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="b64b1-405">Сценарий **GazeCursor** присоединяется к **GazeCursor** объекта.</span><span class="sxs-lookup"><span data-stu-id="b64b1-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="b64b1-406">Сценарий **SpatialMapping** присоединяется к **SpatialMapping** объекта.</span><span class="sxs-lookup"><span data-stu-id="b64b1-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="b64b1-407">В [Глава 5](#chapter-5---create-the-customvisionanalyser-class), шаг 6:</span><span class="sxs-lookup"><span data-stu-id="b64b1-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="b64b1-408">Убедитесь, что вы вставляете вашей **ключ службы прогноза** в **predictionKey** переменной.</span><span class="sxs-lookup"><span data-stu-id="b64b1-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="b64b1-409">Вы вставили вашей **конечной точки прогноза** в **predictionEndpoint** класса.</span><span class="sxs-lookup"><span data-stu-id="b64b1-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="b64b1-410">Глава 13 - построения решения универсальной платформы Windows и загружать неопубликованные приложения</span><span class="sxs-lookup"><span data-stu-id="b64b1-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="b64b1-411">Теперь вы готовы для построения приложения, как решение универсальной платформы Windows, вы сможете развернуть систему на Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b64b1-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="b64b1-412">Чтобы начать процесс построения:</span><span class="sxs-lookup"><span data-stu-id="b64b1-412">To begin the build process:</span></span>

1.  <span data-ttu-id="b64b1-413">Перейдите к **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="b64b1-414">Такт **Unity C\# проекты**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="b64b1-415">Щелкните **Добавление открытых сцен**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="b64b1-416">Это добавит открытые сцены в сборке.</span><span class="sxs-lookup"><span data-stu-id="b64b1-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="b64b1-417">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-417">Click **Build**.</span></span> <span data-ttu-id="b64b1-418">Unity приведет к запуску *проводнике* окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в.</span><span class="sxs-lookup"><span data-stu-id="b64b1-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b64b1-419">Создайте эту папку и назовите его **приложения**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="b64b1-420">Затем с помощью **приложения** щелкните папку, **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="b64b1-421">Unity начнется построение проекта для **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="b64b1-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="b64b1-422">Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="b64b1-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="b64b1-423">Чтобы развернуть систему на Microsoft HoloLens, вам потребуется IP-адрес этого устройства (для удаленного развертывания), и проверять их также имеет **режим разработчика** значение.</span><span class="sxs-lookup"><span data-stu-id="b64b1-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="b64b1-424">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b64b1-424">To do this:</span></span>

    1.  <span data-ttu-id="b64b1-425">Хотя носить вашей HoloLens, откройте **параметры**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="b64b1-426">Перейдите к **сеть и Интернет** > **Wi-Fi** > **Дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="b64b1-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="b64b1-427">Примечание **IPv4** адрес.</span><span class="sxs-lookup"><span data-stu-id="b64b1-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="b64b1-428">Затем перейдите к **параметры**, а затем в **обновление и безопасность** > **для разработчиков**</span><span class="sxs-lookup"><span data-stu-id="b64b1-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="b64b1-429">Задайте **режим разработчика** *на*.</span><span class="sxs-lookup"><span data-stu-id="b64b1-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="b64b1-430">Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="b64b1-431">В списке выберите конфигурацию решения **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="b64b1-432">В платформу решения, выберите **x86, удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="b64b1-433">Вам будет предложено вставить **IP-адрес** удаленного устройства (Microsoft HoloLens, таким образом, который вы записали).</span><span class="sxs-lookup"><span data-stu-id="b64b1-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="b64b1-434">Перейдите к **построения** меню и щелкните **развернуть решение** для загрузки неопубликованных приложений для вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b64b1-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="b64b1-435">Приложения должны появиться в списке установленных приложений на вашей Microsoft HoloLens, Готово к запуску!</span><span class="sxs-lookup"><span data-stu-id="b64b1-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="b64b1-436">Использование приложения:</span><span class="sxs-lookup"><span data-stu-id="b64b1-436">To use the application:</span></span>

* <span data-ttu-id="b64b1-437">Рассмотрим объект, который обучения с вашей **пользовательская служба визуального распознавания Azure, обнаружение объекта**и использовать **касания**.</span><span class="sxs-lookup"><span data-stu-id="b64b1-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="b64b1-438">При обнаружении объекта абсолютном пространстве *текст метки* будет отображаться с именем тега.</span><span class="sxs-lookup"><span data-stu-id="b64b1-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b64b1-439">Каждый раз записать фотографию и отправить его в службу, можно вернуться на страницу службы и переобучить службу с вновь захваченного изображения.</span><span class="sxs-lookup"><span data-stu-id="b64b1-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="b64b1-440">В начале, вы, вероятно, придется исправить *ограничивающий поля* более точные и переобучить службу.</span><span class="sxs-lookup"><span data-stu-id="b64b1-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="b64b1-441">Поместить текст метки может не отображаться рядом с объектом, когда датчиков Microsoft HoloLens и/или SpatialTrackingComponent в Unity не удается разместить соответствующие colliders, относительно объектов реального мира.</span><span class="sxs-lookup"><span data-stu-id="b64b1-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="b64b1-442">Попробуйте использовать приложение в другой рабочей области, если это так.</span><span class="sxs-lookup"><span data-stu-id="b64b1-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="b64b1-443">Ваше видение Custom, обнаружения объекта приложения</span><span class="sxs-lookup"><span data-stu-id="b64b1-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="b64b1-444">Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Azure Custom взгляд в будущее, API обнаружения объекта, который может распознать объекта из образа, а затем обеспечивают приблизительные позиционирование для этого объекта в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="b64b1-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b64b1-445">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="b64b1-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b64b1-446">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="b64b1-446">Exercise 1</span></span>

<span data-ttu-id="b64b1-447">Добавление в текстовую подпись, использовать полупрозрачным куба для упаковки реальный объект в трехмерной *ограничивающий прямоугольник*.</span><span class="sxs-lookup"><span data-stu-id="b64b1-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b64b1-448">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="b64b1-448">Exercise 2</span></span>

<span data-ttu-id="b64b1-449">Обучение пользовательской службы визуального распознавания для распознавания объектов.</span><span class="sxs-lookup"><span data-stu-id="b64b1-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="b64b1-450">Упражнение 3</span><span class="sxs-lookup"><span data-stu-id="b64b1-450">Exercise 3</span></span>

<span data-ttu-id="b64b1-451">Воспроизведение звука, когда объект был распознан.</span><span class="sxs-lookup"><span data-stu-id="b64b1-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="b64b1-452">Упражнение 4</span><span class="sxs-lookup"><span data-stu-id="b64b1-452">Exercise 4</span></span>

<span data-ttu-id="b64b1-453">Используйте API повторного обучения в службу с помощью те же образы, анализ приложения, так чтобы служба стала более точные (выполнять прогноза и одновременно обучения).</span><span class="sxs-lookup"><span data-stu-id="b64b1-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
