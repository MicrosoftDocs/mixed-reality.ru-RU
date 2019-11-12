---
title: MR и Azure 306 — потоковая передача видео
description: Пройдите этот курс, чтобы узнать, как реализовать службы мультимедиа Azure в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, службы мультимедиа, потоковая передача видео, 360, иммерсивное, VR
ms.openlocfilehash: e0350d69eed9b922e174bc521107beac7d11b1bc
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926830"
---
>[!NOTE]
><span data-ttu-id="01746-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="01746-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="01746-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="01746-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="01746-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="01746-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="01746-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="01746-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="01746-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="01746-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="01746-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="01746-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="01746-110">MR и Azure 306: потоковая передача видео</span><span class="sxs-lookup"><span data-stu-id="01746-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="01746-111">![окончательный продукт — запуск](images/AzureLabs-Lab6-00.png)
![окончательного запуска продукта](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="01746-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="01746-112">В этом курсе вы узнаете, как подключить службы мультимедиа Azure к операционной системе Windows Mixed Reality, чтобы разрешить воспроизведение видео в режиме потоковой передачи 360 на впечатляющих наушниках.</span><span class="sxs-lookup"><span data-stu-id="01746-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="01746-113">**Службы мультимедиа Azure** — это набор служб, которые предоставляют высококачественные службы потоковой передачи видео для достижения больших аудиторий на современных наиболее популярных мобильных устройствах.</span><span class="sxs-lookup"><span data-stu-id="01746-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="01746-114">Дополнительные сведения см. на [странице служб мультимедиа Azure](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="01746-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="01746-115">Прополнив этот курс, вы получите иммерсивное приложение для наушников, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="01746-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="01746-116">Получите видео 360 градусов из службы **хранилища Azure**через **службу мультимедиа Azure**.</span><span class="sxs-lookup"><span data-stu-id="01746-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="01746-117">Отобразить полученное видео 360 градусов в сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="01746-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="01746-118">Переход между двумя сценами с двумя различными видео.</span><span class="sxs-lookup"><span data-stu-id="01746-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="01746-119">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="01746-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="01746-120">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="01746-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="01746-121">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="01746-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="01746-122">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="01746-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="01746-123">Хождение</span><span class="sxs-lookup"><span data-stu-id="01746-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="01746-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="01746-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="01746-125"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="01746-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="01746-126">MR и Azure 306: потоковая передача видео</span><span class="sxs-lookup"><span data-stu-id="01746-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="01746-127">✔️</span><span class="sxs-lookup"><span data-stu-id="01746-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="01746-128">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="01746-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="01746-129">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="01746-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="01746-130">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018).</span><span class="sxs-lookup"><span data-stu-id="01746-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="01746-131">Вы можете использовать новейшее программное обеспечение, как указано в [статье Установка средств](install-the-tools.md), но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.</span><span class="sxs-lookup"><span data-stu-id="01746-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="01746-132">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="01746-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="01746-133">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="01746-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="01746-134">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="01746-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="01746-135">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="01746-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="01746-136">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="01746-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="01746-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="01746-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="01746-138">[Головной телефон Windows Mixed Reality (VR)](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="01746-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="01746-139">Доступ к Интернету для установки Azure и извлечения данных</span><span class="sxs-lookup"><span data-stu-id="01746-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="01746-140">Видео 2 360-градусы в формате MP4 ( [на этой странице скачивания](https://www.mettle.com/360vr-master-series-free-360-downloads-page)можно найти бесплатные видеоматериалы)</span><span class="sxs-lookup"><span data-stu-id="01746-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="01746-141">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="01746-141">Before you start</span></span>

1.  <span data-ttu-id="01746-142">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="01746-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="01746-143">Настройка и тестирование иммерсивного наушников смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="01746-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="01746-144">Для этого курса **не** потребуется использовать контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="01746-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="01746-145">Если вам нужна поддержка настройки иммерсивного головного телефона, щелкните ссылку, [чтобы настроить Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="01746-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="01746-146">Глава 1. Создание учетной записи хранения Azure с помощью портала Azure</span><span class="sxs-lookup"><span data-stu-id="01746-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="01746-147">Чтобы использовать **службу хранилища Azure**, вам потребуется создать и настроить **учетную запись хранения** в портал Azure.</span><span class="sxs-lookup"><span data-stu-id="01746-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="01746-148">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="01746-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="01746-149">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="01746-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="01746-150">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="01746-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="01746-151">После входа в меню слева щелкните **учетные записи хранения** .</span><span class="sxs-lookup"><span data-stu-id="01746-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="01746-153">На вкладке **учетные записи хранения** щелкните **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="01746-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="01746-155">На вкладке **Создание учетной записи хранения** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="01746-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="01746-156">Введите **имя** для своей учетной записи. Имейте в виду, что это поле принимает только цифры и строчные буквы.</span><span class="sxs-lookup"><span data-stu-id="01746-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="01746-157">В качестве **модели развертывания** выберите **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="01746-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="01746-158">В качестве **типа учетной записи**выберите **хранилище (общее назначение v1)** .</span><span class="sxs-lookup"><span data-stu-id="01746-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="01746-159">Для **повышения производительности**выберите \**стандартный *.**</span><span class="sxs-lookup"><span data-stu-id="01746-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="01746-160">Для **репликации** выберите **локально избыточное хранилище (LRS)** .</span><span class="sxs-lookup"><span data-stu-id="01746-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="01746-161">Оставьте **защищенное перемещение обязательным** , как **отключено**.</span><span class="sxs-lookup"><span data-stu-id="01746-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="01746-162">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="01746-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="01746-163">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="01746-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="01746-164">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="01746-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="01746-165">Определите **Расположение** группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="01746-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="01746-166">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="01746-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="01746-167">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="01746-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="01746-168">Необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="01746-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="01746-170">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="01746-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="01746-171">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="01746-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="01746-173">На этом этапе вам не нужно следовать за ресурсом, просто перейдите к следующей главе.</span><span class="sxs-lookup"><span data-stu-id="01746-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="01746-174">Глава 2. Создание службы мультимедиа на портале Azure</span><span class="sxs-lookup"><span data-stu-id="01746-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="01746-175">Чтобы использовать службу мультимедиа Azure, необходимо настроить экземпляр службы, чтобы сделать ее доступной для приложения (где владелец учетной записи должен быть администратором).</span><span class="sxs-lookup"><span data-stu-id="01746-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="01746-176">На портале Azure щелкните **создать ресурс** в левом верхнем углу экрана и найдите **службу мультимедиа,** нажав клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="01746-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="01746-177">В настоящий момент ресурс имеет розовый значок; Щелкните здесь, чтобы отобразить новую страницу.</span><span class="sxs-lookup"><span data-stu-id="01746-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="01746-179">На новой странице будет представлено описание **службы мультимедиа**.</span><span class="sxs-lookup"><span data-stu-id="01746-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="01746-180">В нижнем левом углу этого запроса нажмите кнопку " **создать** ", чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="01746-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="01746-182">После нажатия кнопки **создать** панель появится место, где необходимо указать сведения о новой службе мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="01746-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="01746-183">Вставьте имя нужной **учетной записи** для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="01746-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="01746-184">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="01746-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="01746-185">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="01746-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="01746-186">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="01746-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="01746-187">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="01746-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="01746-188">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группами ресурсов Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="01746-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="01746-189">Определите **Расположение** группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="01746-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="01746-190">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="01746-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="01746-191">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="01746-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="01746-192">В разделе **учетная запись хранения** щелкните раздел **выберите...** , а затем щелкните **учетную запись хранения** , созданную в последней главе.</span><span class="sxs-lookup"><span data-stu-id="01746-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="01746-193">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="01746-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="01746-194">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="01746-194">Click **Create**.</span></span>

        ![Портал Azure](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="01746-196">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="01746-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="01746-197">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="01746-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="01746-199">Щелкните уведомление, чтобы просмотреть новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="01746-199">Click on the notification to explore your new Service instance.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="01746-201">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="01746-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="01746-202">На странице Новая служба мультимедиа на панели слева щелкните ссылку **ресурсы** , что находится примерно в середине.</span><span class="sxs-lookup"><span data-stu-id="01746-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="01746-203">На следующей странице в левом верхнем углу страницы щелкните **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="01746-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="01746-205">Щелкните значок **папки** , чтобы просмотреть файлы и выбрать первое 360 видео, которое требуется передать в поток.</span><span class="sxs-lookup"><span data-stu-id="01746-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="01746-206">Можно перейти по этой [ссылке, чтобы скачать пример видео](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="01746-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="01746-208">Длинные имена файлов могут вызвать проблемы с кодировщиком: так, чтобы в видеороликах не было проблем, рекомендуется сократить длину имен видеофайлов.</span><span class="sxs-lookup"><span data-stu-id="01746-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="01746-209">Индикатор выполнения будет зеленым после отправки видео.</span><span class="sxs-lookup"><span data-stu-id="01746-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="01746-211">Щелкните приведенный выше текст (**йоурсервиценаме-Assets**), чтобы вернуться на страницу " **активы** ".</span><span class="sxs-lookup"><span data-stu-id="01746-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="01746-212">Вы увидите, что видео успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="01746-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="01746-213">Щелкните его.</span><span class="sxs-lookup"><span data-stu-id="01746-213">Click on it.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="01746-215">На странице, на которую вы перенаправляетесь, отобразятся подробные сведения о видео.</span><span class="sxs-lookup"><span data-stu-id="01746-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="01746-216">Чтобы иметь возможность использовать видео, необходимо его кодировать, нажав кнопку " **Кодировка** " в верхней левой части страницы.</span><span class="sxs-lookup"><span data-stu-id="01746-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="01746-218">Справа появится новая панель, где можно будет задать параметры кодировки для файла.</span><span class="sxs-lookup"><span data-stu-id="01746-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="01746-219">Задайте следующие свойства (некоторые будут уже заданы по умолчанию):</span><span class="sxs-lookup"><span data-stu-id="01746-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="01746-220">**Имя кодировщика мультимедиа *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="01746-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="01746-221">**Кодирование предустановленного *содержимого Адаптивная* многоскоростная скорость MP4**</span><span class="sxs-lookup"><span data-stu-id="01746-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="01746-222">**Имя задания *Media Encoder Standard обработки файла video1. MP4***</span><span class="sxs-lookup"><span data-stu-id="01746-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="01746-223">**Имя выходного ресурса мультимедиа *video1. MP4--Media Encoder Standard закодировано***</span><span class="sxs-lookup"><span data-stu-id="01746-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Портал Azure](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="01746-225">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="01746-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="01746-226">Вы увидите строку с **добавленным заданием кодирования**, щелкните эту панель, и появится панель со сведениями о ходе кодирования.</span><span class="sxs-lookup"><span data-stu-id="01746-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-17.png)

    ![Портал Azure](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="01746-229">Дождитесь завершения задания.</span><span class="sxs-lookup"><span data-stu-id="01746-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="01746-230">После этого вы можете закрыть панель с крестиком в правом верхнем углу этой панели.</span><span class="sxs-lookup"><span data-stu-id="01746-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-19.png)

    ![Портал Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="01746-233">Время, необходимое для этого, зависит от размера файла видео.</span><span class="sxs-lookup"><span data-stu-id="01746-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="01746-234">Этот процесс может занять довольно много времени.</span><span class="sxs-lookup"><span data-stu-id="01746-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="01746-235">Теперь, когда закодированная версия видео создана, ее можно опубликовать, чтобы сделать доступной.</span><span class="sxs-lookup"><span data-stu-id="01746-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="01746-236">Для этого щелкните ссылку "синие **ресурсы** ", чтобы вернуться на страницу "активы".</span><span class="sxs-lookup"><span data-stu-id="01746-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="01746-238">Вы увидите видео вместе с другим, который относится к **типу ресурса с _несколькими скоростями MP4_** .</span><span class="sxs-lookup"><span data-stu-id="01746-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="01746-240">Вы можете заметить, что новый ресурс, рядом с исходным видео, *неизвестен*и имеет значение 0 байт для его **размера**. просто обновите окно, чтобы обновить его.</span><span class="sxs-lookup"><span data-stu-id="01746-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="01746-241">Щелкните этот новый ресурс.</span><span class="sxs-lookup"><span data-stu-id="01746-241">Click this new asset.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="01746-243">Вы увидите аналогичную панель, которая использовалась ранее, а только это другой ресурс.</span><span class="sxs-lookup"><span data-stu-id="01746-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="01746-244">Нажмите кнопку **опубликовать** , расположенную в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="01746-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="01746-246">Вам будет предложено задать **указатель**, который является точкой входа, к файлу/s в ваших ресурсах.</span><span class="sxs-lookup"><span data-stu-id="01746-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="01746-247">Для сценария задайте следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="01746-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="01746-248">**Тип указателя** > **прогрессивно**.</span><span class="sxs-lookup"><span data-stu-id="01746-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="01746-249">**Дата** и **время** будут установлены для вас, от текущей даты до времени в будущем (в данном случае 100 лет).</span><span class="sxs-lookup"><span data-stu-id="01746-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="01746-250">Оставьте "как есть" или измените его на "масть".</span><span class="sxs-lookup"><span data-stu-id="01746-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="01746-251">Дополнительные сведения об указателях и о том, что можно выбрать, см. в [документации по службам мультимедиа Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="01746-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="01746-252">В нижней части этой панели нажмите кнопку **Добавить** .</span><span class="sxs-lookup"><span data-stu-id="01746-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="01746-254">Теперь ваше видео Опубликовано, и его можно перепотокировать с помощью конечной точки.</span><span class="sxs-lookup"><span data-stu-id="01746-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="01746-255">Ниже приведен раздел « **файлы** ».</span><span class="sxs-lookup"><span data-stu-id="01746-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="01746-256">Именно здесь будут использоваться разные закодированные версии вашего видео.</span><span class="sxs-lookup"><span data-stu-id="01746-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="01746-257">Выберите наибольшее возможное разрешение (на изображении ниже, это файл 1920x960), после чего появится панель справа.</span><span class="sxs-lookup"><span data-stu-id="01746-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="01746-258">Здесь вы найдете **URL-адрес для скачивания**.</span><span class="sxs-lookup"><span data-stu-id="01746-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="01746-259">Скопируйте эту **конечную точку** , так как она будет использоваться позже в коде.</span><span class="sxs-lookup"><span data-stu-id="01746-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-26.png)    

    ![Портал Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="01746-262">Можно также нажать кнопку **Воспроизведение** , чтобы воспроизвести видео и протестировать его.</span><span class="sxs-lookup"><span data-stu-id="01746-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="01746-263">Теперь необходимо отправить второе видео, которое будет использоваться в этой лаборатории.</span><span class="sxs-lookup"><span data-stu-id="01746-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="01746-264">Выполните описанные выше действия, повторив тот же процесс для второго видео.</span><span class="sxs-lookup"><span data-stu-id="01746-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="01746-265">Убедитесь, что вы также скопировали вторую **конечную точку** .</span><span class="sxs-lookup"><span data-stu-id="01746-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="01746-266">[Чтобы скачать второе видео](https://vimeo.com/214402865), используйте следующую ссылку.</span><span class="sxs-lookup"><span data-stu-id="01746-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="01746-267">После публикации обоих видео вы можете перейти к следующей главе.</span><span class="sxs-lookup"><span data-stu-id="01746-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="01746-268">Глава 3. Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="01746-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="01746-269">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="01746-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="01746-270">Откройте **Unity** и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="01746-270">Open **Unity** and click **New**.</span></span> 

    ![Портал Azure](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="01746-272">Теперь необходимо указать имя проекта Unity, вставить **MR\_360VideoStreaming.** .</span><span class="sxs-lookup"><span data-stu-id="01746-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="01746-273">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="01746-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="01746-274">Задайте для расположения нужное расположение (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="01746-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="01746-275">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="01746-275">Then, click **Create project**.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="01746-277">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="01746-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="01746-278">Перейдите к разделу ***изменение* *настроек*** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="01746-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="01746-279">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="01746-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="01746-280">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="01746-280">Close the **Preferences** window.</span></span>

    ![Портал Azure](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="01746-282">Затем перейдите в раздел  ***параметры сборки* файлов** и переключите платформу на **универсальная платформа Windows**, нажав кнопку **коммутатора на платформе** .</span><span class="sxs-lookup"><span data-stu-id="01746-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="01746-283">Также убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="01746-283">Also make sure that:</span></span>

    1. <span data-ttu-id="01746-284">**Целевое устройство** настроено для **любого устройства.**</span><span class="sxs-lookup"><span data-stu-id="01746-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="01746-285">Для **типа сборки** задано значение **D3D.**</span><span class="sxs-lookup"><span data-stu-id="01746-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="01746-286">**Пакет SDK** установлен в значение " **Последняя установка".**</span><span class="sxs-lookup"><span data-stu-id="01746-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="01746-287">**Установлена последняя установленная** **версия Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="01746-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="01746-288">**Сборка и запуск** настроены на **локальный компьютер.**</span><span class="sxs-lookup"><span data-stu-id="01746-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="01746-289">Не беспокойтесь о настройке **сцен** прямо сейчас, так как они будут настроены позже.</span><span class="sxs-lookup"><span data-stu-id="01746-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="01746-290">Остальные параметры должны остаться в данный момент по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="01746-290">The remaining settings should be left as default for now.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="01746-292">В окне **параметры сборки** нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится **инспектор** .</span><span class="sxs-lookup"><span data-stu-id="01746-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="01746-293">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="01746-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="01746-294">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="01746-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="01746-295">**Версия среды выполнения** сценариев должна быть **стабильной** (эквивалент .NET 3,5).</span><span class="sxs-lookup"><span data-stu-id="01746-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="01746-296">**Серверная часть сценариев** должна быть **.NET.**</span><span class="sxs-lookup"><span data-stu-id="01746-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="01746-297">**Уровень совместимости API** должен быть **.NET 4,6.**</span><span class="sxs-lookup"><span data-stu-id="01746-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="01746-299">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="01746-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="01746-301">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="01746-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="01746-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="01746-302">**InternetClient**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="01746-304">После внесения этих изменений закройте окно **параметры сборки** .</span><span class="sxs-lookup"><span data-stu-id="01746-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="01746-305">Сохраните проект \**файл* \* сохранить проект \* \*.</span><span class="sxs-lookup"><span data-stu-id="01746-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="01746-306">Глава 4. Импорт пакета Unity Инсидеаутсфере</span><span class="sxs-lookup"><span data-stu-id="01746-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01746-307">Если вы хотите пропустить компонент *установки Unity, установленный* в этом курсе, и продолжить работу с кодом, скачайте этот файл [. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), импортируйте его в проект как [**пользовательский пакет**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в **главе 5**.</span><span class="sxs-lookup"><span data-stu-id="01746-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="01746-308">Вам все равно придется создать проект Unity.</span><span class="sxs-lookup"><span data-stu-id="01746-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="01746-309">Для этого курса необходимо скачать пакет ресурса Unity с именем [**инсидеаутсфере. пакет unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="01746-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="01746-310">Как импортировать **пакет unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="01746-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="01746-311">Теперь, когда панель мониторинга Unity находится перед вами, щелкните **ресурсы** в меню в верхней части экрана, а затем щелкните **Импорт пакета > настраиваемый пакет**.</span><span class="sxs-lookup"><span data-stu-id="01746-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Импорт пакета Unity Инсидеаутсфере](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="01746-313">Используйте средство выбора файлов, чтобы выбрать пакет **инсидеаутсфере. пакет unitypackage** , и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="01746-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="01746-314">Отобразится список компонентов для этого актива.</span><span class="sxs-lookup"><span data-stu-id="01746-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="01746-315">Подтвердите импорт, нажав кнопку **Импорт**.</span><span class="sxs-lookup"><span data-stu-id="01746-315">Confirm the import by clicking **Import**.</span></span>

    ![Импорт пакета Unity Инсидеаутсфере](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="01746-317">После завершения импорта вы увидите три новые папки, **материалы**, **модели**и **Prefabs**, добавленные в папку **Assets** .</span><span class="sxs-lookup"><span data-stu-id="01746-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="01746-318">Такой тип структуры папок является типичным для проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="01746-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Импорт пакета Unity Инсидеаутсфере](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="01746-320">Откройте папку **Models** , и вы увидите, что модель **инсидеаутсфере** была импортирована.</span><span class="sxs-lookup"><span data-stu-id="01746-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="01746-321">В папке **Materials** вы найдете **инсидеаутсферес** Material *lambert1*, а также материал с именем *буттонматериал*, который используется газебуттон, который вы увидите в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="01746-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="01746-322">Папка **Prefabs** содержит **инсидеаутсфере** prefab, который содержит *модель* **инсидеаутсфере** и *газебуттон*.</span><span class="sxs-lookup"><span data-stu-id="01746-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="01746-323">**Код не включается**, вы пишете код, следуя этому курсу.</span><span class="sxs-lookup"><span data-stu-id="01746-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="01746-324">В **иерархии**выберите **основной объект Camera** и обновите следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="01746-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="01746-325">**Преобразует**</span><span class="sxs-lookup"><span data-stu-id="01746-325">**Transform**</span></span>

        1.  <span data-ttu-id="01746-326">Положением = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="01746-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="01746-327">Поворот = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="01746-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="01746-328">Масштаб **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="01746-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="01746-329">**Камера**</span><span class="sxs-lookup"><span data-stu-id="01746-329">**Camera**</span></span>

        1. <span data-ttu-id="01746-330">**Снять флаги**: сплошной цвет.</span><span class="sxs-lookup"><span data-stu-id="01746-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="01746-331">**Обтравочные плоскости**: Near: 0,1, дальнее: 6.</span><span class="sxs-lookup"><span data-stu-id="01746-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Импорт пакета Unity Инсидеаутсфере](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="01746-333">Перейдите в папку **prefab** , а затем перетащите **инсидеаутсфере** prefab на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="01746-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Импорт пакета Unity Инсидеаутсфере](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="01746-335">Разверните объект **инсидеаутсфере** в **иерархии** , щелкнув маленькую стрелку рядом с ней.</span><span class="sxs-lookup"><span data-stu-id="01746-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="01746-336">Вы увидите **дочерний** объект под ним под названием **газебуттон**.</span><span class="sxs-lookup"><span data-stu-id="01746-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="01746-337">Это будет использоваться для изменения сцен и, таким как, видео.</span><span class="sxs-lookup"><span data-stu-id="01746-337">This will be used to change scenes and thus videos.</span></span>

    ![Импорт пакета Unity Инсидеаутсфере](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="01746-339">В окне инспектора щелкните компонент преобразования **инсидеаутсфере**, убедитесь, что установлены следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="01746-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="01746-340">TRANSFORM-ПОЗИЦИОНИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="01746-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="01746-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="01746-341">**X** 0</span></span>  |          <span data-ttu-id="01746-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="01746-342">**Y** 0</span></span>          |  <span data-ttu-id="01746-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="01746-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="01746-344">ПОВОРОТ ПРЕОБРАЗОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="01746-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="01746-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="01746-345">**X** 0</span></span>  |          <span data-ttu-id="01746-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="01746-346">**Y** -50</span></span>        |  <span data-ttu-id="01746-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="01746-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="01746-348">ПРЕОБРАЗОВАНИЕ — МАСШТАБИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="01746-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="01746-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="01746-349">**X** 1</span></span>   |          <span data-ttu-id="01746-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="01746-350">**Y** 1</span></span>          |  <span data-ttu-id="01746-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="01746-351">**Z** 1</span></span>  |

    ![Импорт пакета Unity Инсидеаутсфере](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="01746-353">Щелкните дочерний объект **газебуттон** и задайте его **Преобразование** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="01746-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="01746-354">TRANSFORM-ПОЗИЦИОНИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="01746-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="01746-355">**X** 3,6</span><span class="sxs-lookup"><span data-stu-id="01746-355">**X** 3.6</span></span>|          <span data-ttu-id="01746-356">**Y** 1,3</span><span class="sxs-lookup"><span data-stu-id="01746-356">**Y** 1.3</span></span>        |  <span data-ttu-id="01746-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="01746-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="01746-358">ПОВОРОТ ПРЕОБРАЗОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="01746-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="01746-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="01746-359">**X** 0</span></span>  |          <span data-ttu-id="01746-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="01746-360">**Y** 0</span></span>          |  <span data-ttu-id="01746-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="01746-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="01746-362">ПРЕОБРАЗОВАНИЕ — МАСШТАБИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="01746-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="01746-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="01746-363">**X** 1</span></span>   |          <span data-ttu-id="01746-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="01746-364">**Y** 1</span></span>          |  <span data-ttu-id="01746-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="01746-365">**Z** 1</span></span>  |

    ![Импорт пакета Unity Инсидеаутсфере](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="01746-367">Глава 5. Создание класса видеоконтроллер</span><span class="sxs-lookup"><span data-stu-id="01746-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="01746-368">Класс **Видеоконтроллер** содержит две конечные точки видео, которые будут использоваться для потоковой передачи содержимого из службы мультимедиа Azure.</span><span class="sxs-lookup"><span data-stu-id="01746-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="01746-369">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="01746-369">To create this class:</span></span>

1.  <span data-ttu-id="01746-370">Щелкните правой кнопкой мыши **папку Asset**, расположенную на панели **проект** , и выберите пункт **Создать > папку**.</span><span class="sxs-lookup"><span data-stu-id="01746-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="01746-371">Назовите папку **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="01746-371">Name the folder **Scripts**.</span></span>

    ![Создание класса видеоконтроллер](images/AzureLabs-Lab6-43.png)

    ![Создание класса видеоконтроллер](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="01746-374">Дважды щелкните папку **Scripts** , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="01746-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="01746-375">Щелкните правой кнопкой мыши внутри папки, а затем выберите **Create > C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="01746-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="01746-376">Назовите сценарий **Видеоконтроллер**.</span><span class="sxs-lookup"><span data-stu-id="01746-376">Name the script **VideoController**.</span></span>

    ![Создание класса видеоконтроллер](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="01746-378">Дважды щелкните новый скрипт **Видеоконтроллер** , чтобы открыть его в **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="01746-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Создание класса видеоконтроллер](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="01746-380">Обновите пространства имен в верхней части файла кода следующим образом:</span><span class="sxs-lookup"><span data-stu-id="01746-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="01746-381">Введите следующие переменные в класс **Видеоконтроллер** вместе с методом **спящего режима ()** :</span><span class="sxs-lookup"><span data-stu-id="01746-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

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

7.  <span data-ttu-id="01746-382">Теперь пора ввести конечные точки из видео службы мультимедиа Azure:</span><span class="sxs-lookup"><span data-stu-id="01746-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="01746-383">Первый объект в переменной *video1endpoint* .</span><span class="sxs-lookup"><span data-stu-id="01746-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="01746-384">Второй объект в переменной *video2endpoint* .</span><span class="sxs-lookup"><span data-stu-id="01746-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="01746-385">Существует известная ошибка, связанная с использованием *протокола HTTPS* в Unity с версией 2017.4.1 F1.</span><span class="sxs-lookup"><span data-stu-id="01746-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="01746-386">Если видео выдает ошибку при воспроизведении, попробуйте использовать вместо него "http".</span><span class="sxs-lookup"><span data-stu-id="01746-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="01746-387">Затем необходимо изменить метод **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="01746-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="01746-388">Этот метод будет запускаться каждый раз, когда пользователь переключает сцену (в результате переключается видео) с помощью кнопки "Взгляните".</span><span class="sxs-lookup"><span data-stu-id="01746-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="01746-389">После метода **Start ()** вставьте метод **PlayVideo ()** *IEnumerator* , который будет использоваться для легкого запуска видео (Поэтому перебои не отображается).</span><span class="sxs-lookup"><span data-stu-id="01746-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

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

10. <span data-ttu-id="01746-390">Последний метод, необходимый для этого класса, — это метод **чанжесцене ()** , который будет использоваться для переключения между сценами.</span><span class="sxs-lookup"><span data-stu-id="01746-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="01746-391">Метод **чанжесцене ()** использует удобную функцию C\#, называемую *условным оператором*.</span><span class="sxs-lookup"><span data-stu-id="01746-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="01746-392">Это позволяет проверять условия, а затем значения, возвращаемые в зависимости от результата проверки, в пределах одной инструкции.</span><span class="sxs-lookup"><span data-stu-id="01746-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="01746-393">[Чтобы узнать больше об условном операторе](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator), перейдите по этой ссылке.</span><span class="sxs-lookup"><span data-stu-id="01746-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="01746-394">Сохраните изменения в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="01746-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="01746-395">В редакторе Unity щелкните и перетащите класс **Видеоконтроллер** [from] {. подчеркнутый} в папку **Scripts** для **основного объекта Camera** на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="01746-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="01746-396">Щелкните **основную камеру** и посмотрите на **Панель инспектора**.</span><span class="sxs-lookup"><span data-stu-id="01746-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="01746-397">Вы заметите, что в вновь добавленном компоненте скрипта есть поле с пустым значением.</span><span class="sxs-lookup"><span data-stu-id="01746-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="01746-398">Это ссылочное поле, которое предназначено для открытых переменных в коде.</span><span class="sxs-lookup"><span data-stu-id="01746-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="01746-399">Перетащите объект **инсидеаутсфере** с **панели Иерархия** в область **Сфера** , как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="01746-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="01746-400">![создать класс видеоконтроллер](images/AzureLabs-Lab6-47.png)
    ![создать класс видеоконтроллер](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="01746-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="01746-401">Глава 6. Создание класса «взгляд»</span><span class="sxs-lookup"><span data-stu-id="01746-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="01746-402">Этот класс отвечает за создание **райкаст** , который будет проецирован вперед с **основной камеры**для определения объекта, на котором пользователь смотрит.</span><span class="sxs-lookup"><span data-stu-id="01746-402">This class is responsible for creating a **Raycast** that will be projected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="01746-403">В этом случае **райкаст** потребуется выяснить, просматривает ли пользователь объект **газебуттон** в сцене и инициирует поведение.</span><span class="sxs-lookup"><span data-stu-id="01746-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="01746-404">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="01746-404">To create this Class:</span></span>

1.  <span data-ttu-id="01746-405">Перейдите к созданной ранее папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="01746-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="01746-406">Щелкните правой кнопкой мыши на панели **проекта** , \**Create* \* C\# сценарий \* \*.</span><span class="sxs-lookup"><span data-stu-id="01746-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="01746-407">Присвойте скрипту имя « **взгляд**».</span><span class="sxs-lookup"><span data-stu-id="01746-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="01746-408">Дважды щелкните новый скрипт " ***Взгляните*** ", чтобы открыть его в **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="01746-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="01746-409">Убедитесь, что в начале скрипта находится следующее пространство имен, и удалите все остальные:</span><span class="sxs-lookup"><span data-stu-id="01746-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="01746-410">Затем добавьте следующие переменные в класс **Взгляните** :</span><span class="sxs-lookup"><span data-stu-id="01746-410">Then add the following variables inside the **Gaze** class:</span></span>

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

6.  <span data-ttu-id="01746-411">Теперь необходимо добавить код для методов **спящего режима ()** и **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="01746-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="01746-412">Добавьте следующий код в метод **Update ()** для проецирования райкаст и обнаружения попадания целевого объекта:</span><span class="sxs-lookup"><span data-stu-id="01746-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

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

8.  <span data-ttu-id="01746-413">Сохраните изменения в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="01746-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="01746-414">Щелкните и **Перетащите класс «указатель» из** папки «скрипты» в основной объект Camera на панели « **Иерархия** ».</span><span class="sxs-lookup"><span data-stu-id="01746-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="01746-415">Глава 7. Настройка двух сцен Unity</span><span class="sxs-lookup"><span data-stu-id="01746-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="01746-416">Целью этой главы является настройка двух сцен, каждый из которых размещает видео в потоке.</span><span class="sxs-lookup"><span data-stu-id="01746-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="01746-417">Вы создадите уже созданную сцену, поэтому вам больше не нужно настраивать ее, хотя вы измените новую сцену, чтобы объект *газебуттон* настроился в другом расположении и имел другой внешний вид.</span><span class="sxs-lookup"><span data-stu-id="01746-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="01746-418">Это показывает, как изменить между сценами.</span><span class="sxs-lookup"><span data-stu-id="01746-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="01746-419">Для этого перейдите в **файл > сохранить сцену как...** . Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="01746-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="01746-420">Нажмите кнопку **создать папку** .</span><span class="sxs-lookup"><span data-stu-id="01746-420">Click the **New folder** button.</span></span>

    ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="01746-422">Присвойте папке имя " **сцены**".</span><span class="sxs-lookup"><span data-stu-id="01746-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="01746-423">Окно **сохранить сцену** по-прежнему будет открыто.</span><span class="sxs-lookup"><span data-stu-id="01746-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="01746-424">Откройте только что созданную папку **сцен** .</span><span class="sxs-lookup"><span data-stu-id="01746-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="01746-425">В текстовом поле **имя файла** введите **VideoScene1**, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="01746-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="01746-426">Вернувшись в Unity, откройте папку **сцены** и щелкните файл **VideoScene1** левой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="01746-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="01746-427">Используйте клавиатуру и нажмите клавиши **CTRL + D** , чтобы дублировать сцену</span><span class="sxs-lookup"><span data-stu-id="01746-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="01746-428">**Повторяющуюся** команду также можно выполнить, перейдя в **Edit > дублировать**.</span><span class="sxs-lookup"><span data-stu-id="01746-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="01746-429">Unity автоматически увеличит номер названия сцены, но проверьте его все равно, чтобы убедиться, что он соответствует ранее вставленному коду.</span><span class="sxs-lookup"><span data-stu-id="01746-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="01746-430">У вас должны быть **VideoScene1** и **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="01746-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="01746-431">В двух сценах перейдите в раздел **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="01746-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="01746-432">Открыв окно **параметры сборки** , перетащите фоновый кадр в раздел **сцены в сборке** .</span><span class="sxs-lookup"><span data-stu-id="01746-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="01746-434">Вы можете выбрать оба монтажных кадра из папки « **сцены** », удерживая нажатой **клавишу CTRL** , а затем выделив каждую из них левой кнопкой мыши, и, наконец, перетащите обе эти сцены.</span><span class="sxs-lookup"><span data-stu-id="01746-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="01746-435">Закройте окно " **параметры сборки** " и дважды щелкните **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="01746-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="01746-436">После открытия второй сцены щелкните дочерний объект **газебуттон** объекта **инсидеаутсфере**и задайте его преобразование следующим образом:</span><span class="sxs-lookup"><span data-stu-id="01746-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="01746-437">TRANSFORM-ПОЗИЦИОНИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="01746-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="01746-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="01746-438">**X** 0</span></span>  |         <span data-ttu-id="01746-439">**Y** 1,3</span><span class="sxs-lookup"><span data-stu-id="01746-439">**Y** 1.3</span></span>         | <span data-ttu-id="01746-440">**Z** 3,6</span><span class="sxs-lookup"><span data-stu-id="01746-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="01746-441">ПОВОРОТ ПРЕОБРАЗОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="01746-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="01746-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="01746-442">**X** 0</span></span>  |          <span data-ttu-id="01746-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="01746-443">**Y** 0</span></span>          |  <span data-ttu-id="01746-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="01746-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="01746-445">ПРЕОБРАЗОВАНИЕ — МАСШТАБИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="01746-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="01746-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="01746-446">**X** 1</span></span>   |          <span data-ttu-id="01746-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="01746-447">**Y** 1</span></span>          |  <span data-ttu-id="01746-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="01746-448">**Z** 1</span></span>  |

10. <span data-ttu-id="01746-449">Если дочерний элемент **газебуттон** все еще выбран, Взгляните на **инспектор** и **Фильтр сетки**.</span><span class="sxs-lookup"><span data-stu-id="01746-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="01746-450">Щелкните небольшое целевое поле рядом с полем ссылка на **сетку** :</span><span class="sxs-lookup"><span data-stu-id="01746-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="01746-452">Появится всплывающее окно **Выбор сетки** .</span><span class="sxs-lookup"><span data-stu-id="01746-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="01746-453">Дважды щелкните сетку **куба** в списке **ресурсов**.</span><span class="sxs-lookup"><span data-stu-id="01746-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="01746-455">**Фильтр сетки** будет обновлен и теперь станет **кубом**.</span><span class="sxs-lookup"><span data-stu-id="01746-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="01746-456">Теперь щелкните значок **шестеренки** рядом с полем " **Сфера** ", а затем щелкните **удалить компонент**, чтобы удалить его из этого объекта.</span><span class="sxs-lookup"><span data-stu-id="01746-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="01746-458">Выбрав **газебуттон** , нажмите кнопку **Добавить компонент** в нижней части **инспектора**.</span><span class="sxs-lookup"><span data-stu-id="01746-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="01746-459">В поле поиска введите **Box**, а в поле " **конфликт"** будет выбран параметр, чтобы добавить в объект **газебуттон** **рамку** .</span><span class="sxs-lookup"><span data-stu-id="01746-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="01746-461">**Газебуттон** теперь частично обновляется, чтобы выглядеть иначе, вы создадите новый **материал**, чтобы он полностью отличался, и проще распознать его как другой объект, чем объект в первой сцене.</span><span class="sxs-lookup"><span data-stu-id="01746-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="01746-462">Перейдите в папку « **материалы** » на **панели «проект»** .</span><span class="sxs-lookup"><span data-stu-id="01746-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="01746-463">Дублировать материал **буттонматериал** (нажмите клавиши **CTRL** + **D** на клавиатуре или **щелкните его левой кнопкой мыши, а**затем в меню **изменить** файл выберите **дублировать**).</span><span class="sxs-lookup"><span data-stu-id="01746-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="01746-464">![главе 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-55.png)
    ![главе 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="01746-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="01746-465">Выберите новый материал **буттонматериал** (под названием **буттонматериал 1**) и в **инспекторе**щелкните окно цвета **албедо** .</span><span class="sxs-lookup"><span data-stu-id="01746-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="01746-466">Появится всплывающее окно, где можно выбрать другой цвет (выберите любой из них), а затем закрыть всплывающее окно.</span><span class="sxs-lookup"><span data-stu-id="01746-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="01746-467">Материал будет его собственным экземпляром и отличаться от исходного.</span><span class="sxs-lookup"><span data-stu-id="01746-467">The Material will be its own instance, and different to the original.</span></span>

    ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="01746-469">Перетащите новый **материал** на дочерний элемент **газебуттон** , чтобы полностью обновить его внешний вид, чтобы его можно было легко отличать от первой кнопки сцены.</span><span class="sxs-lookup"><span data-stu-id="01746-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="01746-471">На этом этапе можно протестировать проект в редакторе перед созданием проекта UWP.</span><span class="sxs-lookup"><span data-stu-id="01746-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="01746-472">Нажмите кнопку **Воспроизведение** в **редакторе** и обменяйте гарнитуру.</span><span class="sxs-lookup"><span data-stu-id="01746-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Глава 7. Настройка двух сцен Unity](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="01746-474">Взгляните на два объекта **газебуттон** для переключения между первым и вторым видео.</span><span class="sxs-lookup"><span data-stu-id="01746-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="01746-475">Глава 8. Создание решения UWP</span><span class="sxs-lookup"><span data-stu-id="01746-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="01746-476">После проверки того, что в редакторе нет ошибок, можно приступать к сборке.</span><span class="sxs-lookup"><span data-stu-id="01746-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="01746-477">Для сборки:</span><span class="sxs-lookup"><span data-stu-id="01746-477">To Build:</span></span>

1.  <span data-ttu-id="01746-478">Сохраните текущую сцену, щелкнув **файл > сохранить**.</span><span class="sxs-lookup"><span data-stu-id="01746-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="01746-479">Установите флажок **проекты с именем Unity C\#** (это важно, так как он позволит изменять классы после завершения сборки).</span><span class="sxs-lookup"><span data-stu-id="01746-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="01746-480">Последовательно выберите **файл > параметры сборки**, щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="01746-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="01746-481">Вам будет предложено выбрать папку, в которой нужно построить решение.</span><span class="sxs-lookup"><span data-stu-id="01746-481">You will be prompted to select the folder where you want to build the Solution.</span></span>

5.  <span data-ttu-id="01746-482">Создайте папку **Builds** и в этой папке создайте другую папку с соответствующим именем по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="01746-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="01746-483">Щелкните новую папку, а затем выберите пункт **выбрать папку**, чтобы выбрать эту папку, чтобы начать сборку в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="01746-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="01746-484">![главе 8-Создание решения UWP](images/AzureLabs-Lab6-60.png)
    ![главе 8 — Создание решения UWP](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="01746-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="01746-485">После завершения сборки Unity (может занять некоторое время) он откроет окно **проводника** в расположении сборки.</span><span class="sxs-lookup"><span data-stu-id="01746-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="01746-486">Глава 9. развертывание на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="01746-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="01746-487">После завершения сборки в расположение сборки появится окно **проводника файлов** .</span><span class="sxs-lookup"><span data-stu-id="01746-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="01746-488">Откройте папку с именем и построением, а затем дважды щелкните файл решения (SLN) в этой папке, чтобы открыть решение с помощью Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="01746-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="01746-489">Осталось всего лишь развернуть приложение на компьютере (или на *локальном компьютере*).</span><span class="sxs-lookup"><span data-stu-id="01746-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="01746-490">Чтобы выполнить развертывание на локальном компьютере, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="01746-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="01746-491">В **Visual Studio 2017**откройте только что созданный файл решения.</span><span class="sxs-lookup"><span data-stu-id="01746-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="01746-492">На **платформе решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="01746-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="01746-493">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="01746-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Глава 9--развертывание на локальном компьютере](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="01746-495">Теперь необходимо восстановить все пакеты в решении.</span><span class="sxs-lookup"><span data-stu-id="01746-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="01746-496">Щелкните **решение**правой кнопкой мыши и выберите команду **восстановить пакеты NuGet для решения...**</span><span class="sxs-lookup"><span data-stu-id="01746-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="01746-497">Это делается потому, что пакеты, для которых построен Unity должен быть предназначен для работы со ссылками на локальные компьютеры.</span><span class="sxs-lookup"><span data-stu-id="01746-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="01746-498">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютере.</span><span class="sxs-lookup"><span data-stu-id="01746-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="01746-499">Visual Studio сначала построит и развернет приложение.</span><span class="sxs-lookup"><span data-stu-id="01746-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="01746-500">Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску.</span><span class="sxs-lookup"><span data-stu-id="01746-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Глава 9--развертывание на локальном компьютере](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="01746-502">При запуске приложения Mixed Reality вы будете находиться в модели **инсидеаутсфере** , используемой в приложении.</span><span class="sxs-lookup"><span data-stu-id="01746-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="01746-503">Эта сфера будет использоваться для потоковой передачи видео, предоставляя представление в 360 градусов для входящего видео (которое было на пленке для этого типа перспективы).</span><span class="sxs-lookup"><span data-stu-id="01746-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="01746-504">Не удивит, если видео занимает несколько секунд для загрузки, ваше приложение зависит от доступной скорости Интернета, так как требуется получить и загрузить видео, чтобы выполнить потоковую передачу в приложение.</span><span class="sxs-lookup"><span data-stu-id="01746-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="01746-505">Когда вы будете готовы, измените сцены и откройте второе видео, облаками на красную шар!</span><span class="sxs-lookup"><span data-stu-id="01746-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="01746-506">Затем вы можете вернуться назад, используя синий куб во второй сцене!</span><span class="sxs-lookup"><span data-stu-id="01746-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="01746-507">Законченное приложение службы мультимедиа Azure</span><span class="sxs-lookup"><span data-stu-id="01746-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="01746-508">Поздравляем! вы создали приложение смешанной реальности, которое использует службу мультимедиа Azure для потоковой передачи видео 360.</span><span class="sxs-lookup"><span data-stu-id="01746-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![результат лаборатории](images/AzureLabs-Lab6-00.png)

![результат лаборатории](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="01746-511">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="01746-511">Bonus Exercises</span></span>

<span data-ttu-id="01746-512">**Упражнение 1**</span><span class="sxs-lookup"><span data-stu-id="01746-512">**Exercise 1**</span></span>

<span data-ttu-id="01746-513">Для изменения видео в рамках этого руководства можно использовать только одну сцену.</span><span class="sxs-lookup"><span data-stu-id="01746-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="01746-514">Поэкспериментируйте с приложением и сделайте его одним монтажным кадром!</span><span class="sxs-lookup"><span data-stu-id="01746-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="01746-515">Возможно, даже добавить еще одно видео в набор.</span><span class="sxs-lookup"><span data-stu-id="01746-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="01746-516">**Упражнение 2**</span><span class="sxs-lookup"><span data-stu-id="01746-516">**Exercise 2**</span></span>

<span data-ttu-id="01746-517">Поэкспериментируйте с Azure и Unity и попытайтесь реализовать возможность приложения автоматически выбирать видео с другим размером файла в зависимости от надежности подключения к Интернету.</span><span class="sxs-lookup"><span data-stu-id="01746-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


