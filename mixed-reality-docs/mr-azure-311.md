---
title: MR и Azure 311 — Microsoft Graph
description: Пройдите этот курс, чтобы узнать, как использовать Microsoft Graph и подключиться к данным, которые повышают производительность, в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, Microsoft Graph, hololens, иммерсивное, VR
ms.openlocfilehash: 775971c4e4289d2dc963dfa2bf033192d9f3489e
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047206"
---
>[!NOTE]
><span data-ttu-id="e193f-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e193f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e193f-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="e193f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e193f-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e193f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e193f-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="e193f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e193f-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e193f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e193f-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="e193f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="e193f-110">MR и Azure 311 — Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="e193f-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="e193f-111">В этом курсе вы узнаете, как использовать *Microsoft Graph* для входа в учетная запись Майкрософт с помощью безопасной проверки подлинности в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e193f-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="e193f-112">Затем вы получите и отобразите запланированные собрания в интерфейсе приложения.</span><span class="sxs-lookup"><span data-stu-id="e193f-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="e193f-113">*Microsoft Graph* — это набор интерфейсов API, предназначенных для обеспечения доступа ко многим службам Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="e193f-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="e193f-114">Корпорация Майкрософт описывает Microsoft Graph как матрица ресурсов, Соединенных связями, то есть позволяет приложению получать доступ ко всем данным о подключенных пользователях.</span><span class="sxs-lookup"><span data-stu-id="e193f-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="e193f-115">Дополнительные сведения см. на [странице Microsoft Graph](https://developer.microsoft.com/graph).</span><span class="sxs-lookup"><span data-stu-id="e193f-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="e193f-116">Разработка будет включать в себя создание приложения, в котором пользователю будет предложено Взгляните на сферу, а затем коснуться сферы, которая предложит пользователю безопасно войти в учетная запись Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="e193f-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="e193f-117">После входа в учетную запись пользователь увидит список собраний, запланированных на данный день.</span><span class="sxs-lookup"><span data-stu-id="e193f-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="e193f-118">Прополнив этот курс, вы получите приложение HoloLens для смешанной реальности, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="e193f-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="e193f-119">С помощью жеста TAP Коснитесь объекта, который предложит пользователю войти в учетную запись Майкрософт (выход из приложения для входа в систему, а затем снова вернуться в приложение).</span><span class="sxs-lookup"><span data-stu-id="e193f-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="e193f-120">Просмотр списка собраний, запланированных на данный день.</span><span class="sxs-lookup"><span data-stu-id="e193f-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="e193f-121">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="e193f-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="e193f-122">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="e193f-123">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e193f-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="e193f-124">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="e193f-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e193f-125">Хождение</span><span class="sxs-lookup"><span data-stu-id="e193f-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e193f-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e193f-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e193f-127"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="e193f-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e193f-128">MR и Azure 311: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="e193f-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="e193f-129">✔️</span><span class="sxs-lookup"><span data-stu-id="e193f-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="e193f-130">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="e193f-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="e193f-131">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="e193f-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="e193f-132">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018).</span><span class="sxs-lookup"><span data-stu-id="e193f-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="e193f-133">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="e193f-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="e193f-134">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="e193f-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="e193f-135">ПК для разработки</span><span class="sxs-lookup"><span data-stu-id="e193f-135">A development PC</span></span>
- [<span data-ttu-id="e193f-136">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="e193f-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e193f-137">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="e193f-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e193f-138">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="e193f-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e193f-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e193f-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="e193f-140">[Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="e193f-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="e193f-141">Доступ к Интернету для установки Azure и Microsoft Graph получение данных</span><span class="sxs-lookup"><span data-stu-id="e193f-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="e193f-142">Допустимая **учетная запись Майкрософт** (личная или рабочая или учебная)</span><span class="sxs-lookup"><span data-stu-id="e193f-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="e193f-143">Несколько собраний, запланированных на текущий день, с использованием той же учетной записи Майкрософт</span><span class="sxs-lookup"><span data-stu-id="e193f-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="e193f-144">Перед началом</span><span class="sxs-lookup"><span data-stu-id="e193f-144">Before you start</span></span>

1.  <span data-ttu-id="e193f-145">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="e193f-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="e193f-146">Настройка и тестирование HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e193f-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="e193f-147">Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="e193f-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="e193f-148">Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="e193f-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="e193f-149">Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="e193f-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="e193f-150">Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="e193f-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="e193f-151">Глава 1. Создание приложения на портале регистрации приложений</span><span class="sxs-lookup"><span data-stu-id="e193f-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="e193f-152">Для начала вам потребуется создать и зарегистрировать приложение на **портале регистрации приложений**.</span><span class="sxs-lookup"><span data-stu-id="e193f-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="e193f-153">В этой главе вы также найдете ключ службы, который позволит выполнять вызовы *Microsoft Graph* для доступа к содержимому вашей учетной записи.</span><span class="sxs-lookup"><span data-stu-id="e193f-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="e193f-154">Перейдите на [портал регистрации приложений Майкрософт](https://apps.dev.microsoft.com) и войдите с помощью учетной записи Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="e193f-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="e193f-155">После входа вы будете перенаправлены на **портал регистрации приложений**.</span><span class="sxs-lookup"><span data-stu-id="e193f-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="e193f-156">В разделе **Мои приложения** нажмите кнопку **Добавить приложение**.</span><span class="sxs-lookup"><span data-stu-id="e193f-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="e193f-157">**Портал регистрации приложений** может выглядеть по-разному в зависимости от того, работал ли ранее *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="e193f-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="e193f-158">На следующих снимках экрана показаны эти различные версии.</span><span class="sxs-lookup"><span data-stu-id="e193f-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="e193f-159">Добавьте имя приложения и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="e193f-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="e193f-160">После создания приложения вы будете перенаправлены на главную страницу приложения.</span><span class="sxs-lookup"><span data-stu-id="e193f-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="e193f-161">Скопируйте **идентификатор приложения** и запишите это значение в безопасном месте, вы будете использовать его вскоре в своем коде.</span><span class="sxs-lookup"><span data-stu-id="e193f-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="e193f-162">В разделе **платформы** убедитесь, что отображается **собственное приложение** .</span><span class="sxs-lookup"><span data-stu-id="e193f-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="e193f-163">Если *не* щелкнуть **Добавить платформу** и выбрать **собственное приложение**.</span><span class="sxs-lookup"><span data-stu-id="e193f-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="e193f-164">Прокрутите вниз на той же странице и в разделе, который называется **Microsoft Graph** разрешениями, необходимо добавить дополнительные разрешения для приложения.</span><span class="sxs-lookup"><span data-stu-id="e193f-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="e193f-165">Щелкните **Добавить** рядом с **делегированными**разрешениями.</span><span class="sxs-lookup"><span data-stu-id="e193f-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="e193f-166">Так как вы хотите, чтобы приложение поменяло доступ к календарю пользователя, установите флажок **календари. чтение** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="e193f-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="e193f-167">Прокрутите вниз и нажмите кнопку **сохранить** .</span><span class="sxs-lookup"><span data-stu-id="e193f-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="e193f-168">Сохранение будет подтверждено, и вы можете выйти из **портала регистрации приложений**.</span><span class="sxs-lookup"><span data-stu-id="e193f-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="e193f-169">Глава 2. Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="e193f-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="e193f-170">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="e193f-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="e193f-171">Откройте *Unity* и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="e193f-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="e193f-172">Необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="e193f-173">Вставьте **мсграфмр**.</span><span class="sxs-lookup"><span data-stu-id="e193f-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="e193f-174">Убедитесь, что для шаблона проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="e193f-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="e193f-175">Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="e193f-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="e193f-176">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="e193f-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="e193f-177">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="e193f-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="e193f-178">Перейдите к разделу **изменение** > **настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="e193f-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="e193f-179">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="e193f-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="e193f-180">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="e193f-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="e193f-181">Перейдите в раздел**параметры сборки** **файлов** > и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.</span><span class="sxs-lookup"><span data-stu-id="e193f-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="e193f-182">Несмотря на то, что все еще находятся в**параметрах сборки** **файлов** > , убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="e193f-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="e193f-183">**Целевое устройство** имеет значение **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e193f-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="e193f-184">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="e193f-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="e193f-185">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="e193f-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="e193f-186">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="e193f-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="e193f-187">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="e193f-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="e193f-188">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="e193f-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="e193f-189">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="e193f-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="e193f-190">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="e193f-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="e193f-191">Создайте новую папку для этой и любой будущей сцены.</span><span class="sxs-lookup"><span data-stu-id="e193f-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="e193f-192">Нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="e193f-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="e193f-193">Откройте только что созданную папку **сцены** , а затем в поле *имя файла*: введите **MR_ComputerVisionScene**, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="e193f-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="e193f-194">Помните, что сцены Unity необходимо сохранять в папке Assets , так как они должны быть связаны с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="e193f-195">Создание папки «сцены» (и других аналогичных папок) — типичный способ структуризации проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="e193f-196">Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e193f-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="e193f-197">В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .</span><span class="sxs-lookup"><span data-stu-id="e193f-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="e193f-198">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="e193f-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="e193f-199">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e193f-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="e193f-200">**Создание сценариев** **Версия среды выполнения** должна быть экспериментальной (эквивалент .NET 4,6), что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="e193f-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="e193f-201">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="e193f-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="e193f-202">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="e193f-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="e193f-203">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="e193f-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="e193f-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="e193f-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="e193f-205">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**) Проверьте, **поддерживается**ли **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="e193f-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="e193f-206">Вернувшись в *параметры сборки*, *проекты C# Unity* больше не заключаются. Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="e193f-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="e193f-207">Закройте окно *параметры сборки* .</span><span class="sxs-lookup"><span data-stu-id="e193f-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="e193f-208">Сохраните сцену и проект (**файл** > **сохранить сцены/файл** > **сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="e193f-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="e193f-209">Глава 3. импорт библиотек в Unity</span><span class="sxs-lookup"><span data-stu-id="e193f-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e193f-210">Если вы хотите пропустить компонент *установки Unity* , установленный в этом курсе, и продолжить работу с кодом, скачайте этот [Azure-MR-311. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в [главе 5 ](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="e193f-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="e193f-211">Чтобы использовать *Microsoft Graph* в Unity, необходимо использовать библиотеку DLL **Microsoft. Identity. Client** .</span><span class="sxs-lookup"><span data-stu-id="e193f-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="e193f-212">Можно использовать пакет SDK для Microsoft Graph, однако после сборки проекта Unity потребуется добавить пакет NuGet (то есть редактирует проект после сборки).</span><span class="sxs-lookup"><span data-stu-id="e193f-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="e193f-213">Проще импортировать необходимые библиотеки DLL непосредственно в Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="e193f-214">В Unity существует известная ошибка, которая требует перенастройки подключаемых модулей после импорта.</span><span class="sxs-lookup"><span data-stu-id="e193f-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="e193f-215">Эти действия (4-7 в этом разделе) больше не понадобятся после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="e193f-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="e193f-216">Чтобы импортировать *Microsoft Graph* в собственный проект, [скачайте файл MSGraph_LabPlugins. zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="e193f-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="e193f-217">Этот пакет был создан с использованием версий библиотек, которые были проверены.</span><span class="sxs-lookup"><span data-stu-id="e193f-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="e193f-218">Если вы хотите узнать больше о том, как добавить пользовательские библиотеки DLL в проект Unity, [перейдите по этой ссылке](https://docs.unity3d.com/Manual/UsingDLL.html).</span><span class="sxs-lookup"><span data-stu-id="e193f-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="e193f-219">Чтобы импортировать пакет, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e193f-219">To import the package:</span></span>

1.  <span data-ttu-id="e193f-220">Добавьте пакет Unity в Unity с помощью команды меню**настраиваемый пакет** **Импорт** >  **активов** > .</span><span class="sxs-lookup"><span data-stu-id="e193f-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="e193f-221">Выберите только что скачанный пакет.</span><span class="sxs-lookup"><span data-stu-id="e193f-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="e193f-222">В появившемся окне **Импорт пакета Unity** убедитесь, что выбраны все компоненты **подключаемых модулей** (включая).</span><span class="sxs-lookup"><span data-stu-id="e193f-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="e193f-223">Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="e193f-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="e193f-224">Перейдите в папку **мсграф** в разделе **подключаемые модули** на *панели проект* и выберите подключаемый модуль **Microsoft. Identity. Client**.</span><span class="sxs-lookup"><span data-stu-id="e193f-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="e193f-225">Выбрав *подключаемый модуль* , убедитесь, что **все платформы** не установлены, убедитесь, что флажок **всаплайер** также не установлен, а затем нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="e193f-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="e193f-226">Это необходимо только для того, чтобы убедиться, что файлы настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="e193f-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="e193f-227">Пометка этих подключаемых модулей настраивает их для использования только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="e193f-228">В папке WSA имеется другой набор библиотек DLL, который будет использоваться после экспорта проекта из Unity в качестве универсального приложения Windows.</span><span class="sxs-lookup"><span data-stu-id="e193f-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="e193f-229">Далее необходимо открыть папку **WSA** в папке **мсграф**</span><span class="sxs-lookup"><span data-stu-id="e193f-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="e193f-230">Вы увидите копию того же файла, который вы только что настроили.</span><span class="sxs-lookup"><span data-stu-id="e193f-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="e193f-231">Выберите файл, а затем в инспекторе:</span><span class="sxs-lookup"><span data-stu-id="e193f-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="e193f-232">Убедитесь, что **все платформы** не **установлены и установлен** **флажок** **только** **всаплайер** .</span><span class="sxs-lookup"><span data-stu-id="e193f-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="e193f-233">Убедитесь, что **пакет SDK** имеет значение **UWP**, а для **серверной части скрипта** задано значение **net** .</span><span class="sxs-lookup"><span data-stu-id="e193f-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="e193f-234">Убедитесь, что флажок **не обрабатывать** **установлен**.</span><span class="sxs-lookup"><span data-stu-id="e193f-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="e193f-235">Щелкните **Применить**.</span><span class="sxs-lookup"><span data-stu-id="e193f-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="e193f-236">Глава 4. Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="e193f-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="e193f-237">В этой главе вы настроите основную камеру для сцены:</span><span class="sxs-lookup"><span data-stu-id="e193f-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="e193f-238">На *панели Иерархия*выберите **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="e193f-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="e193f-239">После выбора вы сможете увидеть все компоненты **основной камеры** на панели *инспектора* .</span><span class="sxs-lookup"><span data-stu-id="e193f-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="e193f-240">**Объект Camera** должен называться **основной камерой** (Обратите внимание на орфографию!)</span><span class="sxs-lookup"><span data-stu-id="e193f-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="e193f-241">Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на правописание).</span><span class="sxs-lookup"><span data-stu-id="e193f-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="e193f-242">Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .</span><span class="sxs-lookup"><span data-stu-id="e193f-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="e193f-243">Установить для чистых флагов **сплошной цвет**</span><span class="sxs-lookup"><span data-stu-id="e193f-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="e193f-244">Установить черный **цвет фона** для компонента камеры **, альфа 0** **(шестнадцатеричный код: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="e193f-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="e193f-245">Итоговая структура объектов на *панели Иерархия* должна выглядеть так, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="e193f-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="e193f-246">Глава 5. Создание класса Митингсуи</span><span class="sxs-lookup"><span data-stu-id="e193f-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="e193f-247">Первый сценарий, который необходимо создать, — это **митингсуи**, который отвечает за размещение и заполнение пользовательского интерфейса приложения (приветственное сообщение, инструкции и сведения о собраниях).</span><span class="sxs-lookup"><span data-stu-id="e193f-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="e193f-248">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="e193f-248">To create this class:</span></span>

1.  <span data-ttu-id="e193f-249">Щелкните правой кнопкой мыши папку **Assets** на *панели проект*, а затем выберите **создать** > **папку**.</span><span class="sxs-lookup"><span data-stu-id="e193f-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="e193f-250">Назовите папку **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="e193f-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="e193f-251">Откройте папку **Scripts** , а затем в этой папке щелкните правой кнопкой мыши, **Создайте**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="e193f-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="e193f-252">Назовите сценарий **митингсуи.**</span><span class="sxs-lookup"><span data-stu-id="e193f-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="e193f-253">Дважды щелкните новый скрипт **митингсуи** , чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="e193f-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="e193f-254">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="e193f-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="e193f-255">Внутри класса вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="e193f-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="e193f-256">Затем замените метод **Start ()** и добавьте метод спящего режима **()** .</span><span class="sxs-lookup"><span data-stu-id="e193f-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="e193f-257">Они будут вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="e193f-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="e193f-258">Добавьте методы, отвечающие за создание *пользовательского интерфейса совещаний* , и заполните его текущими собраниями по запросу:</span><span class="sxs-lookup"><span data-stu-id="e193f-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="e193f-259">**Удалите** метод **Update ()** и **Сохраните изменения** в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="e193f-260">Глава 6. Создание класса Graph</span><span class="sxs-lookup"><span data-stu-id="e193f-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="e193f-261">Следующий скрипт для создания — это сценарий **графа** .</span><span class="sxs-lookup"><span data-stu-id="e193f-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="e193f-262">Этот сценарий отвечает за выполнение вызовов для проверки подлинности пользователя и получение запланированных собраний за текущий день из календаря пользователя.</span><span class="sxs-lookup"><span data-stu-id="e193f-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="e193f-263">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="e193f-263">To create this class:</span></span>

1.  <span data-ttu-id="e193f-264">Дважды щелкните папку Scripts , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="e193f-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e193f-265">Щелкните правой кнопкой мыши внутри папки Scripts и выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="e193f-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e193f-266">Присвойте имя **графу**скрипта.</span><span class="sxs-lookup"><span data-stu-id="e193f-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="e193f-267">Дважды щелкните скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e193f-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="e193f-268">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="e193f-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="e193f-269">Обратите внимание, что части кода в этом скрипте заключены в оболочку для [директив предварительной компиляции](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html). Это позволяет избежать проблем с библиотеками при построении решения Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e193f-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="e193f-270">Удалите методы **Start ()** и **Update ()** , так как они не будут использоваться.</span><span class="sxs-lookup"><span data-stu-id="e193f-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="e193f-271">За пределами класса **Graph** вставьте следующие объекты, которые необходимы для десериализации объекта JSON, представляющего ежедневные запланированные собрания:</span><span class="sxs-lookup"><span data-stu-id="e193f-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="e193f-272">В классе **Graph** добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="e193f-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="e193f-273">Измените значение **AppID** , чтобы оно было **идентификатором приложения** , записанным в  **[главе 1](#chapter-1---create-your-app-in-the-application-registration-portal), шаг 4**.</span><span class="sxs-lookup"><span data-stu-id="e193f-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="e193f-274">Это значение должно совпадать со значением, отображаемым на **портале регистрации приложений** на странице регистрации приложения.</span><span class="sxs-lookup"><span data-stu-id="e193f-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="e193f-275">В классе **Graph** добавьте методы **сигнинасинк ()** и **акуиретокенасинк ()** , которые предложит пользователю вставить учетные данные для входа.</span><span class="sxs-lookup"><span data-stu-id="e193f-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="e193f-276">Добавьте следующие два метода:</span><span class="sxs-lookup"><span data-stu-id="e193f-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="e193f-277">**Буилдтодайкалендарендпоинт ()** , который создает URI, указывающий день, и интервал времени, в который извлекаются запланированные собрания.</span><span class="sxs-lookup"><span data-stu-id="e193f-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="e193f-278">**Листмитингсасинк ()** , которая запрашивает запланированные собрания *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="e193f-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="e193f-279">Вы завершили выполнение скрипта **Graph** .</span><span class="sxs-lookup"><span data-stu-id="e193f-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="e193f-280">**Сохраните изменения** в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="e193f-281">Глава 7. Создание скрипта Газеинпут</span><span class="sxs-lookup"><span data-stu-id="e193f-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="e193f-282">Теперь создадим **газеинпут**.</span><span class="sxs-lookup"><span data-stu-id="e193f-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="e193f-283">Этот класс обрабатывает и отслеживает взгляд пользователя, используя **райкаст** , поступающий от **основной камеры**, проецирование вперед.</span><span class="sxs-lookup"><span data-stu-id="e193f-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="e193f-284">Чтобы создать скрипт, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e193f-284">To create the script:</span></span>

1.  <span data-ttu-id="e193f-285">Дважды щелкните папку Scripts , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="e193f-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e193f-286">Щелкните правой кнопкой мыши внутри папки Scripts и выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="e193f-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e193f-287">Назовите сценарий **газеинпут**.</span><span class="sxs-lookup"><span data-stu-id="e193f-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="e193f-288">Дважды щелкните скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e193f-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="e193f-289">Измените код пространства имен, чтобы он соответствовал приведенному ниже, вместе с добавлением **\[тега System.\]Serializable**над классом **газеинпут** , чтобы его можно было сериализовать:</span><span class="sxs-lookup"><span data-stu-id="e193f-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="e193f-290">В классе **газеинпут** добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="e193f-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="e193f-291">Добавьте метод **креатекурсор ()** , чтобы создать курсор HoloLens в сцене, и вызовите метод из метода **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="e193f-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="e193f-292">Следующие методы позволяют Райкасту взгляда и отслеживание объектов с сортировкой.</span><span class="sxs-lookup"><span data-stu-id="e193f-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="e193f-293">**Сохраните изменения** в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="e193f-294">Глава 8. Создание класса взаимодействий</span><span class="sxs-lookup"><span data-stu-id="e193f-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="e193f-295">Теперь потребуется создать скрипт **взаимодействия** , который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="e193f-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="e193f-296">Обработка взаимодействия **касания** и **обзора камеры**, которая позволяет пользователю взаимодействовать с журналом "Кнопка" в сцене.</span><span class="sxs-lookup"><span data-stu-id="e193f-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="e193f-297">Создание входного объекта "Кнопка" в сцене для пользователя, с которым будет взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="e193f-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="e193f-298">Чтобы создать скрипт, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e193f-298">To create the script:</span></span>

1.  <span data-ttu-id="e193f-299">Дважды щелкните папку Scripts , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="e193f-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e193f-300">Щелкните правой кнопкой мыши внутри папки Scripts и выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="e193f-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e193f-301">Назовите скрипт **взаимодействия**.</span><span class="sxs-lookup"><span data-stu-id="e193f-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="e193f-302">Дважды щелкните скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e193f-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="e193f-303">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="e193f-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="e193f-304">Измените наследование класса **взаимодействия** , используя неизменное *поведение* , на **газеинпут**.</span><span class="sxs-lookup"><span data-stu-id="e193f-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="e193f-305">~~Взаимодействие с открытым классом: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="e193f-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="e193f-306">Внутри класса **взаимодействия** вставьте следующую переменную:</span><span class="sxs-lookup"><span data-stu-id="e193f-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="e193f-307">Замените метод **Start** ; Обратите внимание, что это метод переопределения, который вызывает метод класса взгляда Base.</span><span class="sxs-lookup"><span data-stu-id="e193f-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="e193f-308">**Start ()** будет вызываться при инициализации класса, регистрации для распознавания ввода и создании *кнопки* входа в сцене:</span><span class="sxs-lookup"><span data-stu-id="e193f-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="e193f-309">Добавьте метод **креатесигнинбуттон ()** , который создаст экземпляр *кнопки* входа в сцене и установит его свойства:</span><span class="sxs-lookup"><span data-stu-id="e193f-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="e193f-310">Добавьте метод **GestureRecognizer_Tapped ()** , отвечающий на событие *TAP* User.</span><span class="sxs-lookup"><span data-stu-id="e193f-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="e193f-311">**Удалите** метод **Update ()** , а затем **Сохраните изменения** в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="e193f-312">Глава 9. Настройка ссылок на скрипты</span><span class="sxs-lookup"><span data-stu-id="e193f-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="e193f-313">В этой главе необходимо разместить сценарий **взаимодействия** на **основной камере**.</span><span class="sxs-lookup"><span data-stu-id="e193f-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="e193f-314">Затем этот скрипт будет обрабатывать размещение других сценариев, где они должны быть.</span><span class="sxs-lookup"><span data-stu-id="e193f-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="e193f-315">В папке **скрипты** на *панели проект*перетащите диалоговые окна **взаимодействия** сценария в **основной объект Camera** , как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="e193f-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="e193f-316">Глава 10. Настройка тега</span><span class="sxs-lookup"><span data-stu-id="e193f-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="e193f-317">Код, обрабатывающий взгляд, будет использовать тег **сигнинбуттон** для указания объекта, с которым пользователь будет взаимодействовать для входа в *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="e193f-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="e193f-318">Чтобы создать тег, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e193f-318">To create the Tag:</span></span>

1.  <span data-ttu-id="e193f-319">В редакторе Unity щелкните **главную камеру** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="e193f-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="e193f-320">На *панели инспектора* щелкните *тег* **маинкамера** , чтобы открыть раскрывающийся список.</span><span class="sxs-lookup"><span data-stu-id="e193f-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="e193f-321">Щелкните **Добавить тег...**</span><span class="sxs-lookup"><span data-stu-id="e193f-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="e193f-322">**+** Нажмите кнопку.</span><span class="sxs-lookup"><span data-stu-id="e193f-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="e193f-323">Запишите имя тега как **сигнинбуттон** и нажмите кнопку Сохранить.</span><span class="sxs-lookup"><span data-stu-id="e193f-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="e193f-324">Глава 11. Создание проекта Unity для UWP</span><span class="sxs-lookup"><span data-stu-id="e193f-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="e193f-325">Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.</span><span class="sxs-lookup"><span data-stu-id="e193f-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="e193f-326">Перейдите к *параметры сборки* (**файл*>*построения параметры**).</span><span class="sxs-lookup"><span data-stu-id="e193f-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="e193f-327">Если это еще не так, то тактовые **проекты Unity на C\#** .</span><span class="sxs-lookup"><span data-stu-id="e193f-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="e193f-328">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="e193f-328">Click **Build**.</span></span> <span data-ttu-id="e193f-329">Unity запустит окно **проводника** , в котором необходимо создать, а затем выбрать папку для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="e193f-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="e193f-330">Создайте эту папку сейчас и назовите ее **app**Name.</span><span class="sxs-lookup"><span data-stu-id="e193f-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="e193f-331">Затем выберите папку **приложения** и щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="e193f-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="e193f-332">Unity начнет сборку проекта в папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="e193f-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="e193f-333">После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).</span><span class="sxs-lookup"><span data-stu-id="e193f-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="e193f-334">Глава 12. Развертывание в HoloLens</span><span class="sxs-lookup"><span data-stu-id="e193f-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="e193f-335">Для развертывания на HoloLens выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e193f-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="e193f-336">Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика.**</span><span class="sxs-lookup"><span data-stu-id="e193f-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="e193f-337">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="e193f-337">To do this:</span></span>

    1.  <span data-ttu-id="e193f-338">Людьми HoloLens, откройте **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="e193f-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="e193f-339">Выберите сетевые &**Дополнительные параметры** **сети Интернет** > **Wi-Fi** > </span><span class="sxs-lookup"><span data-stu-id="e193f-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="e193f-340">Запишите **IPv4** -адрес.</span><span class="sxs-lookup"><span data-stu-id="e193f-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="e193f-341">Затем вернитесь к параметрами **Обновите & безопасности** > **для разработчиков** .</span><span class="sxs-lookup"><span data-stu-id="e193f-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="e193f-342">Задайте **режим разработчика на**.</span><span class="sxs-lookup"><span data-stu-id="e193f-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="e193f-343">Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="e193f-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="e193f-344">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="e193f-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="e193f-345">На **платформе решения**выберите **x86, удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="e193f-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="e193f-346">Вам будет предложено вставить **IP-адрес** удаленного устройства (в данном случае это HoloLens).</span><span class="sxs-lookup"><span data-stu-id="e193f-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="e193f-347">Перейдите в меню **Сборка** и щелкните **Развернуть решение** , чтобы загружать неопубликованные приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e193f-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="e193f-348">Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.</span><span class="sxs-lookup"><span data-stu-id="e193f-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="e193f-349">Приложение Microsoft Graph HoloLens</span><span class="sxs-lookup"><span data-stu-id="e193f-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="e193f-350">Поздравляем, вы создали приложение смешанной реальности, которое использует Microsoft Graph для чтения и просмотра данных календаря пользователя.</span><span class="sxs-lookup"><span data-stu-id="e193f-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="e193f-351">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="e193f-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="e193f-352">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="e193f-352">Exercise 1</span></span>

<span data-ttu-id="e193f-353">Использование Microsoft Graph для просмотра других сведений о пользователе</span><span class="sxs-lookup"><span data-stu-id="e193f-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="e193f-354">Адрес электронной почты пользователя, номер телефона или изображение профиля</span><span class="sxs-lookup"><span data-stu-id="e193f-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="e193f-355">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="e193f-355">Exercise 1</span></span>

<span data-ttu-id="e193f-356">Реализуйте голосовое управление для навигации по Microsoft Graph пользовательскому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="e193f-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
