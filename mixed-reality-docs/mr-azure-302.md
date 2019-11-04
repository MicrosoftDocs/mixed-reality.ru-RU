---
title: MR и Azure 302 — компьютерное зрение
description: Пройдите этот курс, чтобы узнать, как распознать визуальное содержимое в предоставленном образе с помощью Компьютерное зрение Azure в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, компьютерное зрение, hololens, иммерсивное, VR
ms.openlocfilehash: d6f792a67adfd1038ca4cdbc44b2ef1bf12a1173
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437944"
---
>[!NOTE]
><span data-ttu-id="199b6-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="199b6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="199b6-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="199b6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="199b6-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="199b6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="199b6-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="199b6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="199b6-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="199b6-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="199b6-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="199b6-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="199b6-110">MR и Azure 302: компьютерное зрение</span><span class="sxs-lookup"><span data-stu-id="199b6-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="199b6-111">В этом курсе вы узнаете, как распознать визуальное содержимое в предоставленном образе, используя возможности Компьютерное зрение Azure в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="199b6-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="199b6-112">Результаты распознавания будут отображаться в виде описательных тегов.</span><span class="sxs-lookup"><span data-stu-id="199b6-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="199b6-113">Эту службу можно использовать без обучения модели машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="199b6-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="199b6-114">Если для реализации требуется обучение модели машинного обучения, см. статью [MR and Azure 302B](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="199b6-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![результат лаборатории](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="199b6-116">Microsoft Компьютерное зрение — это набор интерфейсов API, предназначенных для предоставления разработчикам возможности обработки и анализа изображений (с возвращаемыми сведениями) с использованием расширенных алгоритмов из облака.</span><span class="sxs-lookup"><span data-stu-id="199b6-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="199b6-117">Разработчики отправляют URL-адрес образа или изображения, а алгоритмы Microsoft API компьютерного зрения анализируют визуальное содержимое на основе входных данных, выбранных пользователем, которые затем могут возвращать информацию, в том числе определение типа и качества изображения, обнаружение людей-лиц ( Возврат координат), добавление тегов или категоризация изображений.</span><span class="sxs-lookup"><span data-stu-id="199b6-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="199b6-118">Дополнительные сведения см. на [странице API компьютерного зрения Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="199b6-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="199b6-119">Прополнив этот курс, вы получите приложение HoloLens для смешанной реальности, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="199b6-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="199b6-120">С помощью жеста касания Камера HoloLens захватывает изображение.</span><span class="sxs-lookup"><span data-stu-id="199b6-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="199b6-121">Образ будет отправлен в службу API компьютерного зрения Azure.</span><span class="sxs-lookup"><span data-stu-id="199b6-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="199b6-122">Распознанные объекты будут перечислены в простой группе пользовательского интерфейса, расположенной в сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="199b6-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="199b6-123">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="199b6-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="199b6-124">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="199b6-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="199b6-125">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="199b6-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="199b6-126">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="199b6-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="199b6-127">Хождение</span><span class="sxs-lookup"><span data-stu-id="199b6-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="199b6-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="199b6-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="199b6-129"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="199b6-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="199b6-130">MR и Azure 302: компьютерное зрение</span><span class="sxs-lookup"><span data-stu-id="199b6-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="199b6-131">✔️</span><span class="sxs-lookup"><span data-stu-id="199b6-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="199b6-132">✔️</span><span class="sxs-lookup"><span data-stu-id="199b6-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="199b6-133">Хотя этот курс в основном ориентирован на HoloLens, вы можете также применить сведения, которые вы узнаете в этом курсе, к головным телефонам Windows Mixed Reality (VR).</span><span class="sxs-lookup"><span data-stu-id="199b6-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="199b6-134">Так как у головных гарнитур нет доступных камер, вам потребуется внешняя камера, подключенная к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="199b6-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="199b6-135">При работе с курсом вы увидите заметки о любых изменениях, которые могут потребоваться для поддержки головных телефонов (VR).</span><span class="sxs-lookup"><span data-stu-id="199b6-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="199b6-136">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="199b6-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="199b6-137">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="199b6-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="199b6-138">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018).</span><span class="sxs-lookup"><span data-stu-id="199b6-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="199b6-139">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.</span><span class="sxs-lookup"><span data-stu-id="199b6-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="199b6-140">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="199b6-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="199b6-141">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="199b6-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="199b6-142">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="199b6-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="199b6-143">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="199b6-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="199b6-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="199b6-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="199b6-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="199b6-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="199b6-146">Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="199b6-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="199b6-147">Камера, подключенная к компьютеру (для разработки в увлекательной гарнитуре)</span><span class="sxs-lookup"><span data-stu-id="199b6-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="199b6-148">Доступ к Интернету для установки Azure и извлечения API компьютерного зрения</span><span class="sxs-lookup"><span data-stu-id="199b6-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="199b6-149">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="199b6-149">Before you start</span></span>

1.  <span data-ttu-id="199b6-150">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="199b6-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="199b6-151">Настройка и тестирование HoloLens.</span><span class="sxs-lookup"><span data-stu-id="199b6-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="199b6-152">Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="199b6-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="199b6-153">Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="199b6-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="199b6-154">Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="199b6-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="199b6-155">Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="199b6-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="199b6-156">Глава 1 — портал Azure</span><span class="sxs-lookup"><span data-stu-id="199b6-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="199b6-157">Чтобы использовать службу *API компьютерного зрения* в Azure, необходимо настроить экземпляр службы, чтобы сделать ее доступной для приложения.</span><span class="sxs-lookup"><span data-stu-id="199b6-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="199b6-158">Сначала войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="199b6-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="199b6-159">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="199b6-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="199b6-160">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="199b6-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="199b6-161">Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу, найдите *API компьютерного зрения*и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="199b6-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Создание нового ресурса в Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="199b6-163">Слово **New** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="199b6-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="199b6-164">На новой странице будет представлено описание службы *API компьютерного зрения* .</span><span class="sxs-lookup"><span data-stu-id="199b6-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="199b6-165">В нижнем левом углу этой страницы нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="199b6-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Сведения о службе API компьютерного зрения](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="199b6-167">После нажатия кнопки **создать**:</span><span class="sxs-lookup"><span data-stu-id="199b6-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="199b6-168">Вставьте нужное **имя** для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="199b6-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="199b6-169">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="199b6-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="199b6-170">Выберите **ценовую категорию** , подходящую для вас. Если вы впервые создаете службу *API компьютерного зрения* , вам будет доступен бесплатный уровень (с именем F0).</span><span class="sxs-lookup"><span data-stu-id="199b6-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="199b6-171">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="199b6-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="199b6-172">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="199b6-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="199b6-173">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="199b6-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="199b6-174">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="199b6-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="199b6-175">Определите расположение группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="199b6-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="199b6-176">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="199b6-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="199b6-177">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="199b6-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="199b6-178">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="199b6-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="199b6-179">Нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="199b6-179">Click Create.</span></span>

        ![Сведения о создании службы](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="199b6-181">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="199b6-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="199b6-182">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="199b6-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Просмотреть новое уведомление для новой службы](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="199b6-184">Щелкните уведомление, чтобы просмотреть новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="199b6-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Нажмите кнопку Переход к ресурсу.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="199b6-186">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="199b6-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="199b6-187">Вы будете перенаправлены на новый экземпляр службы API компьютерного зрения.</span><span class="sxs-lookup"><span data-stu-id="199b6-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![Новая служба API компьютерного зрения](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="199b6-189">В рамках этого руководства приложение должно будет вызывать службу, что выполняется с помощью ключа подписки вашей службы.</span><span class="sxs-lookup"><span data-stu-id="199b6-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="199b6-190">На странице *Быстрый запуск* службы *API компьютерного зрения* , перейдите к первому шагу, *Возьмите ключи*и щелкните **ключи** (это можно также сделать, щелкнув синие клавиши-гиперссылки, расположенные в меню навигации службы. отмечается значком ключа).</span><span class="sxs-lookup"><span data-stu-id="199b6-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="199b6-191">При этом будут раскрыты *ключи*службы.</span><span class="sxs-lookup"><span data-stu-id="199b6-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="199b6-192">Сделайте копию одного из отображаемых ключей, так как это потребуется позже в проекте.</span><span class="sxs-lookup"><span data-stu-id="199b6-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="199b6-193">Вернитесь на страницу *быстрого запуска* и извлеките конечную точку.</span><span class="sxs-lookup"><span data-stu-id="199b6-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="199b6-194">Имейте в виду, что в зависимости от региона (что, если это так, вам потребуется внести изменения в код), это может быть иначе.</span><span class="sxs-lookup"><span data-stu-id="199b6-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="199b6-195">Создать копию этой конечной точки для последующего использования:</span><span class="sxs-lookup"><span data-stu-id="199b6-195">Take a copy of this endpoint for use later:</span></span>

    ![Новая служба API компьютерного зрения](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="199b6-197">Вы можете проверить, какие конечные точки находятся [здесь](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="199b6-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="199b6-198">Глава 2 — Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="199b6-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="199b6-199">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="199b6-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="199b6-200">Откройте *Unity* и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="199b6-200">Open *Unity* and click **New**.</span></span> 

    ![Запуск нового проекта Unity.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="199b6-202">Теперь необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="199b6-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="199b6-203">Вставьте **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="199b6-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="199b6-204">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="199b6-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="199b6-205">Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="199b6-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="199b6-206">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="199b6-206">Then, click **Create project**.</span></span>

    ![Укажите сведения о новом проекте Unity.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="199b6-208">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="199b6-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="199b6-209">Перейдите к разделу **изменение параметров >** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="199b6-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="199b6-210">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="199b6-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="199b6-211">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="199b6-211">Close the **Preferences** window.</span></span>

    ![Обновить настройки редактора скриптов.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="199b6-213">Затем перейдите в раздел **файл > параметры сборки** и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.</span><span class="sxs-lookup"><span data-stu-id="199b6-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Окно "параметры сборки". Переключите платформу в UWP.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="199b6-215">Несмотря на то что в **файле > параметры сборки** , убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="199b6-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="199b6-216">**Целевое устройство** имеет значение **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="199b6-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="199b6-217">Для впечатляющих головных телефонов задайте для параметра **целевое устройство** *любое устройство*.</span><span class="sxs-lookup"><span data-stu-id="199b6-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="199b6-218">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="199b6-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="199b6-219">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="199b6-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="199b6-220">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="199b6-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="199b6-221">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="199b6-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="199b6-222">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="199b6-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="199b6-223">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="199b6-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="199b6-224">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="199b6-224">A save window will appear.</span></span>
        
            ![Нажмите кнопку Добавить кнопку "открыть сцены"](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="199b6-226">Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="199b6-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создать новую папку скриптов](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="199b6-228">Откройте только что созданную папку **сцены** , а затем в поле *имя файла*: введите **MR_ComputerVisionScene**, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="199b6-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Присвойте имя новой сцене.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="199b6-230">Помните, что сцены Unity необходимо сохранять в папке *Assets* , так как они должны быть связаны с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="199b6-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="199b6-231">Создание папки «сцены» (и других аналогичных папок) — типичный способ структуризации проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="199b6-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="199b6-232">Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="199b6-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="199b6-233">В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .</span><span class="sxs-lookup"><span data-stu-id="199b6-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Откройте параметры проигрывателя.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="199b6-235">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="199b6-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="199b6-236">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="199b6-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="199b6-237">**Версия среды выполнения сценариев** должна быть **стабильной** (эквивалент .NET 3,5).</span><span class="sxs-lookup"><span data-stu-id="199b6-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="199b6-238">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="199b6-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="199b6-239">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="199b6-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Обновите другие параметры.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="199b6-241">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="199b6-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="199b6-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="199b6-242">**InternetClient**</span></span>
        2. <span data-ttu-id="199b6-243">**Бесед**</span><span class="sxs-lookup"><span data-stu-id="199b6-243">**Webcam**</span></span>

            ![Обновляются параметры публикации.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="199b6-245">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="199b6-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Обновите параметры X R.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="199b6-247">Назад в *параметрах сборки* проект _Unity C#_  больше не является серым. Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="199b6-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="199b6-248">Закройте окно параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="199b6-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="199b6-249">Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="199b6-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="199b6-250">Глава 3 — Настройка основной камеры</span><span class="sxs-lookup"><span data-stu-id="199b6-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="199b6-251">Если вы хотите пропустить компонент *установки Unity, установленный* в этом курсе, и продолжить работу с кодом, скачайте этот файл [. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), импортируйте его в проект как [пользовательский пакет](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в [главе 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="199b6-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="199b6-252">На *панели Иерархия*выберите **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="199b6-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="199b6-253">После выбора вы сможете увидеть все компоненты **основной камеры** на *панели инспектора*.</span><span class="sxs-lookup"><span data-stu-id="199b6-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="199b6-254">**Объект Camera** должен называться **основной камерой** (Обратите внимание на орфографию!)</span><span class="sxs-lookup"><span data-stu-id="199b6-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="199b6-255">Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на правописание).</span><span class="sxs-lookup"><span data-stu-id="199b6-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="199b6-256">Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .</span><span class="sxs-lookup"><span data-stu-id="199b6-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="199b6-257">Установите для параметра **сбросить флаги** **сплошной цвет** (не обращайте внимания на иммерсивное гарнитуру).</span><span class="sxs-lookup"><span data-stu-id="199b6-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="199b6-258">Задайте черный цвет **фона** для компонента камеры **, альфа-канал 0 (шестнадцатеричный код: #00000000)** (не учитывать это для иммерсивного головного телефона).</span><span class="sxs-lookup"><span data-stu-id="199b6-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Обновите компоненты камеры.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="199b6-260">Далее необходимо создать простой объект Cursor, присоединенный к **основной камере**, который поможет разместить выходные данные анализа изображений во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="199b6-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="199b6-261">Этот курсор определит центральную точку фокуса камеры.</span><span class="sxs-lookup"><span data-stu-id="199b6-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="199b6-262">Чтобы создать курсор, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="199b6-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="199b6-263">На *панели Иерархия*щелкните правой кнопкой мыши **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="199b6-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="199b6-264">В разделе **3D-объект**щелкните **Sphere**.</span><span class="sxs-lookup"><span data-stu-id="199b6-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Выберите объект курсора.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="199b6-266">Переименуйте **сферу** в **курсор** (дважды щелкните объект курсора или нажмите клавишу "F2" с выделенным объектом) и убедитесь, что он находится в качестве дочернего элемента **основной камеры**.</span><span class="sxs-lookup"><span data-stu-id="199b6-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="199b6-267">На *панели Иерархия*щелкните **курсор**левой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="199b6-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="199b6-268">Выбрав курсор, измените следующие переменные на *панели инспектора*:</span><span class="sxs-lookup"><span data-stu-id="199b6-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="199b6-269">Установить для параметра " *Преобразование* " значение **0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="199b6-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="199b6-270">Установите *масштаб* **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="199b6-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Обновите расположение и масштаб преобразования.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="199b6-272">Глава 4 — Настройка системы меток</span><span class="sxs-lookup"><span data-stu-id="199b6-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="199b6-273">После записи образа с камерой HoloLens этот образ будет отправлен в экземпляр службы *API компьютерного зрения Azure* для анализа.</span><span class="sxs-lookup"><span data-stu-id="199b6-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="199b6-274">Результаты этого анализа будут представлять собой список распознаваемых объектов, именуемых **тегами**.</span><span class="sxs-lookup"><span data-stu-id="199b6-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="199b6-275">Для отображения этих тегов в месте, где была создана фотография, будут использоваться метки (в виде трехмерного текста в мировом пространстве).</span><span class="sxs-lookup"><span data-stu-id="199b6-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="199b6-276">В следующих шагах показано, как настроить объект **Label** .</span><span class="sxs-lookup"><span data-stu-id="199b6-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="199b6-277">Щелкните правой кнопкой мыши в любом месте панели Иерархия (расположение не имеет значения), в разделе **трехмерный объект**добавьте **трехмерный текст**.</span><span class="sxs-lookup"><span data-stu-id="199b6-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="199b6-278">Назовите его **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="199b6-278">Name it **LabelText**.</span></span>

    ![Создание трехмерного текстового объекта.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="199b6-280">На *панели Иерархия*щелкните **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="199b6-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="199b6-281">Выбрав **LabelText** , настройте следующие переменные на *панели инспектора*:</span><span class="sxs-lookup"><span data-stu-id="199b6-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="199b6-282">Установить значение **0, 0,** 0</span><span class="sxs-lookup"><span data-stu-id="199b6-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="199b6-283">Установите **масштаб** **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="199b6-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="199b6-284">В **сетке текста**компонента:</span><span class="sxs-lookup"><span data-stu-id="199b6-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="199b6-285">Замените весь текст в **тексте**на "..."</span><span class="sxs-lookup"><span data-stu-id="199b6-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="199b6-286">Установить **привязку** к **середине по центру**</span><span class="sxs-lookup"><span data-stu-id="199b6-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="199b6-287">Задать **Выравнивание** по **центру**</span><span class="sxs-lookup"><span data-stu-id="199b6-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="199b6-288">Установите **размер табуляции** **4**</span><span class="sxs-lookup"><span data-stu-id="199b6-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="199b6-289">Задайте **Размер шрифта** **50**</span><span class="sxs-lookup"><span data-stu-id="199b6-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="199b6-290">Задать **Цвет** для **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="199b6-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Компонент текста](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="199b6-292">Перетащите **LabelText** из *панели Иерархия*в *папку Asset*на *панели проект*.</span><span class="sxs-lookup"><span data-stu-id="199b6-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="199b6-293">Это сделает **LabelText** prefab, чтобы его можно было создать в коде.</span><span class="sxs-lookup"><span data-stu-id="199b6-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Создайте prefab объекта LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="199b6-295">Необходимо удалить **LabelText** с *панели Иерархия*, чтобы она не отображалась в открывающей сцене.</span><span class="sxs-lookup"><span data-stu-id="199b6-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="199b6-296">Так как теперь это prefab, который будет вызываться для отдельных экземпляров из папки Assets, не нужно размещать его в сцене.</span><span class="sxs-lookup"><span data-stu-id="199b6-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="199b6-297">Итоговая структура объектов на *панели Иерархия* должна выглядеть так, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="199b6-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Окончательная структура панели иерархии.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="199b6-299">Глава 5 — Создание класса Ресултслабел</span><span class="sxs-lookup"><span data-stu-id="199b6-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="199b6-300">Первый скрипт, который необходимо создать, — это класс *ресултслабел* , который отвечает за следующее:</span><span class="sxs-lookup"><span data-stu-id="199b6-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="199b6-301">Создание меток в соответствующем мировом пространстве относительно положения камеры.</span><span class="sxs-lookup"><span data-stu-id="199b6-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="199b6-302">Отображение тегов из изображения устраняйте.</span><span class="sxs-lookup"><span data-stu-id="199b6-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="199b6-303">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="199b6-303">To create this class:</span></span> 

1.  <span data-ttu-id="199b6-304">Щелкните правой кнопкой мыши на *панели проект*, а затем **Создайте > папку**.</span><span class="sxs-lookup"><span data-stu-id="199b6-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="199b6-305">Назовите папку **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="199b6-305">Name the folder **Scripts**.</span></span> 

    ![Создайте папку Scripts.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="199b6-307">Создав папку **Scripts** , дважды щелкните ее, чтобы открыть.</span><span class="sxs-lookup"><span data-stu-id="199b6-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="199b6-308">Затем в этой папке щелкните правой кнопкой мыши и выберите **Создать >** затем  **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="199b6-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="199b6-309">Назовите сценарий *ресултслабел*.</span><span class="sxs-lookup"><span data-stu-id="199b6-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="199b6-310">Дважды щелкните новый скрипт *ресултслабел* , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="199b6-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="199b6-311">Внутри класса вставьте следующий код в класс *ресултслабел* :</span><span class="sxs-lookup"><span data-stu-id="199b6-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

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

6.  <span data-ttu-id="199b6-312">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="199b6-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="199b6-313">В *редакторе Unity*щелкните и перетащите класс *Ресултслабел* из папки **сценарии** в объект **Main** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="199b6-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="199b6-314">Щелкните **основную камеру** и посмотрите на *Панель инспектора*.</span><span class="sxs-lookup"><span data-stu-id="199b6-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="199b6-315">Вы заметите, что из скрипта, который вы только что переместили в камеру, есть два поля: **курсор** и **Метка prefab**.</span><span class="sxs-lookup"><span data-stu-id="199b6-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="199b6-316">Перетащите объект с именем **cursor** с *панели иерархий* в область **курсора**, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="199b6-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="199b6-317">Перетащите объект с именем **LabelText** из *папки Assets (ресурсы* ) на *панели проекта* в гнездо с именем **Label prefab**, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="199b6-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Установите целевые объекты ссылок в Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="199b6-319">Глава 6 — создание класса Имажекаптуре</span><span class="sxs-lookup"><span data-stu-id="199b6-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="199b6-320">Следующий класс, который предстоит создать, — это класс *имажекаптуре* .</span><span class="sxs-lookup"><span data-stu-id="199b6-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="199b6-321">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="199b6-321">This class is responsible for:</span></span>

-   <span data-ttu-id="199b6-322">Запись изображения с помощью камеры HoloLens и сохранение его в папке приложения.</span><span class="sxs-lookup"><span data-stu-id="199b6-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="199b6-323">Захват жестов касания от пользователя.</span><span class="sxs-lookup"><span data-stu-id="199b6-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="199b6-324">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="199b6-324">To create this class:</span></span> 

1.  <span data-ttu-id="199b6-325">Перейдите к созданной ранее папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="199b6-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="199b6-326">Щелкните правой кнопкой мыши внутри папки, **Создайте скрипт C# >** .</span><span class="sxs-lookup"><span data-stu-id="199b6-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="199b6-327">Вызовите скрипт *имажекаптуре*.</span><span class="sxs-lookup"><span data-stu-id="199b6-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="199b6-328">Дважды щелкните новый скрипт *имажекаптуре* , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="199b6-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="199b6-329">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="199b6-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="199b6-330">Затем добавьте следующие переменные в класс *имажекаптуре* над методом *Start ()* :</span><span class="sxs-lookup"><span data-stu-id="199b6-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="199b6-331">Переменная **тапскаунт** сохранит количество жестов касаний, полученных от пользователя.</span><span class="sxs-lookup"><span data-stu-id="199b6-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="199b6-332">Этот номер используется в именах захваченных образов.</span><span class="sxs-lookup"><span data-stu-id="199b6-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="199b6-333">Теперь необходимо добавить код для методов *"спящий" ()* и *"начало" ()* .</span><span class="sxs-lookup"><span data-stu-id="199b6-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="199b6-334">Они будут вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="199b6-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="199b6-335">Реализуйте обработчик, который будет вызываться при возникновении жеста касания.</span><span class="sxs-lookup"><span data-stu-id="199b6-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

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
 
<span data-ttu-id="199b6-336">Метод *тафандлер ()* увеличивает число касаний, полученных от пользователя, и использует текущую позицию курсора для определения места размещения новой метки.</span><span class="sxs-lookup"><span data-stu-id="199b6-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="199b6-337">Затем этот метод вызывает метод *ексекутеимажекаптуреанданалисис ()* , чтобы начать основные функциональные возможности этого приложения.</span><span class="sxs-lookup"><span data-stu-id="199b6-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="199b6-338">После записи и сохранения образа будут вызваны следующие обработчики.</span><span class="sxs-lookup"><span data-stu-id="199b6-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="199b6-339">Если процесс выполнен успешно, результат передается в *висионманажер* (который еще создается) для анализа.</span><span class="sxs-lookup"><span data-stu-id="199b6-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

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
 
9.  <span data-ttu-id="199b6-340">Затем добавьте метод, используемый приложением для запуска процесса записи образа и сохранения образа.</span><span class="sxs-lookup"><span data-stu-id="199b6-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

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
> <span data-ttu-id="199b6-341">На этом этапе вы увидите ошибку на *панели консоли редактора Unity*.</span><span class="sxs-lookup"><span data-stu-id="199b6-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="199b6-342">Это обусловлено тем, что код ссылается на класс *висионманажер* , который будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="199b6-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="199b6-343">Глава 7 — вызов Azure и анализ изображений</span><span class="sxs-lookup"><span data-stu-id="199b6-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="199b6-344">Последним скриптом, который необходимо создать, является класс *висионманажер* .</span><span class="sxs-lookup"><span data-stu-id="199b6-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="199b6-345">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="199b6-345">This class is responsible for:</span></span>

-   <span data-ttu-id="199b6-346">Загрузка последнего образа, записанного в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="199b6-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="199b6-347">Отправка массива байтов в экземпляр службы *API компьютерного зрения Azure* для анализа.</span><span class="sxs-lookup"><span data-stu-id="199b6-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="199b6-348">Получение ответа в виде строки JSON.</span><span class="sxs-lookup"><span data-stu-id="199b6-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="199b6-349">Десериализация ответа и передача результирующих тегов классу *ресултслабел* .</span><span class="sxs-lookup"><span data-stu-id="199b6-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="199b6-350">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="199b6-350">To create this class:</span></span>

1.  <span data-ttu-id="199b6-351">Дважды щелкните папку **Scripts** , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="199b6-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="199b6-352">Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать C# > скрипт**.</span><span class="sxs-lookup"><span data-stu-id="199b6-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="199b6-353">Назовите сценарий *висионманажер*.</span><span class="sxs-lookup"><span data-stu-id="199b6-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="199b6-354">Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="199b6-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="199b6-355">Обновите пространства имен, как показано ниже, в верхней части класса *висионманажер* :</span><span class="sxs-lookup"><span data-stu-id="199b6-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="199b6-356">В верхней части скрипта, *внутри* класса *висионманажер* (над методом *Start ()* ), теперь необходимо создать два *класса* , которые будут представлять Десериализованный ответ JSON из Azure:</span><span class="sxs-lookup"><span data-stu-id="199b6-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

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
    > <span data-ttu-id="199b6-357">В классах *тагдата* и *аналиседобжект* должен быть добавлен атрибут *[System. Serializable]* , прежде чем объявление может быть десериализовано с помощью библиотек Unity.</span><span class="sxs-lookup"><span data-stu-id="199b6-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="199b6-358">В классе Висионманажер следует добавить следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="199b6-358">In the VisionManager class, you should add the following variables:</span></span>

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
    > <span data-ttu-id="199b6-359">Убедитесь, что **ключ проверки подлинности** вставлен в переменную **authorizationkey согласно инструкциям** .</span><span class="sxs-lookup"><span data-stu-id="199b6-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="199b6-360">Вы заговорили **ключ проверки подлинности** в начале этого курса, [раздел 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="199b6-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="199b6-361">Переменная **висионаналисисендпоинт** может отличаться от той, которая указана в этом примере.</span><span class="sxs-lookup"><span data-stu-id="199b6-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="199b6-362">**Западная часть США** относится к экземплярам службы, созданным для региона "Западная часть США".</span><span class="sxs-lookup"><span data-stu-id="199b6-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="199b6-363">Обновите его, указав [URL-адрес конечной точки](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). Вот несколько примеров того, что может выглядеть:</span><span class="sxs-lookup"><span data-stu-id="199b6-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="199b6-364">Западная Европа: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="199b6-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="199b6-365">Юго-Восточная Азия: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="199b6-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="199b6-366">Восточная Австралия: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="199b6-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="199b6-367">Теперь необходимо добавить код для спящего режима.</span><span class="sxs-lookup"><span data-stu-id="199b6-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="199b6-368">Затем добавьте соподпрограмму (с помощью метода статического потока ниже), который будет получать результаты анализа изображения, захваченного классом *имажекаптуре* .</span><span class="sxs-lookup"><span data-stu-id="199b6-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

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

9.  <span data-ttu-id="199b6-369">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="199b6-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="199b6-370">В редакторе Unity щелкните и перетащите классы *висионманажер* и *Имажекаптуре* из папки **сценарии** в **основной объект Camera** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="199b6-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="199b6-371">Глава 8 – перед сборкой</span><span class="sxs-lookup"><span data-stu-id="199b6-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="199b6-372">Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="199b6-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="199b6-373">Перед этим убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="199b6-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="199b6-374">Все параметры, упомянутые в [главе 2](#chapter-2--set-up-the-unity-project) , заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="199b6-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="199b6-375">Все скрипты присоединяются к **главному объекту Camera** .</span><span class="sxs-lookup"><span data-stu-id="199b6-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="199b6-376">Все поля на *панели инспектора основной камеры* назначены должным образом.</span><span class="sxs-lookup"><span data-stu-id="199b6-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="199b6-377">Убедитесь, что **ключ проверки подлинности** вставлен в переменную **authorizationkey согласно инструкциям** .</span><span class="sxs-lookup"><span data-stu-id="199b6-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="199b6-378">Убедитесь, что вы также проверили конечную точку в сценарии *висионманажер* и соответствуете *региону (в этом* документе по умолчанию используется *Запад-US* ).</span><span class="sxs-lookup"><span data-stu-id="199b6-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="199b6-379">Глава 9 — Создание решения UWP и загружать неопубликованные приложения</span><span class="sxs-lookup"><span data-stu-id="199b6-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="199b6-380">Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.</span><span class="sxs-lookup"><span data-stu-id="199b6-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="199b6-381">Перейдите к разделу *параметры сборки* - **Файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="199b6-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="199b6-382">В окне " *параметры сборки* " щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="199b6-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Создание приложения из Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="199b6-384">Если это еще не так, то проекты Ticks **Unity C#** .</span><span class="sxs-lookup"><span data-stu-id="199b6-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="199b6-385">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="199b6-385">Click **Build**.</span></span> <span data-ttu-id="199b6-386">Unity запустит окно *проводника* , в котором необходимо создать, а затем выбрать папку для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="199b6-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="199b6-387">Создайте эту папку сейчас и назовите ее *app*Name.</span><span class="sxs-lookup"><span data-stu-id="199b6-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="199b6-388">Затем выберите папку *приложения* и нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="199b6-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="199b6-389">Unity начнет сборку проекта в папку *приложения* .</span><span class="sxs-lookup"><span data-stu-id="199b6-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="199b6-390">После того как Unity завершит сборку (может занять некоторое время), он откроет окно *проводника* в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).</span><span class="sxs-lookup"><span data-stu-id="199b6-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="199b6-391">Глава 10 — развертывание в HoloLens</span><span class="sxs-lookup"><span data-stu-id="199b6-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="199b6-392">Для развертывания на HoloLens выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="199b6-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="199b6-393">Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика**.</span><span class="sxs-lookup"><span data-stu-id="199b6-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="199b6-394">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="199b6-394">To do this:</span></span>

    1. <span data-ttu-id="199b6-395">Людьми HoloLens, откройте **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="199b6-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="199b6-396">Последовательно выберите пункты **сеть & интернет > Wi-Fi > дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="199b6-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="199b6-397">Запишите **IPv4** -адрес.</span><span class="sxs-lookup"><span data-stu-id="199b6-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="199b6-398">Затем вернитесь к **параметрам**и **обновите & > безопасности для разработчиков** .</span><span class="sxs-lookup"><span data-stu-id="199b6-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="199b6-399">Задайте режим разработчика на.</span><span class="sxs-lookup"><span data-stu-id="199b6-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="199b6-400">Перейдите к новой сборке Unity (папка *приложения* ) и откройте файл решения в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="199b6-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="199b6-401">В конфигурации решения выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="199b6-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="199b6-402">На платформе решения выберите **x86**, **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="199b6-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="199b6-404">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение**", чтобы загружать неопубликованные приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="199b6-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="199b6-405">Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.</span><span class="sxs-lookup"><span data-stu-id="199b6-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="199b6-406">Чтобы выполнить развертывание в иммерсивное *виртуальную*гарнитуру, задайте для **платформы решения** значение локальный компьютер и задайте для параметра **Конфигурация** значение *Отладка*( *x86* в качестве **платформы**).</span><span class="sxs-lookup"><span data-stu-id="199b6-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="199b6-407">Затем выполните развертывание на локальном компьютере с помощью **меню "сборка**" и выберите пункт " *Развернуть решение*".</span><span class="sxs-lookup"><span data-stu-id="199b6-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="199b6-408">Законченное API компьютерного зрения приложение</span><span class="sxs-lookup"><span data-stu-id="199b6-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="199b6-409">Поздравляем! вы создали приложение смешанной реальности, которое использует API компьютерного зрения Azure для распознавания реальных объектов и отображает уверенность в том, что было обнаружено.</span><span class="sxs-lookup"><span data-stu-id="199b6-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![результат лаборатории](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="199b6-411">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="199b6-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="199b6-412">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="199b6-412">Exercise 1</span></span>

<span data-ttu-id="199b6-413">Так же, как вы использовали параметр *Tags* (как свидетельствует в *конечной точке* , используемой в *висионманажер*), расширьте приложение, чтобы обнаружить другие сведения. Ознакомьтесь с другими параметрами [, к которым](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)у вас есть доступ.</span><span class="sxs-lookup"><span data-stu-id="199b6-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="199b6-414">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="199b6-414">Exercise 2</span></span>

<span data-ttu-id="199b6-415">Отображение возвращенных данных Azure в более удобном для общения и удобочитаемом виде, возможно, скрытия чисел.</span><span class="sxs-lookup"><span data-stu-id="199b6-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="199b6-416">Хотя робот может говорить пользователю.</span><span class="sxs-lookup"><span data-stu-id="199b6-416">As though a bot might be speaking to the user.</span></span>
