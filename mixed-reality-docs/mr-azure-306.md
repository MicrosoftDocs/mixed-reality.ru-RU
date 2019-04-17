---
title: Г-н и 306 Azure - потоковой передачи видео
description: Выполните этот курс, чтобы узнать, как реализовать приложение смешанной реальности служб мультимедиа Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, служб мультимедиа, потоковое видео, 360, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599486"
---
>[!NOTE]
><span data-ttu-id="93080-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="93080-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="93080-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="93080-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="93080-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="93080-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="93080-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="93080-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="93080-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="93080-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="93080-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="93080-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="93080-110">Г-н и Azure 306: Потоковое видео</span><span class="sxs-lookup"><span data-stu-id="93080-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="93080-111">![конечный продукт-запуск](images/AzureLabs-Lab6-00.png)
![конечный продукт-запуск](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="93080-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="93080-112">В этом курсе вы узнаете, как подключаться служб мультимедиа Azure с работой смешанной реальности VR Windows позволяют передавать всеохватывающее воспроизведение видео в иммерсивную.</span><span class="sxs-lookup"><span data-stu-id="93080-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="93080-113">**Службы мультимедиа Azure** представляют собой коллекцию служб, которая предоставляет службы потоковой передачи видео высокого качества для более широкой аудитории на современных наиболее популярных мобильных устройствах.</span><span class="sxs-lookup"><span data-stu-id="93080-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="93080-114">Дополнительные сведения см. в статье [страницы служб мультимедиа Azure](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="93080-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="93080-115">После выполнения этого курса, у вас будет приложении иммерсивных гарнитуры смешанной реальности, смогут осуществлять следующее:</span><span class="sxs-lookup"><span data-stu-id="93080-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="93080-116">Получить видео 360 градусов из **хранилища Azure**, до **Azure Media Service**.</span><span class="sxs-lookup"><span data-stu-id="93080-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="93080-117">Отображение видео извлеченных 360 градусов в сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="93080-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="93080-118">Перемещаться между двумя сценами, с помощью двух разных видео.</span><span class="sxs-lookup"><span data-stu-id="93080-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="93080-119">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="93080-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="93080-120">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="93080-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="93080-121">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="93080-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="93080-122">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="93080-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="93080-123">Курс</span><span class="sxs-lookup"><span data-stu-id="93080-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="93080-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="93080-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="93080-125"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="93080-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="93080-126">Г-н и Azure 306: Потоковое видео</span><span class="sxs-lookup"><span data-stu-id="93080-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="93080-127">✔️</span><span class="sxs-lookup"><span data-stu-id="93080-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="93080-128">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="93080-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="93080-129">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="93080-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="93080-130">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="93080-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="93080-131">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства статье](install-the-tools.md), хотя следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="93080-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="93080-132">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="93080-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="93080-133">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="93080-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="93080-134">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="93080-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="93080-135">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="93080-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="93080-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="93080-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="93080-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="93080-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="93080-138">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="93080-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="93080-139">Доступ к Интернету для Azure установки и извлечения данных</span><span class="sxs-lookup"><span data-stu-id="93080-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="93080-140">Два характеристиках видео в формате mp4 (можно найти некоторые видеоматериалы, бесплатные [на этой странице загрузки](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="93080-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="93080-141">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="93080-141">Before you start</span></span>

1.  <span data-ttu-id="93080-142">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="93080-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="93080-143">Настройка и проверка вашего смешанной реальности гарнитура Иммерсивных.</span><span class="sxs-lookup"><span data-stu-id="93080-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="93080-144">Вы будете **не** требуются контроллеры движения курс с демороликами.</span><span class="sxs-lookup"><span data-stu-id="93080-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="93080-145">Если вам нужна поддерживает настройку Иммерсивных гарнитура, нажмите кнопку [ссылку о том, как настроить Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="93080-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="93080-146">Глава 1 - на портале Azure: Создание учетной записи хранения Azure</span><span class="sxs-lookup"><span data-stu-id="93080-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="93080-147">Чтобы использовать **службы хранилища Azure**, вам потребуется создать и настроить **учетной записи хранения** на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="93080-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="93080-148">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="93080-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="93080-149">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="93080-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="93080-150">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="93080-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="93080-151">После входа в систему щелкните **учетные записи хранения** в меню слева.</span><span class="sxs-lookup"><span data-stu-id="93080-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="93080-153">На **учетные записи хранения** , щелкните на **добавить**.</span><span class="sxs-lookup"><span data-stu-id="93080-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="93080-155">В **учетная запись хранения** вкладке:</span><span class="sxs-lookup"><span data-stu-id="93080-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="93080-156">Вставить **имя** для вашей учетной записи, помните, это поле принимает только цифры и строчные буквы.</span><span class="sxs-lookup"><span data-stu-id="93080-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="93080-157">Для **модели развертывания,** выберите **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="93080-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="93080-158">Для **тип учетной записи**выберите **хранилища (общего назначения версии 1)**.</span><span class="sxs-lookup"><span data-stu-id="93080-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="93080-159">Для **производительности**выберите \**Standard *.**</span><span class="sxs-lookup"><span data-stu-id="93080-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="93080-160">Для **репликации** выберите **локально избыточное хранилище (LRS)**.</span><span class="sxs-lookup"><span data-stu-id="93080-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="93080-161">Оставьте **требуется безопасное перемещение** как **отключено**.</span><span class="sxs-lookup"><span data-stu-id="93080-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="93080-162">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="93080-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="93080-163">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="93080-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="93080-164">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="93080-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="93080-165">Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="93080-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="93080-166">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="93080-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="93080-167">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="93080-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="93080-168">Будет необходимо подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="93080-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="93080-170">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="93080-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="93080-171">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="93080-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="93080-173">На этом этапе вы не обязательно должны следовать ресурса — просто переход к следующей главе.</span><span class="sxs-lookup"><span data-stu-id="93080-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="93080-174">Глава 2 - на портале Azure: создание службы мультимедиа</span><span class="sxs-lookup"><span data-stu-id="93080-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="93080-175">Чтобы использовать службы мультимедиа Azure, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения (при котором владелец учетной записи должен иметь права администратора).</span><span class="sxs-lookup"><span data-stu-id="93080-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="93080-176">На портале Azure щелкните **создать ресурс** в левом верхнем углу, а поиск **службы мультимедиа** клавишу **ввод**.</span><span class="sxs-lookup"><span data-stu-id="93080-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="93080-177">Ресурс, который вы хотите в настоящее время имеет розовый значка. Выберите этот параметр, чтобы отобразить новую страницу.</span><span class="sxs-lookup"><span data-stu-id="93080-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="93080-179">Новая страница будет предоставить описание **службы мультимедиа**.</span><span class="sxs-lookup"><span data-stu-id="93080-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="93080-180">В нижней левой части этого запроса, нажмите кнопку **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="93080-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="93080-182">Когда вы перейдете на **создать** панели будет отображаться, когда необходимо предоставить некоторые сведения о новой службы мультимедиа:</span><span class="sxs-lookup"><span data-stu-id="93080-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="93080-183">Вставить нужный **имя учетной записи** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="93080-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="93080-184">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="93080-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="93080-185">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="93080-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="93080-186">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="93080-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="93080-187">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="93080-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="93080-188">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылка на сведения об управлении группами ресурсов Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="93080-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="93080-189">Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="93080-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="93080-190">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="93080-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="93080-191">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="93080-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="93080-192">Для **учетной записи хранения** щелкните **выберите...**  раздела, а затем щелкните **учетной записи хранения** созданный в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="93080-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="93080-193">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="93080-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="93080-194">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="93080-194">Click **Create**.</span></span>

        ![Портал Azure](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="93080-196">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="93080-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="93080-197">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="93080-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="93080-199">Щелкните уведомление, чтобы изучить ваш новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="93080-199">Click on the notification to explore your new Service instance.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="93080-201">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="93080-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="93080-202">На странице новой службы мультимедиа на панели слева щелкните **активы** ссылку, которая посвящена равном вниз.</span><span class="sxs-lookup"><span data-stu-id="93080-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="93080-203">На следующей странице в левом верхнем углу страницы, нажмите кнопку **отправить**.</span><span class="sxs-lookup"><span data-stu-id="93080-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="93080-205">Щелкните **папку** значок, чтобы просматривать файлы и выберите сначала 360 видео, которое вы хотите выполнять потоковую передачу.</span><span class="sxs-lookup"><span data-stu-id="93080-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="93080-206">Это можно выполнить [ссылку, чтобы загрузить пример видео](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="93080-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="93080-208">Длинные имена файлов может вызвать проблемы с помощью кодировщика: таким образом чтобы видео проблем нет, необходимо рассмотреть возможность сокращения длина имен видеофайл.</span><span class="sxs-lookup"><span data-stu-id="93080-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="93080-209">Индикатор станет зеленым, если видео завершил передачу.</span><span class="sxs-lookup"><span data-stu-id="93080-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="93080-211">Щелкните текст выше (**yourservicename - активы**) чтобы вернуться к **активы** страницы.</span><span class="sxs-lookup"><span data-stu-id="93080-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="93080-212">Обратите внимание, что видео был успешно загружен.</span><span class="sxs-lookup"><span data-stu-id="93080-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="93080-213">Щелкните ее.</span><span class="sxs-lookup"><span data-stu-id="93080-213">Click on it.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="93080-215">Вы будете перенаправлены на страницу будет показывать, подробные сведения о видео.</span><span class="sxs-lookup"><span data-stu-id="93080-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="93080-216">Чтобы иметь возможность использовать ваше видео, их нужно кодировать его, щелкнув **Encode** кнопку в верхней левой части страницы.</span><span class="sxs-lookup"><span data-stu-id="93080-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="93080-218">Новая панель появится справа, где можно задать параметры для файла кодировки.</span><span class="sxs-lookup"><span data-stu-id="93080-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="93080-219">Задайте следующие свойства (некоторые будет уже установлено по умолчанию):</span><span class="sxs-lookup"><span data-stu-id="93080-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="93080-220">**Имя кодировщика мультимедиа *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="93080-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="93080-221">**Предустановки для кодирования *Content Adaptive Multiple Bitrate MP4***</span><span class="sxs-lookup"><span data-stu-id="93080-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="93080-222">**Имя задания *Media Encoder Standard обработки Video1.mp4***</span><span class="sxs-lookup"><span data-stu-id="93080-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="93080-223">**Имя ресурса-контейнера мультимедиа выходные данные *Video1.mp4--Media Encoder Standard в кодировке***</span><span class="sxs-lookup"><span data-stu-id="93080-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Портал Azure](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="93080-225">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="93080-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="93080-226">Появится панель с **задания кодирования добавлен**, щелкните на этой панели и панель будет отображаться с помощью процесса кодирования, в нем отображается.</span><span class="sxs-lookup"><span data-stu-id="93080-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-17.png)

    ![Портал Azure](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="93080-229">Дождитесь завершения задания.</span><span class="sxs-lookup"><span data-stu-id="93080-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="93080-230">После этого, вы можете закрыть панель с «X» в правом верхнем углу этой панели.</span><span class="sxs-lookup"><span data-stu-id="93080-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-19.png)

    ![Портал Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="93080-233">Время, которое для этого потребуется, зависит от размера файла видео.</span><span class="sxs-lookup"><span data-stu-id="93080-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="93080-234">Этот процесс может занять довольно много времени.</span><span class="sxs-lookup"><span data-stu-id="93080-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="93080-235">Теперь, когда закодированная версия параметра видео будет создана, можно опубликовать его, чтобы сделать его доступным.</span><span class="sxs-lookup"><span data-stu-id="93080-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="93080-236">Чтобы сделать это, щелкните синий ссылку **активы** чтобы вернуться на страницу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="93080-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="93080-238">Вы увидите видео вместе с другой, принадлежащей \*\* тип актива \* MP4 с несколькими скоростями \*\*\*.</span><span class="sxs-lookup"><span data-stu-id="93080-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="93080-240">Вы можете заметить, что новый ресурс, наряду с начальной видео, является *Неизвестный*, и имеет "0" байт, он является **размер**, просто обновите окно для ее обновления.</span><span class="sxs-lookup"><span data-stu-id="93080-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="93080-241">Щелкните этот новый ресурс.</span><span class="sxs-lookup"><span data-stu-id="93080-241">Click this new asset.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="93080-243">Вы увидите аналогичные панели тот, который использовался ранее, просто это другой ресурс.</span><span class="sxs-lookup"><span data-stu-id="93080-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="93080-244">Нажмите кнопку **публикации** расположенную в центре верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="93080-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="93080-246">Вам будет предложено задать **локатора**, который является точкой входа, в файл/s, в ресурсах.</span><span class="sxs-lookup"><span data-stu-id="93080-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="93080-247">Для вашего сценария установите следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="93080-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="93080-248">**Тип указателя** > **последовательной**.</span><span class="sxs-lookup"><span data-stu-id="93080-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="93080-249">**Даты** и **время** будет присвоено, с вашей текущей даты, время в будущем (Сто лет в данном случае).</span><span class="sxs-lookup"><span data-stu-id="93080-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="93080-250">Оставьте как есть или изменить его в соответствии с.</span><span class="sxs-lookup"><span data-stu-id="93080-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="93080-251">Дополнительные сведения о Локаторах и вы можете [документацию по службам мультимедиа Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="93080-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="93080-252">В нижней части этой панели, щелкните **добавить** кнопки.</span><span class="sxs-lookup"><span data-stu-id="93080-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="93080-254">Видео, опубликованы и может передаваться с помощью конечной точки.</span><span class="sxs-lookup"><span data-stu-id="93080-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="93080-255">Далее вниз, данная страница является **файлы** раздел.</span><span class="sxs-lookup"><span data-stu-id="93080-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="93080-256">Это, где будет различных версий закодированное видео.</span><span class="sxs-lookup"><span data-stu-id="93080-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="93080-257">Выберите наибольшее возможное решение, один (на приведенном ниже рисунке это файл 1920 x 960), и затем будут отображаться панели справа.</span><span class="sxs-lookup"><span data-stu-id="93080-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="93080-258">Там вы найдете **URL-адрес скачивания**.</span><span class="sxs-lookup"><span data-stu-id="93080-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="93080-259">Скопируйте этот **конечной точки** так как оно будет использоваться в коде.</span><span class="sxs-lookup"><span data-stu-id="93080-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-26.png)    

    ![Портал Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="93080-262">Можно также нажать **воспроизведение** кнопку, чтобы воспроизвести видео и протестировать его.</span><span class="sxs-lookup"><span data-stu-id="93080-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="93080-263">Теперь необходимо передать второй видео, которое будет использоваться в этом лабораторном занятии.</span><span class="sxs-lookup"><span data-stu-id="93080-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="93080-264">Выполните действия, описанные в повторение тот же процесс для второго видео.</span><span class="sxs-lookup"><span data-stu-id="93080-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="93080-265">Убедитесь, вы скопировали вторая **конечной точки** также.</span><span class="sxs-lookup"><span data-stu-id="93080-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="93080-266">Используйте следующую команду [ссылку на загрузку второй видео](https://vimeo.com/214402865).</span><span class="sxs-lookup"><span data-stu-id="93080-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="93080-267">После публикации обеих видео вы готовы перейти к следующей главе.</span><span class="sxs-lookup"><span data-stu-id="93080-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="93080-268">Глава 3 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="93080-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="93080-269">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="93080-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="93080-270">Откройте **Unity** и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="93080-270">Open **Unity** and click **New**.</span></span> 

    ![Портал Azure](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="93080-272">Введите имя проекта Unity, теперь нужно вставить **MR\_360VideoStreaming.**.</span><span class="sxs-lookup"><span data-stu-id="93080-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="93080-273">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="93080-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="93080-274">Задание расположения в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="93080-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="93080-275">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="93080-275">Then, click **Create project**.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="93080-277">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="93080-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="93080-278">Перейдите к ***изменить* *предпочтения*** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="93080-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="93080-279">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="93080-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="93080-280">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="93080-280">Close the **Preferences** window.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="93080-282">Перейдите к ***файл* *параметры построения*** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **Переключить платформу** кнопки.</span><span class="sxs-lookup"><span data-stu-id="93080-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="93080-283">Также убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="93080-283">Also make sure that:</span></span>

    1. <span data-ttu-id="93080-284">**Целевое устройство** присваивается **любого устройства.**</span><span class="sxs-lookup"><span data-stu-id="93080-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="93080-285">**Тип сборки** присваивается **D3D.**</span><span class="sxs-lookup"><span data-stu-id="93080-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="93080-286">**Пакет SDK для** присваивается **самую новую установленную.**</span><span class="sxs-lookup"><span data-stu-id="93080-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="93080-287">**Версия Visual Studio** присваивается **самую новую установленную.**</span><span class="sxs-lookup"><span data-stu-id="93080-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="93080-288">**Сборка и запуск** присваивается **локального компьютера.**</span><span class="sxs-lookup"><span data-stu-id="93080-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="93080-289">Не беспокоиться о настройке **сцены** прямо сейчас, как вы настроите их позже.</span><span class="sxs-lookup"><span data-stu-id="93080-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="93080-290">Остальные параметры следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="93080-290">The remaining settings should be left as default for now.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="93080-292">В **параметры построения** щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где **инспектор** находится.</span><span class="sxs-lookup"><span data-stu-id="93080-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="93080-293">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="93080-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="93080-294">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="93080-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="93080-295">**Сценарии** **версии среды выполнения** должно быть **стабильной** (.NET 3.5 эквивалент).</span><span class="sxs-lookup"><span data-stu-id="93080-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="93080-296">**Создание сценариев серверной части** должно быть **.NET.**</span><span class="sxs-lookup"><span data-stu-id="93080-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="93080-297">**Уровень совместимости API** должно быть **.NET 4.6.**</span><span class="sxs-lookup"><span data-stu-id="93080-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="93080-299">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.</span><span class="sxs-lookup"><span data-stu-id="93080-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="93080-301">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="93080-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="93080-302">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="93080-302">**InternetClient**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="93080-304">После внесения этих изменений, закройте **параметры построения** окна.</span><span class="sxs-lookup"><span data-stu-id="93080-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="93080-305">Сохраните проект \**файл* \* сохранить проект \*\*.</span><span class="sxs-lookup"><span data-stu-id="93080-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="93080-306">Глава 4 — Импорт пакета InsideOutSphere Unity</span><span class="sxs-lookup"><span data-stu-id="93080-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93080-307">Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из **Глава 5**.</span><span class="sxs-lookup"><span data-stu-id="93080-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="93080-308">По-прежнему необходимо будет создать проект Unity.</span><span class="sxs-lookup"><span data-stu-id="93080-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="93080-309">Для этого курса необходимо загрузить пакет средств Unity, которые называются [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="93080-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="93080-310">Инструкции импорта **пакет unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="93080-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="93080-311">С помощью панели мониторинга Unity перед глазами, щелкните **активы** в меню в верхней части экрана, нажмите кнопку **Импорт пакета > пользовательского пакета**.</span><span class="sxs-lookup"><span data-stu-id="93080-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Импорт пакета InsideOutSphere Unity](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="93080-313">Используйте средство выбора файлов для выбора **InsideOutSphere.unitypackage** пакета и нажмите кнопку **откройте**.</span><span class="sxs-lookup"><span data-stu-id="93080-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="93080-314">Список компонентов для этого ресурса будет отображаться пользователю.</span><span class="sxs-lookup"><span data-stu-id="93080-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="93080-315">Подтверждение импорта, щелкнув **импорта**.</span><span class="sxs-lookup"><span data-stu-id="93080-315">Confirm the import by clicking **Import**.</span></span>

    ![Импорт пакета InsideOutSphere Unity](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="93080-317">После его завершения импорта вы заметите три новых папок, **материалы**, **моделей**, и **Prefabs**, были добавлены к **активы**папки.</span><span class="sxs-lookup"><span data-stu-id="93080-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="93080-318">Такого рода структуру папок является типичным для проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="93080-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Импорт пакета InsideOutSphere Unity](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="93080-320">Откройте **моделей** папки и вы увидите, **InsideOutSphere** модели был импортирован.</span><span class="sxs-lookup"><span data-stu-id="93080-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="93080-321">В рамках **материалы** вы найдете папку **InsideOutSpheres** материал *lambert1*, вместе с именем материал *ButtonMaterial*, который используется системой GazeButton, который появится в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="93080-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="93080-322">**Prefabs** папка содержит **InsideOutSphere** готового блока, который содержит оба **InsideOutSphere** *модели* и  *GazeButton*.</span><span class="sxs-lookup"><span data-stu-id="93080-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="93080-323">**Включено без кода**, вы напишете код, выполнив этот курс.</span><span class="sxs-lookup"><span data-stu-id="93080-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="93080-324">В рамках **иерархии**выберите **Main Camera** объекта и обновите следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="93080-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="93080-325">**Преобразование**</span><span class="sxs-lookup"><span data-stu-id="93080-325">**Transform**</span></span>

        1.  <span data-ttu-id="93080-326">Позиция = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="93080-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="93080-327">Поворот = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="93080-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="93080-328">Масштаб **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="93080-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="93080-329">**Камера**</span><span class="sxs-lookup"><span data-stu-id="93080-329">**Camera**</span></span>

        1. <span data-ttu-id="93080-330">**Очистить флаги**: Сплошным цветом.</span><span class="sxs-lookup"><span data-stu-id="93080-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="93080-331">**Обрезки плоскостей**: Рядом с: 0,1, далеко: 6.</span><span class="sxs-lookup"><span data-stu-id="93080-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Импорт пакета InsideOutSphere Unity](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="93080-333">Перейдите к **Prefab** папку, а затем перетащите **InsideOutSphere** prefab в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="93080-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Импорт пакета InsideOutSphere Unity](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="93080-335">Разверните **InsideOutSphere** объекта в пределах **иерархии** , щелкнув небольшой стрелку рядом с ним.</span><span class="sxs-lookup"><span data-stu-id="93080-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="93080-336">Вы увидите **дочерних** объекта, именуемое **GazeButton**.</span><span class="sxs-lookup"><span data-stu-id="93080-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="93080-337">Это будет использоваться для изменения автоматически и таким образом видео.</span><span class="sxs-lookup"><span data-stu-id="93080-337">This will be used to change scenes and thus videos.</span></span>

    ![Импорт пакета InsideOutSphere Unity](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="93080-339">В окне инспектора щелкните **InsideOutSphere**преобразовать компонент, убедитесь, что заданы следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="93080-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="93080-340">ПРЕОБРАЗОВАНИЕ - ПОЗИЦИИ</span><span class="sxs-lookup"><span data-stu-id="93080-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="93080-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="93080-341">**X** 0</span></span>  |          <span data-ttu-id="93080-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="93080-342">**Y** 0</span></span>          |  <span data-ttu-id="93080-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="93080-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="93080-344">ПРЕОБРАЗОВАНИЕ - ПОВОРОТА</span><span class="sxs-lookup"><span data-stu-id="93080-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="93080-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="93080-345">**X** 0</span></span>  |          <span data-ttu-id="93080-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="93080-346">**Y** -50</span></span>        |  <span data-ttu-id="93080-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="93080-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="93080-348">ПРЕОБРАЗОВАНИЕ - МАСШТАБИРОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="93080-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="93080-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="93080-349">**X** 1</span></span>   |          <span data-ttu-id="93080-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="93080-350">**Y** 1</span></span>          |  <span data-ttu-id="93080-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="93080-351">**Z** 1</span></span>  |

    ![Импорт пакета InsideOutSphere Unity](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="93080-353">Щелкните **GazeButton** дочерний объект и задать его **преобразования** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="93080-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="93080-354">ПРЕОБРАЗОВАНИЕ - ПОЗИЦИИ</span><span class="sxs-lookup"><span data-stu-id="93080-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="93080-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="93080-355">**X** 3.6</span></span>|          <span data-ttu-id="93080-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="93080-356">**Y** 1.3</span></span>        |  <span data-ttu-id="93080-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="93080-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="93080-358">ПРЕОБРАЗОВАНИЕ - ПОВОРОТА</span><span class="sxs-lookup"><span data-stu-id="93080-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="93080-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="93080-359">**X** 0</span></span>  |          <span data-ttu-id="93080-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="93080-360">**Y** 0</span></span>          |  <span data-ttu-id="93080-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="93080-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="93080-362">ПРЕОБРАЗОВАНИЕ - МАСШТАБИРОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="93080-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="93080-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="93080-363">**X** 1</span></span>   |          <span data-ttu-id="93080-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="93080-364">**Y** 1</span></span>          |  <span data-ttu-id="93080-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="93080-365">**Z** 1</span></span>  |

    ![Импорт пакета InsideOutSphere Unity](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="93080-367">Глава 5 - создание класса VideoController</span><span class="sxs-lookup"><span data-stu-id="93080-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="93080-368">**VideoController** класс размещает две конечные точки видео, которые будут использоваться для потоковой передачи содержимого из службы мультимедиа Azure.</span><span class="sxs-lookup"><span data-stu-id="93080-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="93080-369">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="93080-369">To create this class:</span></span>

1.  <span data-ttu-id="93080-370">Щелкните правой кнопкой мыши в **папке Asset**, который находится в **проекта** панели и щелкните **Создать > Папка**.</span><span class="sxs-lookup"><span data-stu-id="93080-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="93080-371">Назовите папку **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="93080-371">Name the folder **Scripts**.</span></span>

    ![Создание класса VideoController](images/AzureLabs-Lab6-43.png)

    ![Создание класса VideoController](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="93080-374">Дважды щелкните **сценариев** папку, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="93080-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="93080-375">Щелкните правой кнопкой мыши внутри папки, а затем щелкните **Создать > C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="93080-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="93080-376">Назовите сценарий **VideoController**.</span><span class="sxs-lookup"><span data-stu-id="93080-376">Name the script **VideoController**.</span></span>

    ![Создание класса VideoController](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="93080-378">Дважды щелкните новый **VideoController** скрипт, чтобы открыть его с **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="93080-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Создание класса VideoController](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="93080-380">Обновите пространства имен в верхней части файла кода следующим образом:</span><span class="sxs-lookup"><span data-stu-id="93080-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="93080-381">Введите следующие переменные в **VideoController** класса, наряду с **Awake()** метод:</span><span class="sxs-lookup"><span data-stu-id="93080-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="93080-382">Пришло время для ввода конечные точки на основе видео Azure Media Service:</span><span class="sxs-lookup"><span data-stu-id="93080-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="93080-383">Первый в *video1endpoint* переменной.</span><span class="sxs-lookup"><span data-stu-id="93080-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="93080-384">Второй в *video2endpoint* переменной.</span><span class="sxs-lookup"><span data-stu-id="93080-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="93080-385">Имеется известная проблема, с помощью *https* в Unity, при использовании версии 2017.4.1f1.</span><span class="sxs-lookup"><span data-stu-id="93080-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="93080-386">Если видео содержат ошибку в play, попробуйте вместо этого использовать «http».</span><span class="sxs-lookup"><span data-stu-id="93080-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="93080-387">Далее, **Start()** метод подходит для редактирования.</span><span class="sxs-lookup"><span data-stu-id="93080-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="93080-388">Этот метод запускается каждый раз при переключении сцены (следовательно переключение видео), просмотрев кнопку помощи.</span><span class="sxs-lookup"><span data-stu-id="93080-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="93080-389">Следуя **Start()** метод, вставьте **PlayVideo()** *IEnumerator* метод, который будет использоваться для запуска видео без проблем (поэтому наблюдается без дерганья изображения).</span><span class="sxs-lookup"><span data-stu-id="93080-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="93080-390">Последний метод, необходимые для этого класса **ChangeScene()** метод, который будет использоваться для переключения между сценами.</span><span class="sxs-lookup"><span data-stu-id="93080-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="93080-391">**ChangeScene()** метод использует под рукой C\# , называемого *условный оператор*.</span><span class="sxs-lookup"><span data-stu-id="93080-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="93080-392">Это позволяет для условий для проверки, и затем значения возвращаются в зависимости от результата проверки, все в одной инструкции.</span><span class="sxs-lookup"><span data-stu-id="93080-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="93080-393">Выполните это [ссылку, чтобы узнать больше о условный оператор](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span><span class="sxs-lookup"><span data-stu-id="93080-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="93080-394">Сохраните изменения в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="93080-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="93080-395">Обратно в редакторе Unity, щелкните и перетащите **VideoController** класса [из] {.underline} **сценарии** папку **Main Camera** объекта в  **Иерархия** панели.</span><span class="sxs-lookup"><span data-stu-id="93080-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="93080-396">Щелкните **Main Camera** и просмотрите **панели Инспектора**.</span><span class="sxs-lookup"><span data-stu-id="93080-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="93080-397">Обратите внимание, что в компоненте скрипта вновь добавленный есть поле с пустым значением.</span><span class="sxs-lookup"><span data-stu-id="93080-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="93080-398">Это поле ссылки, которая нацелена на открытые переменные в коде.</span><span class="sxs-lookup"><span data-stu-id="93080-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="93080-399">Перетащите **InsideOutSphere** объекта из **панели иерархии** для **Sphere** область памяти, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="93080-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="93080-400">![Создайте класс VideoController](images/AzureLabs-Lab6-47.png)
    ![создать класс VideoController](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="93080-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="93080-401">Глава 6 - создание класса взглядом</span><span class="sxs-lookup"><span data-stu-id="93080-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="93080-402">Этот класс отвечает за создание **Raycast** что будет beprojected вперед от **Main Camera**, для обнаружения какой объект, который просматривает пользователь.</span><span class="sxs-lookup"><span data-stu-id="93080-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="93080-403">В этом случае **Raycast** будет необходимо определить, если пользователь просматривает **GazeButton** объект в сцене и активировать поведение.</span><span class="sxs-lookup"><span data-stu-id="93080-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="93080-404">Для создания данного класса:</span><span class="sxs-lookup"><span data-stu-id="93080-404">To create this Class:</span></span>

1.  <span data-ttu-id="93080-405">Перейдите к **сценариев** папку, созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="93080-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="93080-406">Щелкните правой кнопкой мыши в **проекта** панели \**создать* \* C\# Script \*\*.</span><span class="sxs-lookup"><span data-stu-id="93080-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="93080-407">Назовите сценарий **помощи**.</span><span class="sxs-lookup"><span data-stu-id="93080-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="93080-408">Дважды щелкните новый ***помощи*** скрипт, чтобы открыть его с **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="93080-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="93080-409">Убедитесь, что следующее пространство имен в верхней части сценария и удалите любые другие:</span><span class="sxs-lookup"><span data-stu-id="93080-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="93080-410">Затем добавьте следующие переменные внутри **помощи** класса:</span><span class="sxs-lookup"><span data-stu-id="93080-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="93080-411">Код для **Awake()** и **Start()** методы теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="93080-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="93080-412">Добавьте следующий код в **Update()** метод для проекта Raycast и выявления попаданий целевой:</span><span class="sxs-lookup"><span data-stu-id="93080-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="93080-413">Сохраните изменения в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="93080-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="93080-414">Щелкните и перетащите **помощи** класса из папки скриптов для объекта Main Camera в **иерархии** панели.</span><span class="sxs-lookup"><span data-stu-id="93080-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="93080-415">Глава 7 - два Unity сцены</span><span class="sxs-lookup"><span data-stu-id="93080-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="93080-416">В этой главе предназначена для настройки двух сцен, каждый из которых размещает видео в stream.</span><span class="sxs-lookup"><span data-stu-id="93080-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="93080-417">Вы приведет к дублированию сцены, вы уже создали, таким образом, чтобы не нужно настроить еще раз, то, что вы затем измените новую сцену, чтобы *GazeButton* объект находится в другом месте и имеет различный внешний вид.</span><span class="sxs-lookup"><span data-stu-id="93080-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="93080-418">Это позволяет продемонстрировать изменение между сценами.</span><span class="sxs-lookup"><span data-stu-id="93080-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="93080-419">Это можно сделать, выбрав **файл > Сохранить сцену как...** . Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="93080-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="93080-420">Нажмите кнопку **новую папку** кнопки.</span><span class="sxs-lookup"><span data-stu-id="93080-420">Click the **New folder** button.</span></span>

    ![Глава 7 - два Unity сцены](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="93080-422">Назовите папку **сцены**.</span><span class="sxs-lookup"><span data-stu-id="93080-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="93080-423">**Сохранить сцену** окно по-прежнему будут открыты.</span><span class="sxs-lookup"><span data-stu-id="93080-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="93080-424">Откройте только что созданный **сцены** папки.</span><span class="sxs-lookup"><span data-stu-id="93080-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="93080-425">В **имя файла:** текстовое поле, тип **VideoScene1**, затем нажмите клавишу **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="93080-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="93080-426">В Unity, откройте ваш **сцены** папку, а затем выберите пункт вашей **VideoScene1** файл.</span><span class="sxs-lookup"><span data-stu-id="93080-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="93080-427">Использование клавиатуры и нажмите клавишу **Ctrl + D** дублируются сцены</span><span class="sxs-lookup"><span data-stu-id="93080-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="93080-428">**Дублировать** также можно выполнить команду, перейдя по адресу **изменить > Дублировать**.</span><span class="sxs-lookup"><span data-stu-id="93080-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="93080-429">Unity будет автоматически увеличивать количество имен сцены, но включить его в любом случае, убедитесь, что он соответствует ранее вставленный код.</span><span class="sxs-lookup"><span data-stu-id="93080-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="93080-430">Вы должны иметь **VideoScene1** и **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="93080-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="93080-431">С вашей двумя сценами, перейдите к **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="93080-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="93080-432">С помощью **параметры построения** открытое окно, перетащите вашей работает **сцены в сборке** раздел.</span><span class="sxs-lookup"><span data-stu-id="93080-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="93080-434">Можно выбрать оба вашей сцены из вашей **сцены** общему ресурсу посредством совместного хранения **Ctrl** кнопку, затем щелчок левой кнопкой мыши каждый сцены и наконец перетащите оба по.</span><span class="sxs-lookup"><span data-stu-id="93080-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="93080-435">Закрыть **параметры построения** окно и двойного щелчка по **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="93080-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="93080-436">Откройте второй сцены, выберите команду **GazeButton** дочерний объект **InsideOutSphere**и установите его преобразования следующим образом:</span><span class="sxs-lookup"><span data-stu-id="93080-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="93080-437">ПРЕОБРАЗОВАНИЕ - ПОЗИЦИИ</span><span class="sxs-lookup"><span data-stu-id="93080-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="93080-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="93080-438">**X** 0</span></span>  |         <span data-ttu-id="93080-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="93080-439">**Y** 1.3</span></span>         | <span data-ttu-id="93080-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="93080-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="93080-441">ПРЕОБРАЗОВАНИЕ - ПОВОРОТА</span><span class="sxs-lookup"><span data-stu-id="93080-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="93080-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="93080-442">**X** 0</span></span>  |          <span data-ttu-id="93080-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="93080-443">**Y** 0</span></span>          |  <span data-ttu-id="93080-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="93080-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="93080-445">ПРЕОБРАЗОВАНИЕ - МАСШТАБИРОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="93080-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="93080-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="93080-446">**X** 1</span></span>   |          <span data-ttu-id="93080-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="93080-447">**Y** 1</span></span>          |  <span data-ttu-id="93080-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="93080-448">**Z** 1</span></span>  |

10. <span data-ttu-id="93080-449">С **GazeButton** все еще выбран, поиск в дочерних **инспектор** и **Сетка фильтра**.</span><span class="sxs-lookup"><span data-stu-id="93080-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="93080-450">Щелкните рядом с полем мало целевой **Mesh** эталонное поле:</span><span class="sxs-lookup"><span data-stu-id="93080-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="93080-452">Объект **выберите Mesh** Откроется всплывающее окно.</span><span class="sxs-lookup"><span data-stu-id="93080-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="93080-453">Дважды щелкните **куба** mesh из списка **активы**.</span><span class="sxs-lookup"><span data-stu-id="93080-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="93080-455">**Сетка фильтра** будет обновить и теперь **куба**.</span><span class="sxs-lookup"><span data-stu-id="93080-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="93080-456">Теперь щелкните **шестеренки** значок рядом с полем **Sphere Collider** и нажмите кнопку **удалить компонент**, чтобы удалить collider от этого объекта.</span><span class="sxs-lookup"><span data-stu-id="93080-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="93080-458">С помощью **GazeButton** все еще выбран, щелкните **добавить компонент** кнопки в нижней части **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="93080-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="93080-459">В поле поиска введите **поле**, и **Collider поле** будет иметь параметр — щелкните, чтобы добавить **Collider поле** для вашей **GazeButton** объекта .</span><span class="sxs-lookup"><span data-stu-id="93080-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="93080-461">**GazeButton** — теперь частично обновлена, чтобы выглядеть по-другому, тем не менее, теперь вы создадите новый **материал**, в котором она выглядит совершенно по-разному и легче распознать как другой объект, чем объект в первую сцену.</span><span class="sxs-lookup"><span data-stu-id="93080-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="93080-462">Перейдите к вашей **материалы** папку, в пределах **панель проекта**.</span><span class="sxs-lookup"><span data-stu-id="93080-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="93080-463">Дублировать **ButtonMaterial** материал (нажмите клавишу **Ctrl** + **D** на клавиатуре или щелкните левой кнопкой **материал**, затем из **изменить** пункт меню, выберите файл **дублировать**).</span><span class="sxs-lookup"><span data-stu-id="93080-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="93080-464">![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-55.png)
    ![Глава 7 — Настройка двумя сценами Unity](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="93080-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="93080-465">Выберите новый **ButtonMaterial** материал (здесь с именем **ButtonMaterial 1**) и в **инспектор**, нажмите кнопку **Albedo** цвет окно.</span><span class="sxs-lookup"><span data-stu-id="93080-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="93080-466">Откроется всплывающее окно, в котором можно выбрать другой цвет (выберите, какое угодно), затем закройте всплывающее окно.</span><span class="sxs-lookup"><span data-stu-id="93080-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="93080-467">Материал будет свой собственный экземпляр и отличается от исходного.</span><span class="sxs-lookup"><span data-stu-id="93080-467">The Material will be its own instance, and different to the original.</span></span>

    ![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="93080-469">Перетащите новый **материал** на **GazeButton** дочерний элемент, теперь полностью обновить его внешний вид, так как это легко отличить от первой кнопки сцены.</span><span class="sxs-lookup"><span data-stu-id="93080-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="93080-471">На этом этапе можно проверить проекта в редакторе перед построением проекта универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="93080-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="93080-472">Нажмите клавишу **воспроизведение** кнопку **редактор** и wear вашей гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="93080-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Глава 7 - Настройка двумя сценами Unity](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="93080-474">Рассмотрим два **GazeButton** объектов для переключения между первым и вторым видео.</span><span class="sxs-lookup"><span data-stu-id="93080-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="93080-475">Глава 8 - выполнить сборку решения универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="93080-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="93080-476">Когда вы убедились, что редактор не содержит ошибок, вы будете готовы сборки.</span><span class="sxs-lookup"><span data-stu-id="93080-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="93080-477">Для сборки:</span><span class="sxs-lookup"><span data-stu-id="93080-477">To Build:</span></span>

1.  <span data-ttu-id="93080-478">Сохранить текущую сцену, щелкнув **файл > Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="93080-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="93080-479">Проверьте поле, называемое **Unity C\# проекты** (это важно, так как он позволит вам изменить классы, после завершения сборки).</span><span class="sxs-lookup"><span data-stu-id="93080-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="93080-480">Перейдите к **файл > Параметры сборки**, щелкните **построения**.</span><span class="sxs-lookup"><span data-stu-id="93080-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="93080-481">Вам будет предложено выбрать папку, где вы хотите buildthe решения.</span><span class="sxs-lookup"><span data-stu-id="93080-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="93080-482">Создание **ПОСТРОЕНИЯ** папку и в этой папке создайте другую папку с соответствующим именем, по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="93080-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="93080-483">Щелкните новую папку и нажмите кнопку **Выбор папки**, таким образом, для выбора этой папки, чтобы начать построение в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="93080-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="93080-484">![Глава 8 — Построить решение UWP](images/AzureLabs-Lab6-60.png)
    ![главе 8 — построить решение универсальной платформы Windows](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="93080-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="93080-485">Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окно в папке построения.</span><span class="sxs-lookup"><span data-stu-id="93080-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="93080-486">Глава 9 — развертывание на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="93080-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="93080-487">После завершения построения **проводнике** окно будет отображаться в папке построения.</span><span class="sxs-lookup"><span data-stu-id="93080-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="93080-488">Откройте папку с именем и созданная для, а затем дважды щелкните файл решения (SLN) в этой папке, чтобы открыть решение в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="93080-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="93080-489">Единственное, что осталось сделать, — это развертывание приложения в компьютер (или *локальный компьютер*).</span><span class="sxs-lookup"><span data-stu-id="93080-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="93080-490">Для развертывания на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="93080-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="93080-491">В **Visual Studio 2017**, откройте файл решения, который был только что создан.</span><span class="sxs-lookup"><span data-stu-id="93080-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="93080-492">В **платформа решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="93080-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="93080-493">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="93080-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Глава 9 — Развертывание на локальном компьютере](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="93080-495">Теперь необходимо будет восстановить все пакеты в решение.</span><span class="sxs-lookup"><span data-stu-id="93080-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="93080-496">Щелкните правой кнопкой мыши ваш **решение**и нажмите кнопку **восстановить пакеты NuGet для решения...**</span><span class="sxs-lookup"><span data-stu-id="93080-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="93080-497">Это делается, так как пакеты, которые созданы Unity должны быть предназначены для работы со ссылками на локальных компьютерах.</span><span class="sxs-lookup"><span data-stu-id="93080-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="93080-498">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на компьютер.</span><span class="sxs-lookup"><span data-stu-id="93080-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="93080-499">Visual Studio создаст сначала и затем развернуть приложение.</span><span class="sxs-lookup"><span data-stu-id="93080-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="93080-500">Приложения появятся в списке установленных приложений, Готово к запуску.</span><span class="sxs-lookup"><span data-stu-id="93080-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Глава 9 — Развертывание на локальном компьютере](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="93080-502">Когда вы запустите приложение смешанной реальности, вам будет вам быть в пределах **InsideOutSphere** модели, которые использовались в приложении.</span><span class="sxs-lookup"><span data-stu-id="93080-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="93080-503">Это сфера будет где потоковую передачу видео, благодаря представлению 360 градусов, входящее видео (который был расположенным для такого рода перспективы).</span><span class="sxs-lookup"><span data-stu-id="93080-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="93080-504">Не удивляйтесь, если видео занимает несколько секунд для загрузки, приложение регулируется доступные скорости подключения к Интернету, мере видео для выборки, а затем загружаться, поэтому для потоковой передачи в приложение.</span><span class="sxs-lookup"><span data-stu-id="93080-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="93080-505">Когда будете готовы, изменить сцен и открыть второй видео, gazing в красный шар!</span><span class="sxs-lookup"><span data-stu-id="93080-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="93080-506">Затем вы можете вернуться назад, используя голубой куб в сцене второй!</span><span class="sxs-lookup"><span data-stu-id="93080-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="93080-507">Готового приложения служб мультимедиа Azure</span><span class="sxs-lookup"><span data-stu-id="93080-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="93080-508">Поздравляем, вы создали приложение смешанной реальности, которое использует службы мультимедиа Azure для потоковой передачи видео 360.</span><span class="sxs-lookup"><span data-stu-id="93080-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![Результат лаборатории](images/AzureLabs-Lab6-00.png)

![Результат лаборатории](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="93080-511">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="93080-511">Bonus Exercises</span></span>

<span data-ttu-id="93080-512">**Упражнение 1**</span><span class="sxs-lookup"><span data-stu-id="93080-512">**Exercise 1**</span></span>

<span data-ttu-id="93080-513">Это вполне возможно, только изменение видео в этом руководстве с помощью одной сценой.</span><span class="sxs-lookup"><span data-stu-id="93080-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="93080-514">Поэкспериментировать с приложением и сделать его одной сценой!</span><span class="sxs-lookup"><span data-stu-id="93080-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="93080-515">Возможно даже добавьте другого видео, в набор.</span><span class="sxs-lookup"><span data-stu-id="93080-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="93080-516">**Упражнение 2**</span><span class="sxs-lookup"><span data-stu-id="93080-516">**Exercise 2**</span></span>

<span data-ttu-id="93080-517">Поэкспериментируйте с Azure и Unity и пытается реализовать возможность для приложения, чтобы автоматически выбрать видео с размером другой файл, в зависимости от надежности подключение к Интернету.</span><span class="sxs-lookup"><span data-stu-id="93080-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


