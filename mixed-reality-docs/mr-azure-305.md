---
title: Г-н и 305 Azure — функции и хранилища
description: Выполните этот курс, чтобы узнать, как реализовать приложение смешанной реальности хранилища Azure и функций.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, функции, хранилища, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598299"
---
>[!NOTE]
><span data-ttu-id="9fdcf-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9fdcf-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9fdcf-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9fdcf-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9fdcf-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9fdcf-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="9fdcf-110">Г-н и Azure 305: Функции и хранилища</span><span class="sxs-lookup"><span data-stu-id="9fdcf-110">MR and Azure 305: Functions and storage</span></span>

![конечный продукт-запуск](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="9fdcf-112">В рамках этого курса вы узнаете, как создать и использовать функции Azure и хранить данные с ресурса службы хранилища Azure, в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="9fdcf-113">*Функции Azure* является служба, которая позволяет разработчикам запускать небольшие фрагменты кода, «», в функциях Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="9fdcf-114">Это позволяет делегировать работу в облаке, а не локального приложения, который может иметь множество преимуществ.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="9fdcf-115">*Функции Azure* поддерживает несколько языков разработки, в том числе C\#, F\#, Node.js, Java и PHP.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="9fdcf-116">Дополнительные сведения см. в статье ["функции Azure" статьи](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="9fdcf-117">*Служба хранилища Azure* — это облачная служба Microsoft, которая позволяет разработчикам хранить данные с страхования, что он будет высокодоступных, безопасной, устойчивой, масштабируемой и избыточных.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="9fdcf-118">Это означает, что Майкрософт будет обрабатывать все техническое обслуживание и критические проблемы для вас.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="9fdcf-119">Дополнительные сведения см. в статье [статье хранилища Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="9fdcf-120">После выполнения этого курса, у вас будет приложение иммерсивных гарнитуры смешанной реальности, которое сможет выполнить следующие:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="9fdcf-121">Разрешает пользователю помощи вокруг сцены.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="9fdcf-122">Активируйте, запускающая объектов, когда пользователь gazes в трехмерной «button».</span><span class="sxs-lookup"><span data-stu-id="9fdcf-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="9fdcf-123">Порожденный объекты выбирается с помощью функции Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="9fdcf-124">Так как каждый объект порождается, приложение сохранит тип объекта в *файлов Azure*, который находится в *хранилища Azure*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="9fdcf-125">После загрузки второй раз, *файлов Azure* данные будут получены и использован для воспроизведения порождающих действия из предыдущего экземпляра приложения.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="9fdcf-126">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="9fdcf-127">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="9fdcf-128">Это задания для использования знания, полученные в результате этот курс поможет вам улучшить ваши приложения для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="9fdcf-129">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="9fdcf-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9fdcf-130">Курс</span><span class="sxs-lookup"><span data-stu-id="9fdcf-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9fdcf-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9fdcf-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9fdcf-132"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="9fdcf-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9fdcf-133">Г-н и Azure 305: Функции и хранилища</span><span class="sxs-lookup"><span data-stu-id="9fdcf-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="9fdcf-134">✔️</span><span class="sxs-lookup"><span data-stu-id="9fdcf-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9fdcf-135">✔️</span><span class="sxs-lookup"><span data-stu-id="9fdcf-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="9fdcf-136">Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="9fdcf-137">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9fdcf-138">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="9fdcf-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="9fdcf-139">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="9fdcf-140">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="9fdcf-141">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="9fdcf-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="9fdcf-142">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="9fdcf-143">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="9fdcf-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="9fdcf-144">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="9fdcf-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="9fdcf-145">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="9fdcf-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="9fdcf-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="9fdcf-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="9fdcf-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9fdcf-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="9fdcf-148">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="9fdcf-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="9fdcf-149">Подписка на учетную запись Azure для создания ресурсов Azure</span><span class="sxs-lookup"><span data-stu-id="9fdcf-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="9fdcf-150">Доступ к Интернету для Azure установки и извлечения данных</span><span class="sxs-lookup"><span data-stu-id="9fdcf-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="9fdcf-151">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="9fdcf-151">Before you start</span></span>

<span data-ttu-id="9fdcf-152">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="9fdcf-153">Глава 1 - портала Azure</span><span class="sxs-lookup"><span data-stu-id="9fdcf-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="9fdcf-154">Чтобы использовать **службы хранилища Azure**, вам потребуется создать и настроить **учетной записи хранения** на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="9fdcf-155">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="9fdcf-156">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="9fdcf-157">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="9fdcf-158">После входа в систему щелкните **New** в левом верхнем углу, а поиск *учетной записи хранения*и нажмите кнопку **ввод**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![Поиск хранилища Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="9fdcf-160">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="9fdcf-161">Новая страница будет предоставить описание *учетной записи хранения Azure* службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="9fdcf-162">В нижней левой части этого запроса, выберите **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Создание службы](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="9fdcf-164">Когда вы перейдете на **создать**:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="9fdcf-165">Вставить *имя* для вашей учетной записи, помните, это поле принимает только цифры и строчные буквы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="9fdcf-166">Для *модели развертывания*выберите **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="9fdcf-167">Для *тип учетной записи*выберите **хранилища (общего назначения версии 1)**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="9fdcf-168">Определить *расположение* для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="9fdcf-169">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="9fdcf-170">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="9fdcf-171">Для *репликации* выберите **Read-access геоизбыточного хранилища (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="9fdcf-172">Для *производительности*выберите **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="9fdcf-173">Оставьте *требуется безопасное перемещение* как **отключено**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="9fdcf-174">Выберите *подписки*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="9fdcf-175">Выберите *группы ресурсов* или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="9fdcf-176">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="9fdcf-177">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="9fdcf-178">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="9fdcf-179">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="9fdcf-180">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-180">Select **Create**.</span></span>

        ![сведения о службе ввода](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="9fdcf-182">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="9fdcf-183">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![новое уведомление на портале azure](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="9fdcf-185">Щелкните уведомлений для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-185">Click on the notifications to explore your new Service instance.</span></span>

    ![Перейти к ресурсу](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="9fdcf-187">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="9fdcf-188">Вы перейдете на новый *учетной записи хранения* экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![Ключи доступа](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="9fdcf-190">Нажмите кнопку *ключи доступа*, чтобы показать конечные точки для этой облачной службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="9fdcf-191">Используйте *Блокнот* или аналогичную Скопируйте один из ключей для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="9fdcf-192">Кроме того, *строку подключения* значение, так как оно будет использоваться в *служб AzureServices* класс, который будет создан позже.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![Скопируйте строку подключения](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="9fdcf-194">Глава 2 - Настройка функции Azure</span><span class="sxs-lookup"><span data-stu-id="9fdcf-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="9fdcf-195">Теперь создадим **Azure** **функция** в службе Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="9fdcf-196">Можно использовать **функции Azure** делать практически все, что это делается с помощью классической функции в коде, разница, что эта функция может осуществляться любым приложением, имеет учетные данные для доступа к учетной записи Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="9fdcf-197">Чтобы создать функцию Azure:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="9fdcf-198">Из вашего *портал Azure*, щелкните **New** в левом верхнем углу, а поиск *приложения-функции*и нажмите кнопку **ввод**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Создание приложения-функции](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="9fdcf-200">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="9fdcf-201">Новая страница будет предоставить описание *приложение-функцию Azure* службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="9fdcf-202">В нижней левой части этого запроса, выберите **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![сведения о приложении функции](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="9fdcf-204">Когда вы перейдете на **создать**:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="9fdcf-205">Укажите *имя_приложения*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-205">Provide an *App name*.</span></span> <span data-ttu-id="9fdcf-206">Только буквы и цифры могут быть использованы (допускается либо верхний или нижний регистр).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="9fdcf-207">Выберите предпочтительный *подписки*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="9fdcf-208">Выберите *группы ресурсов* или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="9fdcf-209">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="9fdcf-210">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="9fdcf-211">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="9fdcf-212">Для этого упражнения выберите *Windows* присвоили **ОС**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="9fdcf-213">Выберите *план потребления* для **план размещения**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="9fdcf-214">Определить *расположение* для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="9fdcf-215">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="9fdcf-216">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="9fdcf-217">Для обеспечения оптимальной производительности выберите тот же регион, что учетная запись хранения.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="9fdcf-218">Для *хранения*выберите **использовать существующий**, и затем с помощью раскрывающегося списка, найти ранее созданного хранилища.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="9fdcf-219">Оставьте *Application Insights* отключено для этого упражнения.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-219">Leave *Application Insights* off for this exercise.</span></span>

        ![сведения о приложении входная функция](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="9fdcf-221">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="9fdcf-222">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="9fdcf-223">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![новые уведомления с портала azure](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="9fdcf-225">Щелкните уведомлений для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![Перейдите к ресурсу приложения-функции](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="9fdcf-227">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="9fdcf-228">Вы перейдете на новый *приложения-функции* экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="9fdcf-229">На *приложения-функции* панели мониторинга, наведите указатель мыши *функции*, определенным в пределах панели в левой части и нажмите кнопку **+ (плюс)** символов.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![Создание функции](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="9fdcf-231">На следующей странице убедитесь **веб-перехватчик + API** выбран и для *выберите язык,* выберите **CSharp**, поскольку оно будет использоваться язык, используемый в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="9fdcf-232">Наконец, щелкните **создайте эту функцию** кнопки.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-232">Lastly, click the **Create this function** button.</span></span>

    ![Выберите web ловушка csharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="9fdcf-234">Должна открыться в код страницы (run.csx), если нет, щелкните только что созданной функции в списке функций на панели слева.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![Откройте новую функцию](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="9fdcf-236">Скопируйте следующий код в функцию.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-236">Copy the following code into your function.</span></span> <span data-ttu-id="9fdcf-237">Эта функция просто возвращает случайное целое число от 0 до 2 при вызове.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="9fdcf-238">Не беспокоиться о существующий код, вы можете вставить его поверх.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

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

13. <span data-ttu-id="9fdcf-239">Выберите **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-239">Select **Save**.</span></span>

14. <span data-ttu-id="9fdcf-240">Результат должен выглядеть как на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="9fdcf-241">Щелкните **получить URL-адрес функции** и запишите *конечной точки* отображается.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="9fdcf-242">Необходимо вставить его в *служб AzureServices* класс, который вы создадите далее в этом курсе.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![Получение конечной точки функции](images/AzureLabs-Lab5-16.png)

    ![Получение конечной точки функции](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="9fdcf-245">Глава 3 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="9fdcf-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="9fdcf-246">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="9fdcf-247">Настроить и проверить ваш иммерсивных гарнитуры смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="9fdcf-248">Вы будете **не** требуются контроллеры движения курс с демороликами.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="9fdcf-249">Если вам требуется поддерживает настройку иммерсивных гарнитура, [посетите смешанной реальности, Настройка статье](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="9fdcf-250">Откройте Unity и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-250">Open Unity and click **New**.</span></span>

    ![Создание нового проекта unity](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="9fdcf-252">Теперь необходимо будет указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="9fdcf-253">Вставить **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="9fdcf-254">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="9fdcf-255">Задайте *расположение* в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="9fdcf-256">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-256">Then, click **Create project**.</span></span>

    ![Назовите новый проект unity](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="9fdcf-258">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="9fdcf-259">Перейдите к **изменить* > *предпочтения** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-259">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="9fdcf-260">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="9fdcf-261">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-261">Close the **Preferences** window.</span></span>

    ![набор visual studio в качестве редактора скриптов](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="9fdcf-263">Перейдите к **файл > Параметры сборки** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-263">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![переключить платформу для универсальной платформы Windows](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="9fdcf-265">Перейдите к **файл > Параметры сборки** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-265">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="9fdcf-266">**Целевое устройство** присваивается **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="9fdcf-267">Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="9fdcf-268">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="9fdcf-269">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="9fdcf-270">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="9fdcf-271">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="9fdcf-272">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="9fdcf-273">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="9fdcf-274">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-274">A save window will appear.</span></span>

            ![Добавление открытых сцен](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="9fdcf-276">Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создайте папку сцены](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="9fdcf-278">Откройте только что созданный **сцены** папку, а затем в **имя файла:** текстовое поле, тип **FunctionsScene**, нажмите клавишу **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![Сохраните сцену функции](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="9fdcf-280">Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![Сохраните сцену функции](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="9fdcf-282">В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![Параметры проигрывателя в инспекторе](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="9fdcf-284">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="9fdcf-285">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="9fdcf-286">**Сценарии версии среды выполнения** должно быть **экспериментальный** (.NET 4.6 эквивалент), что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="9fdcf-287">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="9fdcf-288">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="9fdcf-289">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="9fdcf-290">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-290">**InternetClient**</span></span>

            ![набор возможностей](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="9fdcf-292">Далее панели в **XR параметры** (под **параметров публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **Windows Mixed Reality Пакет SDK** добавляется.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![задать параметры XR](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="9fdcf-294">Вернитесь в *параметры построения* *Unity C# проекты* больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![проекты c# делений](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="9fdcf-296">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="9fdcf-297">Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="9fdcf-298">Глава 4 – Настройка главной камеры</span><span class="sxs-lookup"><span data-stu-id="9fdcf-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fdcf-299">Если вы хотите пропустить *Настройка Unity* компоненты этого курса и по-прежнему непосредственно в код, вы можете [загрузить этот .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)и импортировать его в проект в качестве [Custom Пакет](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="9fdcf-300">Оно также будет содержать библиотеки DLL из следующей главе.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="9fdcf-301">После импорта, по-прежнему из [Глава 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="9fdcf-302">В *панели иерархии*, вы найдете объект с именем **Main Camera**, этот объект представляет вашей точки зрения «head» приложения «в».</span><span class="sxs-lookup"><span data-stu-id="9fdcf-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="9fdcf-303">С помощью панели мониторинга Unity перед глазами, выберите **GameObject камеры Main**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="9fdcf-304">Можно будет заметить, что *панели Инспектора* (обычно находится в правой части панели мониторинга) будут отображаться различные компоненты, *GameObject*, с помощью *преобразования* в верхней, за которым следует *камеры*и некоторые другие компоненты.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="9fdcf-305">Необходимо будет сбросить преобразование объекта Main Camera, поэтому расположено верно.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="9fdcf-306">Чтобы сделать это, выберите **шестеренки** значок рядом с камеры *преобразования* компонент и выберите **сбросить**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![Сброс преобразования](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="9fdcf-308">Затем обновите **преобразования** компонента, чтобы выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="9fdcf-309">ПРЕОБРАЗОВАНИЕ - ПОЗИЦИИ</span><span class="sxs-lookup"><span data-stu-id="9fdcf-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="9fdcf-310">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-310">**X**</span></span>   | <span data-ttu-id="9fdcf-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-311">**Y**</span></span>                     | <span data-ttu-id="9fdcf-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-312">**Z**</span></span> |
    | <span data-ttu-id="9fdcf-313">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-313">0</span></span>       | <span data-ttu-id="9fdcf-314">1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-314">1</span></span>                         | <span data-ttu-id="9fdcf-315">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-315">0</span></span>     |    

    |       | <span data-ttu-id="9fdcf-316">ПРЕОБРАЗОВАНИЕ - ПОВОРОТА</span><span class="sxs-lookup"><span data-stu-id="9fdcf-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="9fdcf-317">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-317">**X**</span></span> | <span data-ttu-id="9fdcf-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-318">**Y**</span></span>                | <span data-ttu-id="9fdcf-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-319">**Z**</span></span> |
    | <span data-ttu-id="9fdcf-320">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-320">0</span></span>     | <span data-ttu-id="9fdcf-321">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-321">0</span></span>                    | <span data-ttu-id="9fdcf-322">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-322">0</span></span>     |

    |       | <span data-ttu-id="9fdcf-323">ПРЕОБРАЗОВАНИЕ - МАСШТАБИРОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="9fdcf-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="9fdcf-324">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-324">**X**</span></span> | <span data-ttu-id="9fdcf-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-325">**Y**</span></span>             | <span data-ttu-id="9fdcf-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-326">**Z**</span></span> |
    | <span data-ttu-id="9fdcf-327">1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-327">1</span></span>     | <span data-ttu-id="9fdcf-328">1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-328">1</span></span>                 | <span data-ttu-id="9fdcf-329">1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-329">1</span></span>     |

    ![Преобразование набора камеры](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="9fdcf-331">Глава 5 - Настройка сцене Unity</span><span class="sxs-lookup"><span data-stu-id="9fdcf-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="9fdcf-332">Щелкните правой кнопкой мыши пустую часть области *панели иерархии*в разделе **трехмерный объект**, добавьте **плоскости**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![создать новый плоскость](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="9fdcf-334">С помощью **плоскости** объекта выбран, измените следующие параметры в *панели Инспектора*:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="9fdcf-335">ПРЕОБРАЗОВАНИЕ - ПОЗИЦИИ</span><span class="sxs-lookup"><span data-stu-id="9fdcf-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="9fdcf-336">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-336">**X**</span></span> | <span data-ttu-id="9fdcf-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-337">**Y**</span></span>                | <span data-ttu-id="9fdcf-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-338">**Z**</span></span> |
    | <span data-ttu-id="9fdcf-339">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-339">0</span></span>     | <span data-ttu-id="9fdcf-340">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-340">0</span></span>                    | <span data-ttu-id="9fdcf-341">4</span><span class="sxs-lookup"><span data-stu-id="9fdcf-341">4</span></span>     |

    |       | <span data-ttu-id="9fdcf-342">ПРЕОБРАЗОВАНИЕ - МАСШТАБИРОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="9fdcf-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="9fdcf-343">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-343">**X**</span></span> | <span data-ttu-id="9fdcf-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-344">**Y**</span></span>             | <span data-ttu-id="9fdcf-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-345">**Z**</span></span> |
    | <span data-ttu-id="9fdcf-346">10</span><span class="sxs-lookup"><span data-stu-id="9fdcf-346">10</span></span>    | <span data-ttu-id="9fdcf-347">1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-347">1</span></span>                 | <span data-ttu-id="9fdcf-348">10</span><span class="sxs-lookup"><span data-stu-id="9fdcf-348">10</span></span>    |

    ![задать положение плоскости и масштабирования](images/AzureLabs-Lab5-32.png)

    ![представление сцену плоскость](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="9fdcf-351">Щелкните правой кнопкой мыши пустую часть области *панели иерархии*в разделе **трехмерный объект**, добавьте **куба**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="9fdcf-352">Переименуйте куб, чтобы **GazeButton** (куба, выбранного, нажмите клавишу «F2»).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="9fdcf-353">Измените следующие параметры в *панели Инспектора*:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="9fdcf-354">ПРЕОБРАЗОВАНИЕ - ПОЗИЦИИ</span><span class="sxs-lookup"><span data-stu-id="9fdcf-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="9fdcf-355">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-355">**X**</span></span> | <span data-ttu-id="9fdcf-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-356">**Y**</span></span>                | <span data-ttu-id="9fdcf-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-357">**Z**</span></span> |
        | <span data-ttu-id="9fdcf-358">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-358">0</span></span>     | <span data-ttu-id="9fdcf-359">3</span><span class="sxs-lookup"><span data-stu-id="9fdcf-359">3</span></span>                    | <span data-ttu-id="9fdcf-360">5</span><span class="sxs-lookup"><span data-stu-id="9fdcf-360">5</span></span>     |


        ![набор взглядом кнопки преобразования](images/AzureLabs-Lab5-34.png)

        ![При помощи кнопки представлении сцены](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="9fdcf-363">Щелкните **тега** кнопку раскрывающегося списка и щелкните **добавить тег** открыть *теги & область слои*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Добавление нового тега](images/AzureLabs-Lab5-36.png)

        ![Выберите плюс](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="9fdcf-366">Выберите **+ (плюс)** кнопки, а затем в *новое имя тега* введите **GazeButton**и нажмите клавишу **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![имя нового тега](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="9fdcf-368">Щелкните **GazeButton** объекта в *панели иерархии*и в *панели Инспектора*, назначьте только что созданный **GazeButton** тега.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![назначить взглядом кнопку новый тег](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="9fdcf-370">Щелкните правой кнопкой мыши **GazeButton** объекта, в *панели иерархии*и добавьте **пустой объект GameObject** (который будет добавлен в качестве *дочерних* объект).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="9fdcf-371">Выберите новый объект и присвойте ему **ShapeSpawnPoint**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="9fdcf-372">Измените следующие параметры в *панели Инспектора*:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="9fdcf-373">ПРЕОБРАЗОВАНИЕ - ПОЗИЦИИ</span><span class="sxs-lookup"><span data-stu-id="9fdcf-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="9fdcf-374">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-374">**X**</span></span> |<span data-ttu-id="9fdcf-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-375">**Y**</span></span>                 | <span data-ttu-id="9fdcf-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-376">**Z**</span></span> |
        | <span data-ttu-id="9fdcf-377">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-377">0</span></span>     | <span data-ttu-id="9fdcf-378">-1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-378">-1</span></span>                   | <span data-ttu-id="9fdcf-379">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-379">0</span></span>     |

        ![Преобразование точки spawn фигуры обновления](images/AzureLabs-Lab5-40.png)

        ![представлении сцены точки spawn фигуры](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="9fdcf-382">Затем вы создадите **трехмерного текста** объект, отзыв о состоянии службы Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="9fdcf-383">Щелкните правой кнопкой мыши **GazeButton** в иерархии панели снова и добавьте **трехмерный объект > трехмерного текста** объекта в виде *дочерних*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object > 3D Text** object as a *child*.</span></span>

    ![Создайте новый объект трехмерного текста](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="9fdcf-385">Переименуйте **трехмерного текста** объект **AzureStatusText**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="9fdcf-386">Изменение **AzureStatusText** объекта преобразования следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="9fdcf-387">ПРЕОБРАЗОВАНИЕ - ПОЗИЦИИ</span><span class="sxs-lookup"><span data-stu-id="9fdcf-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="9fdcf-388">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-388">**X**</span></span> | <span data-ttu-id="9fdcf-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-389">**Y**</span></span>                | <span data-ttu-id="9fdcf-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-390">**Z**</span></span> |
    | <span data-ttu-id="9fdcf-391">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-391">0</span></span>     | <span data-ttu-id="9fdcf-392">0</span><span class="sxs-lookup"><span data-stu-id="9fdcf-392">0</span></span>                    | <span data-ttu-id="9fdcf-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="9fdcf-393">-0.6</span></span>  |

    |       | <span data-ttu-id="9fdcf-394">ПРЕОБРАЗОВАНИЕ - МАСШТАБИРОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="9fdcf-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="9fdcf-395">**X**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-395">**X**</span></span> | <span data-ttu-id="9fdcf-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-396">**Y**</span></span>             | <span data-ttu-id="9fdcf-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="9fdcf-397">**Z**</span></span> |
    | <span data-ttu-id="9fdcf-398">0.1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-398">0.1</span></span>   | <span data-ttu-id="9fdcf-399">0.1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-399">0.1</span></span>               | <span data-ttu-id="9fdcf-400">0.1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="9fdcf-401">Не волнуйтесь, если он отображается в off centre, как это будет исправлено при ниже текст Mesh компонент обновляется.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="9fdcf-402">Изменение **Mesh текст** компонента в соответствии с ниже:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-402">Change the **Text Mesh** component to match the below:</span></span>

    ![Компонент сетки набора текста](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="9fdcf-404">Выбранный цвет здесь является Hex цветом: **000000FF**, однако вы можете выбрать собственные, просто убедитесь, он доступен для чтения.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="9fdcf-405">Структуры вашей иерархии панели теперь должна выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![текст mesh в представлении сцены](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="9fdcf-407">Сцена теперь должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-407">Your scene should now look like this:</span></span>

    ![текст mesh в представлении сцены](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="9fdcf-409">Глава 6 - Импорт хранилища Azure для Unity</span><span class="sxs-lookup"><span data-stu-id="9fdcf-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="9fdcf-410">Вы будете использовать службу хранилища Azure для Unity (который сам использует пакет SDK для Azure .net).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="9fdcf-411">Дополнительные сведения см. в [хранилища Azure для Unity статьи](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="9fdcf-412">В Unity, который требует подключаемых модулей, чтобы повторно настроить после импорта в настоящее время имеется известная проблема.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="9fdcf-413">Эти шаги (4 – 7 в этом разделе), не будет обязательным после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="9fdcf-414">Чтобы импортировать пакет SDK в свой проект, убедитесь, что вы скачали последнюю версию [«.unitypackage» из GitHub](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="9fdcf-415">Затем сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-415">Then, do the following:</span></span>

1.  <span data-ttu-id="9fdcf-416">Добавить **.unitypackage** файла к Unity с помощью **ресурсы > Импорт пакета > пользовательского пакета** пункт меню.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-416">Add the **.unitypackage** file to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="9fdcf-417">В **Импорт пакета Unity** поле, отобразятся, вы сможете выбрать все данные \**подключаемый модуль* > \*хранилища\*\*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-417">In the **Import Unity Package** box that pops up, you can select everything under \**Plugin* > \*Storage\*\*.</span></span> <span data-ttu-id="9fdcf-418">Снимите флажок, все остальное, так как он не требуется для этого курса.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Импорт пакета](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="9fdcf-420">Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="9fdcf-421">Перейдите к *хранения* папке *подключаемые модули*, в представлении проекта и выберите следующие подключаемые модули *только*:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="9fdcf-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="9fdcf-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="9fdcf-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="9fdcf-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="9fdcf-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="9fdcf-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="9fdcf-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="9fdcf-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="9fdcf-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="9fdcf-426">System.Spatial</span></span>

        ![Снимите флажок для любой платформы](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="9fdcf-428">С помощью *этих конкретных подключаемых модулей* выбран, **снимите** *Any платформы* и **снимите флажок** *WSAPlayer* Нажмите кнопку **применить**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![Применение платформы библиотек DLL](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="9fdcf-430">Мы отмечаем эти определенного подключаемые модули можно использовать только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="9fdcf-431">Это, так как существуют различные версии одной подключаемые модули в папку WSA, которая будет использоваться после проект будет экспортирован из Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="9fdcf-432">В *хранения* папку подключаемый модуль, выберите только:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="9fdcf-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="9fdcf-433">Microsoft.Data.Services.Client</span></span>

        ![не обрабатывать набор библиотек DLL](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="9fdcf-435">Проверьте **процесса не** поле в разделе *параметры платформы* и нажмите кнопку **применить**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![применить без обработки](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="9fdcf-437">Мы отмечаем этот подключаемый модуль «Не процесс» из-за сложности обработки этот подключаемый модуль средство исправления сборки Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="9fdcf-438">Подключаемый модуль по-прежнему будет работать, несмотря на то, что он не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="9fdcf-439">Глава 7 - создание класса служб AzureServices</span><span class="sxs-lookup"><span data-stu-id="9fdcf-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="9fdcf-440">Вы собираетесь создать первый класс — *служб AzureServices* класса.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="9fdcf-441">*Служб AzureServices* класс будет отвечать за:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="9fdcf-442">Хранение учетных данных учетной записи Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="9fdcf-443">Вызов Azure приложения-функции.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="9fdcf-444">Отправки и скачивания файла данных в облачном хранилище Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="9fdcf-445">Для создания данного класса:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-445">To create this Class:</span></span>

1.  <span data-ttu-id="9fdcf-446">Щелкните правой кнопкой мыши в *активов* папка «проект», **Создать > Папка**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="9fdcf-447">Назовите папку **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-447">Name the folder **Scripts**.</span></span>

    ![Создание новой папки](images/AzureLabs-Lab5-50.png)

    ![вызов папку - сценарии](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="9fdcf-450">Дважды щелкните папку, только что создали, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="9fdcf-451">Щелкните правой кнопкой мыши внутри папки **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-451">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="9fdcf-452">Вызовите сценарий *служб AzureServices*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="9fdcf-453">Дважды щелкните новый *служб AzureServices* класса, чтобы открыть его с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="9fdcf-454">Добавьте следующие пространства имен в верхнюю часть *служб AzureServices*:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="9fdcf-455">Добавьте следующие поля инспектор внутри *служб AzureServices* класса:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

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

7.  <span data-ttu-id="9fdcf-456">Затем добавьте следующие переменные-члены внутри *служб AzureServices* класса:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-456">Then add the following member variables inside the *AzureServices* class:</span></span>

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
    > <span data-ttu-id="9fdcf-457">Убедитесь, что вы замените *конечной точки* и *строку подключения* значения значениями из хранилища Azure, найти на портале Azure</span><span class="sxs-lookup"><span data-stu-id="9fdcf-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="9fdcf-458">Код для *Awake()* и *Start()* методы теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="9fdcf-459">Эти методы будут вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-459">These methods will be called when the class initializes:</span></span>

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
    > <span data-ttu-id="9fdcf-460">Мы заполнит код *CallAzureFunctionForNextShape()* в [будущих глава](#chapter-10---completing-the-AzureServices-class).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-AzureServices-class).</span></span>

9.  <span data-ttu-id="9fdcf-461">Удалить *Update()* метод, так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="9fdcf-462">Сохранить изменения в Visual Studio и затем вернитесь к Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="9fdcf-463">Щелкните и перетащите *служб AzureServices* класса из папки скриптов для объекта Main Camera в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="9fdcf-464">Выберите Main Camera, а затем взять **AzureStatusText** дочерний объект из под **GazeButton** объекта и поместите его в **AzureStatusText** цель ссылки в поле *инспектор*, чтобы указать ссылку на *служб AzureServices* скрипта.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![assign azure status text reference target](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="9fdcf-466">Глава 8 - создать класс ShapeFactory</span><span class="sxs-lookup"><span data-stu-id="9fdcf-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="9fdcf-467">Далее сценарий для создания, *ShapeFactory* класса.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="9fdcf-468">Роли этого класса является создание новой фигуры, при запросе и сохранять в журнале фигур, созданных в *списка журнала фигуры*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="9fdcf-469">Каждый раз при создании фигуры *списка журнала фигуры* обновляется в *AzureService* класса, а затем сохраняются в вашей *хранилища Azure*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="9fdcf-470">При запуске приложения, если найден сохраненного файла в вашей *хранилища Azure*, *списка журнала фигуры* извлекается и воспроизводимой с **трехмерного текста** предоставления объекта является ли создаваемый фигуры из хранилища или новые.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="9fdcf-471">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-471">To create this class:</span></span>

1.  <span data-ttu-id="9fdcf-472">Перейдите к **сценариев** папку, созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="9fdcf-473">Щелкните правой кнопкой мыши внутри папки **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-473">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="9fdcf-474">Вызовите сценарий *ShapeFactory*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="9fdcf-475">Дважды щелкните новый *ShapeFactory* скрипт, чтобы открыть его с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="9fdcf-476">Убедитесь, *ShapeFactory* класс включает следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="9fdcf-477">Добавьте переменные, указанные ниже *ShapeFactory* класса и замените *Start()* и *Awake()* функции со значениями ниже:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

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

6.  <span data-ttu-id="9fdcf-478">*CreateShape() позволяет* метод создает простые фигуры, основываясь на предоставленном *целое число* параметра.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="9fdcf-479">Логический параметр, используемые для указания, является ли созданных фигуры из хранилище или новый.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="9fdcf-480">Поместите следующий код в ваш *ShapeFactory* класс ниже предыдущих методов:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

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

7.  <span data-ttu-id="9fdcf-481">Не забудьте сохранить изменения в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="9fdcf-482">Обратно в редакторе Unity, щелкните и перетащите *ShapeFactory* класса из **сценарии** папку **Main Camera** объекта в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="9fdcf-483">С Main Camera выбран можно заметить, *ShapeFactory* компонента скрипта отсутствует *Spawn точки* ссылки.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="9fdcf-484">Чтобы устранить ее, перетащите **ShapeSpawnPoint** объекта из *панели иерархии* для **Spawn точки** цель ссылки.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![цель ссылки фабрики набора фигуры](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="9fdcf-486">Глава 9 — создать класс взглядом</span><span class="sxs-lookup"><span data-stu-id="9fdcf-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="9fdcf-487">— Последний скрипт, чтобы создать *помощи* класса.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="9fdcf-488">Этот класс отвечает за создание **Raycast** , будет проецироваться вперед от Main Camera, для обнаружения какой объект, который просматривает пользователь.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="9fdcf-489">В этом случае Raycast будет необходимо определить, если пользователь просматривает **GazeButton** объект в сцене и активировать поведение.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="9fdcf-490">Для создания данного класса:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-490">To create this Class:</span></span>

1.  <span data-ttu-id="9fdcf-491">Перейдите к **сценариев** папку, созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="9fdcf-492">Щелкните правой кнопкой мыши в панели «проект» **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-492">Right-click in the Project Panel, **Create > C# Script**.</span></span> <span data-ttu-id="9fdcf-493">Вызовите сценарий *помощи*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="9fdcf-494">Дважды щелкните новый *помощи* скрипт, чтобы открыть его с *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="9fdcf-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="9fdcf-495">Убедитесь, что в верхней части скрипта включается следующее пространство имен:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="9fdcf-496">Затем добавьте следующие переменные внутри *помощи* класса:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-496">Then add the following variables inside the *Gaze* class:</span></span>

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
> <span data-ttu-id="9fdcf-497">Некоторые из этих переменных будут иметь возможность редактировать в *редактор*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="9fdcf-498">Код для *Awake()* и *Start()* методы теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="9fdcf-499">Добавьте следующий код, который создает объект курсора в начале, вместе с *Update()* метод, который будет выполнен метод Raycast, кроме того, где установлен GazeEnabled логическое значение:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

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

8. <span data-ttu-id="9fdcf-500">Далее добавьте *UpdateRaycast()* метод, который будет проект Raycast и обнаружить попаданий целевой объект.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

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

9. <span data-ttu-id="9fdcf-501">Наконец, добавьте *ResetFocusedObject()* метод, который будет составляться GazeButton объектов текущего цвета, указывающее, является ли он создает новую фигуру или нет.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

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

10.  <span data-ttu-id="9fdcf-502">Сохраните изменения в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="9fdcf-503">Щелкните и перетащите *помощи* класс из папки скриптов для **Main Camera** объекта в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="9fdcf-504">Глава 10 — завершение работы класса служб AzureServices</span><span class="sxs-lookup"><span data-stu-id="9fdcf-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="9fdcf-505">С помощью других сценариев на месте, он теперь имеется возможность *полный* *служб AzureServices* класса.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="9fdcf-506">Это будет осуществляться через:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="9fdcf-507">Добавление нового метода с именем *CreateCloudIdentityAsync()*, чтобы задать переменные проверки подлинности, необходимые для взаимодействия с Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="9fdcf-508">Этот метод также проверяет наличие ранее сохраненный файл, содержащий список фигуры.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="9fdcf-509">**Если файл найден**, она происходит отключение пользователя *помощи*и запустить создание фигуры, согласно шаблону фигур, в том случае, как хранящиеся в **файла хранилища Azure**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="9fdcf-510">Пользователь может видеть, как **Mesh текст** предоставит отображения «Хранилище» или «New», в зависимости от начала координат фигуры.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="9fdcf-511">**Если не найден файл**, это позволит *помощи*, позволяя пользователям для создания фигур, рассматривая **GazeButton** объект в сцене.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

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

2.  <span data-ttu-id="9fdcf-512">В следующем фрагменте кода является изнутри *Start()* метод; в случае, если будет выполнен вызов *CreateCloudIdentityAsync()* метод.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="9fdcf-513">Вы можете скопировать текущий *Start()* метод, с помощью ниже:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

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

3.  <span data-ttu-id="9fdcf-514">Введите код для метода *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="9fdcf-515">Вы будет использовать ранее созданный *приложение-функцию Azure* для запроса индекса фигуры.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="9fdcf-516">После его получения, этот метод будет отправлять в фигуру, чтобы *ShapeFactory* класс, чтобы создать новую фигуру в сцену.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="9fdcf-517">Используйте приведенный ниже код для завершения тело *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

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

4.  <span data-ttu-id="9fdcf-518">Добавьте метод для создания строки, объединяя целых чисел, хранимых в журнале фигуры и помещения их в вашей *хранилища файлов Azure*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

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

5.  <span data-ttu-id="9fdcf-519">Добавьте метод для извлечения текста, хранящегося в файле, расположенном в вашей *хранилища файлов Azure* и *десериализации* его в список.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="9fdcf-520">После завершения этого процесса, метод повторно включает взглядом, таким образом, пользователь может добавлять дополнительные фигуры в сцену.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

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

7.  <span data-ttu-id="9fdcf-521">Сохраните изменения в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="9fdcf-522">Глава 11 - выполнить сборку решения универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="9fdcf-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="9fdcf-523">Чтобы начать процесс построения:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="9fdcf-524">Перейдите к **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-524">Go to **File > Build Settings**.</span></span>

    ![Построение приложения](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="9fdcf-526">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-526">Click **Build**.</span></span> <span data-ttu-id="9fdcf-527">Unity приведет к запуску *проводнике* окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="9fdcf-528">Создайте эту папку и назовите его *приложения*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="9fdcf-529">Затем с помощью *приложения* папку, нажмите клавишу **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="9fdcf-530">Unity начнется построение проекта для *приложения* папки.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="9fdcf-531">Один раз Unity завершил построение (может занять некоторое время), он будет открыт *проводнике* окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="9fdcf-532">Глава 12 - развертывания приложения</span><span class="sxs-lookup"><span data-stu-id="9fdcf-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="9fdcf-533">Для развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-533">To deploy your application:</span></span>

1.  <span data-ttu-id="9fdcf-534">Перейдите к *приложения* папку, которая была создана в [последняя глава](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="9fdcf-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="9fdcf-535">Вы увидите файл с именем вашего приложения, с расширением «.sln», который следует дважды щелкнуть, таким образом, чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="9fdcf-536">В **платформа решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="9fdcf-537">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="9fdcf-538">Для Microsoft HoloLens, может быть проще устанавливать равным *удаленный компьютер*, таким образом, не связанном устройстве на компьютер.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="9fdcf-539">Однако необходимо будет выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="9fdcf-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="9fdcf-540">Знать **IP-адрес** из HoloLens, которую можно найти в *параметры > сеть и Интернет > Wi-Fi > Дополнительно*; IPv4 — это адрес, следует использовать.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-540">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="9fdcf-541">Убедитесь, **режим разработчика** — **на**; найдено в *параметры > обновление и безопасность > для разработчиков*.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-541">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Развертывание решения](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="9fdcf-543">Перейдите к **построения** меню и щелкните **развернуть решение** для загрузки неопубликованных приложений на компьютер.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="9fdcf-544">Приложения должны появиться в списке установленных приложений, все готово для запуска и протестировано!</span><span class="sxs-lookup"><span data-stu-id="9fdcf-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="9fdcf-545">По завершении функций Azure и приложение службы хранилища</span><span class="sxs-lookup"><span data-stu-id="9fdcf-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="9fdcf-546">Поздравляем, вы создали приложение смешанной реальности, которое использует службы "функции Azure" и службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="9fdcf-547">Приложения будут иметь возможность рисования на сохраненных данных и укажите действие на основе этих данных.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![конечный продукт-end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="9fdcf-549">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="9fdcf-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="9fdcf-550">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="9fdcf-550">Exercise 1</span></span>

<span data-ttu-id="9fdcf-551">Создание второй spawn, точки и записи, которая порождает точки, для которого был создан объект.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="9fdcf-552">Когда вы загружаете файл данных, воспроизведение фигуры порожденных из расположения, в которых они изначально были созданы.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="9fdcf-553">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="9fdcf-553">Exercise 2</span></span>

<span data-ttu-id="9fdcf-554">Создайте способ перезапустить приложение, вместо того чтобы повторно открыть его каждый раз.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="9fdcf-555">**Загрузка сцены** -подходящее место для запуска.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="9fdcf-556">После этого создайте очистки списка хранимых в *хранилища Azure*, так что можно легко восстановить ее из приложения.</span><span class="sxs-lookup"><span data-stu-id="9fdcf-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
