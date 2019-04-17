---
title: Г-н и Azure 302 - компьютерного зрения
description: Выполните этот курс, чтобы узнать, как распознать визуального содержимого в образ, предоставленный, использование компьютерного зрения Azure в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, компьютерного зрения, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597889"
---
>[!NOTE]
><span data-ttu-id="54be0-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="54be0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="54be0-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="54be0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="54be0-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="54be0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="54be0-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="54be0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="54be0-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="54be0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="54be0-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="54be0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="54be0-110">Г-н и Azure 302: Компьютерное зрение</span><span class="sxs-lookup"><span data-stu-id="54be0-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="54be0-111">В рамках этого курса вы узнаете как распознать визуальное содержимое в указанный образ, с помощью возможностей компьютерного зрения Azure в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="54be0-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="54be0-112">Результаты распознавания будут отображаться как теги с описанием.</span><span class="sxs-lookup"><span data-stu-id="54be0-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="54be0-113">Эту службу можно использовать без необходимости для обучения модели машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="54be0-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="54be0-114">Если реализация требует от обучения модели машинного обучения, см. в разделе [MR и Azure 302b](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="54be0-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![Результат лаборатории](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="54be0-116">Компьютерного зрения Microsoft — это набор API-интерфейсов позволяет предоставить разработчикам с обработка изображений и анализ (с помощью возвращают сведения), с помощью усовершенствованных алгоритмов, все из облака.</span><span class="sxs-lookup"><span data-stu-id="54be0-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="54be0-117">Разработчики добавьте изображение или URL-адрес изображения, и алгоритмы API компьютерного зрения Microsoft анализировать визуальное содержимое, в зависимости от входных данных, выбранного пользователя, который затем можно получить сведения, включая определение типа и качества изображения, обнаружить (человеческих лиц возвращение их координаты) и меток или классификации изображений.</span><span class="sxs-lookup"><span data-stu-id="54be0-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="54be0-118">Дополнительные сведения см. в статье [страницы API компьютерного зрения Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="54be0-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="54be0-119">После выполнения этого курса, у вас будет смешанной реальности HoloLens приложения, который будет осуществлять следующее:</span><span class="sxs-lookup"><span data-stu-id="54be0-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="54be0-120">С помощью жеста касания, камеры HoloLens записать образ.</span><span class="sxs-lookup"><span data-stu-id="54be0-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="54be0-121">Изображение будет отправляться службы API компьютерного зрения Azure компьютера.</span><span class="sxs-lookup"><span data-stu-id="54be0-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="54be0-122">Объект, который распознается отображаются в группе простого пользовательского интерфейса, расположенный в сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="54be0-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="54be0-123">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="54be0-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="54be0-124">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="54be0-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="54be0-125">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="54be0-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="54be0-126">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="54be0-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="54be0-127">Курс</span><span class="sxs-lookup"><span data-stu-id="54be0-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="54be0-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="54be0-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="54be0-129"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="54be0-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="54be0-130">Г-н и Azure 302: Компьютерное зрение</span><span class="sxs-lookup"><span data-stu-id="54be0-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="54be0-131">✔️</span><span class="sxs-lookup"><span data-stu-id="54be0-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="54be0-132">✔️</span><span class="sxs-lookup"><span data-stu-id="54be0-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="54be0-133">Хотя этот курс основное внимание уделяется HoloLens, можно также применить полученные знания в этот курс поможет вам Windows Mixed Reality иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="54be0-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="54be0-134">Поскольку иммерсивную (VR) не имеют доступных камеры, вам потребуется внешний камеры, подключенном к ПК.</span><span class="sxs-lookup"><span data-stu-id="54be0-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="54be0-135">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="54be0-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54be0-136">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="54be0-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="54be0-137">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="54be0-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="54be0-138">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="54be0-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="54be0-139">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="54be0-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="54be0-140">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="54be0-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="54be0-141">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="54be0-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="54be0-142">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="54be0-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="54be0-143">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="54be0-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="54be0-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="54be0-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="54be0-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="54be0-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="54be0-146">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="54be0-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="54be0-147">Камера, подключенном к ПК (для разработки иммерсивных гарнитуры)</span><span class="sxs-lookup"><span data-stu-id="54be0-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="54be0-148">Доступ к Интернету для настройки Azure и API компьютерного зрения извлечения</span><span class="sxs-lookup"><span data-stu-id="54be0-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="54be0-149">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="54be0-149">Before you start</span></span>

1.  <span data-ttu-id="54be0-150">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="54be0-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="54be0-151">Настроить и проверить ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="54be0-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="54be0-152">Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="54be0-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="54be0-153">Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="54be0-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="54be0-154">Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="54be0-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="54be0-155">Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="54be0-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="54be0-156">Глава 1 – портала Azure</span><span class="sxs-lookup"><span data-stu-id="54be0-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="54be0-157">Чтобы использовать *API компьютерного зрения* службы в Azure, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="54be0-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="54be0-158">Во-первых, войдите в [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="54be0-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="54be0-159">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="54be0-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="54be0-160">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="54be0-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="54be0-161">После входа в систему щелкните **New** в левом верхнем углу, а поиск *API компьютерного зрения*и нажмите кнопку **ввод**.</span><span class="sxs-lookup"><span data-stu-id="54be0-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Создание нового ресурса в Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="54be0-163">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="54be0-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="54be0-164">Новая страница будет предоставить описание *API компьютерного зрения* службы.</span><span class="sxs-lookup"><span data-stu-id="54be0-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="54be0-165">В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="54be0-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Сведения о службе api компьютерного зрения компьютера](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="54be0-167">Когда вы перейдете на **создать**:</span><span class="sxs-lookup"><span data-stu-id="54be0-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="54be0-168">Вставить нужный **имя** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="54be0-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="54be0-169">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="54be0-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="54be0-170">Выберите **Ценовая** подходит для вас, если это первое времени на создание *API компьютерного зрения* службы, уровень "бесплатный" (с именем F0) должны быть доступны для вас.</span><span class="sxs-lookup"><span data-stu-id="54be0-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="54be0-171">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="54be0-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="54be0-172">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="54be0-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="54be0-173">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="54be0-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="54be0-174">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="54be0-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="54be0-175">Определите расположение для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="54be0-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="54be0-176">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="54be0-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="54be0-177">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="54be0-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="54be0-178">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="54be0-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="54be0-179">Нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="54be0-179">Click Create.</span></span>

        ![Сведения о создании службы](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="54be0-181">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="54be0-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="54be0-182">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="54be0-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![См. в разделе новое уведомление для новой службы](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="54be0-184">Щелкните уведомление, чтобы изучить ваш новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="54be0-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Нажмите кнопку Go для ресурсов.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="54be0-186">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="54be0-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="54be0-187">Откроется в новом экземпляре службы API компьютерного зрения.</span><span class="sxs-lookup"><span data-stu-id="54be0-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![В новой службе API компьютерного зрения](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="54be0-189">В этом руководстве описано приложение должно выполнять вызовы в службу, которая осуществляется с помощью ключа подписки вашей службы.</span><span class="sxs-lookup"><span data-stu-id="54be0-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="54be0-190">Из *быстрого запуска* странице из вашей *API компьютерного зрения* службы, перейдите к первому шагу *получите ключи*и нажмите кнопку **ключи** () Это можно также сделать, щелкнув синий гиперссылки ключи, расположенный в меню навигации служб, обозначенное с помощью значок ключа).</span><span class="sxs-lookup"><span data-stu-id="54be0-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="54be0-191">Это позволит службе *ключи*.</span><span class="sxs-lookup"><span data-stu-id="54be0-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="54be0-192">Сделайте копию один из отображаемых разделов, так как он потребуется позже в проекте.</span><span class="sxs-lookup"><span data-stu-id="54be0-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="54be0-193">Вернитесь к *быстрого запуска* странице и оттуда выборку конечной точки.</span><span class="sxs-lookup"><span data-stu-id="54be0-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="54be0-194">Имейте в виду, вам может различаться в зависимости от региона (который в противном случае необходимо будет внести изменения в код позже).</span><span class="sxs-lookup"><span data-stu-id="54be0-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="54be0-195">Сделайте копию этой конечной точки для дальнейшего использования:</span><span class="sxs-lookup"><span data-stu-id="54be0-195">Take a copy of this endpoint for use later:</span></span>

    ![В новой службе API компьютерного зрения](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="54be0-197">Вы можете проверить, каковы конечных точках [здесь](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="54be0-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="54be0-198">Глава 2 – Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="54be0-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="54be0-199">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="54be0-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="54be0-200">Откройте *Unity* и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="54be0-200">Open *Unity* and click **New**.</span></span> 

    ![Начните новый проект Unity.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="54be0-202">Теперь необходимо будет указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="54be0-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="54be0-203">Вставить **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="54be0-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="54be0-204">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="54be0-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="54be0-205">Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="54be0-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="54be0-206">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="54be0-206">Then, click **Create project**.</span></span>

    ![Укажите сведения для нового проекта Unity.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="54be0-208">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="54be0-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="54be0-209">Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="54be0-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="54be0-210">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="54be0-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="54be0-211">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="54be0-211">Close the **Preferences** window.</span></span>

    ![Обновите настройки редактора скриптов.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="54be0-213">Перейдите к **файл > Параметры сборки** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** кнопку, чтобы применить выбранные параметры.</span><span class="sxs-lookup"><span data-stu-id="54be0-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Создавайте окно "Параметры", переключить платформу для универсальной платформы Windows.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="54be0-215">Оставаясь в **файл > Параметры сборки** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="54be0-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="54be0-216">**Целевое устройство** присваивается **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="54be0-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="54be0-217">Иммерсивную, задайте **целевое устройство** для *любого устройства*.</span><span class="sxs-lookup"><span data-stu-id="54be0-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="54be0-218">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="54be0-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="54be0-219">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="54be0-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="54be0-220">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="54be0-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="54be0-221">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="54be0-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="54be0-222">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="54be0-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="54be0-223">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="54be0-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="54be0-224">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="54be0-224">A save window will appear.</span></span>
        
            ![Нажмите кнопку Добавить кнопку open сцены](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="54be0-226">Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="54be0-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создание новой папки scripts](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="54be0-228">Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **MR_ComputerVisionScene**, нажмите кнопку **Сохранить** .</span><span class="sxs-lookup"><span data-stu-id="54be0-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Присвойте имя новой сцены.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="54be0-230">Следует помнить, что необходимо сохранить в Unity кадром *активы* папку, так как они должны быть связаны с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="54be0-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="54be0-231">Создание папки сцены (и другие аналогичные папки) — это типичный способ структурирования проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="54be0-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="54be0-232">Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="54be0-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="54be0-233">В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.</span><span class="sxs-lookup"><span data-stu-id="54be0-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Открытие параметров проигрывателя.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="54be0-235">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="54be0-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="54be0-236">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="54be0-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="54be0-237">**Версия среды выполнения сценариев** должно быть **стабильной** (.NET 3.5 эквивалент).</span><span class="sxs-lookup"><span data-stu-id="54be0-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="54be0-238">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="54be0-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="54be0-239">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="54be0-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Обновите другие параметры.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="54be0-241">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="54be0-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="54be0-242">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="54be0-242">**InternetClient**</span></span>
        2. <span data-ttu-id="54be0-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="54be0-243">**Webcam**</span></span>

            ![Обновление параметров публикации.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="54be0-245">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.</span><span class="sxs-lookup"><span data-stu-id="54be0-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Обновление параметров R X.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="54be0-247">Вернитесь в *параметры построения* _Unity C#_  проектов больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="54be0-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="54be0-248">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="54be0-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="54be0-249">Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="54be0-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="54be0-250">Глава 3 — Настройка Main Camera</span><span class="sxs-lookup"><span data-stu-id="54be0-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54be0-251">Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), импортировать его в проект в качестве [пользовательского пакета ](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="54be0-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="54be0-252">В *панели иерархии*выберите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="54be0-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="54be0-253">После выбора можно видеть все компоненты **Main Camera** в *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="54be0-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="54be0-254">**Объекта Camera** должен иметь имя **Main Camera** (Обратите внимание, правильность написания!)</span><span class="sxs-lookup"><span data-stu-id="54be0-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="54be0-255">Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания!)</span><span class="sxs-lookup"><span data-stu-id="54be0-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="54be0-256">Убедитесь, что **преобразование положения** присваивается **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="54be0-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="54be0-257">Задайте **очистить флаги** для **Одноцветная** (игнорировать это для иммерсивных гарнитура).</span><span class="sxs-lookup"><span data-stu-id="54be0-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="54be0-258">Задайте **фона** цвет компонента камеры для **черная, альфа-значение 0 (шестнадцатеричный код: #00000000)** (игнорировать это для иммерсивных гарнитура).</span><span class="sxs-lookup"><span data-stu-id="54be0-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Обновления компонентов камеры.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="54be0-260">Далее необходимо создать простой «курсор» объект, присоединяемый к **Main Camera**, обеспечивают размещение анализ образов выходные данные при приложения.</span><span class="sxs-lookup"><span data-stu-id="54be0-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="54be0-261">Этот курсор определит центральную точку фокуса камеры.</span><span class="sxs-lookup"><span data-stu-id="54be0-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="54be0-262">Чтобы создать курсора:</span><span class="sxs-lookup"><span data-stu-id="54be0-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="54be0-263">В *панели иерархии*, щелкните правой кнопкой мыши **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="54be0-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="54be0-264">В разделе **трехмерный объект**, щелкните **Sphere**.</span><span class="sxs-lookup"><span data-stu-id="54be0-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Выберите объект курсора.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="54be0-266">Переименуйте **Sphere** для **курсор** (дважды щелкните объект курсора или нажмите кнопку «F2» клавиатуры объект выбран) и убедитесь, что он находится в качестве дочернего элемента **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="54be0-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="54be0-267">В *панели иерархии*, щелчок левой кнопкой на **курсор**.</span><span class="sxs-lookup"><span data-stu-id="54be0-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="54be0-268">Курсор выбран, настройте следующие переменные в *панели Инспектора*:</span><span class="sxs-lookup"><span data-stu-id="54be0-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="54be0-269">Задайте *преобразование положения* для **0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="54be0-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="54be0-270">Задайте *масштабирования* для **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="54be0-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Обновление преобразования положение и размер.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="54be0-272">Глава 4 – установки системы метки</span><span class="sxs-lookup"><span data-stu-id="54be0-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="54be0-273">Созданный изображение с камеры HoloLens, этот образ будет отправляться в *API компьютерного зрения Azure* экземпляр службы для анализа.</span><span class="sxs-lookup"><span data-stu-id="54be0-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="54be0-274">Результаты этого анализа будет представлять собой список распознанных объекты, называемые **теги**.</span><span class="sxs-lookup"><span data-stu-id="54be0-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="54be0-275">Эти теги отображаются в указанном месте снимок был сделан, будет использовать метки (в виде трехмерного текста в абсолютном пространстве).</span><span class="sxs-lookup"><span data-stu-id="54be0-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="54be0-276">Ниже будет показано, как настроить **метка** объекта.</span><span class="sxs-lookup"><span data-stu-id="54be0-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="54be0-277">Щелкните правой кнопкой мыши в любом месте панели «иерархии» (расположение не имеет значения, на этом этапе) в разделе **трехмерный объект**, добавьте **трехмерного текста**.</span><span class="sxs-lookup"><span data-stu-id="54be0-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="54be0-278">Назовите его **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="54be0-278">Name it **LabelText**.</span></span>

    ![Создание трехмерного текста объекта.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="54be0-280">В *панели иерархии*, щелчок левой кнопкой на **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="54be0-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="54be0-281">С помощью **LabelText** флажок установлен, настройте следующие переменные в *панели Инспектора*:</span><span class="sxs-lookup"><span data-stu-id="54be0-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="54be0-282">Задайте **позиции** для **0,0,0**</span><span class="sxs-lookup"><span data-stu-id="54be0-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="54be0-283">Задайте **масштабирования** для **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="54be0-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="54be0-284">В компоненте **Mesh текст**:</span><span class="sxs-lookup"><span data-stu-id="54be0-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="54be0-285">Замените весь текст в **текст**, с помощью «...»</span><span class="sxs-lookup"><span data-stu-id="54be0-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="54be0-286">Задайте **привязки** для **в середине**</span><span class="sxs-lookup"><span data-stu-id="54be0-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="54be0-287">Задайте **выравнивание** для **Center**</span><span class="sxs-lookup"><span data-stu-id="54be0-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="54be0-288">Задайте **размера табуляции** для **4**</span><span class="sxs-lookup"><span data-stu-id="54be0-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="54be0-289">Задайте **размер шрифта** для **50**</span><span class="sxs-lookup"><span data-stu-id="54be0-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="54be0-290">Задайте **цвет** для **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="54be0-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Компонент текста](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="54be0-292">Перетащите **LabelText** из *панели иерархии*, в *папке Asset*с соблюдением в *проекта панели*.</span><span class="sxs-lookup"><span data-stu-id="54be0-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="54be0-293">Это сделает **LabelText** готового блока, так что он может быть создано в коде.</span><span class="sxs-lookup"><span data-stu-id="54be0-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Создайте prefab LabelText объекта.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="54be0-295">Следует удалить **LabelText** из *панели иерархии*, так что он не отображается в сцене открытия.</span><span class="sxs-lookup"><span data-stu-id="54be0-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="54be0-296">Так как это готового блока, который будет вызвать в отдельных экземплярах из папки средств, нет необходимости чтобы сохранить его в сцене.</span><span class="sxs-lookup"><span data-stu-id="54be0-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="54be0-297">Структура результирующий объект в *панели иерархии* должно быть, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="54be0-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Окончательная структура панели иерархии.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="54be0-299">Глава 5 – создать класс ResultsLabel</span><span class="sxs-lookup"><span data-stu-id="54be0-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="54be0-300">Первый скрипт, чтобы создать *ResultsLabel* класс, который отвечает за следующее:</span><span class="sxs-lookup"><span data-stu-id="54be0-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="54be0-301">Создание метки в соответствующие мировом пространстве, относительно положения камеры.</span><span class="sxs-lookup"><span data-stu-id="54be0-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="54be0-302">Отображение тегов из Anaysis изображения.</span><span class="sxs-lookup"><span data-stu-id="54be0-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="54be0-303">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="54be0-303">To create this class:</span></span> 

1.  <span data-ttu-id="54be0-304">Щелкните правой кнопкой мыши в *проекта панели*, затем **Создать > Папка**.</span><span class="sxs-lookup"><span data-stu-id="54be0-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="54be0-305">Назовите папку **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="54be0-305">Name the folder **Scripts**.</span></span> 

    ![Создайте папку scripts.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="54be0-307">С помощью **сценариев** папке создайте, дважды щелкните его, чтобы открыть.</span><span class="sxs-lookup"><span data-stu-id="54be0-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="54be0-308">Затем в этой папке, щелкните правой кнопкой мыши и выберите **Создать >** затем  **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="54be0-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="54be0-309">Назовите сценарий *ResultsLabel*.</span><span class="sxs-lookup"><span data-stu-id="54be0-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="54be0-310">Дважды щелкните новый *ResultsLabel* скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="54be0-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="54be0-311">Внутри класса вставьте следующий код в *ResultsLabel* класса:</span><span class="sxs-lookup"><span data-stu-id="54be0-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="54be0-312">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="54be0-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="54be0-313">Вернитесь в *редактора Unity*щелкните и перетащите *ResultsLabel* класса из **сценарии** папку для **Main Camera** объекта в  *Панель иерархии*.</span><span class="sxs-lookup"><span data-stu-id="54be0-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="54be0-314">Щелкните **Main Camera** и просмотрите *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="54be0-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="54be0-315">Обратите внимание, что из сценария, который пользователь перетащил в камеру, содержатся два поля: **Курсор** и **метки Prefab**.</span><span class="sxs-lookup"><span data-stu-id="54be0-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="54be0-316">Перетащите объект вызывается **курсор** из *панели иерархии* в слот с именем **курсор**, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="54be0-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="54be0-317">Перетащите объект вызывается **LabelText** из *папку Assets* в *панель проекта* в слот с именем **метка Prefab**, как показано на изображение ниже.</span><span class="sxs-lookup"><span data-stu-id="54be0-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Задайте целевые объекты ссылки в Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="54be0-319">Глава 6 – создать класс ImageCapture</span><span class="sxs-lookup"><span data-stu-id="54be0-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="54be0-320">Далее нужно создать класс является *ImageCapture* класса.</span><span class="sxs-lookup"><span data-stu-id="54be0-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="54be0-321">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="54be0-321">This class is responsible for:</span></span>

-   <span data-ttu-id="54be0-322">Создание образа с помощью камеры HoloLens и сохранив его в папке приложения.</span><span class="sxs-lookup"><span data-stu-id="54be0-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="54be0-323">Записи жесты Tap от пользователя.</span><span class="sxs-lookup"><span data-stu-id="54be0-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="54be0-324">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="54be0-324">To create this class:</span></span> 

1.  <span data-ttu-id="54be0-325">Перейдите к **сценариев** папку, созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="54be0-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="54be0-326">Щелкните правой кнопкой мыши внутри папки **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="54be0-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="54be0-327">Вызовите сценарий *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="54be0-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="54be0-328">Дважды щелкните новый *ImageCapture* скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="54be0-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="54be0-329">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="54be0-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="54be0-330">Затем добавьте следующие переменные внутри *ImageCapture* класса выше *Start()* метод:</span><span class="sxs-lookup"><span data-stu-id="54be0-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="54be0-331">**TapsCount** хранятся в переменной число жестов касания, собранные от пользователя.</span><span class="sxs-lookup"><span data-stu-id="54be0-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="54be0-332">Это число используется в именах образы, созданные.</span><span class="sxs-lookup"><span data-stu-id="54be0-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="54be0-333">Код для *Awake()* и *Start()* методы теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="54be0-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="54be0-334">Это будет вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="54be0-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="54be0-335">Реализуйте обработчик, который будет вызываться при возникновении жеста касания.</span><span class="sxs-lookup"><span data-stu-id="54be0-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="54be0-336">*TapHandler()* метод увеличивает на единицу числом ответвлений, собранные от пользователя и использует текущей позиции курсора для определения места для размещения новую метку.</span><span class="sxs-lookup"><span data-stu-id="54be0-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="54be0-337">Этот метод вызывает *ExecuteImageCaptureAndAnalysis()* метод для начала основные функциональные возможности этого приложения.</span><span class="sxs-lookup"><span data-stu-id="54be0-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="54be0-338">После создания и сохранения изображения будет вызываться следующие обработчики.</span><span class="sxs-lookup"><span data-stu-id="54be0-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="54be0-339">Если процесс прошел успешно, результат передается *VisionManager* (который вы еще для создания) для анализа.</span><span class="sxs-lookup"><span data-stu-id="54be0-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="54be0-340">Затем добавьте метод, который приложение использует для запуска процесса захвата образа и сохранения образа.</span><span class="sxs-lookup"><span data-stu-id="54be0-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="54be0-341">На этом этапе вы заметите ошибку в *панель консоли редактора Unity*.</span><span class="sxs-lookup"><span data-stu-id="54be0-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="54be0-342">Это так, как код ссылается на *VisionManager* класс, который будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="54be0-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="54be0-343">Глава 7 – вызов к Azure и анализ образов</span><span class="sxs-lookup"><span data-stu-id="54be0-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="54be0-344">— Последний скрипт, чтобы создать *VisionManager* класса.</span><span class="sxs-lookup"><span data-stu-id="54be0-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="54be0-345">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="54be0-345">This class is responsible for:</span></span>

-   <span data-ttu-id="54be0-346">Загрузка последней версии образа, записано в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="54be0-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="54be0-347">Массив байтов для отправки вашего *API компьютерного зрения Azure* экземпляр службы для анализа.</span><span class="sxs-lookup"><span data-stu-id="54be0-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="54be0-348">Получение ответа как строку JSON.</span><span class="sxs-lookup"><span data-stu-id="54be0-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="54be0-349">Десериализации ответа и передачи итоговый теги для *ResultsLabel* класса.</span><span class="sxs-lookup"><span data-stu-id="54be0-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="54be0-350">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="54be0-350">To create this class:</span></span>

1.  <span data-ttu-id="54be0-351">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="54be0-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="54be0-352">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="54be0-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="54be0-353">Назовите сценарий *VisionManager*.</span><span class="sxs-lookup"><span data-stu-id="54be0-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="54be0-354">Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54be0-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="54be0-355">Обновите пространства имен должны совпадать, как показано ниже, в верхней части *VisionManager* класса:</span><span class="sxs-lookup"><span data-stu-id="54be0-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="54be0-356">В верхней части сценария *внутри* *VisionManager* класс (выше *Start()* метод), необходимо создать два *классы* , Представляет Десериализованный ответ JSON от Azure:</span><span class="sxs-lookup"><span data-stu-id="54be0-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="54be0-357">*TagData* и *AnalysedObject* классы должны иметь *[System.Serializable]* атрибут, добавленный перед объявлением, чтобы иметь возможность десериализации в Unity библиотеки.</span><span class="sxs-lookup"><span data-stu-id="54be0-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="54be0-358">В классе VisionManager следует добавить следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="54be0-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="54be0-359">Убедитесь, что вы вставляете вашей **ключом проверки подлинности** в **authorizationKey** переменной.</span><span class="sxs-lookup"><span data-stu-id="54be0-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="54be0-360">Будет записанными вашей **ключом проверки подлинности** в начале этого курса [главе 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="54be0-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="54be0-361">**VisionAnalysisEndpoint** переменной может отличаться от указанного в этом примере.</span><span class="sxs-lookup"><span data-stu-id="54be0-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="54be0-362">**Западно-нам** строго относится к экземплярам службы, созданные для западной части США.</span><span class="sxs-lookup"><span data-stu-id="54be0-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="54be0-363">Обновить его с вашей [URL-адрес конечной точки](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); здесь являются некоторые примеры того, что это может выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="54be0-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="54be0-364">Западная Европа: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="54be0-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="54be0-365">Юго-Восточной Азии: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="54be0-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="54be0-366">Восточная Австралия: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="54be0-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="54be0-367">Теперь необходимо добавить код для Awake.</span><span class="sxs-lookup"><span data-stu-id="54be0-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="54be0-368">Добавьте соподпрограмме (методом статического потока под ним), которой будет получать результаты анализа, изображения, охватываемым *ImageCapture* класса.</span><span class="sxs-lookup"><span data-stu-id="54be0-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="54be0-369">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="54be0-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="54be0-370">Обратно в редакторе Unity, щелкните и перетащите *VisionManager* и *ImageCapture* классы из **сценарии** папку **Main Camera**объекта в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="54be0-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="54be0-371">Глава 8 – перед сборкой</span><span class="sxs-lookup"><span data-stu-id="54be0-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="54be0-372">Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="54be0-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="54be0-373">Прежде чем сделать, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="54be0-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="54be0-374">Все параметры, упомянутые в [Глава 2](#chapter-2--set-up-the-unity-project) заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="54be0-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="54be0-375">Все сценарии, присоединяются к **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="54be0-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="54be0-376">Все поля в *главной панели Инспектора камеры* назначаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="54be0-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="54be0-377">Убедитесь, что вы вставляете вашей **ключом проверки подлинности** в **authorizationKey** переменной.</span><span class="sxs-lookup"><span data-stu-id="54be0-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="54be0-378">Убедитесь, что вы также проверили конечной точки вашей *VisionManager* скрипт, и что он выравнивает по *вашей* регион (в этом документе используется *западно-нам* по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="54be0-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="54be0-379">Глава 9 – построения решения универсальной платформы Windows и загружать неопубликованные приложения</span><span class="sxs-lookup"><span data-stu-id="54be0-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="54be0-380">Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.</span><span class="sxs-lookup"><span data-stu-id="54be0-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="54be0-381">Перейдите к *параметры сборки* - **файл > Параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="54be0-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="54be0-382">Из *параметры построения* окно, нажмите кнопку **построения**.</span><span class="sxs-lookup"><span data-stu-id="54be0-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Создание приложения из Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="54be0-384">Если не сделали, установите **Unity C# проекты**.</span><span class="sxs-lookup"><span data-stu-id="54be0-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="54be0-385">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="54be0-385">Click **Build**.</span></span> <span data-ttu-id="54be0-386">Unity приведет к запуску *проводнике* окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в.</span><span class="sxs-lookup"><span data-stu-id="54be0-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="54be0-387">Создайте эту папку и назовите его *приложения*.</span><span class="sxs-lookup"><span data-stu-id="54be0-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="54be0-388">Затем с помощью *приложения* папку, нажмите клавишу **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="54be0-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="54be0-389">Unity начнется построение проекта для *приложения* папки.</span><span class="sxs-lookup"><span data-stu-id="54be0-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="54be0-390">Один раз Unity завершил построение (может занять некоторое время), он будет открыт *проводнике* окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="54be0-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="54be0-391">Глава 10 — развертывание в HoloLens</span><span class="sxs-lookup"><span data-stu-id="54be0-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="54be0-392">Для развертывания на HoloLens:</span><span class="sxs-lookup"><span data-stu-id="54be0-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="54be0-393">Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="54be0-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="54be0-394">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="54be0-394">To do this:</span></span>

    1. <span data-ttu-id="54be0-395">Хотя носить вашей HoloLens, откройте **параметры**.</span><span class="sxs-lookup"><span data-stu-id="54be0-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="54be0-396">Перейдите к **сеть и Интернет > Wi-Fi > Дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="54be0-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="54be0-397">Примечание **IPv4** адрес.</span><span class="sxs-lookup"><span data-stu-id="54be0-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="54be0-398">Затем перейдите к **параметры**, а затем в **обновление и безопасность > для разработчиков**</span><span class="sxs-lookup"><span data-stu-id="54be0-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="54be0-399">Включен режим разработчика.</span><span class="sxs-lookup"><span data-stu-id="54be0-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="54be0-400">Перейдите к новой сборки Unity ( *приложения* папки) и откройте файл решения с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="54be0-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="54be0-401">В списке выберите конфигурацию решения **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="54be0-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="54be0-402">В платформу решения, выберите **x86**, **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="54be0-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="54be0-404">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение**, чтобы загрузить неопубликованное приложение для вашего HoloLens.</span><span class="sxs-lookup"><span data-stu-id="54be0-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="54be0-405">Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!</span><span class="sxs-lookup"><span data-stu-id="54be0-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="54be0-406">Чтобы развернуть иммерсивных гарнитура, переключите **платформа решения** для *локального компьютера*и задайте **конфигурации** для *Отладка*, с *x86* как **платформы**.</span><span class="sxs-lookup"><span data-stu-id="54be0-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="54be0-407">Затем развернуть на локальный компьютер, с помощью **меню "сборка"**, выбрав *развернуть решение*.</span><span class="sxs-lookup"><span data-stu-id="54be0-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="54be0-408">Готового приложения API компьютерного зрения</span><span class="sxs-lookup"><span data-stu-id="54be0-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="54be0-409">Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Azure API компьютерного зрения для распознавания объектов реального мира и отображения уверенность в том, что было показано выше.</span><span class="sxs-lookup"><span data-stu-id="54be0-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![Результат лаборатории](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="54be0-411">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="54be0-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="54be0-412">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="54be0-412">Exercise 1</span></span>

<span data-ttu-id="54be0-413">Так же, как вы использовали *теги* параметра (как видно в *конечной точки* используется в *VisionManager*), расширение приложения для обнаружения других сведений о; взглянем на какие другие параметры, у вас есть доступ к [здесь](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="54be0-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="54be0-414">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="54be0-414">Exercise 2</span></span>

<span data-ttu-id="54be0-415">Отображение возвращаемых данных Azure, более естественный и для чтения, возможно скрытие чисел.</span><span class="sxs-lookup"><span data-stu-id="54be0-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="54be0-416">Так, будто программы-робота, может обращаться к пользователю.</span><span class="sxs-lookup"><span data-stu-id="54be0-416">As though a bot might be speaking to the user.</span></span>
