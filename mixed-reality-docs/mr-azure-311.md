---
title: Г-н и Azure 311 - Microsoft Graph
description: Выполните этот курс поможет вам научиться использовать Microsoft Graph и подключения к данным, влияющим на производительность приложения смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, microsoft graph, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 98fe2c872f332a21fff3af6751ae555968073a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597659"
---
>[!NOTE]
><span data-ttu-id="99fab-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="99fab-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="99fab-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="99fab-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="99fab-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="99fab-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="99fab-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="99fab-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="99fab-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="99fab-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="99fab-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="99fab-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="99fab-110">Г-н и Azure 311 - Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="99fab-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="99fab-111">В рамках этого курса вы узнаете, как использовать *Microsoft Graph* для входа в учетную запись Майкрософт, с помощью безопасной проверки подлинности в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="99fab-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="99fab-112">Затем извлечения и отображения запланированных собраниях в интерфейсе приложения.</span><span class="sxs-lookup"><span data-stu-id="99fab-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="99fab-113">*Microsoft Graph* — это набор API-интерфейсы, обеспечивающие доступ к множеству служб корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="99fab-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="99fab-114">Майкрософт описывает Microsoft Graph как матрицу, соединенным отношениями, это означает, что он позволяет приложению получить доступ к все виды данных подключенного пользователя.</span><span class="sxs-lookup"><span data-stu-id="99fab-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="99fab-115">Дополнительные сведения см. в статье [страницы Microsoft Graph](https://developer.microsoft.com/graph).</span><span class="sxs-lookup"><span data-stu-id="99fab-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="99fab-116">Разработки будет включать создание приложения, где пользователю будет рекомендовано для помощи в, а затем нажмите сфера, который предложит пользователю безопасно входить в систему с учетной записью Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="99fab-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="99fab-117">После входа в систему с учетной записью, пользователь будет иметь возможность просмотреть список встреч, запланированных на день.</span><span class="sxs-lookup"><span data-stu-id="99fab-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="99fab-118">После выполнения этого курса, у вас будет смешанной реальности HoloLens приложения, который будет осуществлять следующее:</span><span class="sxs-lookup"><span data-stu-id="99fab-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="99fab-119">С помощью жеста касания, коснитесь кнопки на объект, который предложит пользователю выполнять вход в учетную запись Майкрософт (перемещение из приложения для входа и затем обратно в приложение).</span><span class="sxs-lookup"><span data-stu-id="99fab-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="99fab-120">Просмотрите список встреч, запланированных на день.</span><span class="sxs-lookup"><span data-stu-id="99fab-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="99fab-121">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="99fab-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="99fab-122">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="99fab-123">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="99fab-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="99fab-124">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="99fab-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="99fab-125">Курс</span><span class="sxs-lookup"><span data-stu-id="99fab-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="99fab-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="99fab-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="99fab-127"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="99fab-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="99fab-128">Г-н и Azure 311: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="99fab-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="99fab-129">✔️</span><span class="sxs-lookup"><span data-stu-id="99fab-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="99fab-130">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="99fab-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="99fab-131">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="99fab-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="99fab-132">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="99fab-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="99fab-133">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="99fab-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="99fab-134">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="99fab-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="99fab-135">Компьютере разработки</span><span class="sxs-lookup"><span data-stu-id="99fab-135">A development PC</span></span>
- [<span data-ttu-id="99fab-136">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="99fab-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="99fab-137">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="99fab-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="99fab-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="99fab-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="99fab-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="99fab-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="99fab-140">Объект [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="99fab-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="99fab-141">Доступ к Интернету для настройки Azure и получения данных Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="99fab-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="99fab-142">Является допустимым **учетной записи Майкрософт** (личные или рабочие или учебные учетные записи)</span><span class="sxs-lookup"><span data-stu-id="99fab-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="99fab-143">Несколько собраний, запланировано на текущий день, с использованием одной и той же учетной записи Майкрософт</span><span class="sxs-lookup"><span data-stu-id="99fab-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="99fab-144">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="99fab-144">Before you start</span></span>

1.  <span data-ttu-id="99fab-145">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="99fab-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="99fab-146">Настроить и проверить ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="99fab-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="99fab-147">Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="99fab-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="99fab-148">Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="99fab-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="99fab-149">Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="99fab-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="99fab-150">Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="99fab-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="99fab-151">Глава 1 - Создание приложения на портале регистрации приложений</span><span class="sxs-lookup"><span data-stu-id="99fab-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="99fab-152">Начнем с того, необходимо будет создать и зарегистрировать приложение в **портал регистрации приложений**.</span><span class="sxs-lookup"><span data-stu-id="99fab-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="99fab-153">В этой главе вы также найдете ключ службы, который позволит вам выполнять вызовы к *Microsoft Graph* для доступа к содержимому вашей учетной записи.</span><span class="sxs-lookup"><span data-stu-id="99fab-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="99fab-154">Перейдите к [портале регистрации приложений Майкрософт](https://apps.dev.microsoft.com) и войдите в систему с учетной записью Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="99fab-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="99fab-155">После входа, вы будете перенаправлены к **портал регистрации приложений**.</span><span class="sxs-lookup"><span data-stu-id="99fab-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="99fab-156">В **моих приложений** щелкните кнопку **Добавление веб-приложения**.</span><span class="sxs-lookup"><span data-stu-id="99fab-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="99fab-157">**Портал регистрации приложений** может выглядеть иначе, в зависимости от того, является ли вы ранее работали с *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="99fab-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="99fab-158">Ниже снимках экрана отображают эти разные версии.</span><span class="sxs-lookup"><span data-stu-id="99fab-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="99fab-159">Добавьте имя для приложения и выберите **создать**.</span><span class="sxs-lookup"><span data-stu-id="99fab-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="99fab-160">После создания приложения, вы будете перенаправлены на главную страницу приложения.</span><span class="sxs-lookup"><span data-stu-id="99fab-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="99fab-161">Копировать **идентификатор приложения** и обязательно запишите это значение в безопасном месте, он будет использоваться только в коде.</span><span class="sxs-lookup"><span data-stu-id="99fab-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="99fab-162">В **платформ** разделе, убедитесь, что **собственное приложение** отображается.</span><span class="sxs-lookup"><span data-stu-id="99fab-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="99fab-163">Если *не* щелкните **Добавление платформы** и выберите **собственное приложение**.</span><span class="sxs-lookup"><span data-stu-id="99fab-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="99fab-164">Прокрутите вниз, в той же странице и в разделе **разрешения Microsoft Graph** необходимо будет добавить дополнительные разрешения для приложения.</span><span class="sxs-lookup"><span data-stu-id="99fab-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="99fab-165">Щелкните **добавить** рядом с полем **делегированные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="99fab-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="99fab-166">Так как требуется приложению доступ к календарю пользователя, установите флажок называется **Calendars.Read** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="99fab-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="99fab-167">Прокрутите вниз и нажмите кнопку **Сохранить** кнопки.</span><span class="sxs-lookup"><span data-stu-id="99fab-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="99fab-168">Сохранения будет подтвержден и вы можете выйти из **портал регистрации приложений**.</span><span class="sxs-lookup"><span data-stu-id="99fab-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="99fab-169">Глава 2 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="99fab-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="99fab-170">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="99fab-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="99fab-171">Откройте *Unity* и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="99fab-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="99fab-172">Необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="99fab-173">Вставить **MSGraphMR**.</span><span class="sxs-lookup"><span data-stu-id="99fab-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="99fab-174">Убедитесь, что шаблон проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="99fab-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="99fab-175">Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="99fab-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="99fab-176">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="99fab-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="99fab-177">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99fab-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="99fab-178">Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="99fab-178">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="99fab-179">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="99fab-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="99fab-180">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="99fab-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="99fab-181">Перейдите к **файл > Параметры сборки** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** кнопку, чтобы применить выбранные параметры.</span><span class="sxs-lookup"><span data-stu-id="99fab-181">Go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="99fab-182">Оставаясь в **файл > Параметры сборки**, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="99fab-182">While still in **File > Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="99fab-183">**Целевое устройство** присваивается **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="99fab-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="99fab-184">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="99fab-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="99fab-185">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="99fab-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="99fab-186">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="99fab-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="99fab-187">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="99fab-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="99fab-188">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="99fab-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="99fab-189">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="99fab-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="99fab-190">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="99fab-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="99fab-191">Создайте новую папку и все будущие, сцены.</span><span class="sxs-lookup"><span data-stu-id="99fab-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="99fab-192">Выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="99fab-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="99fab-193">Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **MR_ComputerVisionScene**, нажмите кнопку **Сохранить** .</span><span class="sxs-lookup"><span data-stu-id="99fab-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="99fab-194">Следует помнить, что необходимо сохранить в Unity кадром *активы* папку, так как они должны быть связаны с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="99fab-195">Создание папки сцены (и другие аналогичные папки) — это типичный способ структурирования проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="99fab-196">Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="99fab-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="99fab-197">В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.</span><span class="sxs-lookup"><span data-stu-id="99fab-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="99fab-198">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="99fab-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="99fab-199">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="99fab-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="99fab-200">**Scripting** **версии среды выполнения** должно быть **экспериментальные** (.NET 4.6 эквивалент), что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="99fab-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="99fab-201">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="99fab-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="99fab-202">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="99fab-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="99fab-203">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="99fab-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="99fab-204">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="99fab-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="99fab-205">Далее панели в **параметры XR** (под **параметры публикации**), проверьте **поддерживается виртуальной реальности**, убедитесь, что **Windows Mixed Reality Пакет SDK** добавляется.</span><span class="sxs-lookup"><span data-stu-id="99fab-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="99fab-206">Вернитесь в *параметры построения*, *Unity C# проекты* больше не отображается серым, установите флажок возле это.</span><span class="sxs-lookup"><span data-stu-id="99fab-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="99fab-207">Закрыть *параметры построения* окна.</span><span class="sxs-lookup"><span data-stu-id="99fab-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="99fab-208">Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНЫ / FILE > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="99fab-208">Save your scene and project (**FILE > SAVE SCENES / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="99fab-209">Глава 3 - библиотеки импорта в Unity</span><span class="sxs-lookup"><span data-stu-id="99fab-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99fab-210">Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 5](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="99fab-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="99fab-211">Для использования *Microsoft Graph* в Unity, необходимо использовать **Microsoft.Identity.Client** библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="99fab-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="99fab-212">Можно использовать пакет SDK для Microsoft Graph, однако потребуется Добавление пакета NuGet после построения проекта Unity (то есть редактирования после построения проекта).</span><span class="sxs-lookup"><span data-stu-id="99fab-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="99fab-213">Он считается проще импортировать необходимые библиотеки DLL непосредственно в Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="99fab-214">В Unity, который требует подключаемых модулей, чтобы повторно настроить после импорта в настоящее время имеется известная проблема.</span><span class="sxs-lookup"><span data-stu-id="99fab-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="99fab-215">Эти шаги (4 – 7 в этом разделе), не будет обязательным после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="99fab-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="99fab-216">Чтобы импортировать *Microsoft Graph* в проект, [Загрузите файл MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="99fab-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="99fab-217">Этот пакет был создан с версиями библиотек, которые были протестированы.</span><span class="sxs-lookup"><span data-stu-id="99fab-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="99fab-218">Если вы хотите узнать больше о том, как добавить особые DLL-файлы в проект Unity [перейдите по этой ссылке](https://docs.unity3d.com/Manual/UsingDLL.html).</span><span class="sxs-lookup"><span data-stu-id="99fab-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="99fab-219">Чтобы импортировать пакет:</span><span class="sxs-lookup"><span data-stu-id="99fab-219">To import the package:</span></span>

1.  <span data-ttu-id="99fab-220">Добавьте пакет Unity Unity с помощью **активы* > *Импорт пакета* > *пользовательского пакета** пункт меню.</span><span class="sxs-lookup"><span data-stu-id="99fab-220">Add the Unity Package to Unity by using the **Assets* > *Import Package* > *Custom Package** menu option.</span></span> <span data-ttu-id="99fab-221">Выберите пакет, который вы только что загрузили.</span><span class="sxs-lookup"><span data-stu-id="99fab-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="99fab-222">В **Импорт пакета Unity** который появится убедитесь, что все, что в разделе (вплоть до) **подключаемые модули** выбран.</span><span class="sxs-lookup"><span data-stu-id="99fab-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="99fab-223">Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="99fab-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="99fab-224">Перейдите к **MSGraph** папке **подключаемые модули** в *панель проекта* и выберите подключаемый модуль **Microsoft.Identity.Client**.</span><span class="sxs-lookup"><span data-stu-id="99fab-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="99fab-225">С помощью *подключаемый модуль* выбран, убедитесь, что **Any платформы** не установлен, а затем убедитесь, что **WSAPlayer** также не установлен, а затем щелкните **применить**.</span><span class="sxs-lookup"><span data-stu-id="99fab-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="99fab-226">Это, чтобы убедиться, что файлы настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="99fab-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="99fab-227">Пометка этих подключаемых модулей позволяет настроить их только для использования в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="99fab-228">Существует другой набор библиотек DLL в папке WSA, которая будет использоваться после проект будет экспортирован из Unity как универсальное приложение Windows.</span><span class="sxs-lookup"><span data-stu-id="99fab-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="99fab-229">Затем необходимо открыть **WSA** папку, в пределах **MSGraph** папки.</span><span class="sxs-lookup"><span data-stu-id="99fab-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="99fab-230">Вы увидите копию тот же файл, который вы только что настроили.</span><span class="sxs-lookup"><span data-stu-id="99fab-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="99fab-231">Выберите файл, а затем в окне инспектора:</span><span class="sxs-lookup"><span data-stu-id="99fab-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="99fab-232">Убедитесь, что **Any платформы** — **unchecked**и что **только** **WSAPlayer** — **проверяется**.</span><span class="sxs-lookup"><span data-stu-id="99fab-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="99fab-233">Убедитесь, **SDK** имеет значение **UWP**, и **сценариев серверной части** присваивается **точка Net**</span><span class="sxs-lookup"><span data-stu-id="99fab-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="99fab-234">Убедитесь, что **не обрабатывать** — **проверяется**.</span><span class="sxs-lookup"><span data-stu-id="99fab-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="99fab-235">Щелкните **Применить**.</span><span class="sxs-lookup"><span data-stu-id="99fab-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="99fab-236">Глава 4 – Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="99fab-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="99fab-237">Во время этой главе вы настроите Main Camera часть сцены:</span><span class="sxs-lookup"><span data-stu-id="99fab-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="99fab-238">В *панели иерархии*выберите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="99fab-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="99fab-239">После выбора можно видеть все компоненты **Main Camera** в *инспектор* панели.</span><span class="sxs-lookup"><span data-stu-id="99fab-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="99fab-240">**Объекта Camera** должен иметь имя **Main Camera** (Обратите внимание, правильность написания!)</span><span class="sxs-lookup"><span data-stu-id="99fab-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="99fab-241">Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания!)</span><span class="sxs-lookup"><span data-stu-id="99fab-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="99fab-242">Убедитесь, что **преобразование положения** присваивается **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="99fab-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="99fab-243">Задайте **очистить флаги** для **сплошным цветом**</span><span class="sxs-lookup"><span data-stu-id="99fab-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="99fab-244">Задайте **цвет фона** компонента камеры для **черная, альфа-канал 0** **(шестнадцатеричный код: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="99fab-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="99fab-245">Структура результирующий объект в *панели иерархии* должно быть, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="99fab-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="99fab-246">Глава 5 - создание класса MeetingsUI</span><span class="sxs-lookup"><span data-stu-id="99fab-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="99fab-247">Первый скрипт, чтобы создать **MeetingsUI**, который отвечает за размещение и заполнения UI приложения (приветственное сообщение, инструкции и сведения собрания).</span><span class="sxs-lookup"><span data-stu-id="99fab-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="99fab-248">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="99fab-248">To create this class:</span></span>

1.  <span data-ttu-id="99fab-249">Щелкните правой кнопкой мыши **активы** папку в *панель проекта*, а затем выберите \**создать* > \* папки \*\*.</span><span class="sxs-lookup"><span data-stu-id="99fab-249">Right-click on the **Assets** folder in the *Project Panel*, then select \**Create* > \*Folder\*\*.</span></span> <span data-ttu-id="99fab-250">Назовите папку **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="99fab-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="99fab-251">Откройте **сценарии** папки затем, внутри этой папки, щелкните правой кнопкой мыши, \**создать* > \* C\# Script \*\*.</span><span class="sxs-lookup"><span data-stu-id="99fab-251">Open the **Scripts** folder then, within that folder, right-click, \**Create* > \*C\# Script\*\*.</span></span> <span data-ttu-id="99fab-252">Назовите сценарий **MeetingsUI.**</span><span class="sxs-lookup"><span data-stu-id="99fab-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="99fab-253">Дважды щелкните новый **MeetingsUI** скрипт, чтобы открыть его с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="99fab-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="99fab-254">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="99fab-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="99fab-255">Внутри класса вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="99fab-255">Inside the class insert the following variables:</span></span>

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

6.  <span data-ttu-id="99fab-256">Затем замените **Start()** метод и добавьте **Awake()** метод.</span><span class="sxs-lookup"><span data-stu-id="99fab-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="99fab-257">Это будет вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="99fab-257">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="99fab-258">Добавьте методы, ответственный за создание *пользовательского интерфейса собрания* и заполняет ее текущего собраниях по запросу:</span><span class="sxs-lookup"><span data-stu-id="99fab-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

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

8. <span data-ttu-id="99fab-259">**Удалить** **Update()** метод, и **сохранить изменения** в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="99fab-260">Глава 6 - создание класса Graph</span><span class="sxs-lookup"><span data-stu-id="99fab-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="99fab-261">Далее сценарий для создания **Graph** скрипта.</span><span class="sxs-lookup"><span data-stu-id="99fab-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="99fab-262">Этот сценарий отвечает за обеспечение вызовов для проверки подлинности пользователя и получения запланированных собраний за текущий день из календаря пользователя.</span><span class="sxs-lookup"><span data-stu-id="99fab-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="99fab-263">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="99fab-263">To create this class:</span></span>

1.  <span data-ttu-id="99fab-264">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="99fab-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="99fab-265">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="99fab-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="99fab-266">Назовите сценарий **Graph**.</span><span class="sxs-lookup"><span data-stu-id="99fab-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="99fab-267">Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99fab-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="99fab-268">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="99fab-268">Insert the following namespaces:</span></span>

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
    > <span data-ttu-id="99fab-269">Обратите внимание, что фрагменты кода в этом сценарии являются оболочкой [директивы предварительной компиляции](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), это позволяет избежать проблем с библиотеками, при построении решения Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99fab-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="99fab-270">Удалить **Start()** и **Update()** методы, так как они не будут использоваться.</span><span class="sxs-lookup"><span data-stu-id="99fab-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="99fab-271">За пределами **Graph** класса, вставьте следующие объекты, которые являются необходимыми для десериализации объекта JSON, представляющего ежедневных запланированных собраний:</span><span class="sxs-lookup"><span data-stu-id="99fab-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

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

7.  <span data-ttu-id="99fab-272">Внутри **Graph** добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="99fab-272">Inside the **Graph** class, add the following variables:</span></span>

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
    > <span data-ttu-id="99fab-273">Изменение **appId** значение должно быть **идентификатор приложения** , записанными в  **[главе 1](#chapter-1---create-your-app-in-the-application-registration-portal), шаг 4**.</span><span class="sxs-lookup"><span data-stu-id="99fab-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="99fab-274">Это значение должно быть такой же, как в **портал регистрации приложений,** на странице регистрации приложения.</span><span class="sxs-lookup"><span data-stu-id="99fab-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="99fab-275">В рамках **Graph** добавьте методы **SignInAsync()** и **AquireTokenAsync()**, который предложит пользователю вставлять учетные данные входа.</span><span class="sxs-lookup"><span data-stu-id="99fab-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

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

9.  <span data-ttu-id="99fab-276">Добавьте следующие два метода:</span><span class="sxs-lookup"><span data-stu-id="99fab-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="99fab-277">**BuildTodayCalendarEndpoint()**, который строит URI, указав день и интервал времени, в которой извлекаются запланированных собраниях.</span><span class="sxs-lookup"><span data-stu-id="99fab-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="99fab-278">**ListMeetingsAsync()**, которая запрашивает запланированных встреч из *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="99fab-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

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

10. <span data-ttu-id="99fab-279">Вы завершили **Graph** скрипта.</span><span class="sxs-lookup"><span data-stu-id="99fab-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="99fab-280">**Сохраните внесенные** в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="99fab-281">Глава 7 - создание скрипта GazeInput</span><span class="sxs-lookup"><span data-stu-id="99fab-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="99fab-282">Теперь вы создадите **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="99fab-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="99fab-283">Этот класс обрабатывает и отслеживает взглядом пользователя, с помощью **Raycast** из **Main Camera**, проецирование вперед.</span><span class="sxs-lookup"><span data-stu-id="99fab-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="99fab-284">Для создания скрипта:</span><span class="sxs-lookup"><span data-stu-id="99fab-284">To create the script:</span></span>

1.  <span data-ttu-id="99fab-285">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="99fab-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="99fab-286">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="99fab-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="99fab-287">Назовите сценарий **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="99fab-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="99fab-288">Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99fab-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="99fab-289">Изменить код пространства имен, чтобы соответствовать приведенному ниже, а также добавление "**\[System.Serializable\]**" тег выше вашей **GazeInput** класса, чтобы его можно было сериализовать:</span><span class="sxs-lookup"><span data-stu-id="99fab-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="99fab-290">Внутри **GazeInput** добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="99fab-290">Inside the **GazeInput** class, add the following variables:</span></span>

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

6.  <span data-ttu-id="99fab-291">Добавить **CreateCursor()** метод для создания курсора HoloLens в сцене и вызовите метод из **Start()** метод:</span><span class="sxs-lookup"><span data-stu-id="99fab-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

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

7.  <span data-ttu-id="99fab-292">Следующие методы включить взглядом Raycast и отслеживать фокус объекты.</span><span class="sxs-lookup"><span data-stu-id="99fab-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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

8.  <span data-ttu-id="99fab-293">**Сохраните внесенные** в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="99fab-294">Глава 8 - создать класс взаимодействия</span><span class="sxs-lookup"><span data-stu-id="99fab-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="99fab-295">Теперь необходимо будет создать **взаимодействия** сценарий, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="99fab-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="99fab-296">Обработка **коснитесь** взаимодействия и **помощи камеры**, который позволяет пользователю взаимодействовать с журналом в «кнопка» в сцене.</span><span class="sxs-lookup"><span data-stu-id="99fab-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="99fab-297">Создание журнала в объект «кнопка» в сцене для взаимодействия с пользователем.</span><span class="sxs-lookup"><span data-stu-id="99fab-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="99fab-298">Для создания скрипта:</span><span class="sxs-lookup"><span data-stu-id="99fab-298">To create the script:</span></span>

1.  <span data-ttu-id="99fab-299">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="99fab-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="99fab-300">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="99fab-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="99fab-301">Назовите сценарий **взаимодействия**.</span><span class="sxs-lookup"><span data-stu-id="99fab-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="99fab-302">Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99fab-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="99fab-303">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="99fab-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="99fab-304">Изменение порядка наследования класса **взаимодействия** класса из *MonoBehaviour* для **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="99fab-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="99fab-305">~~открытый класс взаимодействия: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="99fab-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="99fab-306">Внутри **взаимодействия** класс вставить следующую переменную:</span><span class="sxs-lookup"><span data-stu-id="99fab-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="99fab-307">Замените **запустить** метод; Обратите внимание, что он является методом переопределения, который вызывает метод класса «base» взглядом.</span><span class="sxs-lookup"><span data-stu-id="99fab-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="99fab-308">**Start()** будет вызываться при инициализации класса, регистрацию для ввода распознавания и Создание входа *кнопку* в сцене:</span><span class="sxs-lookup"><span data-stu-id="99fab-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

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

8.  <span data-ttu-id="99fab-309">Добавить **CreateSignInButton()** метод, который будет создавать входа *кнопку* в сцене и задать его свойства:</span><span class="sxs-lookup"><span data-stu-id="99fab-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

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

9.  <span data-ttu-id="99fab-310">Добавить **GestureRecognizer_Tapped()** метод, который будет отвечать на запросы *коснитесь* событием пользователя.</span><span class="sxs-lookup"><span data-stu-id="99fab-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

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

10. <span data-ttu-id="99fab-311">**Удалить** **Update()** метод, а затем **сохранить изменения** в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="99fab-312">Глава 9 - Настройка ссылки на скрипты</span><span class="sxs-lookup"><span data-stu-id="99fab-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="99fab-313">В этой главе, вам потребуется разместить **взаимодействия** скрипт на **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="99fab-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="99fab-314">Затем этот скрипт обрабатывающий размещение другие сценарии, где они должны быть.</span><span class="sxs-lookup"><span data-stu-id="99fab-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="99fab-315">Из **сценарии** папку в *панель проекта*, перетащить сценарий **взаимодействия** для **Main Camera** объекта, как на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="99fab-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="99fab-316">Глава 10 - Настройка тега</span><span class="sxs-lookup"><span data-stu-id="99fab-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="99fab-317">Код, обрабатывающий взглядом будут работать с тега **SignInButton** для идентификации объекта, который пользователь будет взаимодействовать с для входа в *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="99fab-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="99fab-318">Создание тега:</span><span class="sxs-lookup"><span data-stu-id="99fab-318">To create the Tag:</span></span>

1.  <span data-ttu-id="99fab-319">Щелкните в редакторе Unity **Main Camera** в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="99fab-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="99fab-320">В *панели Инспектора* щелкните **MainCamera** *тега* для открытия раскрывающегося списка.</span><span class="sxs-lookup"><span data-stu-id="99fab-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="99fab-321">Щелкните **добавьте тег...**</span><span class="sxs-lookup"><span data-stu-id="99fab-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="99fab-322">Щелкните **+** кнопки.</span><span class="sxs-lookup"><span data-stu-id="99fab-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="99fab-323">Имя тега, как написать **SignInButton** и щелкните "Сохранить".</span><span class="sxs-lookup"><span data-stu-id="99fab-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="99fab-324">Глава 11 - сборки проекта Unity для универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="99fab-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="99fab-325">Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.</span><span class="sxs-lookup"><span data-stu-id="99fab-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="99fab-326">Перейдите к *параметры сборки* (\**файл* > \* построения параметры \*\*).</span><span class="sxs-lookup"><span data-stu-id="99fab-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="99fab-327">Если не сделали, установите **Unity C\# проекты**.</span><span class="sxs-lookup"><span data-stu-id="99fab-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="99fab-328">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="99fab-328">Click **Build**.</span></span> <span data-ttu-id="99fab-329">Unity приведет к запуску **проводнике** окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в.</span><span class="sxs-lookup"><span data-stu-id="99fab-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="99fab-330">Создайте эту папку и назовите его **приложения**.</span><span class="sxs-lookup"><span data-stu-id="99fab-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="99fab-331">Затем с помощью **приложения** щелкните папку, **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="99fab-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="99fab-332">Unity начнется построение проекта для **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="99fab-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="99fab-333">Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="99fab-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="99fab-334">Глава 12 - развертывание в HoloLens</span><span class="sxs-lookup"><span data-stu-id="99fab-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="99fab-335">Для развертывания на HoloLens:</span><span class="sxs-lookup"><span data-stu-id="99fab-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="99fab-336">Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика.**</span><span class="sxs-lookup"><span data-stu-id="99fab-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="99fab-337">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="99fab-337">To do this:</span></span>

    1.  <span data-ttu-id="99fab-338">Хотя носить вашей HoloLens, откройте **параметры**.</span><span class="sxs-lookup"><span data-stu-id="99fab-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="99fab-339">Перейдите к **сеть и Интернет** > **Wi-Fi** > **Дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="99fab-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="99fab-340">Примечание **IPv4** адрес.</span><span class="sxs-lookup"><span data-stu-id="99fab-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="99fab-341">Затем перейдите к **параметры**, а затем в **обновление и безопасность** > **для разработчиков**</span><span class="sxs-lookup"><span data-stu-id="99fab-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="99fab-342">Задайте **режим разработчика на**.</span><span class="sxs-lookup"><span data-stu-id="99fab-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="99fab-343">Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99fab-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="99fab-344">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="99fab-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="99fab-345">В **платформа решения**выберите **x86, удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="99fab-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="99fab-346">Вам будет предложено вставить **IP-адрес** удаленного устройства (HoloLens, таким образом, который вы записали).</span><span class="sxs-lookup"><span data-stu-id="99fab-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="99fab-347">Перейдите к **построения** меню и щелкните **развернуть решение** для загрузки неопубликованных приложений для вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="99fab-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="99fab-348">Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!</span><span class="sxs-lookup"><span data-stu-id="99fab-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="99fab-349">Приложение Microsoft Graph HoloLens</span><span class="sxs-lookup"><span data-stu-id="99fab-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="99fab-350">Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Microsoft Graph, для чтения и отображения данных календаря пользователя.</span><span class="sxs-lookup"><span data-stu-id="99fab-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="99fab-351">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="99fab-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="99fab-352">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="99fab-352">Exercise 1</span></span>

<span data-ttu-id="99fab-353">Использовать Microsoft Graph для отображения других сведений о пользователе</span><span class="sxs-lookup"><span data-stu-id="99fab-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="99fab-354">Адрес электронной почты пользователя, номер телефона, изображение профиля</span><span class="sxs-lookup"><span data-stu-id="99fab-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="99fab-355">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="99fab-355">Exercise 1</span></span>

<span data-ttu-id="99fab-356">Реализуйте управление голосовой связью для перехода в пользовательский Интерфейс Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="99fab-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
