---
title: Г-н и 304 Azure — распознавание лиц.
description: Выполните этот курс, чтобы узнать, как реализовать распознавание лиц Azure в приложениях смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанного реальность, academy, unity, учебник, api, сталкиваются с распознавания, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603808"
---
>[!NOTE]
><span data-ttu-id="2ec53-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="2ec53-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2ec53-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="2ec53-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2ec53-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ec53-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2ec53-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="2ec53-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2ec53-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ec53-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="2ec53-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="2ec53-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="2ec53-110">Г-н и Azure 304: Распознавание лиц.</span><span class="sxs-lookup"><span data-stu-id="2ec53-110">MR and Azure 304: Face recognition</span></span>

![результат выполнения этого курса](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="2ec53-112">В этом курсе вы узнаете, как для добавления возможностей распознавания лиц с приложением смешанной реальности, с помощью Azure Cognitive Services, с помощью API распознавания лиц Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="2ec53-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="2ec53-113">*Azure API распознавания лиц* — это служба Майкрософт, которая предоставляет разработчикам наиболее эффективные алгоритмы распознавания лиц, все это в облаке.</span><span class="sxs-lookup"><span data-stu-id="2ec53-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="2ec53-114">*API распознавания лиц* имеет две основные функции: обнаружение с помощью атрибутов лиц и распознавание.</span><span class="sxs-lookup"><span data-stu-id="2ec53-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="2ec53-115">Это позволяет разработчикам просто задать набор групп для лиц, а затем отправить изображения запрос в службу позже, чтобы определить, к которому принадлежит грани.</span><span class="sxs-lookup"><span data-stu-id="2ec53-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="2ec53-116">Дополнительные сведения см. в статье [страницы распознавания лиц Azure](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="2ec53-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="2ec53-117">После выполнения этого курса, у вас будет смешанной реальности HoloLens приложения, который будет осуществлять следующее:</span><span class="sxs-lookup"><span data-stu-id="2ec53-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="2ec53-118">Используйте **коснитесь жест** начать захват изображения с помощью встроенного HoloLens камеры.</span><span class="sxs-lookup"><span data-stu-id="2ec53-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="2ec53-119">Отправьте записанный образ для *API распознавания лиц Azure* службы.</span><span class="sxs-lookup"><span data-stu-id="2ec53-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="2ec53-120">Получать результаты проверки *API распознавания лиц* алгоритм.</span><span class="sxs-lookup"><span data-stu-id="2ec53-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="2ec53-121">Используйте простой интерфейс пользователя, для отображения имени соответствующих пользователей.</span><span class="sxs-lookup"><span data-stu-id="2ec53-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="2ec53-122">Вы изучите способы получения результатов от службы API распознавания лиц в приложение на базе Unity смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2ec53-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="2ec53-123">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="2ec53-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="2ec53-124">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="2ec53-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="2ec53-125">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2ec53-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="2ec53-126">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="2ec53-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2ec53-127">Курс</span><span class="sxs-lookup"><span data-stu-id="2ec53-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2ec53-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2ec53-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2ec53-129"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="2ec53-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="2ec53-130">Г-н и Azure 304: Распознавание лиц.</span><span class="sxs-lookup"><span data-stu-id="2ec53-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="2ec53-131">✔️</span><span class="sxs-lookup"><span data-stu-id="2ec53-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2ec53-132">✔️</span><span class="sxs-lookup"><span data-stu-id="2ec53-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="2ec53-133">Хотя этот курс основное внимание уделяется HoloLens, можно также применить полученные знания в этот курс поможет вам Windows Mixed Reality иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="2ec53-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="2ec53-134">Поскольку иммерсивную (VR) не имеют доступных камеры, вам потребуется внешний камеры, подключенном к ПК.</span><span class="sxs-lookup"><span data-stu-id="2ec53-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="2ec53-135">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="2ec53-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ec53-136">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="2ec53-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="2ec53-137">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="2ec53-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="2ec53-138">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="2ec53-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="2ec53-139">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="2ec53-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="2ec53-140">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="2ec53-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="2ec53-141">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="2ec53-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="2ec53-142">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="2ec53-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="2ec53-143">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="2ec53-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="2ec53-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="2ec53-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="2ec53-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2ec53-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="2ec53-146">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="2ec53-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="2ec53-147">Камера, подключенном к ПК (для разработки иммерсивных гарнитуры)</span><span class="sxs-lookup"><span data-stu-id="2ec53-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="2ec53-148">Доступ к Интернету для настройки Azure и извлечения API распознавания лиц</span><span class="sxs-lookup"><span data-stu-id="2ec53-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="2ec53-149">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="2ec53-149">Before you start</span></span>

1.  <span data-ttu-id="2ec53-150">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="2ec53-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="2ec53-151">Настроить и проверить ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ec53-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="2ec53-152">Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="2ec53-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="2ec53-153">Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="2ec53-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="2ec53-154">Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="2ec53-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="2ec53-155">Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="2ec53-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="2ec53-156">Глава 1 - портала Azure</span><span class="sxs-lookup"><span data-stu-id="2ec53-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="2ec53-157">Чтобы использовать *API распознавания лиц* службы в Azure, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="2ec53-158">Во-первых, войдите в [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="2ec53-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="2ec53-159">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="2ec53-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="2ec53-160">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="2ec53-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="2ec53-161">После входа в систему щелкните **New** в левом верхнем углу, а поиск *API распознавания лиц*, нажмите клавишу **ввод**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![Поиск api распознавания лиц](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="2ec53-163">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="2ec53-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="2ec53-164">Новая страница будет предоставить описание *API распознавания лиц* службы.</span><span class="sxs-lookup"><span data-stu-id="2ec53-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="2ec53-165">В нижней левой части этого запроса, выберите **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="2ec53-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![сведения об api лиц](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="2ec53-167">Когда вы перейдете на **создать**:</span><span class="sxs-lookup"><span data-stu-id="2ec53-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="2ec53-168">Вставьте желаемого имени для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="2ec53-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="2ec53-169">Выберите подписку.</span><span class="sxs-lookup"><span data-stu-id="2ec53-169">Select a subscription.</span></span>

    3. <span data-ttu-id="2ec53-170">Выберите ценовую категорию, соответствующие, если это первое время создания *служба API распознавания лиц*, уровень "бесплатный" (с именем F0) должны быть доступны для вас.</span><span class="sxs-lookup"><span data-stu-id="2ec53-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="2ec53-171">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="2ec53-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="2ec53-172">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="2ec53-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="2ec53-173">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="2ec53-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="2ec53-174">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="2ec53-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="2ec53-175">Приложения UWP, **Person Maker**, которая будет использоваться далее, необходимо использовать «Западная часть США» для расположения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="2ec53-176">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="2ec53-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="2ec53-177">Выберите \**создайте *.**</span><span class="sxs-lookup"><span data-stu-id="2ec53-177">Select **Create\*.**</span></span>

        ![Создание сталкиваются с api службы](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="2ec53-179">Когда вы перейдете на \*\*создать \*\*\* имеется ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="2ec53-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="2ec53-180">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="2ec53-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![уведомление о создании службы](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="2ec53-182">Щелкните уведомлений для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="2ec53-182">Click on the notifications to explore your new Service instance.</span></span>

    ![Перейти к ресурсов уведомлений](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="2ec53-184">Когда будете готовы, нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="2ec53-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![доступ сталкиваются ключи api](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="2ec53-186">В этом руководстве описано приложение должно выполнять вызовы к службе, что можно сделать с помощью подписки службы «key».</span><span class="sxs-lookup"><span data-stu-id="2ec53-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="2ec53-187">Из *быстрого запуска* странице из вашей *API распознавания лиц* первая точка службы имеет номер 1, до *получите ключи.*</span><span class="sxs-lookup"><span data-stu-id="2ec53-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="2ec53-188">На *службы* выберите либо синюю **ключи** гиперссылку (если на странице "Быстрый запуск"), или **ключи** ссылку в меню навигации служб (слева, обозначенное с помощью " ключ "значок), чтобы увидеть ключи.</span><span class="sxs-lookup"><span data-stu-id="2ec53-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="2ec53-189">Запишите один из ключей и защитить его, так как он понадобится позже.</span><span class="sxs-lookup"><span data-stu-id="2ec53-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="2ec53-190">Глава 2 - Использование приложения универсальной платформы Windows «Person Maker»</span><span class="sxs-lookup"><span data-stu-id="2ec53-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="2ec53-191">Не забудьте загрузить предварительно созданные приложении универсальной платформы Windows с именем [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="2ec53-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="2ec53-192">Это приложение не конечный продукт, этот курс, просто средство для создания вашего Azure операций, которые будут зависят от более поздней версии проекта.</span><span class="sxs-lookup"><span data-stu-id="2ec53-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="2ec53-193">**Person Maker** позволяет создавать Azure операций, которые связаны с людьми и групп пользователей.</span><span class="sxs-lookup"><span data-stu-id="2ec53-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="2ec53-194">Приложение помещает все необходимые сведения в формате, который можно затем позже использоваться FaceAPI для распознавания лиц людей, вы добавили.</span><span class="sxs-lookup"><span data-stu-id="2ec53-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="2ec53-195">[ВАЖНО] **Person Maker** использует некоторые основные регулирования, чтобы гарантировать, что не может превышать число вызовов службы в минуту для **бесплатная подписка уровня**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="2ec53-196">Изменит на красный зеленый текст в верхней и обновления как «АКТИВНОЕ», когда происходит регулирование; Если это так просто ожидания приложения (он будет ждать его рядом сохраняют доступ к службе лиц, обновление «IN-активный» при его можно снова использовать).</span><span class="sxs-lookup"><span data-stu-id="2ec53-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="2ec53-197">Это приложение использует *Microsoft.ProjectOxford.Face* библиотеки, которые вы сможете наиболее полно использовать API распознавания лиц.</span><span class="sxs-lookup"><span data-stu-id="2ec53-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="2ec53-198">Эта библиотека доступна бесплатно в виде пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="2ec53-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="2ec53-199">Дополнительные сведения об этом и аналогично API-интерфейсы [не забудьте посетить справочная статья API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="2ec53-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="2ec53-200">Ниже приведены шаги, необходимые, инструкции для выполнения этих действий ниже документа.</span><span class="sxs-lookup"><span data-stu-id="2ec53-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="2ec53-201">**Person Maker** приложение позволит вам:</span><span class="sxs-lookup"><span data-stu-id="2ec53-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="2ec53-202">Создание *лица группу*, который состоит из нескольких пользователей, которые необходимо связать с ней группу.</span><span class="sxs-lookup"><span data-stu-id="2ec53-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="2ec53-203">С помощью учетной записи Azure можно разместить несколько групп.</span><span class="sxs-lookup"><span data-stu-id="2ec53-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="2ec53-204">Создание *Person*, который является членом группы пользователя.</span><span class="sxs-lookup"><span data-stu-id="2ec53-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="2ec53-205">У каждого пользователя есть ряд *лиц* изображений, связанных с ним.</span><span class="sxs-lookup"><span data-stu-id="2ec53-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="2ec53-206">Назначить *сталкиваются образы* для *Person*, чтобы разрешить службе Azure Face API для распознавания *Person* соответствующим *лиц*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="2ec53-207">*Обучение* вашей *Azure сталкиваются с API службы*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="2ec53-208">Имейте в виду, поэтому для обучения это приложение для распознавания людей, вам десяти (10) крупным планом фотографий каждого человека, который вы хотите добавить в группу пользователя.</span><span class="sxs-lookup"><span data-stu-id="2ec53-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="2ec53-209">Приложение Windows 10 камера может помочь с учетом.</span><span class="sxs-lookup"><span data-stu-id="2ec53-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="2ec53-210">Необходимо убедиться, что каждой фотографии снят (избежать Размытие, скрывая или выполняется слишком далеко от субъекта), иметь фотографии в формате jpg или png, с размером файла образа, его размер не **4 МБ**и не менее, чем **1 КБ**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="2ec53-211">Если выполнить этот учебник, не используйте собственного грани для обучения, HoloLens, загружаемых, не проверяя самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="2ec53-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="2ec53-212">Используйте шрифт, коллеги или специалист учащегося.</span><span class="sxs-lookup"><span data-stu-id="2ec53-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="2ec53-213">Под управлением **Person Maker**:</span><span class="sxs-lookup"><span data-stu-id="2ec53-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="2ec53-214">Откройте **PersonMaker** папку и дважды щелкните *решение PersonMaker* чтобы открыть его с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="2ec53-215">Один раз *PersonMaker решение* еще открыт, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="2ec53-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="2ec53-216">*Конфигурации решения* присваивается **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="2ec53-217">*Платформа решения* присваивается **x86**</span><span class="sxs-lookup"><span data-stu-id="2ec53-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="2ec53-218">*Целевую платформу* — **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="2ec53-219">Также может потребоваться *восстановить пакеты NuGet* (щелкните правой кнопкой мыши *решение* и выберите **восстановить пакеты NuGet**).</span><span class="sxs-lookup"><span data-stu-id="2ec53-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="2ec53-220">Нажмите кнопку *локального компьютера* и запустится приложение.</span><span class="sxs-lookup"><span data-stu-id="2ec53-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="2ec53-221">Имейте в виду, что на экране меньшего размера, все содержимое может не отображаться, хотя можно более детальном на его просмотр.</span><span class="sxs-lookup"><span data-stu-id="2ec53-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![пользовательский интерфейс для создателя Person](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="2ec53-223">Вставить вашей **ключ проверки подлинности Azure**, который должен иметь, из вашего *API распознавания лиц* службы в Azure.</span><span class="sxs-lookup"><span data-stu-id="2ec53-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="2ec53-224">Вставьте:</span><span class="sxs-lookup"><span data-stu-id="2ec53-224">Insert:</span></span>

    1. <span data-ttu-id="2ec53-225">*Идентификатор* вы хотите назначить *лица группу*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="2ec53-226">Идентификатор должен быть в нижнем регистре без пробелов.</span><span class="sxs-lookup"><span data-stu-id="2ec53-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="2ec53-227">Запишите этот идентификатор, так как она понадобится позже в проекте Unity.</span><span class="sxs-lookup"><span data-stu-id="2ec53-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="2ec53-228">*Имя* вы хотите назначить *лица группу* (может содержать пробелы).</span><span class="sxs-lookup"><span data-stu-id="2ec53-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="2ec53-229">Нажмите клавишу **создать лица группу** кнопки.</span><span class="sxs-lookup"><span data-stu-id="2ec53-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="2ec53-230">Под кнопкой появится сообщение с подтверждением.</span><span class="sxs-lookup"><span data-stu-id="2ec53-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="2ec53-231">Если у вас есть ошибка «Отказано в доступе», проверьте расположение, установленные для службы Azure.</span><span class="sxs-lookup"><span data-stu-id="2ec53-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="2ec53-232">Как уже говорилось выше, это приложение предназначен для «Западная часть США».</span><span class="sxs-lookup"><span data-stu-id="2ec53-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ec53-233">Обратите внимание, что можно также щелкнуть **получить группу известные** кнопки: это если вы уже создали лица группу и требуется использовать его, а не создавать новый.</span><span class="sxs-lookup"><span data-stu-id="2ec53-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="2ec53-234">Имейте в виду, если щелкнуть *создать лица группу* с группой известных также будет извлечена группу.</span><span class="sxs-lookup"><span data-stu-id="2ec53-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="2ec53-235">Вставить *имя* из *Person* вы хотите создать.</span><span class="sxs-lookup"><span data-stu-id="2ec53-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="2ec53-236">Нажмите кнопку **создать Person** кнопки.</span><span class="sxs-lookup"><span data-stu-id="2ec53-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="2ec53-237">Под кнопкой появится сообщение с подтверждением.</span><span class="sxs-lookup"><span data-stu-id="2ec53-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="2ec53-238">Если вы хотите удалить пользователя, созданный ранее, можно написать имя в текстовом поле и нажмите клавишу **удалить пользователя**</span><span class="sxs-lookup"><span data-stu-id="2ec53-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="2ec53-239">Убедитесь, что известно расположение десяти (10) фотографий пользователя, которого вы хотите добавить в группу.</span><span class="sxs-lookup"><span data-stu-id="2ec53-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="2ec53-240">Нажмите клавишу **создать и открыть папку** чтобы открыть обозреватель Windows к папке, связанный пользователю.</span><span class="sxs-lookup"><span data-stu-id="2ec53-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="2ec53-241">Добавление изображений десяти (10) в папке.</span><span class="sxs-lookup"><span data-stu-id="2ec53-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="2ec53-242">Они должны иметь *JPG* или *PNG* формат файла.</span><span class="sxs-lookup"><span data-stu-id="2ec53-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="2ec53-243">Щелкните **отправить в Azure**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="2ec53-244">Счетчик покажет состояние отправки, следуют сообщение после ее завершения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="2ec53-245">После завершения счетчика и выводится сообщение с подтверждением щелкните **обучения** для обучения службы.</span><span class="sxs-lookup"><span data-stu-id="2ec53-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="2ec53-246">Когда процесс завершится, вы будете готовы переместить в Unity.</span><span class="sxs-lookup"><span data-stu-id="2ec53-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="2ec53-247">Глава 3 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="2ec53-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="2ec53-248">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="2ec53-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="2ec53-249">Откройте *Unity* и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-249">Open *Unity* and click **New**.</span></span> 

    ![Начните новый проект Unity.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="2ec53-251">Теперь необходимо будет указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="2ec53-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="2ec53-252">Вставить **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="2ec53-253">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="2ec53-254">Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="2ec53-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="2ec53-255">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-255">Then, click **Create project**.</span></span>

    ![Укажите сведения для нового проекта Unity.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="2ec53-257">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="2ec53-258">Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="2ec53-259">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="2ec53-260">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="2ec53-260">Close the **Preferences** window.</span></span>

    ![Обновите настройки редактора скриптов.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="2ec53-262">Перейдите к **файл > Параметры сборки** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.</span><span class="sxs-lookup"><span data-stu-id="2ec53-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Создавайте окно "Параметры", переключить платформу для универсальной платформы Windows.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="2ec53-264">Перейдите к **файл > Параметры сборки** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="2ec53-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="2ec53-265">**Целевое устройство** присваивается **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="2ec53-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="2ec53-266">Иммерсивную, задайте **целевое устройство** для *любого устройства*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="2ec53-267">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="2ec53-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="2ec53-268">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="2ec53-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="2ec53-269">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="2ec53-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="2ec53-270">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="2ec53-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="2ec53-271">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="2ec53-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="2ec53-272">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="2ec53-273">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="2ec53-273">A save window will appear.</span></span>

            ![Нажмите кнопку Добавить кнопку open сцены](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="2ec53-275">Выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создание новой папки scripts](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="2ec53-277">Откройте только что созданный **сцены** папку, а затем в **имя файла**: текстовое поле, тип **FaceRecScene**, нажмите клавишу **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Присвойте имя новой сцены.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="2ec53-279">Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="2ec53-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="2ec53-280">В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.</span><span class="sxs-lookup"><span data-stu-id="2ec53-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Открытие параметров проигрывателя.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="2ec53-282">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="2ec53-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="2ec53-283">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="2ec53-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="2ec53-284">**Сценарии** **версии среды выполнения** должно быть **экспериментальные** (.NET 4.6 эквивалент).</span><span class="sxs-lookup"><span data-stu-id="2ec53-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="2ec53-285">Это изменение вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="2ec53-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="2ec53-286">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="2ec53-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="2ec53-287">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="2ec53-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Обновите другие параметры.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="2ec53-289">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="2ec53-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="2ec53-290">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="2ec53-290">**InternetClient**</span></span>
        - <span data-ttu-id="2ec53-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="2ec53-291">**Webcam**</span></span>

            ![Обновление параметров публикации.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="2ec53-293">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.</span><span class="sxs-lookup"><span data-stu-id="2ec53-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Обновление параметров R X.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="2ec53-295">Вернитесь в *параметры построения*, **Unity C# проекты** больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="2ec53-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="2ec53-296">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="2ec53-297">Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="2ec53-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="2ec53-298">Главе 4 - Main Camera</span><span class="sxs-lookup"><span data-stu-id="2ec53-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ec53-299">Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете [загрузить этот .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)и импортировать его в проект в качестве [Custom Пакет](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="2ec53-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="2ec53-300">Имейте в виду, что этот пакет также включает Импорт *Newtonsoft DLL*, описываемое в [Глава 5](#chapter-5--import-the-newtonsoft.json-library).</span><span class="sxs-lookup"><span data-stu-id="2ec53-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoft.json-library).</span></span> <span data-ttu-id="2ec53-301">Таким образом импортированы, можно продолжить выполнение после [Глава 6](#chapter-6-create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="2ec53-301">With this imported, you can continue from [Chapter 6](#chapter-6-create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="2ec53-302">В *иерархии* панели, выберите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="2ec53-303">После выбора можно видеть все компоненты **Main Camera** в *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="2ec53-304">**Объекта Camera** должен иметь имя **Main Camera** (Обратите внимание, правильность написания!)</span><span class="sxs-lookup"><span data-stu-id="2ec53-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="2ec53-305">Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания!)</span><span class="sxs-lookup"><span data-stu-id="2ec53-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="2ec53-306">Убедитесь, что **преобразование положения** присваивается **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="2ec53-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="2ec53-307">Задайте **очистить флаги** для **сплошным цветом**</span><span class="sxs-lookup"><span data-stu-id="2ec53-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="2ec53-308">Задайте **фона** цвет компонента камеры для **черная, альфа-значение 0 (шестнадцатеричный код: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="2ec53-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![Установка компонентов камеры](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="2ec53-310">Глава 5 – импорт библиотеки Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="2ec53-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ec53-311">Если вы импортировали .unitypackage в [последняя глава](#chapter-4--main-camera-setup), можно пропустить в этой главе.</span><span class="sxs-lookup"><span data-stu-id="2ec53-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4--main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="2ec53-312">Для десериализации и сериализации объектов получаемых и отправляемых в службу программ-роботов необходимо скачать *Newtonsoft.Json* библиотеки.</span><span class="sxs-lookup"><span data-stu-id="2ec53-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="2ec53-313">Вы найдете совместимой версии упорядочены с правильной структурой папок Unity в этом [файл пакета Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="2ec53-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="2ec53-314">Чтобы импортировать библиотеки:</span><span class="sxs-lookup"><span data-stu-id="2ec53-314">To import the library:</span></span>

1.  <span data-ttu-id="2ec53-315">Скачайте пакет Unity.</span><span class="sxs-lookup"><span data-stu-id="2ec53-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="2ec53-316">Щелкните **активы**, **импортировать пакет**, **пользовательского пакета**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Импорт библиотеки Newtonsoft.Json](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="2ec53-318">Найдите загруженный пакет Unity и нажмите кнопку Открыть.</span><span class="sxs-lookup"><span data-stu-id="2ec53-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="2ec53-319">Убедитесь, что все компоненты пакета установлен флажок и нажмите кнопку **импорта**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Импорт библиотеки Newtonsoft.Json](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="2ec53-321">Глава 6 - создание класса FaceAnalysis</span><span class="sxs-lookup"><span data-stu-id="2ec53-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="2ec53-322">Класс FaceAnalysis предназначена для размещения методы, необходимые для взаимодействия со службой Azure распознавания лиц.</span><span class="sxs-lookup"><span data-stu-id="2ec53-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="2ec53-323">После отправки образа записи службы, его анализ его и идентификация лиц в и определить, если любой принадлежат известных человека.</span><span class="sxs-lookup"><span data-stu-id="2ec53-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="2ec53-324">При обнаружении известного человека, этот класс отображается его имя в виде текста пользовательского интерфейса в сцене.</span><span class="sxs-lookup"><span data-stu-id="2ec53-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="2ec53-325">Чтобы создать *FaceAnalysis* класса:</span><span class="sxs-lookup"><span data-stu-id="2ec53-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="2ec53-326">Щелкните правой кнопкой мыши в *папку Assets* находится в панели «проект», затем щелкните **создать** > **папку**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="2ec53-327">Вызовите папке **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-327">Call the folder **Scripts**.</span></span> 

    ![Создайте класс FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="2ec53-329">Дважды щелкните папку, только что создали, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="2ec53-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="2ec53-330">Щелкните правой кнопкой мыши внутри папки, а затем **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="2ec53-331">Вызовите сценарий *FaceAnalysis*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="2ec53-332">Дважды щелкните новый *FaceAnalysis* скрипт, чтобы открыть его в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="2ec53-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="2ec53-333">Введите следующие пространства имен выше *FaceAnalysis* класса:</span><span class="sxs-lookup"><span data-stu-id="2ec53-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="2ec53-334">Теперь необходимо добавить все объекты, которые используются для deserialising.</span><span class="sxs-lookup"><span data-stu-id="2ec53-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="2ec53-335">Эти объекты должны быть добавлены **за пределами** из *FaceAnalysis* сценария (под нижней фигурная скобка).</span><span class="sxs-lookup"><span data-stu-id="2ec53-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="2ec53-336">*Start()* и *Update()* методы не будут использоваться, поэтому теперь удалите их.</span><span class="sxs-lookup"><span data-stu-id="2ec53-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="2ec53-337">Внутри *FaceAnalysis* добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="2ec53-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="2ec53-338">Замените **ключ** и **personGroupId** ваш ключ службы и идентификатор группы, которую вы создали ранее.</span><span class="sxs-lookup"><span data-stu-id="2ec53-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="2ec53-339">Добавить *Awake()* метод, который инициализирует класс, добавив *ImageCapture* класс Main Camera и вызывает метод создания метки:</span><span class="sxs-lookup"><span data-stu-id="2ec53-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="2ec53-340">Добавить *CreateLabel()* метод, который создает *метка* объект для отображения результатов:</span><span class="sxs-lookup"><span data-stu-id="2ec53-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="2ec53-341">Добавить *DetectFacesFromImage()* и *GetImageAsByteArray()* метод.</span><span class="sxs-lookup"><span data-stu-id="2ec53-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="2ec53-342">Первое из них будет запрашивать службу распознавания лиц для обнаружения любые возможные лиц отправленного изображения, а второй, необходимая для преобразования записанного образа в массив байтов:</span><span class="sxs-lookup"><span data-stu-id="2ec53-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="2ec53-343">Добавить *IdentifyFaces()* метод, который запрашивает *службы распознавания лиц* для идентификации любой известных лиц, обнаружен ранее отправленного изображения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="2ec53-344">Запрос возвращает идентификатор определенного пользователя, но не имя:</span><span class="sxs-lookup"><span data-stu-id="2ec53-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="2ec53-345">Добавить *GetPerson()* метод.</span><span class="sxs-lookup"><span data-stu-id="2ec53-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="2ec53-346">Предоставляя пользователя, идентификатор, этот метод затем запросы *службы распознавания лиц* для возврата имени определенного пользователя:</span><span class="sxs-lookup"><span data-stu-id="2ec53-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="2ec53-347">Не забудьте **Сохранить** изменения, прежде чем вернуться в редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="2ec53-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="2ec53-348">В редакторе Unity перетащите FaceAnalysis скрипт из папки скриптов в панель «проект» для объекта Main Camera в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="2ec53-349">Новый компонент скрипта таким образом будут добавляться к камере Main.</span><span class="sxs-lookup"><span data-stu-id="2ec53-349">The new script component will be so added to the Main Camera.</span></span> 

![FaceAnalysis месте на главной камеры](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="2ec53-351">Глава 7 - создание класса ImageCapture</span><span class="sxs-lookup"><span data-stu-id="2ec53-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="2ec53-352">Цель *ImageCapture* класс — размещение методы, необходимые для взаимодействия с вашей *службы распознавания лиц Azure* проанализируйте образ будет записан, идентификация лиц на его и Определение, входит ли он известных человека.</span><span class="sxs-lookup"><span data-stu-id="2ec53-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="2ec53-353">При обнаружении известного человека, этот класс отображается его имя в виде текста пользовательского интерфейса в сцене.</span><span class="sxs-lookup"><span data-stu-id="2ec53-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="2ec53-354">Чтобы создать *ImageCapture* класса:</span><span class="sxs-lookup"><span data-stu-id="2ec53-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="2ec53-355">Щелкните правой кнопкой мыши внутри **сценарии** папку, вы создали ранее, а затем щелкните **создать**,  **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="2ec53-356">Вызовите сценарий *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="2ec53-357">Дважды щелкните новый *ImageCapture* скрипт, чтобы открыть его в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="2ec53-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="2ec53-358">Введите следующие пространства имен над классом ImageCapture:</span><span class="sxs-lookup"><span data-stu-id="2ec53-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="2ec53-359">Внутри *ImageCapture* добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="2ec53-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="2ec53-360">Добавить *Awake()* и *Start()* методы, необходимые для инициализации класса и разрешить HoloLens для захвата жесты пользователя:</span><span class="sxs-lookup"><span data-stu-id="2ec53-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="2ec53-361">Добавить *TapHandler()* который вызывается, когда пользователь выполняет *коснитесь* жестов:</span><span class="sxs-lookup"><span data-stu-id="2ec53-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="2ec53-362">Добавить *ExecuteImageCaptureAndAnalysis()* метод, который начнется процесс записи образа:</span><span class="sxs-lookup"><span data-stu-id="2ec53-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="2ec53-363">Добавление обработчиков, которые вызываются после завершения процесса отслеживания photo:</span><span class="sxs-lookup"><span data-stu-id="2ec53-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="2ec53-364">Не забудьте **Сохранить** изменения, прежде чем вернуться в редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="2ec53-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="2ec53-365">Глава 8 - построения решения</span><span class="sxs-lookup"><span data-stu-id="2ec53-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="2ec53-366">Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ec53-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="2ec53-367">Прежде чем сделать, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="2ec53-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="2ec53-368">Все параметры, упомянутые в главе 3 настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="2ec53-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="2ec53-369">Сценарий *FaceAnalysis* присоединяется к объекта Main Camera.</span><span class="sxs-lookup"><span data-stu-id="2ec53-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="2ec53-370">Оба **ключом проверки подлинности** и **идентификатор группы** были заданы в *FaceAnalysis* скрипта.</span><span class="sxs-lookup"><span data-stu-id="2ec53-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="2ec53-371">Этот момент можно приступать к построению решения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="2ec53-372">После построения решения, вы будете готовы для развертывания приложения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="2ec53-373">Чтобы начать процесс построения:</span><span class="sxs-lookup"><span data-stu-id="2ec53-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="2ec53-374">Сохраните текущую сцену, щелкнув файл, сохраните.</span><span class="sxs-lookup"><span data-stu-id="2ec53-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="2ec53-375">Перейдите к файлу, параметры сборки, щелкните Добавить откройте сцены.</span><span class="sxs-lookup"><span data-stu-id="2ec53-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="2ec53-376">Убедитесь, что к такту Unity C# проектов.</span><span class="sxs-lookup"><span data-stu-id="2ec53-376">Make sure to tick Unity C# Projects.</span></span>

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="2ec53-378">Нажмите клавишу сборки.</span><span class="sxs-lookup"><span data-stu-id="2ec53-378">Press Build.</span></span> <span data-ttu-id="2ec53-379">При этом Unity запустится окно проводника, где необходимо создать, а затем выберите папку, чтобы создать приложение в.</span><span class="sxs-lookup"><span data-stu-id="2ec53-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="2ec53-380">Создайте эту папку прямо сейчас, в рамках проекта Unity и назовите его приложение.</span><span class="sxs-lookup"><span data-stu-id="2ec53-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="2ec53-381">Затем выбранные папки приложения, нажмите клавишу "Выбор папки".</span><span class="sxs-lookup"><span data-stu-id="2ec53-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="2ec53-382">Unity начнется при создании проекта, в папку приложения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="2ec53-383">Один раз Unity завершил построение (может занять некоторое время), откроется окно проводника в папке построения.</span><span class="sxs-lookup"><span data-stu-id="2ec53-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="2ec53-385">Откройте папку приложения и затем открыть новое решение проект (как показано выше, MR_FaceRecognition.sln).</span><span class="sxs-lookup"><span data-stu-id="2ec53-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="2ec53-386">Глава 9 - развертывания приложения</span><span class="sxs-lookup"><span data-stu-id="2ec53-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="2ec53-387">Для развертывания на HoloLens:</span><span class="sxs-lookup"><span data-stu-id="2ec53-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="2ec53-388">Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="2ec53-389">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="2ec53-389">To do this:</span></span>

    1. <span data-ttu-id="2ec53-390">Хотя носить вашей HoloLens, откройте **параметры**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="2ec53-391">Перейдите к **сеть и Интернет > Wi-Fi > Дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="2ec53-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="2ec53-392">Примечание **IPv4** адрес.</span><span class="sxs-lookup"><span data-stu-id="2ec53-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="2ec53-393">Затем перейдите к **параметры**, а затем в **обновление и безопасность > для разработчиков**</span><span class="sxs-lookup"><span data-stu-id="2ec53-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="2ec53-394">Включен режим разработчика.</span><span class="sxs-lookup"><span data-stu-id="2ec53-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="2ec53-395">Перейдите к новой сборки Unity ( *приложения* папки) и откройте файл решения с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="2ec53-396">В списке выберите конфигурацию решения **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="2ec53-397">В платформу решения, выберите **x86**, **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="2ec53-399">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение**, чтобы загрузить неопубликованное приложение для вашего HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ec53-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="2ec53-400">Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!</span><span class="sxs-lookup"><span data-stu-id="2ec53-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="2ec53-401">Чтобы развернуть иммерсивных гарнитура, переключите **платформа решения** для *локального компьютера*и задайте **конфигурации** для *Отладка*, с *x86* как **платформы**.</span><span class="sxs-lookup"><span data-stu-id="2ec53-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="2ec53-402">Затем развернуть на локальный компьютер, с помощью **меню "сборка"**, выбрав *развернуть решение*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="2ec53-403">Глава 10 - с помощью приложения</span><span class="sxs-lookup"><span data-stu-id="2ec53-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="2ec53-404">Носить HoloLens, запустите это приложение.</span><span class="sxs-lookup"><span data-stu-id="2ec53-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="2ec53-405">Рассмотрим пользователя, которая была зарегистрирована с *API распознавания лиц*.</span><span class="sxs-lookup"><span data-stu-id="2ec53-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="2ec53-406">Убедитесь в следующем.</span><span class="sxs-lookup"><span data-stu-id="2ec53-406">Make sure that:</span></span>

    -  <span data-ttu-id="2ec53-407">Лица крупным не слишком удаленных и четко видны</span><span class="sxs-lookup"><span data-stu-id="2ec53-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="2ec53-408">Освещение среды не слишком темный</span><span class="sxs-lookup"><span data-stu-id="2ec53-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="2ec53-409">Используйте жест касания для записи фотографии лица.</span><span class="sxs-lookup"><span data-stu-id="2ec53-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="2ec53-410">Подождите, пока приложение для отправки запроса анализа и получения ответа.</span><span class="sxs-lookup"><span data-stu-id="2ec53-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="2ec53-411">Если пользователь был успешно распознан, его имя будет отображаться как текст пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="2ec53-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="2ec53-412">Можно повторить процесс отслеживания с помощью жеста касания каждые несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="2ec53-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="2ec53-413">Готовое приложение API распознавания лиц Azure</span><span class="sxs-lookup"><span data-stu-id="2ec53-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="2ec53-414">Поздравляем, вы создали приложение смешанной реальности, которое использует службу распознавания лиц Azure для обнаружения лиц в образе и идентификации все известные лица.</span><span class="sxs-lookup"><span data-stu-id="2ec53-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![результат выполнения этого курса](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="2ec53-416">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="2ec53-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="2ec53-417">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="2ec53-417">Exercise 1</span></span>

<span data-ttu-id="2ec53-418">**API распознавания лиц Azure** достаточно производителен, чтобы обнаружить до 64 лиц в одном образе.</span><span class="sxs-lookup"><span data-stu-id="2ec53-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="2ec53-419">Расширения приложения, таким образом, он может распознавания лиц, два или три, среди других пользователей.</span><span class="sxs-lookup"><span data-stu-id="2ec53-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="2ec53-420">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="2ec53-420">Exercise 2</span></span>

<span data-ttu-id="2ec53-421">**API распознавания лиц Azure** он также может предоставить обратно все виды сведений об атрибутах.</span><span class="sxs-lookup"><span data-stu-id="2ec53-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="2ec53-422">Интегрируйте в приложение.</span><span class="sxs-lookup"><span data-stu-id="2ec53-422">Integrate this into the application.</span></span> <span data-ttu-id="2ec53-423">Это может быть еще более интересное в сочетании с [API распознавания эмоций](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="2ec53-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
