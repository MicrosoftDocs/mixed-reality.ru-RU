---
title: MR и Azure 304 — распознавание лиц
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, распознавание лиц, hololens, иммерсивное, VR
ms.openlocfilehash: 7cd2a6683c80279129934c619a9b9cb857badf67
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047185"
---
>[!NOTE]
><span data-ttu-id="26e33-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="26e33-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="26e33-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="26e33-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="26e33-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="26e33-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="26e33-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="26e33-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="26e33-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="26e33-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="26e33-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="26e33-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="26e33-110">MR и Azure 304: Распознавание лиц</span><span class="sxs-lookup"><span data-stu-id="26e33-110">MR and Azure 304: Face recognition</span></span>

![результат выполнения этого курса](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="26e33-112">В этом курсе вы узнаете, как добавить возможности распознавания лиц в приложение смешанной реальности с помощью Cognitive Services Azure с API распознавания лиц Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="26e33-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="26e33-113">*Azure API распознавания лиц* — это служба Майкрософт, которая предоставляет разработчикам самые современные алгоритмы, все в облаке.</span><span class="sxs-lookup"><span data-stu-id="26e33-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="26e33-114">*API распознавания лиц* имеет две основные функции: обнаружение лиц с помощью атрибутов и распознавание лиц.</span><span class="sxs-lookup"><span data-stu-id="26e33-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="26e33-115">Это позволяет разработчикам просто задать набор групп для лиц, а затем отправить образы запросов в службу позже, чтобы определить, кому принадлежит лицо.</span><span class="sxs-lookup"><span data-stu-id="26e33-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="26e33-116">Дополнительные сведения см. на [странице распознавания лиц Azure](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="26e33-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="26e33-117">Прополнив этот курс, вы получите приложение HoloLens для смешанной реальности, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="26e33-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="26e33-118">Используйте **жест касания** , чтобы начать запись изображения с помощью встроенной камеры HoloLens.</span><span class="sxs-lookup"><span data-stu-id="26e33-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="26e33-119">Отправьте захваченный образ в службу *API распознавания лиц Azure* .</span><span class="sxs-lookup"><span data-stu-id="26e33-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="26e33-120">Получение результатов алгоритма *API распознавания лиц* .</span><span class="sxs-lookup"><span data-stu-id="26e33-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="26e33-121">Используйте простой пользовательский интерфейс для просмотра имени сопоставленных людей.</span><span class="sxs-lookup"><span data-stu-id="26e33-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="26e33-122">Вы узнаете, как получить результаты из службы API распознавания лиц в приложении смешанной реальности на основе Unity.</span><span class="sxs-lookup"><span data-stu-id="26e33-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="26e33-123">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="26e33-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="26e33-124">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="26e33-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="26e33-125">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="26e33-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="26e33-126">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="26e33-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="26e33-127">Хождение</span><span class="sxs-lookup"><span data-stu-id="26e33-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="26e33-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="26e33-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="26e33-129"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="26e33-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="26e33-130">MR и Azure 304: Распознавание лиц</span><span class="sxs-lookup"><span data-stu-id="26e33-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="26e33-131">✔️</span><span class="sxs-lookup"><span data-stu-id="26e33-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="26e33-132">✔️</span><span class="sxs-lookup"><span data-stu-id="26e33-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="26e33-133">Хотя этот курс в основном ориентирован на HoloLens, вы можете также применить сведения, которые вы узнаете в этом курсе, к головным телефонам Windows Mixed Reality (VR).</span><span class="sxs-lookup"><span data-stu-id="26e33-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="26e33-134">Так как у головных гарнитур нет доступных камер, вам потребуется внешняя камера, подключенная к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="26e33-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="26e33-135">При работе с курсом вы увидите заметки о любых изменениях, которые могут потребоваться для поддержки головных телефонов (VR).</span><span class="sxs-lookup"><span data-stu-id="26e33-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26e33-136">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="26e33-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="26e33-137">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="26e33-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="26e33-138">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018).</span><span class="sxs-lookup"><span data-stu-id="26e33-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="26e33-139">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.</span><span class="sxs-lookup"><span data-stu-id="26e33-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="26e33-140">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="26e33-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="26e33-141">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="26e33-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="26e33-142">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="26e33-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="26e33-143">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="26e33-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="26e33-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="26e33-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="26e33-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="26e33-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="26e33-146">Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="26e33-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="26e33-147">Камера, подключенная к компьютеру (для разработки в увлекательной гарнитуре)</span><span class="sxs-lookup"><span data-stu-id="26e33-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="26e33-148">Доступ к Интернету для установки Azure и извлечения API распознавания лиц</span><span class="sxs-lookup"><span data-stu-id="26e33-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="26e33-149">Перед началом</span><span class="sxs-lookup"><span data-stu-id="26e33-149">Before you start</span></span>

1.  <span data-ttu-id="26e33-150">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="26e33-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="26e33-151">Настройка и тестирование HoloLens.</span><span class="sxs-lookup"><span data-stu-id="26e33-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="26e33-152">Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="26e33-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="26e33-153">Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="26e33-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="26e33-154">Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="26e33-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="26e33-155">Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="26e33-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="26e33-156">Глава 1. портал Azure</span><span class="sxs-lookup"><span data-stu-id="26e33-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="26e33-157">Чтобы использовать службу *API распознавания лиц* в Azure, необходимо настроить экземпляр службы, чтобы сделать ее доступной для приложения.</span><span class="sxs-lookup"><span data-stu-id="26e33-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="26e33-158">Сначала войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="26e33-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="26e33-159">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="26e33-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="26e33-160">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="26e33-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="26e33-161">Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу и выполните поиск по *API распознавания лиц*нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="26e33-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![Поиск API распознавания лиц](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="26e33-163">Слово **New** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="26e33-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="26e33-164">На новой странице будет представлено описание службы *API распознавания лиц* .</span><span class="sxs-lookup"><span data-stu-id="26e33-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="26e33-165">В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="26e33-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![сведения об API распознавания лиц](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="26e33-167">После нажатия кнопки **создать**:</span><span class="sxs-lookup"><span data-stu-id="26e33-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="26e33-168">Вставьте нужное имя для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="26e33-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="26e33-169">Выберите подписку.</span><span class="sxs-lookup"><span data-stu-id="26e33-169">Select a subscription.</span></span>

    3. <span data-ttu-id="26e33-170">Выберите ценовую категорию, подходящую для вас. Если вы впервые создаете *службу API распознавания лиц*, вам будет доступен бесплатный уровень (с именем F0).</span><span class="sxs-lookup"><span data-stu-id="26e33-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="26e33-171">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="26e33-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="26e33-172">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="26e33-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="26e33-173">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="26e33-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="26e33-174">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="26e33-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="26e33-175">Приложение UWP, котороевы используете позже, должно использовать "Западная часть США" для расположения.</span><span class="sxs-lookup"><span data-stu-id="26e33-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="26e33-176">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="26e33-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="26e33-177">Выберите **создайте\*.**</span><span class="sxs-lookup"><span data-stu-id="26e33-177">Select **Create\*.**</span></span>

        ![Создание службы API распознавания лиц](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="26e33-179">Когда вы перейдете на **создать**\* имеется ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="26e33-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="26e33-180">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="26e33-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![уведомление о создании службы](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="26e33-182">Щелкните уведомления, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="26e33-182">Click on the notifications to explore your new Service instance.</span></span>

    ![Переход к уведомлению о ресурсе](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="26e33-184">Когда будете готовы, нажмите кнопку **Перейти к ресурсу** в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="26e33-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![ключи API лиц для доступа](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="26e33-186">В рамках этого руководства приложение должно будет вызывать службу, что выполняется с помощью ключа подписки вашей службы.</span><span class="sxs-lookup"><span data-stu-id="26e33-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="26e33-187">На странице *быстрого запуска* службы API распознавания лица первая точка — номер 1, чтобы *взять ключи.*</span><span class="sxs-lookup"><span data-stu-id="26e33-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="26e33-188">На странице *Служба* выберите гиперссылку «синие **ключи** » (если на странице быстрого запуска) или ссылку « **ключи** » в меню навигации служб (слева, обозначенном значком «ключ»), чтобы отобразить ключи.</span><span class="sxs-lookup"><span data-stu-id="26e33-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="26e33-189">Запишите либо один из ключей, и защитите его, так как он понадобится позже.</span><span class="sxs-lookup"><span data-stu-id="26e33-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="26e33-190">Глава 2. Использование приложения UWP "Person Maker"</span><span class="sxs-lookup"><span data-stu-id="26e33-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="26e33-191">Обязательно загрузите предварительно созданное приложение UWP с именем [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="26e33-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="26e33-192">Это приложение не является конечным продуктом для этого курса. это просто средство, которое поможет вам создать свои записи Azure, на которые последует последующий проект.</span><span class="sxs-lookup"><span data-stu-id="26e33-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="26e33-193">**Person Maker** позволяет создавать записи Azure, связанные с людьми и группами людей.</span><span class="sxs-lookup"><span data-stu-id="26e33-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="26e33-194">Приложение поместит всю необходимую информацию в формате, который впоследствии может использоваться Фацеапи, чтобы распознать лиц, которые были добавлены.</span><span class="sxs-lookup"><span data-stu-id="26e33-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="26e33-195">СУЩЕСТВЕННО **Person Maker** использует некоторое базовое регулирование, чтобы не превысить количество вызовов службы за минуту для **бесплатного уровня подписки**.</span><span class="sxs-lookup"><span data-stu-id="26e33-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="26e33-196">Зеленый текст в верхней части изменится на красный и будет обновляться как активный при регулировании. Если это так, просто дождитесь приложения (будет ожидать, пока он сможет продолжить доступ к службе распознавания лиц, обновив его как "IN-ACTIVE", когда его можно будет использовать).</span><span class="sxs-lookup"><span data-stu-id="26e33-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="26e33-197">В этом приложении используются библиотеки *Microsoft. прожектоксфорд. Face* , которые позволяют полностью использовать API распознавания лиц.</span><span class="sxs-lookup"><span data-stu-id="26e33-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="26e33-198">Эта библиотека доступна бесплатно в качестве пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="26e33-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="26e33-199">Дополнительные сведения об этих и похожих API-интерфейсах см. [в справочной статье по API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="26e33-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="26e33-200">Это лишь необходимые шаги. инструкции по выполнению этих действий приведены ниже в документе.</span><span class="sxs-lookup"><span data-stu-id="26e33-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="26e33-201">Приложение **Person Maker** позволит вам:</span><span class="sxs-lookup"><span data-stu-id="26e33-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="26e33-202">Создайте *группу Person*, которая состоит из нескольких людей, которые вы хотите связать с ней.</span><span class="sxs-lookup"><span data-stu-id="26e33-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="26e33-203">С помощью учетной записи Azure можно разместить несколько групп людей.</span><span class="sxs-lookup"><span data-stu-id="26e33-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="26e33-204">Создайте *пользователя*, который является членом группы людей.</span><span class="sxs-lookup"><span data-stu-id="26e33-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="26e33-205">С каждым лицом связано несколько изображений, связанных с *лицом* .</span><span class="sxs-lookup"><span data-stu-id="26e33-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="26e33-206">Назначьте *пользователю* *изображения* лиц, чтобы служба Azure API распознавания лиц могла распознать *человека* с помощью соответствующего лица.</span><span class="sxs-lookup"><span data-stu-id="26e33-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="26e33-207">Обучить *службу API распознавания лиц Azure*.</span><span class="sxs-lookup"><span data-stu-id="26e33-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="26e33-208">Имейте в виду, что чтобы обучить это приложение для распознавания людей, вам потребуется десять (10) закрываемых фотографий каждого человека, которого вы хотите добавить в вашу группу лиц.</span><span class="sxs-lookup"><span data-stu-id="26e33-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="26e33-209">Приложение для фотосистемы Windows 10 поможет вам сделать это.</span><span class="sxs-lookup"><span data-stu-id="26e33-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="26e33-210">Необходимо убедиться в том, что каждая фотография является ясной (Избегайте размытия, скрытия или слишком далекого края, от субъекта), постарайтесь иметь фотографию в формате JPG или PNG, размер файла изображения не должен превышать **4 МБ**и не должен быть меньше **1 КБ**.</span><span class="sxs-lookup"><span data-stu-id="26e33-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="26e33-211">Если вы используете этот учебник, не используйте собственные лица для обучения, как при помещении HoloLens на, вы не сможете взглянуть на себя.</span><span class="sxs-lookup"><span data-stu-id="26e33-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="26e33-212">Воспользуйтесь лицом коллеги или учащегося.</span><span class="sxs-lookup"><span data-stu-id="26e33-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="26e33-213">Работающая программа **Person Maker**:</span><span class="sxs-lookup"><span data-stu-id="26e33-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="26e33-214">Откройте папку **персонмакер** и дважды щелкните *решение персонмакер* , чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="26e33-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="26e33-215">После открытия *решения персонмакер* убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="26e33-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="26e33-216">Для *конфигурации решения* задано значение **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="26e33-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="26e33-217">*Платформа решения* установлена в значение " **x86** "</span><span class="sxs-lookup"><span data-stu-id="26e33-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="26e33-218">*Целевая платформа* — **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="26e33-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="26e33-219">Также может потребоваться *восстановить пакеты NuGet* (щелкните *решение* правой кнопкой мыши и выберите пункт **восстановить пакеты NuGet**).</span><span class="sxs-lookup"><span data-stu-id="26e33-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="26e33-220">Щелкните *локальный компьютер* , и приложение запустится.</span><span class="sxs-lookup"><span data-stu-id="26e33-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="26e33-221">Имейте в виду, что на небольших экранах все содержимое может не отображаться, хотя можно прокручивать его вниз для просмотра.</span><span class="sxs-lookup"><span data-stu-id="26e33-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![Пользовательский интерфейс Person Maker](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="26e33-223">Вставьте **ключ проверки подлинности Azure**, который вам необходим, из службы *API распознавания лиц* в Azure.</span><span class="sxs-lookup"><span data-stu-id="26e33-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="26e33-224">Вставляет</span><span class="sxs-lookup"><span data-stu-id="26e33-224">Insert:</span></span>

    1. <span data-ttu-id="26e33-225">*Идентификатор* , который необходимо назначить *группе лиц*.</span><span class="sxs-lookup"><span data-stu-id="26e33-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="26e33-226">Идентификатор должен быть строчным, без пробелов.</span><span class="sxs-lookup"><span data-stu-id="26e33-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="26e33-227">Запишите этот идентификатор, так как он потребуется позже в проекте Unity.</span><span class="sxs-lookup"><span data-stu-id="26e33-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="26e33-228">*Имя* , которое нужно назначить *группе Person* (может содержать пробелы).</span><span class="sxs-lookup"><span data-stu-id="26e33-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="26e33-229">Нажмите кнопку **создать группу Person** .</span><span class="sxs-lookup"><span data-stu-id="26e33-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="26e33-230">Под кнопкой появится сообщение с подтверждением.</span><span class="sxs-lookup"><span data-stu-id="26e33-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="26e33-231">При наличии ошибки "доступ запрещен" проверьте расположение, заданное для службы Azure.</span><span class="sxs-lookup"><span data-stu-id="26e33-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="26e33-232">Как упоминалось выше, это приложение предназначено для "Западная часть США".</span><span class="sxs-lookup"><span data-stu-id="26e33-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26e33-233">Вы заметите, что можно также нажать кнопку **извлечь известную группу** : Если вы уже создали группу лиц и хотите использовать ее, а не создать новую.</span><span class="sxs-lookup"><span data-stu-id="26e33-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="26e33-234">Имейте в виду, что если щелкнуть *создать группу лиц* с известной группой, будет также получена группа.</span><span class="sxs-lookup"><span data-stu-id="26e33-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="26e33-235">Введите *имя* *пользователя* , которого вы хотите создать.</span><span class="sxs-lookup"><span data-stu-id="26e33-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="26e33-236">Нажмите кнопку **создать пользователя** .</span><span class="sxs-lookup"><span data-stu-id="26e33-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="26e33-237">Под кнопкой появится сообщение с подтверждением.</span><span class="sxs-lookup"><span data-stu-id="26e33-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="26e33-238">Если вы хотите удалить ранее созданного пользователя, вы можете записать его в текстовое поле и нажать клавишу **Delete Person** .</span><span class="sxs-lookup"><span data-stu-id="26e33-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="26e33-239">Убедитесь, что вы знаете расположение десяти (10) фотографий человека, которого вы хотите добавить в группу.</span><span class="sxs-lookup"><span data-stu-id="26e33-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="26e33-240">Нажмите кнопку **создать и откройте папку** , чтобы открыть проводник Windows в папке, связанной с пользователем.</span><span class="sxs-lookup"><span data-stu-id="26e33-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="26e33-241">Добавьте в папку десять изображений (10).</span><span class="sxs-lookup"><span data-stu-id="26e33-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="26e33-242">Эти файлы должны иметь формат *JPG* или *PNG* .</span><span class="sxs-lookup"><span data-stu-id="26e33-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="26e33-243">Щелкните **отправить в Azure**.</span><span class="sxs-lookup"><span data-stu-id="26e33-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="26e33-244">Счетчик показывает состояние отправки, за которым следует сообщение после его завершения.</span><span class="sxs-lookup"><span data-stu-id="26e33-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="26e33-245">Когда счетчик будет завершен и появится сообщение с подтверждением, щелкните " **обучение** ", чтобы обучить службу.</span><span class="sxs-lookup"><span data-stu-id="26e33-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="26e33-246">После завершения процесса вы можете перейти в Unity.</span><span class="sxs-lookup"><span data-stu-id="26e33-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="26e33-247">Глава 3. Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="26e33-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="26e33-248">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="26e33-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="26e33-249">Откройте *Unity* и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="26e33-249">Open *Unity* and click **New**.</span></span> 

    ![Запуск нового проекта Unity.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="26e33-251">Теперь необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="26e33-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="26e33-252">Вставьте **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="26e33-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="26e33-253">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="26e33-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="26e33-254">Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="26e33-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="26e33-255">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="26e33-255">Then, click **Create project**.</span></span>

    ![Укажите сведения о новом проекте Unity.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="26e33-257">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="26e33-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="26e33-258">Перейдите к разделу **изменение параметров >** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="26e33-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="26e33-259">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="26e33-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="26e33-260">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="26e33-260">Close the **Preferences** window.</span></span>

    ![Обновить настройки редактора скриптов.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="26e33-262">Затем перейдите в раздел **файл > параметры сборки** и переключите платформу на **универсальная платформа Windows**, нажав кнопку коммутатора **платформы** .</span><span class="sxs-lookup"><span data-stu-id="26e33-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Окно "параметры сборки". Переключите платформу в UWP.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="26e33-264">Перейдите в раздел **файл > параметры сборки** и убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="26e33-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="26e33-265">**Целевое устройство** имеет значение **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="26e33-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="26e33-266">Для впечатляющих головных телефонов задайте для параметра **целевое устройство** *любое устройство*.</span><span class="sxs-lookup"><span data-stu-id="26e33-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="26e33-267">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="26e33-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="26e33-268">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="26e33-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="26e33-269">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="26e33-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="26e33-270">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="26e33-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="26e33-271">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="26e33-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="26e33-272">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="26e33-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="26e33-273">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="26e33-273">A save window will appear.</span></span>

            ![Нажмите кнопку Добавить кнопку "открыть сцены"](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="26e33-275">Нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="26e33-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создать новую папку скриптов](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="26e33-277">Откройте созданную папку **сцены** , а затем в текстовом поле **имя файла**введите **фацерексцене**, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="26e33-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Присвойте имя новой сцене.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="26e33-279">Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="26e33-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="26e33-280">В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .</span><span class="sxs-lookup"><span data-stu-id="26e33-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Откройте параметры проигрывателя.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="26e33-282">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="26e33-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="26e33-283">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="26e33-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="26e33-284">**Создание сценариев** **Версия среды выполнения** должна быть экспериментальной (эквивалент .NET 4,6).</span><span class="sxs-lookup"><span data-stu-id="26e33-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="26e33-285">Изменение этого триггера приведет к необходимости перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="26e33-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="26e33-286">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="26e33-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="26e33-287">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="26e33-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Обновите другие параметры.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="26e33-289">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="26e33-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="26e33-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="26e33-290">**InternetClient**</span></span>
        - <span data-ttu-id="26e33-291">**Бесед**</span><span class="sxs-lookup"><span data-stu-id="26e33-291">**Webcam**</span></span>

            ![Обновляются параметры публикации.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="26e33-293">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="26e33-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Обновите параметры X R.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="26e33-295">Вернувшись в *параметры сборки*, **проекты C# Unity** больше не заключаются. Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="26e33-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="26e33-296">Закройте окно параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="26e33-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="26e33-297">Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="26e33-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="26e33-298">Глава 4 — Настройка основной камеры</span><span class="sxs-lookup"><span data-stu-id="26e33-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26e33-299">Если вы хотите пропустить компонент *установки Unity* , установленный в этом курсе, и продолжить работу с кодом, [Скачайте этот файл. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)и импортируйте его в проект как [пользовательский пакет](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="26e33-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="26e33-300">Имейте в виду, что этот пакет также включает в себя импорт *библиотеки DLL Newtonsoft*, описанной в [главе 5](#chapter-5--import-the-newtonsoftjson-library).</span><span class="sxs-lookup"><span data-stu-id="26e33-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="26e33-301">После импорта можно продолжить с [раздела 6](#chapter-6---create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="26e33-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="26e33-302">На панели *Иерархия* выберите **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="26e33-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="26e33-303">После выбора вы сможете увидеть все компоненты **основной камеры** на *панели инспектора*.</span><span class="sxs-lookup"><span data-stu-id="26e33-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="26e33-304">**Объект Camera** должен называться **основной камерой** (Обратите внимание на орфографию!)</span><span class="sxs-lookup"><span data-stu-id="26e33-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="26e33-305">Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на правописание).</span><span class="sxs-lookup"><span data-stu-id="26e33-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="26e33-306">Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .</span><span class="sxs-lookup"><span data-stu-id="26e33-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="26e33-307">Установить для чистых флагов **сплошной цвет**</span><span class="sxs-lookup"><span data-stu-id="26e33-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="26e33-308">Установить черный цвет **фона** для компонента камеры **, альфа 0 (шестнадцатеричный код: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="26e33-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![Настройка компонентов камеры](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="26e33-310">Глава 5 — Импорт библиотеки Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="26e33-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26e33-311">Если вы импортировали ". пакет unitypackage" в [последней главе](#chapter-4---main-camera-setup), эту главу можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="26e33-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="26e33-312">Чтобы упростить десериализацию и сериализацию объектов, полученных и отправленных службе Bot, необходимо скачать библиотеку *Newtonsoft. JSON* .</span><span class="sxs-lookup"><span data-stu-id="26e33-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="26e33-313">Совместимая версия уже организована с правильной структурой папок Unity в этом [файле пакета Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="26e33-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="26e33-314">Чтобы импортировать библиотеку, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="26e33-314">To import the library:</span></span>

1.  <span data-ttu-id="26e33-315">Скачайте пакет Unity.</span><span class="sxs-lookup"><span data-stu-id="26e33-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="26e33-316">Щелкните **ресурсы**, **импортировать пакет**, **пользовательский пакет**.</span><span class="sxs-lookup"><span data-stu-id="26e33-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Импорт библиотеки Newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="26e33-318">Найдите скачанный пакет Unity и нажмите кнопку Открыть.</span><span class="sxs-lookup"><span data-stu-id="26e33-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="26e33-319">Убедитесь, что все компоненты пакета являются тактовыми, и нажмите кнопку **Импорт**.</span><span class="sxs-lookup"><span data-stu-id="26e33-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Импорт библиотеки Newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="26e33-321">Глава 6. Создание класса Фацеаналисис</span><span class="sxs-lookup"><span data-stu-id="26e33-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="26e33-322">Класс Фацеаналисис предназначен для размещения методов, необходимых для взаимодействия со службой распознавания лиц Azure.</span><span class="sxs-lookup"><span data-stu-id="26e33-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="26e33-323">После отправки службой образа записи он будет анализировать и определять лица в и определять, принадлежат ли какие-либо лица известному человеку.</span><span class="sxs-lookup"><span data-stu-id="26e33-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="26e33-324">Если обнаружено известное лицо, этот класс будет отображать его имя в виде текста пользовательского интерфейса в сцене.</span><span class="sxs-lookup"><span data-stu-id="26e33-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="26e33-325">Чтобы создать класс *фацеаналисис* , сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="26e33-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="26e33-326">Щелкните правой кнопкой мыши *папку активы* , расположенную на панели проект, и выберите команду **создать** > **папку**.</span><span class="sxs-lookup"><span data-stu-id="26e33-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="26e33-327">Вызовите **скрипты**папки.</span><span class="sxs-lookup"><span data-stu-id="26e33-327">Call the folder **Scripts**.</span></span> 

    ![Создайте класс Фацеаналисис.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="26e33-329">Дважды щелкните только что созданную папку, чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="26e33-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="26e33-330">Щелкните правой кнопкой мыши внутри папки, а затем выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="26e33-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="26e33-331">Вызовите скрипт *фацеаналисис*.</span><span class="sxs-lookup"><span data-stu-id="26e33-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="26e33-332">Дважды щелкните новый скрипт *фацеаналисис* , чтобы открыть его в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="26e33-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="26e33-333">Введите следующие пространства имен над классом *фацеаналисис* :</span><span class="sxs-lookup"><span data-stu-id="26e33-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="26e33-334">Теперь необходимо добавить все объекты, используемые для десериалисинг.</span><span class="sxs-lookup"><span data-stu-id="26e33-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="26e33-335">Эти объекты должны быть добавлены **за** пределами сценария *фацеаналисис* (под нижней фигурной скобкой).</span><span class="sxs-lookup"><span data-stu-id="26e33-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

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
7. <span data-ttu-id="26e33-336">Методы *Start ()* и *Update ()* не будут использоваться, поэтому удалите их сейчас.</span><span class="sxs-lookup"><span data-stu-id="26e33-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="26e33-337">В классе *фацеаналисис* добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="26e33-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

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
    > <span data-ttu-id="26e33-338">Замените **ключ** и **персонграупид** ключом службы и идентификатором созданной ранее группы.</span><span class="sxs-lookup"><span data-stu-id="26e33-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="26e33-339">Добавьте метод " *спящий ()* ", который инитиалисес класс, добавив класс *Имажекаптуре* в основную камеру и вызовет метод создания метки:</span><span class="sxs-lookup"><span data-stu-id="26e33-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

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

10. <span data-ttu-id="26e33-340">Добавьте метод *CreateLabel ()* , который создает объект *Label* для вывода результатов анализа:</span><span class="sxs-lookup"><span data-stu-id="26e33-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

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

11. <span data-ttu-id="26e33-341">Добавьте метод *детектфацесфромимаже ()* и *жетимажеасбитеаррай ()* .</span><span class="sxs-lookup"><span data-stu-id="26e33-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="26e33-342">Первый из них запросит службу распознавания лиц обнаружить любое возможное лицо в отправленном изображении, а Последнее необходимо преобразовать записанный образ в массив байтов:</span><span class="sxs-lookup"><span data-stu-id="26e33-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

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

12. <span data-ttu-id="26e33-343">Добавьте метод *идентифифацес ()* , который запрашивает *службу распознавания лиц* для определения известных лиц, обнаруженных ранее в отправленном изображении.</span><span class="sxs-lookup"><span data-stu-id="26e33-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="26e33-344">Запрос возвратит идентификатор идентифицированного человека, но не имя:</span><span class="sxs-lookup"><span data-stu-id="26e33-344">The request will return an id of the identified person but not the name:</span></span>

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

13. <span data-ttu-id="26e33-345">Добавьте метод *-Person ()* .</span><span class="sxs-lookup"><span data-stu-id="26e33-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="26e33-346">Указав идентификатор пользователя, этот метод затем запрашивает *службу распознавания лиц* , чтобы вернуть имя идентифицированного человека:</span><span class="sxs-lookup"><span data-stu-id="26e33-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

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

14.  <span data-ttu-id="26e33-347">Не забудьте **сохранить** изменения перед возвратом в редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="26e33-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="26e33-348">В редакторе Unity перетащите сценарий Фацеаналисис из папки скрипты на панели проект в главный объект Camera на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="26e33-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="26e33-349">Новый компонент скрипта будет добавлен в основную камеру.</span><span class="sxs-lookup"><span data-stu-id="26e33-349">The new script component will be so added to the Main Camera.</span></span> 

![Размещение Фацеаналисис на основной камере](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="26e33-351">Глава 7. Создание класса Имажекаптуре</span><span class="sxs-lookup"><span data-stu-id="26e33-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="26e33-352">Класс *имажекаптуре* предназначен для размещения методов, необходимых для взаимодействия со *службой распознавания лиц Azure* , для анализа образа, который будет записан, определения лиц в нем и определения принадлежности к известному человеку.</span><span class="sxs-lookup"><span data-stu-id="26e33-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="26e33-353">Если обнаружено известное лицо, этот класс будет отображать его имя в виде текста пользовательского интерфейса в сцене.</span><span class="sxs-lookup"><span data-stu-id="26e33-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="26e33-354">Чтобы создать класс *имажекаптуре* , сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="26e33-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="26e33-355">Щелкните правой кнопкой мыши в созданной ранее папке Scripts, а затем выберите **создать**,  **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="26e33-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="26e33-356">Вызовите скрипт *имажекаптуре*.</span><span class="sxs-lookup"><span data-stu-id="26e33-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="26e33-357">Дважды щелкните новый скрипт *имажекаптуре* , чтобы открыть его в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="26e33-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="26e33-358">Введите следующие пространства имен над классом Имажекаптуре:</span><span class="sxs-lookup"><span data-stu-id="26e33-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="26e33-359">В классе *имажекаптуре* добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="26e33-359">Inside the *ImageCapture* class, add the following variables:</span></span>

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

5.  <span data-ttu-id="26e33-360">Добавьте методы *спящего режима ()* и *Start ()* , необходимые для инициализироватьи класса, и разрешите HoloLens захватывать жесты пользователя:</span><span class="sxs-lookup"><span data-stu-id="26e33-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

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

6.  <span data-ttu-id="26e33-361">Добавьте *тафандлер ()* , который вызывается, когда пользователь выполняет жест *касания* :</span><span class="sxs-lookup"><span data-stu-id="26e33-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

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

7.  <span data-ttu-id="26e33-362">Добавьте метод *ексекутеимажекаптуреанданалисис ()* , который начнет процесс записи образа:</span><span class="sxs-lookup"><span data-stu-id="26e33-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

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

8.  <span data-ttu-id="26e33-363">Добавьте обработчики, вызываемые при завершении процесса записи фотографий:</span><span class="sxs-lookup"><span data-stu-id="26e33-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

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

9. <span data-ttu-id="26e33-364">Не забудьте **сохранить** изменения перед возвратом в редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="26e33-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="26e33-365">Глава 8. Создание решения</span><span class="sxs-lookup"><span data-stu-id="26e33-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="26e33-366">Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="26e33-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="26e33-367">Перед этим убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="26e33-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="26e33-368">Все параметры, упомянутые в главе 3, заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="26e33-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="26e33-369">*Фацеаналисис* скрипта прикреплен к главному объекту Camera.</span><span class="sxs-lookup"><span data-stu-id="26e33-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="26e33-370">**Ключ проверки** подлинности и **идентификатор группы** заданы в сценарии *фацеаналисис* .</span><span class="sxs-lookup"><span data-stu-id="26e33-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="26e33-371">Этот момент готов к созданию решения.</span><span class="sxs-lookup"><span data-stu-id="26e33-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="26e33-372">После сборки решения вы будете готовы к развертыванию приложения.</span><span class="sxs-lookup"><span data-stu-id="26e33-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="26e33-373">Чтобы начать процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="26e33-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="26e33-374">Сохраните текущую сцену, щелкнув файл, сохранить.</span><span class="sxs-lookup"><span data-stu-id="26e33-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="26e33-375">Последовательно выберите пункты файл, параметры сборки и добавить открытые сцены.</span><span class="sxs-lookup"><span data-stu-id="26e33-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="26e33-376">Убедитесь, что проект Unity C# является тактовым.</span><span class="sxs-lookup"><span data-stu-id="26e33-376">Make sure to tick Unity C# Projects.</span></span>

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="26e33-378">Нажмите кнопку сборка.</span><span class="sxs-lookup"><span data-stu-id="26e33-378">Press Build.</span></span> <span data-ttu-id="26e33-379">После этого Unity запустит окно проводника, в котором необходимо создать, а затем выбрать папку для построения приложения.</span><span class="sxs-lookup"><span data-stu-id="26e33-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="26e33-380">Создайте эту папку прямо сейчас, в проекте Unity и назовите ее приложение.</span><span class="sxs-lookup"><span data-stu-id="26e33-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="26e33-381">Затем выберите папку приложения и нажмите кнопку Выбрать папку.</span><span class="sxs-lookup"><span data-stu-id="26e33-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="26e33-382">Unity начнет сборку проекта в папку приложения.</span><span class="sxs-lookup"><span data-stu-id="26e33-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="26e33-383">После завершения сборки Unity (может занять некоторое время) он откроет окно проводника в расположении сборки.</span><span class="sxs-lookup"><span data-stu-id="26e33-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="26e33-385">Откройте папку приложения, а затем откройте решение нового проекта (как показано выше, MR_FaceRecognition. sln).</span><span class="sxs-lookup"><span data-stu-id="26e33-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="26e33-386">Глава 9. Развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="26e33-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="26e33-387">Для развертывания на HoloLens выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="26e33-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="26e33-388">Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика**.</span><span class="sxs-lookup"><span data-stu-id="26e33-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="26e33-389">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="26e33-389">To do this:</span></span>

    1. <span data-ttu-id="26e33-390">Людьми HoloLens, откройте **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="26e33-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="26e33-391">Последовательно выберите пункты **сеть & интернет > Wi-Fi > дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="26e33-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="26e33-392">Запишите **IPv4** -адрес.</span><span class="sxs-lookup"><span data-stu-id="26e33-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="26e33-393">Затем вернитесь к параметрами **обновите & > безопасности для разработчиков** .</span><span class="sxs-lookup"><span data-stu-id="26e33-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="26e33-394">Задайте режим разработчика на.</span><span class="sxs-lookup"><span data-stu-id="26e33-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="26e33-395">Перейдите к новой сборке Unity (папка *приложения* ) и откройте файл решения в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="26e33-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="26e33-396">В конфигурации решения выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="26e33-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="26e33-397">На платформе решения выберите **x86**, **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="26e33-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="26e33-399">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение**", чтобы загружать неопубликованные приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="26e33-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="26e33-400">Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.</span><span class="sxs-lookup"><span data-stu-id="26e33-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="26e33-401">Чтобы выполнить развертывание в иммерсивное виртуальную гарнитуру, задайте для **платформы решения** значение *локальный компьютер*и задайте для параметра **Конфигурация** значение *Отладка*( *x86* в качестве **платформы**).</span><span class="sxs-lookup"><span data-stu-id="26e33-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="26e33-402">Затем выполните развертывание на локальном компьютере с помощью **меню "сборка**" и выберите пункт " *Развернуть решение*".</span><span class="sxs-lookup"><span data-stu-id="26e33-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="26e33-403">Глава 10. Использование приложения</span><span class="sxs-lookup"><span data-stu-id="26e33-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="26e33-404">Людьми HoloLens, запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="26e33-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="26e33-405">Взгляните на пользователя, зарегистрированного в *API распознавания лиц*.</span><span class="sxs-lookup"><span data-stu-id="26e33-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="26e33-406">Убедитесь в следующем.</span><span class="sxs-lookup"><span data-stu-id="26e33-406">Make sure that:</span></span>

    -  <span data-ttu-id="26e33-407">Лицо человека не является слишком отдаленным и ясно видимым</span><span class="sxs-lookup"><span data-stu-id="26e33-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="26e33-408">Освещение среды не слишком темнее</span><span class="sxs-lookup"><span data-stu-id="26e33-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="26e33-409">Используйте жест касания, чтобы захватить изображение человека.</span><span class="sxs-lookup"><span data-stu-id="26e33-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="26e33-410">Подождите, пока приложение отправит запрос на анализ и получите ответ.</span><span class="sxs-lookup"><span data-stu-id="26e33-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="26e33-411">Если пользователь успешно распознал, его имя будет отображаться как текст пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="26e33-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="26e33-412">Процесс записи можно повторить с помощью жеста касания каждые несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="26e33-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="26e33-413">Готовое приложение Azure API распознавания лиц</span><span class="sxs-lookup"><span data-stu-id="26e33-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="26e33-414">Поздравляем! вы создали приложение смешанной реальности, которое использует службу распознавания лиц Azure для обнаружения лиц в образе и определения известных лиц.</span><span class="sxs-lookup"><span data-stu-id="26e33-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![результат выполнения этого курса](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="26e33-416">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="26e33-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="26e33-417">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="26e33-417">Exercise 1</span></span>

<span data-ttu-id="26e33-418">**API распознавания лиц Azure** достаточно мощный, чтобы обнаружить до 64 лиц в одном образе.</span><span class="sxs-lookup"><span data-stu-id="26e33-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="26e33-419">Расширьте приложение, чтобы оно могло распознать два или три лица, среди многих других людей.</span><span class="sxs-lookup"><span data-stu-id="26e33-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="26e33-420">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="26e33-420">Exercise 2</span></span>

<span data-ttu-id="26e33-421">**API распознавания лиц Azure** также может предоставлять все виды информации об атрибутах.</span><span class="sxs-lookup"><span data-stu-id="26e33-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="26e33-422">Интегрируйте его в приложение.</span><span class="sxs-lookup"><span data-stu-id="26e33-422">Integrate this into the application.</span></span> <span data-ttu-id="26e33-423">Это может быть еще более интересно при объединении с [API распознавания эмоций](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="26e33-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
