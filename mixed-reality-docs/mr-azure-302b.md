---
title: Г-н и Azure 302b - Custom vision
description: Выполните этот курс, чтобы узнать, как обучить модель машинного обучения, а затем используйте обученной модели для распознавания схожие объекты в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, в пользовательской службе визуального распознавания, hololens, создающий эффект присутствия, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599999"
---
>[!NOTE]
><span data-ttu-id="7efbb-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="7efbb-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7efbb-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="7efbb-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7efbb-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7efbb-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7efbb-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="7efbb-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7efbb-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7efbb-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7efbb-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="7efbb-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="7efbb-110">Г-н и Azure 302b: Пользовательской службе визуального распознавания</span><span class="sxs-lookup"><span data-stu-id="7efbb-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="7efbb-111">В рамках этого курса вы узнаете распознавание пользовательского визуального содержимого в рамках предоставленного образа, используя возможности визуального распознавания Azure в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7efbb-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="7efbb-112">Эта служба позволит вам для обучения модели машинного обучения с использованием объекта изображения.</span><span class="sxs-lookup"><span data-stu-id="7efbb-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="7efbb-113">Затем используется обученной модели для распознавания сходных объектов, предоставленный камеры Microsoft HoloLens или камеры, подключенном к ПК для иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="7efbb-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![результат курс](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="7efbb-115">Azure пользовательской службе визуального распознавания является Microsoft Cognitive Service, что позволяет разработчикам создавать классификаторы пользовательского образа.</span><span class="sxs-lookup"><span data-stu-id="7efbb-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="7efbb-116">Эти классификаторы можно использовать с помощью новых образов для распознавания, или для классификации, объекты в рамках этого нового образа.</span><span class="sxs-lookup"><span data-stu-id="7efbb-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="7efbb-117">Служба предоставляет простой, удобный, online портал для упрощения процесса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="7efbb-118">Дополнительные сведения см. в статье [пользовательская служба визуального распознавания Azure страницы](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="7efbb-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="7efbb-119">По завершении этого курса у вас будет приложение смешанной реальности, в которое будут иметь возможность работать в двух режимах:</span><span class="sxs-lookup"><span data-stu-id="7efbb-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="7efbb-120">**Режим анализа**: Настройка пользовательской службы визуального распознавания вручную путем отправки изображений, создание тегов и службу обучения для распознавания различных объектов (в данном вариантов мыши и клавиатуры).</span><span class="sxs-lookup"><span data-stu-id="7efbb-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="7efbb-121">Затем вы создадите приложение HoloLens, которое будет создание образов с помощью камеры и постараемся понять эти объекты в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="7efbb-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="7efbb-122">**Режима обучения**: вы реализуете код, который позволит «Обучение режим» в приложении.</span><span class="sxs-lookup"><span data-stu-id="7efbb-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="7efbb-123">Режим обучения позволит вам для записи образов с помощью камеры HoloLens, загрузите захваченного изображения в службу и обучения модели пользовательской службе визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="7efbb-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="7efbb-124">Этот курс ознакомят вас для получения результатов из пользовательской службы визуального распознавания в приложение на базе Unity образец.</span><span class="sxs-lookup"><span data-stu-id="7efbb-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="7efbb-125">Это будет необходимо применение этих понятий в пользовательское приложение, возможно, вы разрабатываете.</span><span class="sxs-lookup"><span data-stu-id="7efbb-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="7efbb-126">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="7efbb-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7efbb-127">Курс</span><span class="sxs-lookup"><span data-stu-id="7efbb-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7efbb-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7efbb-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7efbb-129"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="7efbb-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="7efbb-130">Г-н и Azure 302b: Пользовательской службе визуального распознавания</span><span class="sxs-lookup"><span data-stu-id="7efbb-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="7efbb-131">✔️</span><span class="sxs-lookup"><span data-stu-id="7efbb-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7efbb-132">✔️</span><span class="sxs-lookup"><span data-stu-id="7efbb-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="7efbb-133">Хотя этот курс основное внимание уделяется HoloLens, можно также применить полученные знания в этот курс поможет вам Windows Mixed Reality иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="7efbb-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="7efbb-134">Поскольку иммерсивную (VR) не имеют доступных камеры, вам потребуется внешний камеры, подключенном к ПК.</span><span class="sxs-lookup"><span data-stu-id="7efbb-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="7efbb-135">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="7efbb-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7efbb-136">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="7efbb-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="7efbb-137">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="7efbb-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="7efbb-138">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="7efbb-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="7efbb-139">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="7efbb-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="7efbb-140">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="7efbb-141">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="7efbb-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="7efbb-142">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="7efbb-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7efbb-143">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="7efbb-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7efbb-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="7efbb-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7efbb-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7efbb-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="7efbb-146">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="7efbb-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="7efbb-147">Камера, подключенном к ПК (для разработки иммерсивных гарнитуры)</span><span class="sxs-lookup"><span data-stu-id="7efbb-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="7efbb-148">Доступ к Интернету для настройки Azure и извлечения пользовательский API компьютерного зрения</span><span class="sxs-lookup"><span data-stu-id="7efbb-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="7efbb-149">Ряд по крайней мере пять (5) образов (десяти (10) рекомендуется) для каждого объекта, на котором вы хотите пользовательской службы визуального распознавания для распознавания.</span><span class="sxs-lookup"><span data-stu-id="7efbb-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="7efbb-150">При желании можно использовать [изображений, представленных в этом курсе (компьютерной мыши и клавиатуры) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="7efbb-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="7efbb-151">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="7efbb-151">Before you start</span></span>

1.  <span data-ttu-id="7efbb-152">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="7efbb-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="7efbb-153">Настроить и проверить ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7efbb-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="7efbb-154">Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="7efbb-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="7efbb-155">Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="7efbb-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="7efbb-156">Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="7efbb-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="7efbb-157">Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="7efbb-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="7efbb-158">Глава 1 - портале службы пользовательской службе визуального распознавания</span><span class="sxs-lookup"><span data-stu-id="7efbb-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="7efbb-159">Чтобы использовать *пользовательская служба визуального распознавания* в Azure, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="7efbb-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="7efbb-160">Во-первых, [перейдите к *пользовательская служба визуального распознавания* главной странице](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="7efbb-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="7efbb-161">Щелкните **приступить к работе** кнопки.</span><span class="sxs-lookup"><span data-stu-id="7efbb-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="7efbb-162">Войдите в *пользовательская служба визуального распознавания* портала.</span><span class="sxs-lookup"><span data-stu-id="7efbb-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="7efbb-163">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="7efbb-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="7efbb-164">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="7efbb-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="7efbb-165">После входа в первый раз, вам будет предложено с *условиями* панели.</span><span class="sxs-lookup"><span data-stu-id="7efbb-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="7efbb-166">Щелкните флажок, чтобы принять условия.</span><span class="sxs-lookup"><span data-stu-id="7efbb-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="7efbb-167">Нажмите кнопку на **принимаю**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="7efbb-168">Согласии с условиями, вы перейдете к *проекты* раздел на портале.</span><span class="sxs-lookup"><span data-stu-id="7efbb-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="7efbb-169">Щелкните **новый проект**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="7efbb-170">Будет отображаться в области справа, который предложит задать некоторые поля для проекта.</span><span class="sxs-lookup"><span data-stu-id="7efbb-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="7efbb-171">Вставить *имя* для вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="7efbb-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="7efbb-172">Вставить *описание* для проекта (*необязательно*).</span><span class="sxs-lookup"><span data-stu-id="7efbb-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="7efbb-173">Выберите *группы ресурсов* или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="7efbb-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="7efbb-174">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="7efbb-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="7efbb-175">Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="7efbb-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="7efbb-176">Задайте *типы проектов* для **классификации**</span><span class="sxs-lookup"><span data-stu-id="7efbb-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="7efbb-177">Задайте *домены* как **Общие**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="7efbb-178">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="7efbb-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="7efbb-179">Когда вы закончите, нажмите кнопку **создать проект**, вы будете перенаправлены к пользовательской службы визуального распознавания страницы проекта.</span><span class="sxs-lookup"><span data-stu-id="7efbb-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="7efbb-180">Глава 2 - обучение Custom Vision проекта</span><span class="sxs-lookup"><span data-stu-id="7efbb-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="7efbb-181">Один раз на портале Custom Vision ваша основная задача заключается для обучения проекта распознавать определенные объекты на изображениях.</span><span class="sxs-lookup"><span data-stu-id="7efbb-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="7efbb-182">Требуется по крайней мере пять (5) изображения, хотя десяти (10) является предпочтительным для каждого объекта, которые требуется приложение для распознавания.</span><span class="sxs-lookup"><span data-stu-id="7efbb-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="7efbb-183">[Можно использовать образы, предоставленные в этом курсе (компьютерной мыши и клавиатуры)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="7efbb-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="7efbb-184">Для обучения проект пользовательской службы визуального распознавания:</span><span class="sxs-lookup"><span data-stu-id="7efbb-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="7efbb-185">Щелкните **+** рядом с пунктом **теги.**</span><span class="sxs-lookup"><span data-stu-id="7efbb-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="7efbb-186">Добавить **имя** объекта, чтобы распознать.</span><span class="sxs-lookup"><span data-stu-id="7efbb-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="7efbb-187">Щелкните **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="7efbb-188">Обратите внимание на **тега** был добавлен (может потребоваться перезагрузить страницу, чтобы он появился).</span><span class="sxs-lookup"><span data-stu-id="7efbb-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="7efbb-189">Установите флажок рядом с новый тег, если он еще не установлен.</span><span class="sxs-lookup"><span data-stu-id="7efbb-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="7efbb-190">Щелкните **добавить образы** в центре страницы.</span><span class="sxs-lookup"><span data-stu-id="7efbb-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="7efbb-191">Щелкните **Обзор локальных файлов**и поиска, а затем выберите образы, вы хотите отправить, минимальная — пять (5).</span><span class="sxs-lookup"><span data-stu-id="7efbb-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="7efbb-192">Помните, что все эти образы должен содержать объект, который при обучении.</span><span class="sxs-lookup"><span data-stu-id="7efbb-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="7efbb-193">Можно выбрать несколько изображений одновременно, для отправки.</span><span class="sxs-lookup"><span data-stu-id="7efbb-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="7efbb-194">Как только вы видите образы на вкладке, выберите соответствующую метку в **Мои теги** поле.</span><span class="sxs-lookup"><span data-stu-id="7efbb-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="7efbb-195">Щелкните **передача файлов**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-195">Click on **Upload files**.</span></span> <span data-ttu-id="7efbb-196">Файлы начнется передача.</span><span class="sxs-lookup"><span data-stu-id="7efbb-196">The files will begin uploading.</span></span> <span data-ttu-id="7efbb-197">Получив подтверждение отправки, нажмите кнопку **сделать**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="7efbb-198">Повторите этот процесс для создания нового **тега** с именем **клавиатуры** и загрузить соответствующий фотографии для него.</span><span class="sxs-lookup"><span data-stu-id="7efbb-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="7efbb-199">Убедитесь, что **снимите** *мыши* после создания новых тегов, поэтому, чтобы показать *Добавление изображений* окна.</span><span class="sxs-lookup"><span data-stu-id="7efbb-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="7efbb-200">Когда оба тега, Настройка, щелкните **Train**, и первой итерации обучения начнет сборку.</span><span class="sxs-lookup"><span data-stu-id="7efbb-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="7efbb-201">После построения, можно увидеть две кнопки с именем **сделать значением по умолчанию** и **прогноза URL-адрес**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="7efbb-202">Щелкните **сделать значением по умолчанию** сначала, затем щелкните **прогноза URL-адрес**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="7efbb-203">URL-адрес конечной точки, который предоставляется из этого, присваивается какое *итерации* был помечен как по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7efbb-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="7efbb-204">Таким образом, если вы позднее сделать новый *итерации* и обновить его по умолчанию, не потребуется изменять код.</span><span class="sxs-lookup"><span data-stu-id="7efbb-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="7efbb-205">Когда вы перейдете на *прогноза URL-адрес*откройте *Блокнот*, скопируйте и вставьте **URL-адрес** и **прогноза ключ**, чтобы пользователь мог его необходимо получить в том случае, когда это потребуется далее в коде.</span><span class="sxs-lookup"><span data-stu-id="7efbb-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="7efbb-206">Щелкните **шестеренки** в верхней правой части экрана.</span><span class="sxs-lookup"><span data-stu-id="7efbb-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="7efbb-207">Копировать **ключ обучения** и вставьте его в *Блокнот*, для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="7efbb-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="7efbb-208">Также скопируйте вашей **идентификатор проекта**, а также вставьте его в вашей *Блокнот* файл для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="7efbb-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="7efbb-209">Глава 3 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="7efbb-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="7efbb-210">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="7efbb-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="7efbb-211">Откройте *Unity* и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="7efbb-212">Теперь необходимо будет указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="7efbb-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="7efbb-213">Вставить **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="7efbb-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="7efbb-214">Убедитесь, что шаблон проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="7efbb-215">Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="7efbb-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="7efbb-216">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="7efbb-217">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="7efbb-218">Перейдите к **изменить* > *предпочтения** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="7efbb-219">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="7efbb-220">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="7efbb-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="7efbb-221">Перейдите к **файл > Параметры сборки** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** кнопку, чтобы применить выбранные параметры.</span><span class="sxs-lookup"><span data-stu-id="7efbb-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="7efbb-222">Оставаясь в **файл > Параметры сборки** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="7efbb-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="7efbb-223">**Целевое устройство** присваивается **Hololens**</span><span class="sxs-lookup"><span data-stu-id="7efbb-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="7efbb-224">Иммерсивную, задайте **целевое устройство** для *любого устройства*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="7efbb-225">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="7efbb-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="7efbb-226">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="7efbb-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="7efbb-227">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="7efbb-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="7efbb-228">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="7efbb-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="7efbb-229">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="7efbb-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="7efbb-230">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="7efbb-231">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="7efbb-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="7efbb-232">Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="7efbb-233">Откройте только что созданный **сцены** папку, а затем в *имя файла:* текстовое поле, тип **CustomVisionScene**, нажмите кнопку на **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="7efbb-234">Следует помнить, что необходимо сохранить в Unity кадром *активы* папку, так как они должны быть связаны с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="7efbb-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="7efbb-235">Создание папки сцены (и другие аналогичные папки) — это типичный способ структурирования проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="7efbb-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="7efbb-236">Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="7efbb-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="7efbb-237">В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.</span><span class="sxs-lookup"><span data-stu-id="7efbb-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="7efbb-238">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="7efbb-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="7efbb-239">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="7efbb-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="7efbb-240">**Сценарии версии среды выполнения** должно быть **экспериментальная (эквивалент 4.6 .NET)**, что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="7efbb-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="7efbb-241">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="7efbb-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="7efbb-242">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="7efbb-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="7efbb-243">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="7efbb-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="7efbb-244">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="7efbb-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="7efbb-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="7efbb-245">**Webcam**</span></span>

        3. <span data-ttu-id="7efbb-246">**"Микрофон"**</span><span class="sxs-lookup"><span data-stu-id="7efbb-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="7efbb-247">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.</span><span class="sxs-lookup"><span data-stu-id="7efbb-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="7efbb-248">Вернитесь в *параметры построения* *Unity C\# проекты* больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="7efbb-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="7efbb-249">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="7efbb-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="7efbb-250">Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="7efbb-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="7efbb-251">Глава 4 – Импорт Newtonsoft DLL в Unity</span><span class="sxs-lookup"><span data-stu-id="7efbb-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7efbb-252">Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 6](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="7efbb-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="7efbb-253">Этот курс требует использования **Newtonsoft** библиотеки, который можно добавить как библиотеку DLL ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7efbb-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="7efbb-254">Пакет, содержащий [эту библиотеку можно загрузить по этой ссылке](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="7efbb-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="7efbb-255">Чтобы импортировать библиотеки Newtonsoft в проект, используйте пакет Unity, который прилагается этот курс.</span><span class="sxs-lookup"><span data-stu-id="7efbb-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="7efbb-256">Добавить *.unitypackage* к Unity с помощью **активы* > *импорта* *пакета*  >  *Custom* *пакета** пункт меню.</span><span class="sxs-lookup"><span data-stu-id="7efbb-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="7efbb-257">В **Импорт пакета Unity** который появится убедитесь, что все, что в разделе (вплоть до) **подключаемые модули** выбран.</span><span class="sxs-lookup"><span data-stu-id="7efbb-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="7efbb-258">Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="7efbb-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="7efbb-259">Перейдите к **Newtonsoft** папке **подключаемые модули** в представлении проекта и выберите *подключаемый модуль Newtonsoft.Json*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="7efbb-260">С *подключаемый модуль Newtonsoft.Json* выбран, убедитесь, что **Any платформы** — **unchecked**, убедитесь, что флажок **WSAPlayer** также **unchecked**, затем нажмите кнопку **применить**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="7efbb-261">Это, чтобы убедиться, что файлы настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="7efbb-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="7efbb-262">Пометка этих подключаемых модулей позволяет настроить их только для использования в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="7efbb-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="7efbb-263">Существует другой набор их в папке WSA, которая будет использоваться после проект будет экспортирован из Unity.</span><span class="sxs-lookup"><span data-stu-id="7efbb-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="7efbb-264">Затем необходимо открыть **WSA** папку, в пределах **Newtonsoft** папки.</span><span class="sxs-lookup"><span data-stu-id="7efbb-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="7efbb-265">Вы увидите копию тот же файл, который вы только что настроили.</span><span class="sxs-lookup"><span data-stu-id="7efbb-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="7efbb-266">Выберите файл и затем в инспекторе, убедитесь, что</span><span class="sxs-lookup"><span data-stu-id="7efbb-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="7efbb-267">**Любой платформе** является **unchecked**</span><span class="sxs-lookup"><span data-stu-id="7efbb-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="7efbb-268">**только** **WSAPlayer** является **проверки**</span><span class="sxs-lookup"><span data-stu-id="7efbb-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="7efbb-269">**Не обрабатывать** является **проверки**</span><span class="sxs-lookup"><span data-stu-id="7efbb-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="7efbb-270">Глава 5 - Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="7efbb-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="7efbb-271">На панели «иерархии» выберите *Main Camera*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="7efbb-272">После выбора можно видеть все компоненты *Main Camera* в *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="7efbb-273">*Камеры* объект должен иметь имя **Main Camera** (Обратите внимание, правильность написания!)</span><span class="sxs-lookup"><span data-stu-id="7efbb-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="7efbb-274">Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания!)</span><span class="sxs-lookup"><span data-stu-id="7efbb-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="7efbb-275">Убедитесь, что **преобразование положения** присваивается **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="7efbb-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="7efbb-276">Задайте **очистить флаги** для **Одноцветная** (игнорировать это для иммерсивных гарнитура).</span><span class="sxs-lookup"><span data-stu-id="7efbb-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="7efbb-277">Задайте **фона** цвет камеры компонент **черная, альфа-значение 0 (шестнадцатеричный код: #00000000)** (игнорировать это для иммерсивных гарнитура).</span><span class="sxs-lookup"><span data-stu-id="7efbb-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="7efbb-278">Глава 6 - создание класса CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="7efbb-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="7efbb-279">На этом этапе вы готовы написать код.</span><span class="sxs-lookup"><span data-stu-id="7efbb-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="7efbb-280">Вы начнете с *CustomVisionAnalyser* класса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="7efbb-281">Вызовы **пользовательская служба визуального распознавания** внесенные в код, показанный ниже производятся с использованием **Custom Vision REST API**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="7efbb-282">С помощью это, вы увидите, как реализовать и использовать этот API (полезно для понимания того, как выполнить что-то подобное самостоятельно).</span><span class="sxs-lookup"><span data-stu-id="7efbb-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="7efbb-283">Имейте в виду, что корпорация Майкрософт предлагает **Custom Vision Service SDK** , может также использоваться для выполнения вызовов к службе.</span><span class="sxs-lookup"><span data-stu-id="7efbb-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="7efbb-284">Дополнительные сведения см. в статье [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) статьи.</span><span class="sxs-lookup"><span data-stu-id="7efbb-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="7efbb-285">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="7efbb-285">This class is responsible for:</span></span>

-   <span data-ttu-id="7efbb-286">Загрузка последней версии образа, записано в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="7efbb-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="7efbb-287">Отправка массива байтов подписки Azure *пользовательская служба визуального распознавания* экземпляра для анализа.</span><span class="sxs-lookup"><span data-stu-id="7efbb-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="7efbb-288">Получение ответа как строку JSON.</span><span class="sxs-lookup"><span data-stu-id="7efbb-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="7efbb-289">Десериализации ответа и передачи итоговый *прогноза* для *SceneOrganiser* класс, который берет на себя отображения ответа.</span><span class="sxs-lookup"><span data-stu-id="7efbb-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="7efbb-290">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-290">To create this class:</span></span>

1.  <span data-ttu-id="7efbb-291">Щелкните правой кнопкой мыши в *папке Asset* в *панель проекта*, нажмите кнопку **Создать > Папка**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="7efbb-292">Вызовите папке **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="7efbb-293">Дважды щелкните папку, только что создали, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="7efbb-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="7efbb-294">Щелкните правой кнопкой мыши внутри папки, а затем щелкните **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7efbb-295">Назовите сценарий *CustomVisionAnalyser*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="7efbb-296">Дважды щелкните новый *CustomVisionAnalyser* скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="7efbb-297">Обновите пространства имен в верхней части файла в соответствии со следующим:</span><span class="sxs-lookup"><span data-stu-id="7efbb-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="7efbb-298">В *CustomVisionAnalyser* добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="7efbb-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="7efbb-299">Убедитесь, что вы вставляете вашей **ключ прогноза** в **predictionKey** переменной и **конечной точки прогноза** в **predictionEndpoint** переменной.</span><span class="sxs-lookup"><span data-stu-id="7efbb-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="7efbb-300">Вы скопировали их *Блокнот* ранее в этом курсе.</span><span class="sxs-lookup"><span data-stu-id="7efbb-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="7efbb-301">Код для **Awake()** теперь должен быть добавлен для инициализации переменной экземпляра:</span><span class="sxs-lookup"><span data-stu-id="7efbb-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="7efbb-302">Удалить методы **Start()** и **Update()**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="7efbb-303">Добавьте соподпрограмме (с помощью статического **GetImageAsByteArray()** метод под ним), которой будет получать результаты анализа, изображения, охватываемого *ImageCapture* класса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7efbb-304">В **AnalyseImageCapture** соподпрограмме, имеется вызов *SceneOrganiser* класс, который вы еще для создания.</span><span class="sxs-lookup"><span data-stu-id="7efbb-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="7efbb-305">Таким образом **оставлю их строк закомментирована сейчас**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  <span data-ttu-id="7efbb-306">Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="7efbb-307">Глава 7 - создание класса CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="7efbb-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="7efbb-308">Класс, вы создадите теперь является *CustomVisionObjects* класса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="7efbb-309">Этот скрипт содержит некоторое количество объектов, используемые другими классами для сериализации и десериализации вызовы к *пользовательская служба визуального распознавания*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="7efbb-310">Очень важно, что вы запишите конечную точку, пользовательской службы визуального распознавания предоставляет вам, как ниже JSON структура настроен для работы с [ *версии 2.0 Custom Vision прогноза*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="7efbb-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="7efbb-311">При наличии другой версии, может потребоваться обновить ниже структуру.</span><span class="sxs-lookup"><span data-stu-id="7efbb-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="7efbb-312">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-312">To create this class:</span></span>

1.  <span data-ttu-id="7efbb-313">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7efbb-314">Вызовите сценарий *CustomVisionObjects*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="7efbb-315">Дважды щелкните новый **CustomVisionObjects** скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="7efbb-316">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="7efbb-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="7efbb-317">Удалить **Start()** и **Update()** методов внутри *CustomVisionObjects* класса; этот класс будет очищен.</span><span class="sxs-lookup"><span data-stu-id="7efbb-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="7efbb-318">Добавьте следующие классы **за пределами** *CustomVisionObjects* класса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="7efbb-319">Эти объекты используются *Newtonsoft* библиотеки для сериализации и десериализации данных ответа:</span><span class="sxs-lookup"><span data-stu-id="7efbb-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="7efbb-320">Глава 8 - создать класс VoiceRecognizer</span><span class="sxs-lookup"><span data-stu-id="7efbb-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="7efbb-321">Этот класс будет распознавать голосовой ввод от пользователя.</span><span class="sxs-lookup"><span data-stu-id="7efbb-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="7efbb-322">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-322">To create this class:</span></span>

1.  <span data-ttu-id="7efbb-323">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7efbb-324">Вызовите сценарий *VoiceRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="7efbb-325">Дважды щелкните новый **VoiceRecognizer** скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="7efbb-326">Добавьте следующие пространства имен выше *VoiceRecognizer* класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="7efbb-327">Затем добавьте следующие переменные внутри *VoiceRecognizer* класса выше *Start()* метод:</span><span class="sxs-lookup"><span data-stu-id="7efbb-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="7efbb-328">Добавить **Awake()** и **Start()** методы, последний из которых будет установлен пользователь *ключевые слова* распознаваемый при связывании тег для образа:</span><span class="sxs-lookup"><span data-stu-id="7efbb-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="7efbb-329">Удалить **Update()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="7efbb-330">Добавьте следующий обработчик, который вызывается каждый раз, когда распознается голосовой ввод:</span><span class="sxs-lookup"><span data-stu-id="7efbb-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="7efbb-331">Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="7efbb-332">Не беспокойтесь о коде, который может появиться ошибка, как вы будете обеспечивать дополнительные классы скоро, которые будет устранить их.</span><span class="sxs-lookup"><span data-stu-id="7efbb-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="7efbb-333">Глава 9 — создать класс CustomVisionTrainer</span><span class="sxs-lookup"><span data-stu-id="7efbb-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="7efbb-334">Этот класс будет цепочку серию вызовов веб-обучение *пользовательская служба визуального распознавания*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="7efbb-335">Каждый вызов будет быть подробно прямо над кодом.</span><span class="sxs-lookup"><span data-stu-id="7efbb-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="7efbb-336">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-336">To create this class:</span></span>

1.  <span data-ttu-id="7efbb-337">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7efbb-338">Вызовите сценарий *CustomVisionTrainer*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="7efbb-339">Дважды щелкните новый *CustomVisionTrainer* скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="7efbb-340">Добавьте следующие пространства имен выше *CustomVisionTrainer* класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="7efbb-341">Затем добавьте следующие переменные внутри *CustomVisionTrainer* класса выше **Start()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="7efbb-342">Обучение URL-адрес, используемый здесь предоставляется в рамках *Custom Vision обучения 1.2* документации, и имеют структуру: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="7efbb-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="7efbb-343">Дополнительные сведения см. в статье [ *Справочник по версии 1.2 обучения Custom Vision API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="7efbb-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="7efbb-344">Очень важно, что вы запишите конечную точку, пользовательской службы визуального распознавания обеспечивает для режима обучения, как использовать структуру JSON (в пределах **CustomVisionObjects** класс) настроен для работы с [  *Custom визуального распознавания v1.2 обучения*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="7efbb-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="7efbb-345">При наличии другой версии, может потребоваться обновить *объектов* структуры.</span><span class="sxs-lookup"><span data-stu-id="7efbb-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="7efbb-346">Убедитесь, что добавляемые вашей **ключ службы** (ключ обучения) значение и **идентификатор проекта** , значение которого вы записали предыдущих; это значения вы [собранные на портале ранее в курс () Глава 2, шаг 10 и более поздние версии)](#chapter-2---training-your-custom-vision-oroject).</span><span class="sxs-lookup"><span data-stu-id="7efbb-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="7efbb-347">Добавьте следующий **Start()** и **Awake()** методы.</span><span class="sxs-lookup"><span data-stu-id="7efbb-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="7efbb-348">Эти методы вызываются для инициализации и включает вызов для настройки пользовательского интерфейса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="7efbb-349">Удалить **Update()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-349">Delete the **Update()** method.</span></span> <span data-ttu-id="7efbb-350">Этот класс не потребуется.</span><span class="sxs-lookup"><span data-stu-id="7efbb-350">This class will not need it.</span></span>

7.  <span data-ttu-id="7efbb-351">Добавить **RequestTagSelection()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="7efbb-352">Этот метод является первым должен быть вызван, если образ записывается и хранятся в устройстве и готов к отправке *пользовательская служба визуального распознавания*, чтобы выполнить его обучение.</span><span class="sxs-lookup"><span data-stu-id="7efbb-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="7efbb-353">Этот метод отображает в обучающем пользовательского интерфейса, набор ключевые слова, которые пользователь может использовать для пометки образа, захваченное.</span><span class="sxs-lookup"><span data-stu-id="7efbb-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="7efbb-354">Приложение также уведомляет *VoiceRecognizer* класса, чтобы начать прослушивание голосовой ввод пользователя.</span><span class="sxs-lookup"><span data-stu-id="7efbb-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="7efbb-355">Добавить **VerifyTag()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="7efbb-356">Этот метод будет получать голосовой ввод, распознаваемые **VoiceRecognizer** класса и проверьте его допустимость и затем начать процесс обучения.</span><span class="sxs-lookup"><span data-stu-id="7efbb-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="7efbb-357">Добавить **SubmitImageForTraining()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="7efbb-358">Этот метод начнется процесс обучения пользовательской службы визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="7efbb-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="7efbb-359">Первым шагом является извлечение **идентификатор тега** из службы, связанной с проверенного речевой ввод от пользователя.</span><span class="sxs-lookup"><span data-stu-id="7efbb-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="7efbb-360">**Идентификатор тега** будет отправлен вместе с изображением.</span><span class="sxs-lookup"><span data-stu-id="7efbb-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="7efbb-361">Добавить **TrainCustomVisionProject()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="7efbb-362">Когда образ будет отправлен и тегами, этот метод будет вызываться.</span><span class="sxs-lookup"><span data-stu-id="7efbb-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="7efbb-363">Он создаст новую итерацию, будут обучены с предыдущие образы, отправить в службу, а также образ только что отправленного.</span><span class="sxs-lookup"><span data-stu-id="7efbb-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="7efbb-364">После завершения обучения, этот метод будет вызывать метод, позволяющий настраивать только что созданный **итерации** как **по умолчанию**, таким образом, чтобы конечная точка используется для анализа последних обученной итерации.</span><span class="sxs-lookup"><span data-stu-id="7efbb-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="7efbb-365">Добавить **SetDefaultIteration()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="7efbb-366">Этот метод будет задан ранее созданный и обученной итерации как *по умолчанию*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="7efbb-367">После завершения этого метода будет необходимо удалить предыдущей итерации, существующие в службе.</span><span class="sxs-lookup"><span data-stu-id="7efbb-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="7efbb-368">Во время написания этого курса ограничено максимальное десяти (10) итераций должно быть в то же время в службе.</span><span class="sxs-lookup"><span data-stu-id="7efbb-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="7efbb-369">Добавить **DeletePreviousIteration()** метод.</span><span class="sxs-lookup"><span data-stu-id="7efbb-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="7efbb-370">Этот метод будет найти и удалить предыдущей итерации не по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="7efbb-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="7efbb-371">Последний метод для добавления в этот класс является **GetImageAsByteArray()** метод, используемый на веб-вызывает преобразовать изображение, создаваемое в массив байтов.</span><span class="sxs-lookup"><span data-stu-id="7efbb-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
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

14. <span data-ttu-id="7efbb-372">Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="7efbb-373">Глава 10 — создать класс SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="7efbb-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="7efbb-374">Этот класс выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="7efbb-374">This class will:</span></span>

-   <span data-ttu-id="7efbb-375">Создание **курсор** объект необходимо подключить к Main Camera.</span><span class="sxs-lookup"><span data-stu-id="7efbb-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="7efbb-376">Создание **метка** объекта, которое будет отображаться, когда служба распознает реальных объектов.</span><span class="sxs-lookup"><span data-stu-id="7efbb-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="7efbb-377">Настройка Main Camera, подключив к ней соответствующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="7efbb-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="7efbb-378">При работе в **режим анализа**, породить метки во время выполнения, в соответствующие абсолютном относительно положения объекта Main Camera и отобразить данные, полученные из пользовательской службы визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="7efbb-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="7efbb-379">При работе в **режим обучения**, создавать пользовательский Интерфейс, который будет отображаться на разных этапах процесса обучения.</span><span class="sxs-lookup"><span data-stu-id="7efbb-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="7efbb-380">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-380">To create this class:</span></span>

1.  <span data-ttu-id="7efbb-381">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7efbb-382">Назовите сценарий *SceneOrganiser*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="7efbb-383">Дважды щелкните новый *SceneOrganiser* скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="7efbb-384">Вам потребуется только одно пространство имен, удалите остальные выше *SceneOrganiser* класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="7efbb-385">Затем добавьте следующие переменные внутри *SceneOrganiser* класса выше **Start()** метод:</span><span class="sxs-lookup"><span data-stu-id="7efbb-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="7efbb-386">Удалить **Start()** и **Update()** методы.</span><span class="sxs-lookup"><span data-stu-id="7efbb-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="7efbb-387">Прямо под переменные, добавить **Awake()** метод, который будет инициализировать класс и подготовить сцены.</span><span class="sxs-lookup"><span data-stu-id="7efbb-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="7efbb-388">Теперь добавьте **CreateCameraCursor()** метод, который создает и помещает курсор Main Camera, и **CreateLabel()** метод, который создает **Метка анализа** объекта .</span><span class="sxs-lookup"><span data-stu-id="7efbb-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="7efbb-389">Добавить **SetCameraStatus()** метод, который будет обрабатывать сообщения, предназначенные для текста сетки, предоставление состояния камеры.</span><span class="sxs-lookup"><span data-stu-id="7efbb-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="7efbb-390">Добавить **PlaceAnalysisLabel()** и **SetTagsToLastLabel()** методов, которые будут создавать и отображать данные из пользовательской службы визуального распознавания на сцене.</span><span class="sxs-lookup"><span data-stu-id="7efbb-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="7efbb-391">Наконец, добавьте **CreateTrainingUI()** метод, который запустит пользовательский Интерфейс, отображение несколько этапов процесса обучения, в том случае, когда приложение находится в режиме обучения.</span><span class="sxs-lookup"><span data-stu-id="7efbb-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="7efbb-392">Этот метод также будет иметь использовали для создания объекта состояния камеры.</span><span class="sxs-lookup"><span data-stu-id="7efbb-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="7efbb-393">Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7efbb-394">Прежде чем продолжить, откройте **CustomVisionAnalyser** класса и в **AnalyseLastImageCaptured()** метод, *раскомментируйте* следующие строки:</span><span class="sxs-lookup"><span data-stu-id="7efbb-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="7efbb-395">Глава 11. Создание класса ImageCapture</span><span class="sxs-lookup"><span data-stu-id="7efbb-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="7efbb-396">Далее нужно создать класс является *ImageCapture* класса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="7efbb-397">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="7efbb-397">This class is responsible for:</span></span>

-   <span data-ttu-id="7efbb-398">Создание образа с помощью камеры HoloLens и сохранить его в *приложения* папки.</span><span class="sxs-lookup"><span data-stu-id="7efbb-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="7efbb-399">Обработка жесты Tap от пользователя.</span><span class="sxs-lookup"><span data-stu-id="7efbb-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="7efbb-400">Обслуживание *перечисления* значение, определяющее, если приложение будет запущено *Analysis* режиме или *обучения* режим.</span><span class="sxs-lookup"><span data-stu-id="7efbb-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="7efbb-401">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="7efbb-401">To create this class:</span></span>

1.  <span data-ttu-id="7efbb-402">Перейдите к **сценариев** папку, созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="7efbb-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="7efbb-403">Щелкните правой кнопкой мыши внутри папки, а затем щелкните **Создать > C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="7efbb-404">Назовите сценарий *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="7efbb-405">Дважды щелкните новый **ImageCapture** скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="7efbb-406">Замените следующие пространства имен в верхней части файла:</span><span class="sxs-lookup"><span data-stu-id="7efbb-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="7efbb-407">Затем добавьте следующие переменные внутри *ImageCapture* класса выше **Start()** метод:</span><span class="sxs-lookup"><span data-stu-id="7efbb-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="7efbb-408">Код для **Awake()** и **Start()** теперь необходимо добавить методы:</span><span class="sxs-lookup"><span data-stu-id="7efbb-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="7efbb-409">Реализуйте обработчик, который будет вызываться при возникновении жеста касания.</span><span class="sxs-lookup"><span data-stu-id="7efbb-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="7efbb-410">В *Analysis* режиме **TapHandler** метод действует как переключатель для запуска или остановки цикла захват фото.</span><span class="sxs-lookup"><span data-stu-id="7efbb-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="7efbb-411">В *обучения* режим, она будет запись образа с камеры.</span><span class="sxs-lookup"><span data-stu-id="7efbb-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="7efbb-412">Когда курсор имеет зеленый цвет, это означает, что камера находится на изображение.</span><span class="sxs-lookup"><span data-stu-id="7efbb-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="7efbb-413">Когда курсор отображается красным цветом, это означает, что камера занят.</span><span class="sxs-lookup"><span data-stu-id="7efbb-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="7efbb-414">Добавьте метод, который приложение использует для запуска процесса захвата образа и сохранения образа.</span><span class="sxs-lookup"><span data-stu-id="7efbb-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  <span data-ttu-id="7efbb-415">Добавление обработчиков, которые будут вызываться захваченный фотографии и когда он будет готов для анализа.</span><span class="sxs-lookup"><span data-stu-id="7efbb-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="7efbb-416">Результат затем передается *CustomVisionAnalyser* или *CustomVisionTrainer* в зависимости от того, какой режим включен код.</span><span class="sxs-lookup"><span data-stu-id="7efbb-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="7efbb-417">Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="7efbb-418">Теперь, после завершения всех сценариев, вернитесь в редакторе Unity, а затем щелкните и перетащите **SceneOrganiser** класса из **сценарии** папку **Main Camera** объект в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="7efbb-419">Глава 12 - перед сборкой</span><span class="sxs-lookup"><span data-stu-id="7efbb-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="7efbb-420">Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7efbb-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="7efbb-421">Прежде чем сделать, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="7efbb-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="7efbb-422">Все параметры, упомянутые в [Глава 2](#chapter-2---training-your-custom-vision-project) заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="7efbb-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="7efbb-423">Все поля в **Main Camera**, панели Инспектора назначаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="7efbb-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="7efbb-424">Сценарий **SceneOrganiser** присоединяется к **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="7efbb-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="7efbb-425">Убедитесь, что вы вставляете вашей **ключ прогноза** в **predictionKey** переменной.</span><span class="sxs-lookup"><span data-stu-id="7efbb-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="7efbb-426">Вы вставили вашей **конечной точки прогноза** в **predictionEndpoint** переменной.</span><span class="sxs-lookup"><span data-stu-id="7efbb-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="7efbb-427">Вы вставили вашей **ключ обучения** в **trainingKey** переменной, *CustomVisionTrainer* класса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="7efbb-428">Вы вставили вашей **идентификатор проекта** в **projectId** переменной, *CustomVisionTrainer* класса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="7efbb-429">Глава 13 - сборки и загружать неопубликованные приложения</span><span class="sxs-lookup"><span data-stu-id="7efbb-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="7efbb-430">Чтобы начать *построения* процесс:</span><span class="sxs-lookup"><span data-stu-id="7efbb-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="7efbb-431">Перейдите к **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="7efbb-432">Такт **Unity C\# проекты**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="7efbb-433">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-433">Click **Build**.</span></span> <span data-ttu-id="7efbb-434">Unity приведет к запуску **проводнике** окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в.</span><span class="sxs-lookup"><span data-stu-id="7efbb-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="7efbb-435">Создайте эту папку и назовите его **приложения**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="7efbb-436">Затем с помощью **приложения** щелкните папку, **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="7efbb-437">Unity начнется построение проекта для **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="7efbb-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="7efbb-438">Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="7efbb-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="7efbb-439">Для развертывания на HoloLens:</span><span class="sxs-lookup"><span data-stu-id="7efbb-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="7efbb-440">Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="7efbb-441">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="7efbb-441">To do this:</span></span>

    1.  <span data-ttu-id="7efbb-442">Хотя носить вашей HoloLens, откройте **параметры**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="7efbb-443">Перейдите к **сеть и Интернет** > **Wi-Fi** > **Дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="7efbb-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="7efbb-444">Примечание **IPv4** адрес.</span><span class="sxs-lookup"><span data-stu-id="7efbb-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="7efbb-445">Затем перейдите к **параметры**, а затем в **обновление и безопасность** > **для разработчиков**</span><span class="sxs-lookup"><span data-stu-id="7efbb-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="7efbb-446">Задайте **режим разработчика на**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="7efbb-447">Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="7efbb-448">В *конфигурации решения* выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="7efbb-449">В *платформа решения*выберите **x86, удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="7efbb-450">Вам будет предложено вставить **IP-адрес** удаленного устройства (HoloLens, таким образом, который вы записали).</span><span class="sxs-lookup"><span data-stu-id="7efbb-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="7efbb-451">Перейдите к **построения** меню и щелкните **развернуть решение** для загрузки неопубликованных приложений для вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7efbb-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="7efbb-452">Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!</span><span class="sxs-lookup"><span data-stu-id="7efbb-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="7efbb-453">Чтобы развернуть иммерсивных гарнитура, переключите **платформа решения** для *локального компьютера*и задайте **конфигурации** для *Отладка*, с *x86* как **платформы**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="7efbb-454">Затем развернутое в локальном компьютера, с помощью **построения** пункта меню, выбрав *развернуть решение*.</span><span class="sxs-lookup"><span data-stu-id="7efbb-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="7efbb-455">Использование приложения:</span><span class="sxs-lookup"><span data-stu-id="7efbb-455">To use the application:</span></span>

<span data-ttu-id="7efbb-456">Для переключения между функциональные возможности приложения *обучения* режим и *прогноза* режиме, необходимо обновить **Тип_приложения** переменных, который находится в **Awake()** метод, расположенными в пределах *ImageCapture* класса.</span><span class="sxs-lookup"><span data-stu-id="7efbb-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="7efbb-457">или диспетчер конфигурации служб</span><span class="sxs-lookup"><span data-stu-id="7efbb-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="7efbb-458">В *обучения* режиме:</span><span class="sxs-lookup"><span data-stu-id="7efbb-458">In *Training* mode:</span></span>

- <span data-ttu-id="7efbb-459">Рассмотрим **мыши** или **клавиатуры** и использовать **касания**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="7efbb-460">После этого текст будет отображаться, предлагающее укажите тег.</span><span class="sxs-lookup"><span data-stu-id="7efbb-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="7efbb-461">Указано либо **мыши** или **клавиатуры**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="7efbb-462">В *прогноза* режиме:</span><span class="sxs-lookup"><span data-stu-id="7efbb-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="7efbb-463">Посмотреть на объект и использовать **касания**.</span><span class="sxs-lookup"><span data-stu-id="7efbb-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="7efbb-464">Текст будет отображаться, предоставляющего объект обнаружил с наибольшей вероятностью (это нормализуется).</span><span class="sxs-lookup"><span data-stu-id="7efbb-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="7efbb-465">Глава 14 - оценить и улучшить модель Custom Vision</span><span class="sxs-lookup"><span data-stu-id="7efbb-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="7efbb-466">Для предоставления доступа к службе более точные, необходимо будет по-прежнему для обучения модели, используемые для прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="7efbb-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="7efbb-467">Это достигается с помощью нового приложения с обоими *обучения* и *прогноза* режимов; по второй необходимости перейдите на портал, являющийся, что рассматривается в этой главе.</span><span class="sxs-lookup"><span data-stu-id="7efbb-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="7efbb-468">Будьте готовы вернитесь на портал много раз, чтобы постоянно улучшать модели.</span><span class="sxs-lookup"><span data-stu-id="7efbb-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="7efbb-469">Снова перейдите на портал Azure Custom Vision и после входа в проект, выберите *прогнозов* вкладке (в центре верхней части страницы):</span><span class="sxs-lookup"><span data-stu-id="7efbb-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="7efbb-470">Вы увидите все образы, которые были отправлены в службу, пока приложение запущено.</span><span class="sxs-lookup"><span data-stu-id="7efbb-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="7efbb-471">Если навести указатель мыши над изображениями, им будет предоставлен прогнозы, которые были внесены для этого образа:</span><span class="sxs-lookup"><span data-stu-id="7efbb-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="7efbb-472">Выберите один из свои образы, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="7efbb-472">Select one of your images to open it.</span></span> <span data-ttu-id="7efbb-473">После open, вы увидите, что прогнозы для изображения справа.</span><span class="sxs-lookup"><span data-stu-id="7efbb-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="7efbb-474">Если вы прогнозы были правильными, и вы хотите добавить этот образ для обучения модели службы, нажмите кнопку *Мои теги* поле ввода, а также выбрать тег, который вы хотите связать.</span><span class="sxs-lookup"><span data-stu-id="7efbb-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="7efbb-475">Когда вы закончите, нажмите кнопку *сохраните и закройте* кнопку в правом нижнем углу и перейдите к следующему изображению.</span><span class="sxs-lookup"><span data-stu-id="7efbb-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="7efbb-476">Когда вы будете обратно к сетке образов, вы заметите образов, которые вы добавления тегов (и сохранения), будут удалены.</span><span class="sxs-lookup"><span data-stu-id="7efbb-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="7efbb-477">Если вы найдете все образы, которые вы считаете, что заключенные в теги элемента в них нет, их, можно удалить, щелкая деления в этом образе (это можно сделать для нескольких образов) и выбрав *удалить* в правом верхнем углу страницы сетки.</span><span class="sxs-lookup"><span data-stu-id="7efbb-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="7efbb-478">Во всплывающем ниже, можно нажать *Да, удалить* или *нет*, чтобы подтвердить удаление, или отменить его, соответственно.</span><span class="sxs-lookup"><span data-stu-id="7efbb-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="7efbb-479">Когда будете готовы продолжить, нажмите зеленую кнопку *Train* кнопки в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="7efbb-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="7efbb-480">Модель службы будут обучены все образы которых теперь предоставляются (которые будут обеспечивают более высокую точность).</span><span class="sxs-lookup"><span data-stu-id="7efbb-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="7efbb-481">После завершения обучения обязательно откройте *сделать значением по умолчанию* еще раз кнопку, чтобы вашей *прогноза URL-адрес* продолжает использовать самые последние итерации службы.</span><span class="sxs-lookup"><span data-stu-id="7efbb-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="7efbb-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="7efbb-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="7efbb-483">Готового приложения пользовательский API компьютерного зрения</span><span class="sxs-lookup"><span data-stu-id="7efbb-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="7efbb-484">Поздравляем, вы создали приложение смешанной реальности, которое использует API компьютерного зрения Custom Azure распознать объекты реального мира, обучения модели службы и отображать уверенность в том, что было показано выше.</span><span class="sxs-lookup"><span data-stu-id="7efbb-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7efbb-485">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="7efbb-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7efbb-486">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="7efbb-486">Exercise 1</span></span>

<span data-ttu-id="7efbb-487">Обучение вашей **пользовательская служба визуального распознавания** для распознавания объектов.</span><span class="sxs-lookup"><span data-stu-id="7efbb-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="7efbb-488">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="7efbb-488">Exercise 2</span></span>

<span data-ttu-id="7efbb-489">Как способ расширить полученные сведения выполните следующие упражнения:</span><span class="sxs-lookup"><span data-stu-id="7efbb-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="7efbb-490">Воспроизведение звука, когда объект был распознан.</span><span class="sxs-lookup"><span data-stu-id="7efbb-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="7efbb-491">Упражнение 3</span><span class="sxs-lookup"><span data-stu-id="7efbb-491">Exercise 3</span></span>

<span data-ttu-id="7efbb-492">Используйте API повторного обучения в службу с помощью те же образы, анализ приложения, так чтобы служба стала более точные (выполнять прогноза и одновременно обучения).</span><span class="sxs-lookup"><span data-stu-id="7efbb-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
