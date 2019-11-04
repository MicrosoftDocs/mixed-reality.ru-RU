---
title: MR и Azure 305 — функции и хранилище
description: Пройдите этот курс, чтобы узнать, как реализовать службу хранилища Azure и функции в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, функции, хранилище, hololens, иммерсивное, VR
ms.openlocfilehash: 79c276d45163465c9921d02343d41d52d5f094e7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437987"
---
>[!NOTE]
><span data-ttu-id="23ad0-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="23ad0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="23ad0-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="23ad0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="23ad0-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="23ad0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="23ad0-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="23ad0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="23ad0-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="23ad0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="23ad0-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="23ad0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="23ad0-110">MR и Azure 305: функции и хранилище</span><span class="sxs-lookup"><span data-stu-id="23ad0-110">MR and Azure 305: Functions and storage</span></span>

![окончательный продукт — запуск](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="23ad0-112">В этом курсе вы узнаете, как создавать и использовать функции Azure и хранить данные в ресурсе службы хранилища Azure в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="23ad0-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="23ad0-113">*Функции Azure* — это служба Майкрософт, которая позволяет разработчикам запускать небольшие фрагменты кода "функции" в Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="23ad0-114">Это позволяет делегировать работу в облако, а не локальное приложение, которое может иметь множество преимуществ.</span><span class="sxs-lookup"><span data-stu-id="23ad0-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="23ad0-115">*Функции Azure* поддерживают несколько языков разработки, включая C\#, F\#, Node. js, Java и PHP.</span><span class="sxs-lookup"><span data-stu-id="23ad0-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="23ad0-116">Дополнительные сведения см. в [статье о функциях Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="23ad0-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="23ad0-117">*Хранилище Azure* — это облачная служба Майкрософт, которая позволяет разработчикам хранить данные с страховкой, которая будет высокодоступной, безопасной, устойчивой, масштабируемой и избыточной.</span><span class="sxs-lookup"><span data-stu-id="23ad0-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="23ad0-118">Это означает, что корпорация Майкрософт будет выполнять все задачи обслуживания и критические проблемы.</span><span class="sxs-lookup"><span data-stu-id="23ad0-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="23ad0-119">Дополнительные сведения см. в [статье о службе хранилища Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="23ad0-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="23ad0-120">Прополнив этот курс, вы получите иммерсивное приложение для наушников, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="23ad0-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="23ad0-121">Позволяет пользователю взходить на сцену.</span><span class="sxs-lookup"><span data-stu-id="23ad0-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="23ad0-122">Активировать порождение объектов, когда пользователь высматривает трехмерную кнопку "Кнопка".</span><span class="sxs-lookup"><span data-stu-id="23ad0-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="23ad0-123">Порожденные объекты будут выбраны функцией Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="23ad0-124">При порождении каждого объекта приложение сохранит тип объекта в *файле Azure*, расположенном в *службе хранилища Azure*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="23ad0-125">После второй загрузки данные *файла Azure* будут получены и использованы для воспроизведения порожденных действий от предыдущего экземпляра приложения.</span><span class="sxs-lookup"><span data-stu-id="23ad0-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="23ad0-126">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="23ad0-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="23ad0-127">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="23ad0-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="23ad0-128">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="23ad0-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="23ad0-129">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="23ad0-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="23ad0-130">Хождение</span><span class="sxs-lookup"><span data-stu-id="23ad0-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="23ad0-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="23ad0-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="23ad0-132"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="23ad0-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="23ad0-133">MR и Azure 305: функции и хранилище</span><span class="sxs-lookup"><span data-stu-id="23ad0-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="23ad0-134">✔️</span><span class="sxs-lookup"><span data-stu-id="23ad0-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="23ad0-135">✔️</span><span class="sxs-lookup"><span data-stu-id="23ad0-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="23ad0-136">Хотя этот курс в основном ориентирован на гарнитуры Windows Mixed Reality (VR), вы также можете применить сведения, которые вы узнаете в этом курсе, к Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="23ad0-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="23ad0-137">Как вы пройдете вместе с курсом, вы увидите примечания о любых изменениях, которые могут потребоваться для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="23ad0-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="23ad0-138">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="23ad0-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="23ad0-139">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="23ad0-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="23ad0-140">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018).</span><span class="sxs-lookup"><span data-stu-id="23ad0-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="23ad0-141">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.</span><span class="sxs-lookup"><span data-stu-id="23ad0-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="23ad0-142">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="23ad0-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="23ad0-143">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="23ad0-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="23ad0-144">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="23ad0-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="23ad0-145">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="23ad0-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="23ad0-146">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="23ad0-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="23ad0-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="23ad0-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="23ad0-148">Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="23ad0-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="23ad0-149">Подписка на учетную запись Azure для создания ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="23ad0-150">Доступ к Интернету для установки Azure и извлечения данных</span><span class="sxs-lookup"><span data-stu-id="23ad0-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="23ad0-151">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="23ad0-151">Before you start</span></span>

<span data-ttu-id="23ad0-152">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="23ad0-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="23ad0-153">Глава 1. портал Azure</span><span class="sxs-lookup"><span data-stu-id="23ad0-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="23ad0-154">Чтобы использовать **службу хранилища Azure**, вам потребуется создать и настроить **учетную запись хранения** в портал Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="23ad0-155">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="23ad0-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="23ad0-156">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="23ad0-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="23ad0-157">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="23ad0-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="23ad0-158">Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу, а затем найдите *учетную запись хранения*и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![Поиск в службе хранилища Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="23ad0-160">Слово **New** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="23ad0-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="23ad0-161">На новой странице будет представлено описание службы *учетной записи хранения Azure* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="23ad0-162">В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="23ad0-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Создание службы](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="23ad0-164">После нажатия кнопки **создать**:</span><span class="sxs-lookup"><span data-stu-id="23ad0-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="23ad0-165">Введите *имя* для своей учетной записи. Имейте в виду, что это поле принимает только цифры и строчные буквы.</span><span class="sxs-lookup"><span data-stu-id="23ad0-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="23ad0-166">В качестве *модели развертывания*выберите **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="23ad0-167">В качестве *типа учетной записи*выберите **хранилище (общее назначение v1)** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="23ad0-168">Определите *Расположение* группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="23ad0-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="23ad0-169">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="23ad0-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="23ad0-170">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="23ad0-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="23ad0-171">Для *репликации* выберите **геоизбыточное хранилище (RA-GRS) с доступом для чтения**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="23ad0-172">Для *повышения производительности*выберите **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="23ad0-173">Оставьте *защищенное перемещение обязательным* , как **отключено**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="23ad0-174">Выберите *подписку*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="23ad0-175">Выберите *группу ресурсов* или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="23ad0-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="23ad0-176">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="23ad0-177">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="23ad0-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="23ad0-178">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="23ad0-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="23ad0-179">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="23ad0-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="23ad0-180">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-180">Select **Create**.</span></span>

        ![сведения о входной службе](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="23ad0-182">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="23ad0-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="23ad0-183">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="23ad0-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![новое уведомление на портале Azure](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="23ad0-185">Щелкните уведомления, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="23ad0-185">Click on the notifications to explore your new Service instance.</span></span>

    ![Переход к ресурсу](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="23ad0-187">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="23ad0-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="23ad0-188">Вы будете перенаправлены на новый экземпляр службы *учетной записи хранения* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![ключи доступа](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="23ad0-190">Щелкните *ключи доступа*, чтобы отобразить конечные точки для этой облачной службы.</span><span class="sxs-lookup"><span data-stu-id="23ad0-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="23ad0-191">Чтобы скопировать один из ключей для последующего использования, используйте *Блокнот* или аналогичный.</span><span class="sxs-lookup"><span data-stu-id="23ad0-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="23ad0-192">Кроме того, обратите внимание на значение *строки подключения* , так как оно будет использоваться в классе *азуресервицес* , который будет создан позже.</span><span class="sxs-lookup"><span data-stu-id="23ad0-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![Копировать строку подключения](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="23ad0-194">Глава 2. Настройка функции Azure</span><span class="sxs-lookup"><span data-stu-id="23ad0-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="23ad0-195">Теперь вы можете написать функцию **Azure** в службе Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="23ad0-196">**Функцию Azure** можно использовать для практически любых действий, выполняемых с классической функцией в коде. разница заключается в том, что доступ к этой функции может осуществляться любым приложением, имеющим учетные данные для доступа к учетной записи Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="23ad0-197">Чтобы создать функцию Azure, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="23ad0-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="23ad0-198">На *портале Azure*щелкните **создать** в левом верхнем углу и найдите *приложение-функция*и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Создание приложения функции](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="23ad0-200">Слово **New** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="23ad0-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="23ad0-201">На новой странице будет представлено описание службы *приложение-функция Azure* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="23ad0-202">В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="23ad0-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![сведения о приложении функции](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="23ad0-204">После нажатия кнопки **создать**:</span><span class="sxs-lookup"><span data-stu-id="23ad0-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="23ad0-205">Укажите *имя приложения*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-205">Provide an *App name*.</span></span> <span data-ttu-id="23ad0-206">Здесь можно использовать только буквы и цифры (допускается использование прописных и строчных букв).</span><span class="sxs-lookup"><span data-stu-id="23ad0-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="23ad0-207">Выберите предпочитаемую *подписку*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="23ad0-208">Выберите *группу ресурсов* или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="23ad0-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="23ad0-209">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="23ad0-210">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="23ad0-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="23ad0-211">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="23ad0-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="23ad0-212">В этом упражнении выберите *Windows* в качестве выбранной **ОС**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="23ad0-213">Выберите *план потребления* для **плана размещения**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="23ad0-214">Определите *Расположение* группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="23ad0-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="23ad0-215">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="23ad0-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="23ad0-216">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="23ad0-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="23ad0-217">Для оптимальной производительности выберите тот же регион, что и для учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="23ad0-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="23ad0-218">В поле *хранилище*выберите **использовать существующий**, а затем в раскрывающемся меню найдите созданное ранее хранилище.</span><span class="sxs-lookup"><span data-stu-id="23ad0-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="23ad0-219">Для этого упражнения не выполняйте *Application Insights* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-219">Leave *Application Insights* off for this exercise.</span></span>

        ![сведения о приложении входной функции](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="23ad0-221">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="23ad0-222">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="23ad0-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="23ad0-223">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="23ad0-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![новое уведомление на портале Azure](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="23ad0-225">Щелкните уведомления, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="23ad0-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![Переход к приложению функции ресурсов](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="23ad0-227">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="23ad0-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="23ad0-228">Вы будете перенаправлены на новый экземпляр службы *приложение-функция* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="23ad0-229">На панели мониторинга *приложение-функция* наведите указатель мыши на *функции*, расположенные на панели слева, а затем щелкните символ **+ (плюс)** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![создать новую функцию](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="23ad0-231">На следующей странице убедитесь, что **веб-перехватчик + API** выбран, и для *выбора языка* выберите **CSharp**, так как это будет язык, используемый в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="23ad0-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="23ad0-232">Наконец, нажмите кнопку **создать эту функцию** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-232">Lastly, click the **Create this function** button.</span></span>

    ![Выбор веб-перехватчика CSharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="23ad0-234">Вы должны присутствовать на кодовой странице (Run. CSX), если это не так, щелкните созданную функцию в списке функции на панели слева.</span><span class="sxs-lookup"><span data-stu-id="23ad0-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![открыть новую функцию](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="23ad0-236">Скопируйте следующий код в функцию.</span><span class="sxs-lookup"><span data-stu-id="23ad0-236">Copy the following code into your function.</span></span> <span data-ttu-id="23ad0-237">Эта функция будет просто возвращать случайное целое число от 0 до 2 при вызове.</span><span class="sxs-lookup"><span data-stu-id="23ad0-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="23ad0-238">Не беспокойтесь о существующем коде, вы можете вставить его в верхнюю часть.</span><span class="sxs-lookup"><span data-stu-id="23ad0-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="23ad0-239">Выберите **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-239">Select **Save**.</span></span>

14. <span data-ttu-id="23ad0-240">Результат должен выглядеть, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="23ad0-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="23ad0-241">Щелкните **получить URL-адрес функции** и обратите внимание на отображаемую *конечную точку* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="23ad0-242">Его необходимо вставить в класс *азуресервицес* , который будет создан далее в этом курсе.</span><span class="sxs-lookup"><span data-stu-id="23ad0-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![Получение конечной точки функции](images/AzureLabs-Lab5-16.png)

    ![Получение конечной точки функции](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="23ad0-245">Глава 3. Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="23ad0-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="23ad0-246">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="23ad0-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="23ad0-247">Настройка и тестирование иммерсивного наушников смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="23ad0-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="23ad0-248">Для этого курса **не** потребуется использовать контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="23ad0-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="23ad0-249">Если вам нужна поддержка настройки иммерсивного головного телефона, [посетите статью Настройка смешанной реальности](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="23ad0-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="23ad0-250">Откройте Unity и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-250">Open Unity and click **New**.</span></span>

    ![создать новый проект Unity](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="23ad0-252">Теперь необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="23ad0-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="23ad0-253">Вставьте **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="23ad0-254">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="23ad0-255">Задайте для *расположения нужное расположение* (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="23ad0-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="23ad0-256">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-256">Then, click **Create project**.</span></span>

    ![Присвойте имя новому проекту Unity](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="23ad0-258">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="23ad0-259">Перейдите к разделу **изменение** **параметров** > , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="23ad0-260">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="23ad0-261">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-261">Close the **Preferences** window.</span></span>

    ![Установка Visual Studio в качестве редактора скриптов](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="23ad0-263">Затем перейдите в раздел **файл** > **параметры сборки** и переключите платформу на **универсальная платформа Windows**, нажав кнопку **коммутатора платформы** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Переключение платформы в UWP](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="23ad0-265">Перейдите в раздел **файл** > **параметры сборки** и убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="23ad0-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="23ad0-266">**Целевое устройство** настроено для **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="23ad0-267">Для Microsoft HoloLens задайте для параметра **целевое устройство** значение *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="23ad0-268">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="23ad0-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="23ad0-269">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="23ad0-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="23ad0-270">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="23ad0-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="23ad0-271">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="23ad0-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="23ad0-272">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="23ad0-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="23ad0-273">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="23ad0-274">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="23ad0-274">A save window will appear.</span></span>

            ![Добавление открытых сцен](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="23ad0-276">Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="23ad0-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![создать папку сцен](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="23ad0-278">Откройте созданную папку **сцены** , а затем в текстовом поле **имя файла** введите **функтионссцене**, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![сохранить сцену функций](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="23ad0-280">Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="23ad0-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![сохранить сцену функций](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="23ad0-282">В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![Параметры проигрывателя в инспекторе](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="23ad0-284">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="23ad0-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="23ad0-285">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="23ad0-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="23ad0-286">**Версия среды выполнения сценариев** должна быть **экспериментальной** (эквивалент .NET 4,6), что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="23ad0-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="23ad0-287">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="23ad0-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="23ad0-288">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="23ad0-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="23ad0-289">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="23ad0-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="23ad0-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="23ad0-290">**InternetClient**</span></span>

            ![Установка возможностей](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="23ad0-292">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![задать параметры XR](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="23ad0-294">Назад в *параметрах сборки* *проект Unity C#*  больше не является серым. Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="23ad0-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![проекты тактов c#](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="23ad0-296">Закройте окно параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="23ad0-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="23ad0-297">Сохраните сцену и проект (**файл** > **сохранить сцену или файл** > **сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="23ad0-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="23ad0-298">Глава 4. Настройка основной камеры</span><span class="sxs-lookup"><span data-stu-id="23ad0-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23ad0-299">Если вы хотите пропустить *настройку Unity, настроили* компоненты этого курса и продолжить работу с кодом, [Скачайте этот файл. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)и импортируйте его в проект как [пользовательский пакет](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="23ad0-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="23ad0-300">Это также будет содержать библиотеки DLL из следующей главы.</span><span class="sxs-lookup"><span data-stu-id="23ad0-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="23ad0-301">После импорта продолжите работу с [главой 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="23ad0-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="23ad0-302">На *панели Иерархия*вы найдете объект с названием **Главная камера**, этот объект представляет "головную точку представления", когда вы "внутри приложения".</span><span class="sxs-lookup"><span data-stu-id="23ad0-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="23ad0-303">На панели мониторинга Unity перед вами выберите **основную камеру GameObject**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="23ad0-304">Вы заметите, что на *панели инспектора* (как правило, на панели мониторинга) отображаются различные компоненты этого *GameObject*, с помощью кнопки *преобразовывать* в верхней части, за которой следует *Камера*и некоторые другие компоненты.</span><span class="sxs-lookup"><span data-stu-id="23ad0-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="23ad0-305">Необходимо будет сбросить преобразование основной камеры, чтобы она правильно расположиться.</span><span class="sxs-lookup"><span data-stu-id="23ad0-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="23ad0-306">Для этого щелкните значок **шестеренки** рядом с компонентом *преобразования* камеры и выберите **сбросить**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![Сброс преобразования](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="23ad0-308">Затем обновите компонент **преобразования** , чтобы он выглядел следующим образом:</span><span class="sxs-lookup"><span data-stu-id="23ad0-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="23ad0-309">TRANSFORM-ПОЗИЦИОНИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="23ad0-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="23ad0-310">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-310">**X**</span></span>   | <span data-ttu-id="23ad0-311">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-311">**Y**</span></span>                     | <span data-ttu-id="23ad0-312">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-312">**Z**</span></span> |
    | <span data-ttu-id="23ad0-313">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-313">0</span></span>       | <span data-ttu-id="23ad0-314">1</span><span class="sxs-lookup"><span data-stu-id="23ad0-314">1</span></span>                         | <span data-ttu-id="23ad0-315">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-315">0</span></span>     |    

    |       | <span data-ttu-id="23ad0-316">ПОВОРОТ ПРЕОБРАЗОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="23ad0-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="23ad0-317">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-317">**X**</span></span> | <span data-ttu-id="23ad0-318">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-318">**Y**</span></span>                | <span data-ttu-id="23ad0-319">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-319">**Z**</span></span> |
    | <span data-ttu-id="23ad0-320">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-320">0</span></span>     | <span data-ttu-id="23ad0-321">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-321">0</span></span>                    | <span data-ttu-id="23ad0-322">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-322">0</span></span>     |

    |       | <span data-ttu-id="23ad0-323">ПРЕОБРАЗОВАНИЕ — МАСШТАБИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="23ad0-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="23ad0-324">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-324">**X**</span></span> | <span data-ttu-id="23ad0-325">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-325">**Y**</span></span>             | <span data-ttu-id="23ad0-326">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-326">**Z**</span></span> |
    | <span data-ttu-id="23ad0-327">1</span><span class="sxs-lookup"><span data-stu-id="23ad0-327">1</span></span>     | <span data-ttu-id="23ad0-328">1</span><span class="sxs-lookup"><span data-stu-id="23ad0-328">1</span></span>                 | <span data-ttu-id="23ad0-329">1</span><span class="sxs-lookup"><span data-stu-id="23ad0-329">1</span></span>     |

    ![Задание преобразования камеры](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="23ad0-331">Глава 5. Настройка сцены Unity</span><span class="sxs-lookup"><span data-stu-id="23ad0-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="23ad0-332">Щелкните правой кнопкой мыши пустую область *панели Иерархия*в разделе **трехмерный объект**, добавьте **плоскость**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![Создание новой плоскости](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="23ad0-334">Выбрав объект **плоскости** , измените следующие параметры на *панели инспектора*:</span><span class="sxs-lookup"><span data-stu-id="23ad0-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="23ad0-335">TRANSFORM-ПОЗИЦИОНИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="23ad0-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="23ad0-336">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-336">**X**</span></span> | <span data-ttu-id="23ad0-337">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-337">**Y**</span></span>                | <span data-ttu-id="23ad0-338">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-338">**Z**</span></span> |
    | <span data-ttu-id="23ad0-339">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-339">0</span></span>     | <span data-ttu-id="23ad0-340">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-340">0</span></span>                    | <span data-ttu-id="23ad0-341">추가를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23ad0-341">4</span></span>     |

    |       | <span data-ttu-id="23ad0-342">ПРЕОБРАЗОВАНИЕ — МАСШТАБИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="23ad0-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="23ad0-343">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-343">**X**</span></span> | <span data-ttu-id="23ad0-344">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-344">**Y**</span></span>             | <span data-ttu-id="23ad0-345">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-345">**Z**</span></span> |
    | <span data-ttu-id="23ad0-346">10</span><span class="sxs-lookup"><span data-stu-id="23ad0-346">10</span></span>    | <span data-ttu-id="23ad0-347">1</span><span class="sxs-lookup"><span data-stu-id="23ad0-347">1</span></span>                 | <span data-ttu-id="23ad0-348">10</span><span class="sxs-lookup"><span data-stu-id="23ad0-348">10</span></span>    |

    ![Задание расположения и масштаба плоскости](images/AzureLabs-Lab5-32.png)

    ![представление сцены плоскости](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="23ad0-351">Щелкните правой кнопкой мыши пустую область *панели Иерархия*в разделе **трехмерный объект**и добавьте **куб**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="23ad0-352">Переименование Куба в **газебуттон** (с выбранным кубом нажмите клавишу "F2").</span><span class="sxs-lookup"><span data-stu-id="23ad0-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="23ad0-353">Измените следующие параметры на *панели инспектора*:</span><span class="sxs-lookup"><span data-stu-id="23ad0-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="23ad0-354">TRANSFORM-ПОЗИЦИОНИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="23ad0-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="23ad0-355">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-355">**X**</span></span> | <span data-ttu-id="23ad0-356">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-356">**Y**</span></span>                | <span data-ttu-id="23ad0-357">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-357">**Z**</span></span> |
        | <span data-ttu-id="23ad0-358">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-358">0</span></span>     | <span data-ttu-id="23ad0-359">3</span><span class="sxs-lookup"><span data-stu-id="23ad0-359">3</span></span>                    | <span data-ttu-id="23ad0-360">5</span><span class="sxs-lookup"><span data-stu-id="23ad0-360">5</span></span>     |


        ![задать преобразование кнопки взвзгляда](images/AzureLabs-Lab5-34.png)

        ![представление сцены кнопки взгляда](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="23ad0-363">Щелкните раскрывающийся список **тег** и выберите **Добавить тег** , чтобы открыть *панель Теги & слои*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Добавить новый тег](images/AzureLabs-Lab5-36.png)

        ![выбрать плюс](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="23ad0-366">Нажмите кнопку **+ (плюс)** и в поле *новое имя тега* введите **газебуттон**и нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![имя новый тег](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="23ad0-368">Щелкните объект **газебуттон** на *панели Иерархия*, а затем на *панели инспектора*назначьте созданный тег **газебуттон** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![назначить кнопке "взгляд" новый тег](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="23ad0-370">Щелкните правой кнопкой мыши объект **газебуттон** на *панели Иерархия*и добавьте **пустой GameObject** (который будет добавлен в качестве *дочернего* объекта).</span><span class="sxs-lookup"><span data-stu-id="23ad0-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="23ad0-371">Выберите новый объект и переименуйте его в **шапеспавнпоинт**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="23ad0-372">Измените следующие параметры на *панели инспектора*:</span><span class="sxs-lookup"><span data-stu-id="23ad0-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="23ad0-373">TRANSFORM-ПОЗИЦИОНИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="23ad0-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="23ad0-374">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-374">**X**</span></span> |<span data-ttu-id="23ad0-375">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-375">**Y**</span></span>                 | <span data-ttu-id="23ad0-376">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-376">**Z**</span></span> |
        | <span data-ttu-id="23ad0-377">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-377">0</span></span>     | <span data-ttu-id="23ad0-378">-1</span><span class="sxs-lookup"><span data-stu-id="23ad0-378">-1</span></span>                   | <span data-ttu-id="23ad0-379">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-379">0</span></span>     |

        ![Обновление преобразования точки порождения фигуры](images/AzureLabs-Lab5-40.png)

        ![представление сцены создания точки порождения фигуры](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="23ad0-382">Далее предстоит создать **трехмерный текстовый** объект, чтобы оставить отзыв о состоянии службы Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="23ad0-383">Щелкните правой кнопкой мыши **газебуттон** на панели Иерархия и добавьте **трехмерный объект** > **трехмерный текстовый** объект в качестве *дочернего*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![создать новый объект объемного текста](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="23ad0-385">Переименуйте **трехмерный текстовый** объект в **азурестатустекст**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="23ad0-386">Измените преобразование объекта **азурестатустекст** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="23ad0-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="23ad0-387">TRANSFORM-ПОЗИЦИОНИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="23ad0-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="23ad0-388">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-388">**X**</span></span> | <span data-ttu-id="23ad0-389">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-389">**Y**</span></span>                | <span data-ttu-id="23ad0-390">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-390">**Z**</span></span> |
    | <span data-ttu-id="23ad0-391">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-391">0</span></span>     | <span data-ttu-id="23ad0-392">0</span><span class="sxs-lookup"><span data-stu-id="23ad0-392">0</span></span>                    | <span data-ttu-id="23ad0-393">— 0,6</span><span class="sxs-lookup"><span data-stu-id="23ad0-393">-0.6</span></span>  |

    |       | <span data-ttu-id="23ad0-394">ПРЕОБРАЗОВАНИЕ — МАСШТАБИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="23ad0-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="23ad0-395">**X**</span><span class="sxs-lookup"><span data-stu-id="23ad0-395">**X**</span></span> | <span data-ttu-id="23ad0-396">**&**</span><span class="sxs-lookup"><span data-stu-id="23ad0-396">**Y**</span></span>             | <span data-ttu-id="23ad0-397">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="23ad0-397">**Z**</span></span> |
    | <span data-ttu-id="23ad0-398">0,1</span><span class="sxs-lookup"><span data-stu-id="23ad0-398">0.1</span></span>   | <span data-ttu-id="23ad0-399">0,1</span><span class="sxs-lookup"><span data-stu-id="23ad0-399">0.1</span></span>               | <span data-ttu-id="23ad0-400">0,1</span><span class="sxs-lookup"><span data-stu-id="23ad0-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="23ad0-401">Не беспокойтесь, если он находится вне сети, так как это будет исправлено при обновлении компонента сетки текста.</span><span class="sxs-lookup"><span data-stu-id="23ad0-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="23ad0-402">Измените компонент " **Сетка текста** " в соответствии с приведенным ниже:</span><span class="sxs-lookup"><span data-stu-id="23ad0-402">Change the **Text Mesh** component to match the below:</span></span>

    ![Настройка компонента сетки текста](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="23ad0-404">Выбранный цвет имеет шестнадцатеричный цвет: **000000FF**, хотя вы можете выбрать собственный, просто убедитесь, что он доступен для чтения.</span><span class="sxs-lookup"><span data-stu-id="23ad0-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="23ad0-405">Теперь структура панели иерархии должна выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="23ad0-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![сетка текста в представлении сцены](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="23ad0-407">Теперь сцена должна выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="23ad0-407">Your scene should now look like this:</span></span>

    ![сетка текста в представлении сцены](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="23ad0-409">Глава 6. Импорт хранилища Azure для Unity</span><span class="sxs-lookup"><span data-stu-id="23ad0-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="23ad0-410">Вы будете использовать службу хранилища Azure для Unity (которая самостоятельно использует пакет SDK для .NET для Azure).</span><span class="sxs-lookup"><span data-stu-id="23ad0-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="23ad0-411">Дополнительные сведения об этом см. в [статье хранилище Azure для Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="23ad0-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="23ad0-412">В Unity существует известная ошибка, которая требует перенастройки подключаемых модулей после импорта.</span><span class="sxs-lookup"><span data-stu-id="23ad0-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="23ad0-413">Эти действия (4-7 в этом разделе) больше не понадобятся после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="23ad0-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="23ad0-414">Чтобы импортировать пакет SDK в собственный проект, убедитесь, что вы скачали последнюю версию [". пакет unitypackage" из GitHub](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="23ad0-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="23ad0-415">Затем выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="23ad0-415">Then, do the following:</span></span>

1.  <span data-ttu-id="23ad0-416">Добавьте файл **. пакет unitypackage** в Unity с помощью пункта **активы** > **импортировать пакет** > **настраиваемый пакет** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="23ad0-417">В появившемся окне **Импорт пакета Unity** можно выбрать все в разделе **подключаемый модуль** > **хранилище**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="23ad0-418">Снимите флажок все остальное, так как он не требуется для этого курса.</span><span class="sxs-lookup"><span data-stu-id="23ad0-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Импорт в пакет](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="23ad0-420">Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="23ad0-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="23ad0-421">Перейдите в папку *хранилища* *подключаемых модулей*в представлении проекта и выберите *только*следующие подключаемые модули:</span><span class="sxs-lookup"><span data-stu-id="23ad0-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="23ad0-422">Microsoft. Data. EDM</span><span class="sxs-lookup"><span data-stu-id="23ad0-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="23ad0-423">Microsoft. Data. OData</span><span class="sxs-lookup"><span data-stu-id="23ad0-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="23ad0-424">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="23ad0-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="23ad0-425">Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="23ad0-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="23ad0-426">System. пространственные</span><span class="sxs-lookup"><span data-stu-id="23ad0-426">System.Spatial</span></span>

        ![снять флажок с любой платформы](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="23ad0-428">Выбрав *нужные подключаемые модули* , **снимите флажок для** *любой платформы* и **снимите флажок** *всаплайер* , а затем нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![применение библиотек DLL платформы](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="23ad0-430">Мы помечаем эти отдельные подключаемые модули для использования только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="23ad0-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="23ad0-431">Это связано с тем, что в папке WSA существуют разные версии тех же подключаемых модулей, которые будут использоваться после экспорта проекта из Unity.</span><span class="sxs-lookup"><span data-stu-id="23ad0-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="23ad0-432">В папке подключаемый модуль *хранилища* выберите только:</span><span class="sxs-lookup"><span data-stu-id="23ad0-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="23ad0-433">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="23ad0-433">Microsoft.Data.Services.Client</span></span>

        ![Set не обрабатывать библиотеки DLL](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="23ad0-435">Установите флажок **не обрабатывать** в разделе *параметры платформы* и нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![не применять обработку](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="23ad0-437">Мы пометили этот подключаемый модуль как "не обрабатывать", так как при обработке этого подключаемого модуля в установщике сборок Unity возникли трудности.</span><span class="sxs-lookup"><span data-stu-id="23ad0-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="23ad0-438">Подключаемый модуль по-прежнему будет работать, даже если он не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="23ad0-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="23ad0-439">Глава 7. Создание класса Азуресервицес</span><span class="sxs-lookup"><span data-stu-id="23ad0-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="23ad0-440">Первый класс, который предстоит создать, является классом *азуресервицес* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="23ad0-441">Класс *азуресервицес* будет отвечать за:</span><span class="sxs-lookup"><span data-stu-id="23ad0-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="23ad0-442">Хранение учетных данных учетной записи Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="23ad0-443">Вызов функции приложения Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="23ad0-444">Отправка и скачивание файла данных в облачном хранилище Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="23ad0-445">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="23ad0-445">To create this Class:</span></span>

1.  <span data-ttu-id="23ad0-446">Щелкните правой кнопкой мыши папку *Asset* , расположенную на панели проект, и **Создайте** **папку** > .</span><span class="sxs-lookup"><span data-stu-id="23ad0-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="23ad0-447">Назовите папку **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-447">Name the folder **Scripts**.</span></span>

    ![создать новую папку](images/AzureLabs-Lab5-50.png)

    ![Папка вызова — скрипты](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="23ad0-450">Дважды щелкните только что созданную папку, чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="23ad0-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="23ad0-451">Щелкните правой кнопкой мыши внутри папки, **Создайте**  **C# скрипт** > .</span><span class="sxs-lookup"><span data-stu-id="23ad0-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="23ad0-452">Вызовите скрипт *азуресервицес*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="23ad0-453">Дважды щелкните новый класс *азуресервицес* , чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="23ad0-454">Добавьте следующие пространства имен в верхнюю часть *азуресервицес*:</span><span class="sxs-lookup"><span data-stu-id="23ad0-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="23ad0-455">Добавьте следующие поля инспектора в класс *азуресервицес* :</span><span class="sxs-lookup"><span data-stu-id="23ad0-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="23ad0-456">Затем добавьте следующие переменные члена в класс *азуресервицес* :</span><span class="sxs-lookup"><span data-stu-id="23ad0-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="23ad0-457">Убедитесь, что значения *конечных точек* и *строк подключения* заменены значениями из хранилища Azure, расположенными на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="23ad0-458">Теперь необходимо добавить код для методов *"спящий" ()* и *"начало" ()* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="23ad0-459">Эти методы будут вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="23ad0-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="23ad0-460">В [следующей главе](#chapter-10---completing-the-azureservices-class)мы будем заполнять код для *каллазурефунктионфорнекстшапе ()* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="23ad0-461">Удалите метод *Update ()* , так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="23ad0-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="23ad0-462">Сохраните изменения в Visual Studio, а затем вернитесь в Unity.</span><span class="sxs-lookup"><span data-stu-id="23ad0-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="23ad0-463">Щелкните и перетащите класс *азуресервицес* из папки Scripts в основной объект Camera на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="23ad0-464">Выберите основную камеру, затем захватите дочерний объект **азурестатустекст** из объекта **газебуттон** и поместите его в поле Целевой объект ссылки **азурестатустекст** в *инспекторе*, чтобы предоставить ссылку на  *Сценарий Азуресервицес* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![Назначение целевой ссылки на текст состояния Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="23ad0-466">Глава 8. Создание класса Шапефактори</span><span class="sxs-lookup"><span data-stu-id="23ad0-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="23ad0-467">Следующий создаваемый скрипт является классом *шапефактори* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="23ad0-468">Роль этого класса заключается в том, чтобы создать новую фигуру при запросе и удержать историю созданных фигур в *списке журнала фигур*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="23ad0-469">Каждый раз при создании фигуры *список журнала фигур* обновляется в классе *AzureService* , а затем сохраняется в *хранилище Azure*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="23ad0-470">При запуске приложения, если сохраненный файл находится в *хранилище Azure*, *список журнала фигур* извлекается и воспроизводится с помощью объекта **3D Text** , который указывает, является ли созданная фигура из хранилища или новой.</span><span class="sxs-lookup"><span data-stu-id="23ad0-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="23ad0-471">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="23ad0-471">To create this class:</span></span>

1.  <span data-ttu-id="23ad0-472">Перейдите к созданной ранее папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="23ad0-473">Щелкните правой кнопкой мыши внутри папки, **Создайте**  **C# скрипт** > .</span><span class="sxs-lookup"><span data-stu-id="23ad0-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="23ad0-474">Вызовите скрипт *шапефактори*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="23ad0-475">Дважды щелкните новый скрипт *шапефактори* , чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="23ad0-476">Убедитесь, что класс *шапефактори* содержит следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="23ad0-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="23ad0-477">Добавьте указанные ниже переменные в класс *шапефактори* и замените функции *Start ()* и *спящие ()* на указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="23ad0-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="23ad0-478">Метод *креатешапе ()* создает примитивные фигуры на основе указанного *целочисленного* параметра.</span><span class="sxs-lookup"><span data-stu-id="23ad0-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="23ad0-479">Логический параметр используется для указания, является ли создаваемая в данный момент фигура из хранилища или новой.</span><span class="sxs-lookup"><span data-stu-id="23ad0-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="23ad0-480">Поместите следующий код в класс *шапефактори* под предыдущими методами:</span><span class="sxs-lookup"><span data-stu-id="23ad0-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="23ad0-481">Не забудьте сохранить изменения в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="23ad0-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="23ad0-482">В редакторе Unity щелкните и перетащите класс *шапефактори* из папки **сценарии** в объект **Main** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="23ad0-483">Выбрав основную камеру, вы увидите, что в компоненте скрипта *шапефактори* отсутствует ссылка на *точку порождения* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="23ad0-484">Чтобы устранить эту проблему, перетащите объект **шапеспавнпоинт** с *панели Иерархия* в целевой объект ссылки на **точку порождения** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![задать целевую объект ссылки на фабрику фигур](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="23ad0-486">Глава 9. Создание класса «взгляд»</span><span class="sxs-lookup"><span data-stu-id="23ad0-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="23ad0-487">Последний скрипт, который необходимо создать, является классом « *взгляд* ».</span><span class="sxs-lookup"><span data-stu-id="23ad0-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="23ad0-488">Этот класс отвечает за создание **райкаст** , который будет проецирован вперед с основной камеры для определения объекта, на котором пользователь смотрит.</span><span class="sxs-lookup"><span data-stu-id="23ad0-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="23ad0-489">В этом случае Райкаст потребуется выяснить, просматривает ли пользователь объект **газебуттон** в сцене и инициирует поведение.</span><span class="sxs-lookup"><span data-stu-id="23ad0-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="23ad0-490">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="23ad0-490">To create this Class:</span></span>

1.  <span data-ttu-id="23ad0-491">Перейдите к созданной ранее папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="23ad0-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="23ad0-492">Щелкните правой кнопкой мыши на панели проект, **Создайте**  **C# скрипт** > .</span><span class="sxs-lookup"><span data-stu-id="23ad0-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="23ad0-493">Вызовите скрипт *взгляд*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="23ad0-494">Дважды щелкните новый скрипт " *Взгляните* ", чтобы открыть его в *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="23ad0-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="23ad0-495">Убедитесь, что в начале скрипта включено следующее пространство имен:</span><span class="sxs-lookup"><span data-stu-id="23ad0-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="23ad0-496">Затем добавьте следующие переменные в класс *Взгляните* :</span><span class="sxs-lookup"><span data-stu-id="23ad0-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="23ad0-497">Некоторые из этих переменных могут быть изменены в *редакторе*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="23ad0-498">Теперь необходимо добавить код для методов *спящего режима ()* и *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="23ad0-499">Добавьте следующий код, который создаст объект курсора при запуске, а также метод *Update ()* , который будет выполнять метод райкаст вместе с переключением логического газинаблед.</span><span class="sxs-lookup"><span data-stu-id="23ad0-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="23ad0-500">Затем добавьте метод *упдатерайкаст ()* , который выполнит проецирование райкаст и определит цель попадания.</span><span class="sxs-lookup"><span data-stu-id="23ad0-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="23ad0-501">Наконец, добавьте метод *ресетфокуседобжект ()* , который будет переключать текущий цвет объектов газебуттон, указывая, создает ли он новую фигуру.</span><span class="sxs-lookup"><span data-stu-id="23ad0-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="23ad0-502">Сохраните изменения в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="23ad0-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="23ad0-503">Щелкните и *Перетащите класс «указатель» из* папки «скрипты» в основной объект **Camera** на *панели «Иерархия»* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="23ad0-504">Глава 10. Завершение работы с классом Азуресервицес</span><span class="sxs-lookup"><span data-stu-id="23ad0-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="23ad0-505">После выполнения других сценариев теперь можно *завершить* класс *азуресервицес* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="23ad0-506">Это достигается с помощью следующих средств:</span><span class="sxs-lookup"><span data-stu-id="23ad0-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="23ad0-507">Добавление нового метода с именем *креатеклаудидентитясинк ()* для настройки переменных проверки подлинности, необходимых для взаимодействия с Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="23ad0-508">Этот метод также проверяет наличие ранее сохраненного файла, содержащего список фигур.</span><span class="sxs-lookup"><span data-stu-id="23ad0-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="23ad0-509">**Если файл найден**, он отключает пользовательский *взгляд*и активирует создание фигур в соответствии с шаблоном фигур, сохраненным в **файле хранилища Azure**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="23ad0-510">Пользователь может видеть это, так как в **сетке текста** будет отображаться "Storage" или "New" в зависимости от источника фигур.</span><span class="sxs-lookup"><span data-stu-id="23ad0-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="23ad0-511">**Если файл не найден**, будет включен *взгляд*, позволяющий пользователю создавать фигуры при просмотре объекта **газебуттон** в сцене.</span><span class="sxs-lookup"><span data-stu-id="23ad0-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="23ad0-512">Следующий фрагмент кода находится в методе *Start ()* ; где выполняется вызов метода *креатеклаудидентитясинк ()* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="23ad0-513">Вы можете скопировать свой текущий метод *Start ()* следующим образом:</span><span class="sxs-lookup"><span data-stu-id="23ad0-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="23ad0-514">Заполните код метода *каллазурефунктионфорнекстшапе ()* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="23ad0-515">Вы будете использовать ранее созданную *приложение-функция Azure* для запроса индекса фигуры.</span><span class="sxs-lookup"><span data-stu-id="23ad0-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="23ad0-516">После получения новой фигуры этот метод отправит форму в класс *шапефактори* , чтобы создать новую фигуру в сцене.</span><span class="sxs-lookup"><span data-stu-id="23ad0-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="23ad0-517">Используйте приведенный ниже код, чтобы завершить тело *каллазурефунктионфорнекстшапе ()* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="23ad0-518">Добавьте метод для создания строки путем сцепления целых чисел, хранящихся в списке журнала фигур, и сохранения их в *файле хранилища Azure*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="23ad0-519">Добавьте метод для получения текста, хранящегося в файле, расположенном в *файле хранилища Azure* , и *десериализация* его в список.</span><span class="sxs-lookup"><span data-stu-id="23ad0-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="23ad0-520">После завершения этого процесса метод повторно включает взгляд, чтобы пользователь мог добавить дополнительные фигуры в сцену.</span><span class="sxs-lookup"><span data-stu-id="23ad0-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="23ad0-521">Сохраните изменения в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="23ad0-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="23ad0-522">Глава 11. Создание решения UWP</span><span class="sxs-lookup"><span data-stu-id="23ad0-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="23ad0-523">Чтобы начать процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="23ad0-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="23ad0-524">Выберите **файл** > **параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-524">Go to **File** > **Build Settings**.</span></span>

    ![сборка приложения](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="23ad0-526">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-526">Click **Build**.</span></span> <span data-ttu-id="23ad0-527">Unity запустит окно *проводника* , в котором необходимо создать, а затем выбрать папку для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="23ad0-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="23ad0-528">Создайте эту папку сейчас и назовите ее *app*Name.</span><span class="sxs-lookup"><span data-stu-id="23ad0-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="23ad0-529">Затем выберите папку *приложения* и нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="23ad0-530">Unity начнет сборку проекта в папку *приложения* .</span><span class="sxs-lookup"><span data-stu-id="23ad0-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="23ad0-531">После того как Unity завершит сборку (может занять некоторое время), он откроет окно *проводника* в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).</span><span class="sxs-lookup"><span data-stu-id="23ad0-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="23ad0-532">Глава 12. Развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="23ad0-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="23ad0-533">Чтобы развернуть приложение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="23ad0-533">To deploy your application:</span></span>

1.  <span data-ttu-id="23ad0-534">Перейдите к папке *приложения* , созданной в [последней главе](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="23ad0-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="23ad0-535">Вы увидите файл с именем приложения с расширением SLN, который следует дважды щелкнуть, чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="23ad0-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="23ad0-536">На **платформе решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="23ad0-537">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="23ad0-538">Для Microsoft HoloLens может быть проще установить этот параметр на *Удаленный компьютер*, чтобы вы не были подключены к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="23ad0-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="23ad0-539">Однако необходимо также выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="23ad0-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="23ad0-540">Определите **IP-адрес** HoloLens, который можно найти в **параметрах** > **сети & интернет** > **Wi-Fi** > **Дополнительные параметры**. IPv4 — это адрес, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="23ad0-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="23ad0-541">Убедитесь, **что включен** **режим разработчика** ; находится в **параметрах** > **Update & > безопасности** **для разработчиков**.</span><span class="sxs-lookup"><span data-stu-id="23ad0-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![развертывание решения](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="23ad0-543">Перейдите в меню " **Сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютере.</span><span class="sxs-lookup"><span data-stu-id="23ad0-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="23ad0-544">Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску и тестированию.</span><span class="sxs-lookup"><span data-stu-id="23ad0-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="23ad0-545">Готовые функции Azure и приложение для хранения данных</span><span class="sxs-lookup"><span data-stu-id="23ad0-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="23ad0-546">Поздравляем, вы создали приложение смешанной реальности, которое использует функции Azure и службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="23ad0-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="23ad0-547">Приложение сможет рисовать на сохраненных данных и предоставить действие на основе этих данных.</span><span class="sxs-lookup"><span data-stu-id="23ad0-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![окончательный конец продукта](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="23ad0-549">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="23ad0-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="23ad0-550">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="23ad0-550">Exercise 1</span></span>

<span data-ttu-id="23ad0-551">Создайте вторую точку порождения и запишите, из какой порожденной точки был создан объект.</span><span class="sxs-lookup"><span data-stu-id="23ad0-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="23ad0-552">При загрузке файла данных воспроизводите созданные фигуры из первоначально созданного расположения.</span><span class="sxs-lookup"><span data-stu-id="23ad0-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="23ad0-553">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="23ad0-553">Exercise 2</span></span>

<span data-ttu-id="23ad0-554">Создайте способ перезапуска приложения, вместо того чтобы повторно открывать его каждый раз.</span><span class="sxs-lookup"><span data-stu-id="23ad0-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="23ad0-555">**Загрузка сцен** — хорошее место для начала.</span><span class="sxs-lookup"><span data-stu-id="23ad0-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="23ad0-556">После этого создайте способ очистки сохраненного списка в *службе хранилища Azure*, чтобы его можно было легко сбросить из приложения.</span><span class="sxs-lookup"><span data-stu-id="23ad0-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
