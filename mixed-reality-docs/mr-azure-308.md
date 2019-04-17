---
title: Г-н и Azure 308 - уведомлений между устройствами
description: Выполните этот курс, чтобы узнать, как реализовать приложение смешанной реальности центров уведомлений Azure, функции Azure и хранилища Azure и таблиц.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, уведомления, функции, таблицы, центры уведомлений, hololens, создающий эффект присутствия, vr
ms.openlocfilehash: ed56c936a0498b6e0ac804da15a2c6ec98239d0c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604783"
---
>[!NOTE]
><span data-ttu-id="3490b-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="3490b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3490b-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="3490b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3490b-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3490b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3490b-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="3490b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3490b-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3490b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="3490b-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="3490b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="3490b-110">Г-н и Azure 308: Уведомлений между устройствами</span><span class="sxs-lookup"><span data-stu-id="3490b-110">MR and Azure 308: Cross-device notifications</span></span>

![конечный продукт-запуск](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="3490b-112">В рамках этого курса вы узнаете, как добавить возможности центров уведомлений в приложение смешанной реальности, с помощью центров уведомлений Azure, таблицы Azure и функций Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="3490b-113">**Центры уведомлений Azure** — это служба Майкрософт, которую разработчики могут отправлять целевые персонализированные push-уведомления на любую платформу, все на базе облака.</span><span class="sxs-lookup"><span data-stu-id="3490b-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="3490b-114">Это эффективно позволяют разработчикам взаимодействовать с конечными пользователями, или даже обмена данными между различными приложениями, в зависимости от сценария.</span><span class="sxs-lookup"><span data-stu-id="3490b-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="3490b-115">Дополнительные сведения см. в статье **центров уведомлений Azure** [страницы](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span><span class="sxs-lookup"><span data-stu-id="3490b-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="3490b-116">**Функции Azure** является служба, которая позволяет разработчикам запускать небольшие фрагменты кода, «», в функциях Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="3490b-117">Это позволяет делегировать работу в облаке, а не локального приложения, который может иметь множество преимуществ.</span><span class="sxs-lookup"><span data-stu-id="3490b-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="3490b-118">**Функции Azure** поддерживает несколько языков разработки, в том числе C\#, F\#, Node.js, Java и PHP.</span><span class="sxs-lookup"><span data-stu-id="3490b-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="3490b-119">Дополнительные сведения см. в статье **"функции Azure"** [страницы](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="3490b-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="3490b-120">**Таблицы Azure** является облачной службой Майкрософт, которая позволяет разработчикам хранить данные структурированных отличные от SQL в облаке, сделаете его доступным в любом месте.</span><span class="sxs-lookup"><span data-stu-id="3490b-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="3490b-121">Служба может похвастаться бессхемной конструкцией, позволяя развитие таблиц, при необходимости и таким образом обладает большой гибкостью.</span><span class="sxs-lookup"><span data-stu-id="3490b-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="3490b-122">Дополнительные сведения см. в статье **таблицы Azure** [страницы](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="3490b-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="3490b-123">После выполнения этого курса, у вас будет приложении иммерсивных гарнитуры смешанной реальности и это приложение для настольных ПК, которое сможет выполнить следующие:</span><span class="sxs-lookup"><span data-stu-id="3490b-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="3490b-124">Приложения для настольных ПК, позволит пользователю для перемещения объекта в двумерном пространстве (X и Y), с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="3490b-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="3490b-125">Перемещение объектов в приложении ПК будут отправляться в облако с помощью JSON, который может быть в виде строки, содержащая идентификатор объекта, тип и преобразование информации (координаты X и Y).</span><span class="sxs-lookup"><span data-stu-id="3490b-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="3490b-126">Приложение смешанной реальности, которое имеет идентичные сцены в классическое приложение, будет получать уведомлений о перемещение объектов из службы концентраторов уведомлений (который был обновлен в приложении для настольных ПК).</span><span class="sxs-lookup"><span data-stu-id="3490b-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="3490b-127">При получении уведомления, который будет содержать идентификатор объекта, тип и информацию о преобразовании, смешанной реальности применит полученные сведения свой собственный сцену.</span><span class="sxs-lookup"><span data-stu-id="3490b-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="3490b-128">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="3490b-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="3490b-129">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="3490b-130">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="3490b-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="3490b-131">Этот курс — это автономное руководство, которые не предусматривают любых других смешанной реальности лабораторий, напрямую.</span><span class="sxs-lookup"><span data-stu-id="3490b-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="3490b-132">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="3490b-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3490b-133">Курс</span><span class="sxs-lookup"><span data-stu-id="3490b-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3490b-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3490b-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3490b-135"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="3490b-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="3490b-136">Г-н и Azure 308: Уведомлений между устройствами</span><span class="sxs-lookup"><span data-stu-id="3490b-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="3490b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="3490b-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="3490b-138">✔️</span><span class="sxs-lookup"><span data-stu-id="3490b-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="3490b-139">Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3490b-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="3490b-140">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3490b-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="3490b-141">При использовании HoloLens, вы можете заметить некоторые echo во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="3490b-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3490b-142">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="3490b-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="3490b-143">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="3490b-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="3490b-144">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="3490b-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="3490b-145">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="3490b-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="3490b-146">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="3490b-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="3490b-147">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="3490b-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="3490b-148">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="3490b-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3490b-149">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="3490b-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3490b-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="3490b-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3490b-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3490b-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="3490b-152">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="3490b-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="3490b-153">Доступ к Интернету для настройки Azure и получить доступ к концентраторам уведомлений</span><span class="sxs-lookup"><span data-stu-id="3490b-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="3490b-154">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="3490b-154">Before you start</span></span>

- <span data-ttu-id="3490b-155">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="3490b-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="3490b-156">Необходимо быть владельцем портал разработчиков Microsoft и на портале регистрации приложений, в противном случае не будут иметь разрешение на доступ к приложению в [Глава 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="3490b-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="3490b-157">Глава 1 - Создание приложения на портале разработчика Майкрософт</span><span class="sxs-lookup"><span data-stu-id="3490b-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="3490b-158">Чтобы использовать **центров уведомлений Azure** службы, необходимо будет создать приложение на портале разработчика Майкрософт, как приложения нужно будет регистрироваться, чтобы она могла отправлять и получать уведомления.</span><span class="sxs-lookup"><span data-stu-id="3490b-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="3490b-159">Войдите в [портал разработчиков Microsoft](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="3490b-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="3490b-160">Необходимо будет войти учетную запись Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="3490b-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="3490b-161">На панели мониторинга щелкните **создать новое приложение**.</span><span class="sxs-lookup"><span data-stu-id="3490b-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Создание приложения](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="3490b-163">Откроется всплывающее окно, в котором необходимо зарезервировать имя для нового приложения.</span><span class="sxs-lookup"><span data-stu-id="3490b-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="3490b-164">В текстовом поле вставьте соответствующее имя; Если выбранное имя, такт будет отображаться справа от текстового поля.</span><span class="sxs-lookup"><span data-stu-id="3490b-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="3490b-165">При наличии доступных имя, добавленное щелкните **зарезервировать имя продукта** кнопку в левом нижнем углу всплывающего окна.</span><span class="sxs-lookup"><span data-stu-id="3490b-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![обратное имя](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="3490b-167">Используя приложение создано вы будете готовы переместить в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="3490b-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="3490b-168">Глава 2 - получить учетные данные нового приложения</span><span class="sxs-lookup"><span data-stu-id="3490b-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="3490b-169">Войдите на портал регистрации приложений, где будут перечислены и получить учетные данные, которые будут использоваться для установки нового приложения **службы концентраторов уведомлений** в **портал Azure**.</span><span class="sxs-lookup"><span data-stu-id="3490b-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="3490b-170">Перейдите к [портал регистрации приложений](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="3490b-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![портал регистрации приложений](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="3490b-172">Необходимо использовать учетную запись Майкрософт для входа.</span><span class="sxs-lookup"><span data-stu-id="3490b-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="3490b-173">Это **необходимо** быть учетной записи Майкрософт, которые использовались в предыдущем [глава](#chapter-1---create-an-application-on-the-microsoft-developer-portal), на портал разработчиков Windows Store.</span><span class="sxs-lookup"><span data-stu-id="3490b-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="3490b-174">Вы найдете приложение под управлением **моих приложений** раздел.</span><span class="sxs-lookup"><span data-stu-id="3490b-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="3490b-175">Когда вы найдете его, щелкните его, и вы перейдете на новую страницу, на котором установлено приложение а также **регистрации**.</span><span class="sxs-lookup"><span data-stu-id="3490b-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![только что зарегистрированное приложение](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="3490b-177">Прокрутите вниз страницу регистрации, чтобы найти ваш **секретов приложения** раздел и **ИД безопасности пакета** для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="3490b-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="3490b-178">Скопируйте обе для использования с настройкой **службы концентраторов уведомлений Azure** в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="3490b-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![Секреты приложений](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="3490b-180">Глава 3 - Настройка портала Azure: создание службы концентраторов уведомлений</span><span class="sxs-lookup"><span data-stu-id="3490b-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="3490b-181">С помощью учетных данных приложения извлечена, вам потребуется перейти на портал Azure, в которой будет создаваться в службе концентраторов уведомлений Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="3490b-182">Войдите на [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="3490b-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="3490b-183">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="3490b-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="3490b-184">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="3490b-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="3490b-185">После входа в систему щелкните **New** в левом верхнем углу, а поиск **концентратора уведомлений**и нажмите кнопку ***ввод***.</span><span class="sxs-lookup"><span data-stu-id="3490b-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![Поиск концентратора уведомлений](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="3490b-187">Слово ***New*** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="3490b-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="3490b-188">Новая страница будет предоставить описание *центров уведомлений* службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="3490b-189">В нижней левой части этого запроса, выберите **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="3490b-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Создайте экземпляр концентратора уведомлений](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="3490b-191">Когда вы перейдете на ***создать***:</span><span class="sxs-lookup"><span data-stu-id="3490b-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="3490b-192">Вставьте желаемого имени для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="3490b-193">Укажите **пространства имен** которого можно будет связать с этим приложением.</span><span class="sxs-lookup"><span data-stu-id="3490b-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="3490b-194">Выберите **расположение.**</span><span class="sxs-lookup"><span data-stu-id="3490b-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="3490b-195">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="3490b-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="3490b-196">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="3490b-197">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="3490b-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="3490b-198">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="3490b-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="3490b-199">Выберите соответствующее **подписки**.</span><span class="sxs-lookup"><span data-stu-id="3490b-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="3490b-200">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="3490b-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="3490b-201">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="3490b-201">Select **Create**.</span></span>

        ![Заполните сведения о службе](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="3490b-203">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="3490b-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="3490b-204">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![уведомление](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="3490b-206">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="3490b-207">Вы перейдете на новый **концентратора уведомлений** экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Перейти к ресурсу](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="3490b-209">На странице обзора, равном вниз по странице, щелкните **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="3490b-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="3490b-210">На правой панели изменится на Показать два текстовые поля, которые требуют вашего **ИД безопасности пакета** и **ключ безопасности**, из приложения, настроенного ранее.</span><span class="sxs-lookup"><span data-stu-id="3490b-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![созданная служба концентраторов](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="3490b-212">После копирования сведений в нужные поля, нажмите кнопку **Сохранить**, и вы получите уведомление, когда в центре уведомлений успешно обновлен.</span><span class="sxs-lookup"><span data-stu-id="3490b-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![Скопируйте сведения о безопасности](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="3490b-214">Глава 4 - Настройка портала Azure: создание службы таблиц</span><span class="sxs-lookup"><span data-stu-id="3490b-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="3490b-215">После создания экземпляра службы концентраторов уведомлений, перейдите назад на портал Azure, которой будет создаваться в службе таблиц Azure, создав ресурс хранилища.</span><span class="sxs-lookup"><span data-stu-id="3490b-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="3490b-216">Если еще не выполнил вход, вход в [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="3490b-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="3490b-217">После входа в систему, щелкните **New** в левом верхнем углу, а поиск **учетной записи хранения**и нажмите кнопку **ввод**.</span><span class="sxs-lookup"><span data-stu-id="3490b-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="3490b-218">Слово ***New*** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="3490b-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="3490b-219">Выберите **учетная запись хранения — большой двоичный объект, файл, таблица, очередь** из списка.</span><span class="sxs-lookup"><span data-stu-id="3490b-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Поиск учетной записи хранения](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="3490b-221">Новая страница будет предоставить описание **учетной записи хранения** службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="3490b-222">В нижней левой части этого запроса, выберите **создать** кнопку, чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="3490b-224">Когда вы перейдете на **создать**, будут отображаться панели:</span><span class="sxs-lookup"><span data-stu-id="3490b-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="3490b-225">Вставить нужный **имя** для данного экземпляра службы (должны указываться прописными буквами).</span><span class="sxs-lookup"><span data-stu-id="3490b-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="3490b-226">Для **модели развертывания**, нажмите кнопку **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="3490b-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="3490b-227">Для **тип учетной записи**, с помощью раскрывающегося списка выберите **хранилища (общего назначения версии 1)**.</span><span class="sxs-lookup"><span data-stu-id="3490b-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="3490b-228">Выберите соответствующее **расположение**.</span><span class="sxs-lookup"><span data-stu-id="3490b-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="3490b-229">Для **репликации** раскрывающемся меню выберите **Read-access геоизбыточного хранилища (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="3490b-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="3490b-230">Для **производительности**, нажмите кнопку **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="3490b-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="3490b-231">В рамках **требуется безопасное перемещение** выберите **отключено**.</span><span class="sxs-lookup"><span data-stu-id="3490b-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="3490b-232">Из **подписки** в раскрывающемся меню выберите соответствующую подписку.</span><span class="sxs-lookup"><span data-stu-id="3490b-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="3490b-233">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="3490b-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="3490b-234">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="3490b-235">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="3490b-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="3490b-236">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="3490b-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="3490b-237">Оставьте **виртуальные сети** как **отключено** Если этот вариант для вас.</span><span class="sxs-lookup"><span data-stu-id="3490b-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="3490b-238">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="3490b-238">Click **Create**.</span></span>

        ![Заполните сведения о хранилище](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="3490b-240">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="3490b-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="3490b-241">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="3490b-242">Щелкните уведомлений для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-242">Click on the notifications to explore your new Service instance.</span></span>

    ![новое уведомление хранилища](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="3490b-244">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="3490b-245">Вы перейдете на новую страницу Общие сведения о службе хранилища экземпляра.</span><span class="sxs-lookup"><span data-stu-id="3490b-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Перейти к ресурсу](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="3490b-247">На странице обзора, в правой части окна щелкните **таблиц**.</span><span class="sxs-lookup"><span data-stu-id="3490b-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="3490b-248">На правой панели появятся **служба таблиц** сведения, в которой необходимо добавить новую таблицу.</span><span class="sxs-lookup"><span data-stu-id="3490b-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="3490b-249">Это можно сделать, щелкнув **+** **таблицы** кнопку в левом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="3490b-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![Открытие таблиц](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="3490b-251">Новая страница отображается, при котором необходимо ввести **имя таблицы**.</span><span class="sxs-lookup"><span data-stu-id="3490b-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="3490b-252">Это имя, которое будет использовать для обращения к данным в приложении в последующих главах.</span><span class="sxs-lookup"><span data-stu-id="3490b-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="3490b-253">Вставьте соответствующее имя и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="3490b-253">Insert an appropriate name and click **OK**.</span></span>

    ![Создание новой таблицы](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="3490b-255">После создания новой таблицы, можно будет увидеть в **служба таблиц** страницы (внизу).</span><span class="sxs-lookup"><span data-stu-id="3490b-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![создать новую таблицу](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="3490b-257">Глава 5 - завершение работы таблицы Azure в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3490b-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="3490b-258">Теперь, когда ваш **служба таблиц** учетной записи хранения установлен и настроен, пришло время для добавления данных, который будет использоваться для хранения и извлечения данных.</span><span class="sxs-lookup"><span data-stu-id="3490b-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="3490b-259">Редактирование таблиц можно сделать с помощью **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3490b-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="3490b-260">Откройте **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3490b-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="3490b-261">В меню **представление > Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="3490b-261">From the menu, click **View > Cloud Explorer**.</span></span>

    ![Откройте cloud explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="3490b-263">**Cloud Explorer** будут открываться как закрепленного элемента (быть пациента, так как загрузка может занять время).</span><span class="sxs-lookup"><span data-stu-id="3490b-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="3490b-264">Если подписка использовалась для создания вашего *учетные записи хранения* не отображается, убедитесь, что у вас есть:</span><span class="sxs-lookup"><span data-stu-id="3490b-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="3490b-265">Вход в ту же учетную запись, которая использовалась для портала Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="3490b-266">Выбранные подписки на странице управления учетной записью (может потребоваться применить фильтр из параметров учетной записи):</span><span class="sxs-lookup"><span data-stu-id="3490b-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![найти подписку](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="3490b-268">Будут показаны облачных служб Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="3490b-269">Найти **учетные записи хранения** и щелкните стрелку влево, чтобы развернуть учетные записи.</span><span class="sxs-lookup"><span data-stu-id="3490b-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Откройте учетные записи хранения](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="3490b-271">После развернут, только что созданный **учетной записи хранения** должны быть доступны.</span><span class="sxs-lookup"><span data-stu-id="3490b-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="3490b-272">Щелкните стрелку слева от хранилища и найдите после, развернута, **таблиц** и щелкните стрелку рядом с ним, чтобы отобразить **таблицы** созданный в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="3490b-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="3490b-273">Дважды щелкните ваш **таблицы**.</span><span class="sxs-lookup"><span data-stu-id="3490b-273">Double click your **Table**.</span></span>

    ![Откройте таблицу объектов сцены](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="3490b-275">Таблица откроется в центре окна Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3490b-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="3490b-276">Щелкните значок таблицы с **+** (плюс) на нем.</span><span class="sxs-lookup"><span data-stu-id="3490b-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![Добавление новой таблицы](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="3490b-278">Откроется окно с запроса позволяет *Добавление сущности*.</span><span class="sxs-lookup"><span data-stu-id="3490b-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="3490b-279">Вы создадите три сущности в целом, каждая из которых несколько свойств.</span><span class="sxs-lookup"><span data-stu-id="3490b-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="3490b-280">Можно будет заметить, что *PartitionKey* и *RowKey* уже предоставляются, так как они используются в таблице для поиска данных.</span><span class="sxs-lookup"><span data-stu-id="3490b-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![ключ раздела и строки](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="3490b-282">Обновление *значение* из **PartitionKey** и **RowKey** следующим образом (не забудьте сделать это для каждого свойства строки, добавить, однако увеличивайте RowKey каждый раз):</span><span class="sxs-lookup"><span data-stu-id="3490b-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![добавить правильные значения](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="3490b-284">Нажмите кнопку **добавить свойство** для добавления дополнительных строк данных.</span><span class="sxs-lookup"><span data-stu-id="3490b-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="3490b-285">Сделайте вашей первой пустой соответствует приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="3490b-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="3490b-286">Нажмите кнопку **ОК** при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="3490b-286">Click **OK** when you are finished.</span></span>

    ![После завершения, нажмите кнопку ОК](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="3490b-288">Убедитесь, что вы изменили **тип** из **X**, **Y**, и **Z**, записи, чтобы **двойные**.</span><span class="sxs-lookup"><span data-stu-id="3490b-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="3490b-289">Можно заметить, что таблица теперь содержит строки данных.</span><span class="sxs-lookup"><span data-stu-id="3490b-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="3490b-290">Нажмите кнопку **+** (плюс) значок снова, чтобы добавить другой сущности.</span><span class="sxs-lookup"><span data-stu-id="3490b-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![Первая строка](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="3490b-292">Создайте дополнительное свойство, а затем задайте значения новой сущности в соответствии с показанным ниже.</span><span class="sxs-lookup"><span data-stu-id="3490b-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Добавление куба](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="3490b-294">Повторите последний шаг, чтобы добавить другой сущности.</span><span class="sxs-lookup"><span data-stu-id="3490b-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="3490b-295">Задайте значения для этой сущности с приведенными ниже.</span><span class="sxs-lookup"><span data-stu-id="3490b-295">Set the values for this entity to those shown below.</span></span>

    ![добавить цилиндр](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="3490b-297">Таблица теперь должна выглядеть, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="3490b-297">Your table should now look like the one below.</span></span>

    ![Полный таблицы](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="3490b-299">В этой главе завершена.</span><span class="sxs-lookup"><span data-stu-id="3490b-299">You have completed this Chapter.</span></span> <span data-ttu-id="3490b-300">Убедитесь в том, что для сохранения.</span><span class="sxs-lookup"><span data-stu-id="3490b-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="3490b-301">Глава 6 - создание приложения-функции Azure</span><span class="sxs-lookup"><span data-stu-id="3490b-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="3490b-302">Создайте приложение-функцию Azure, который будет вызываться приложением рабочего стола для обновления **таблицы** обработки и отправки уведомления через **концентратора уведомлений**.</span><span class="sxs-lookup"><span data-stu-id="3490b-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="3490b-303">Во-первых необходимо создать файл, который позволит загружать библиотеки, необходимые функции Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="3490b-304">Откройте **Блокнот** (нажмите клавишу Windows ключ и тип Блокнот).</span><span class="sxs-lookup"><span data-stu-id="3490b-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![Откройте в блокноте](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="3490b-306">Откройте Блокнот вставьте в него приведенную ниже структуру JSON.</span><span class="sxs-lookup"><span data-stu-id="3490b-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="3490b-307">Как только вы это сделали, сохраните его на рабочем столе как **project.json**.</span><span class="sxs-lookup"><span data-stu-id="3490b-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="3490b-308">Очень важно, что система именования верен: обеспечить его **нет .txt** расширение файла.</span><span class="sxs-lookup"><span data-stu-id="3490b-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="3490b-309">Этот файл определяет библиотек, которые будет использовать функции, при использовании NuGet, она покажется.</span><span class="sxs-lookup"><span data-stu-id="3490b-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="3490b-310">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="3490b-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="3490b-311">После входа в систему щелкните **New** в левом верхнем углу, а поиск **приложения-функции**, нажмите клавишу **ввод**.</span><span class="sxs-lookup"><span data-stu-id="3490b-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![Поиск приложения-функции](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="3490b-313">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="3490b-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="3490b-314">Новая страница будет предоставить описание **приложения-функции** службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="3490b-315">В нижней левой части этого запроса, выберите **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="3490b-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![экземпляре приложения-функции](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="3490b-317">Когда вы перейдете на **создать**, задайте приведенные ниже:</span><span class="sxs-lookup"><span data-stu-id="3490b-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="3490b-318">Для **имя_приложения**, вставить желаемого имени для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="3490b-319">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="3490b-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="3490b-320">Выберите ценовую категорию, соответствующие, если это первое время создания **функция службы приложений**, уровень "бесплатный" должны быть доступны для вас.</span><span class="sxs-lookup"><span data-stu-id="3490b-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="3490b-321">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="3490b-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="3490b-322">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="3490b-323">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="3490b-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="3490b-324">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="3490b-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="3490b-325">Для **ОС**, нажмите кнопку Windows, так как целевую платформу.</span><span class="sxs-lookup"><span data-stu-id="3490b-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="3490b-326">Выберите **текущему плану размещения и** (этот учебник использование **план потребления**.</span><span class="sxs-lookup"><span data-stu-id="3490b-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="3490b-327">Выберите **расположение** **(выберите то же расположение, как хранилище, вы создали на предыдущем шаге)**</span><span class="sxs-lookup"><span data-stu-id="3490b-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="3490b-328">Для **хранения** разделе **необходимо выбрать службу хранения, созданную на предыдущем шаге**.</span><span class="sxs-lookup"><span data-stu-id="3490b-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="3490b-329">Вам не потребуется *Application Insights* в этом приложении, поэтому вы можете оставить его **Off**.</span><span class="sxs-lookup"><span data-stu-id="3490b-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="3490b-330">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="3490b-330">Click **Create**.</span></span>

        ![Создайте новый экземпляр](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="3490b-332">Когда вы перейдете на **создать** имеется ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="3490b-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="3490b-333">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![новое уведомление](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="3490b-335">Щелкните уведомлений для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="3490b-336">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="3490b-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Перейти к ресурсу](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="3490b-338">Нажмите кнопку **+** (плюс) значок рядом с полем *функции*, *создать*.</span><span class="sxs-lookup"><span data-stu-id="3490b-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Добавление новой функции](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="3490b-340">На центральной панели **функция** откроется окно создания.</span><span class="sxs-lookup"><span data-stu-id="3490b-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="3490b-341">Пропустили информацию в верхней половине панели и нажмите кнопку **пользовательская функция**, который находится ближе к нижней (в синей области, как показано ниже).</span><span class="sxs-lookup"><span data-stu-id="3490b-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="3490b-343">На новой странице в окне будет отображаться различные типы функций.</span><span class="sxs-lookup"><span data-stu-id="3490b-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="3490b-344">Прокрутите вниз, чтобы просмотреть типы сиреневый и нажмите кнопку **HTTP PUT** элемент.</span><span class="sxs-lookup"><span data-stu-id="3490b-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![HTTP put ссылку](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="3490b-346">Может потребоваться переместитесь дальше в списке страницы (и этот образ может выглядеть точно так же, если производились обновления портала Azure), однако вы ищете элемент, названный *HTTP PUT*.</span><span class="sxs-lookup"><span data-stu-id="3490b-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="3490b-347">**HTTP PUT** появится окно, где необходимо настроить функцию (см. ниже изображения).</span><span class="sxs-lookup"><span data-stu-id="3490b-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="3490b-348">Для **языка,** с помощью раскрывающегося меню выберите C\#.</span><span class="sxs-lookup"><span data-stu-id="3490b-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="3490b-349">Для **имя** введите соответствующее имя.</span><span class="sxs-lookup"><span data-stu-id="3490b-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="3490b-350">В **уровень проверки подлинности** раскрывающемся меню выберите **функция**.</span><span class="sxs-lookup"><span data-stu-id="3490b-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="3490b-351">Для **имя таблицы** разделе, необходимо использовать правильное имя, вы использовали для создания вашего **таблицы** службы ранее (включая тот же регистр букв).</span><span class="sxs-lookup"><span data-stu-id="3490b-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="3490b-352">В рамках **подключение к учетной записи хранения** раздела, из раскрывающегося меню и выберите свою учетную запись хранения из него.</span><span class="sxs-lookup"><span data-stu-id="3490b-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="3490b-353">Если он не существует, щелкните **New** hyperlink наряду с название раздела, чтобы показать другую панель, где должна быть указана вашей учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="3490b-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![новое хранилище](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="3490b-355">Нажмите кнопку **создать** и вы получите уведомление, что ваши параметры успешно обновлены.</span><span class="sxs-lookup"><span data-stu-id="3490b-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![Создание функции](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="3490b-357">После нажатия кнопки **создать**, вы будете перенаправлены к редактору функции.</span><span class="sxs-lookup"><span data-stu-id="3490b-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![Обновление кода функции](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="3490b-359">Вставьте следующий код в редакторе функцию (заменив код в функции):</span><span class="sxs-lookup"><span data-stu-id="3490b-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="3490b-360">С помощью включенных библиотек, эта функция получает имя и расположение объекта, который был перемещен в сцене Unity (как C# объекта, называемого **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="3490b-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="3490b-361">Затем этот объект используется для обновления параметров объектов в созданной таблице.</span><span class="sxs-lookup"><span data-stu-id="3490b-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="3490b-362">После этого функция делает вызов к службе созданный концентратор уведомлений, который уведомляет о всех подписанных приложений.</span><span class="sxs-lookup"><span data-stu-id="3490b-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="3490b-363">С помощью кода в месте, нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="3490b-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="3490b-364">Затем щелкните **\<** значок (стрелка), в правой части страницы.</span><span class="sxs-lookup"><span data-stu-id="3490b-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Откройте передачи панели](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="3490b-366">Панель будет слайд в справа.</span><span class="sxs-lookup"><span data-stu-id="3490b-366">A panel will slide in from the right.</span></span> <span data-ttu-id="3490b-367">В этой панели, щелкните **отправить**, и будет отображаться в обозревателе файлов.</span><span class="sxs-lookup"><span data-stu-id="3490b-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="3490b-368">Перейдите к и нажмите кнопку, **project.json** файл, который вы создали в **Блокнот** ранее и нажмите кнопку **откройте** кнопки.</span><span class="sxs-lookup"><span data-stu-id="3490b-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="3490b-369">Этот файл определяет библиотеки, на которые будет использовать функции.</span><span class="sxs-lookup"><span data-stu-id="3490b-369">This file defines the libraries that your function will use.</span></span>

    ![Отправка json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="3490b-371">Когда файл отправлен, он будет отображаться на панели справа.</span><span class="sxs-lookup"><span data-stu-id="3490b-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="3490b-372">Если щелкнуть его, откроется его в **функция** редактора.</span><span class="sxs-lookup"><span data-stu-id="3490b-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="3490b-373">Он должен выглядеть **точно** так же, как Далее (см. ниже шаг 23).</span><span class="sxs-lookup"><span data-stu-id="3490b-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="3490b-374">Затем в панели слева, под **функции**, нажмите кнопку **интегрировать** ссылку.</span><span class="sxs-lookup"><span data-stu-id="3490b-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![Интегрируйте функции](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="3490b-376">На следующей странице в правом верхнем углу, щелкните **расширенный редактор** (как показано ниже).</span><span class="sxs-lookup"><span data-stu-id="3490b-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![откройте расширенный редактор](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="3490b-378">Объект **function.json** на центральной панели, который необходимо заменить на следующий фрагмент кода будет открыт файл.</span><span class="sxs-lookup"><span data-stu-id="3490b-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="3490b-379">Он определяет функцию, вы создаете и параметры передаваемые в функцию.</span><span class="sxs-lookup"><span data-stu-id="3490b-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="3490b-380">В редакторе теперь должна выглядеть как на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="3490b-380">Your editor should now look like the image below:</span></span>

    ![к стандартным редактором](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="3490b-382">Вы можете заметить, входные параметры, которые добавлены может не соответствовать сведениях о таблице и хранилище и поэтому потребуется обновить, используя ваши сведения.</span><span class="sxs-lookup"><span data-stu-id="3490b-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="3490b-383">**Не делайте этого, здесь**, как оно описано далее.</span><span class="sxs-lookup"><span data-stu-id="3490b-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="3490b-384">Просто щелкните **стандартный редактор** ссылку в правом верхнем углу страницы, чтобы вернуться назад.</span><span class="sxs-lookup"><span data-stu-id="3490b-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="3490b-385">Вернитесь в **стандартный редактор**, нажмите кнопку **Azure Table Storage (таблица)** в разделе **входных данных**.</span><span class="sxs-lookup"><span data-stu-id="3490b-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Входные данные таблицы](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="3490b-387">Следующие совпадение, чтобы обеспечить **вашей** сведения, как они могут отличаться (есть изображения до размера менее ниже):</span><span class="sxs-lookup"><span data-stu-id="3490b-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="3490b-388">**Имя таблицы**: имя таблицы, созданной в хранилище Azure, служба таблиц.</span><span class="sxs-lookup"><span data-stu-id="3490b-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="3490b-389">**Подключение к учетной записи хранения:** щелкните **новый**, которая отображается вместе с в раскрывающемся меню и панель будет отображаться в правой части окна.</span><span class="sxs-lookup"><span data-stu-id="3490b-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![новое хранилище](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="3490b-391">Выберите ваш **учетной записи хранения**, который был создан ранее для размещения **приложения-функции.**</span><span class="sxs-lookup"><span data-stu-id="3490b-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="3490b-392">Можно будет заметить, что **учетной записи хранения** значение подключения будет создана.</span><span class="sxs-lookup"><span data-stu-id="3490b-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="3490b-393">Убедитесь, что клавишу **Сохранить** после завершения.</span><span class="sxs-lookup"><span data-stu-id="3490b-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="3490b-394">**Входные данные** странице теперь должно соответствовать ниже, показывающий **вашей** сведения.</span><span class="sxs-lookup"><span data-stu-id="3490b-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![завершить входных данных](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="3490b-396">Затем щелкните **Azure центра уведомлений (уведомление)** — в разделе **выходные данные**.</span><span class="sxs-lookup"><span data-stu-id="3490b-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="3490b-397">Убедитесь, соответствуют следующие **вашей** сведения, как они могут отличаться (есть изображения до размера менее ниже):</span><span class="sxs-lookup"><span data-stu-id="3490b-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="3490b-398">**Имя концентратора уведомлений**: это имя вашего **концентратора уведомлений** экземпляр службы, который был создан ранее.</span><span class="sxs-lookup"><span data-stu-id="3490b-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="3490b-399">**Подключение к пространству имен концентраторов уведомлений**: щелкните **новый**, которая отображается вместе с в раскрывающемся меню.</span><span class="sxs-lookup"><span data-stu-id="3490b-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![Проверьте выходные данные](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="3490b-401">**Подключения** Откроется всплывающее окно (см. рисунок ниже), где необходимо выбрать **пространства имен** из **концентратора уведомлений**, настроенной ранее.</span><span class="sxs-lookup"><span data-stu-id="3490b-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="3490b-402">Выберите ваш **концентратора уведомлений** имя в среднем раскрывающемся меню.</span><span class="sxs-lookup"><span data-stu-id="3490b-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="3490b-403">Задайте **политики** раскрывающемся меню **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="3490b-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="3490b-404">Нажмите кнопку **выберите** кнопку, чтобы вернуться назад.</span><span class="sxs-lookup"><span data-stu-id="3490b-404">Click the **Select** button to go back.</span></span>

        ![Обновление выходных данных](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="3490b-406">**Выходные данные** странице теперь должно соответствовать ниже, но с **вашей** сведения вместо этого.</span><span class="sxs-lookup"><span data-stu-id="3490b-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="3490b-407">Убедитесь, что клавишу **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="3490b-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="3490b-408">*Не изменять имя центра уведомлений напрямую* (должны все это сделать с помощью **расширенный редактор**, если предыдущие шаги выполнены правильно.</span><span class="sxs-lookup"><span data-stu-id="3490b-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![Выводит полный](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="3490b-410">На этом этапе следует протестировать функцию, чтобы убедиться, что он работает.</span><span class="sxs-lookup"><span data-stu-id="3490b-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="3490b-411">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="3490b-411">To do this:</span></span> 

    1. <span data-ttu-id="3490b-412">Перейдите на страницу функции еще раз:</span><span class="sxs-lookup"><span data-stu-id="3490b-412">Navigate to the function page once more:</span></span>

        ![Выводит полный](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="3490b-414">На странице «функция» нажмите **теста** вкладка в крайней правой части страницы, чтобы открыть *теста* колонке:</span><span class="sxs-lookup"><span data-stu-id="3490b-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![Выводит полный](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="3490b-416">В рамках **текст запроса** textbox колонки вставить ниже кода:</span><span class="sxs-lookup"><span data-stu-id="3490b-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="3490b-417">Тестовый код на месте, щелкните **запуска** кнопку в правом нижнем углу, а тест будет выполняться.</span><span class="sxs-lookup"><span data-stu-id="3490b-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="3490b-418">Журналы выходные данные теста будут отображаться в области консоли под код функции.</span><span class="sxs-lookup"><span data-stu-id="3490b-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![Выводит полный](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="3490b-420">Если выше тест не пройден, необходимо тщательно проверить, что указанные выше шаги выполнены точно, особенно параметров в рамках **интегрировать панели**.</span><span class="sxs-lookup"><span data-stu-id="3490b-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="3490b-421">Глава 7 - Настройка проекта Unity рабочего стола</span><span class="sxs-lookup"><span data-stu-id="3490b-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3490b-422">Классическое приложение, в которой вы создаете теперь **не** работают в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="3490b-423">Он должен быть запущен вне редактора, выполнив построение приложения, с помощью Visual Studio (или развернутое приложение).</span><span class="sxs-lookup"><span data-stu-id="3490b-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="3490b-424">Следующие запущена типичный набор для разработки с помощью Unity и смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="3490b-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="3490b-425">Настроить и проверить ваш иммерсивных гарнитуры смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="3490b-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="3490b-426">Вы будете **не** требуются контроллеры движения курс с демороликами.</span><span class="sxs-lookup"><span data-stu-id="3490b-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="3490b-427">Если вам нужна поддерживает настройку иммерсивных гарнитуры, выполните инструкции из этого [ссылку о том, как настроить Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="3490b-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="3490b-428">Откройте **Unity** и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="3490b-428">Open **Unity** and click **New**.</span></span>

    ![новый проект unity](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="3490b-430">Необходимо указать имя проекта Unity, вставить **UnityDesktopNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="3490b-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="3490b-431">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="3490b-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="3490b-432">Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="3490b-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="3490b-433">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="3490b-433">Then, click **Create project**.</span></span>

    ![Создание проекта](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="3490b-435">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3490b-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="3490b-436">Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="3490b-436">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="3490b-437">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="3490b-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="3490b-438">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="3490b-438">Close the **Preferences** window.</span></span>

    ![набор внешних инструментов VS](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="3490b-440">Перейдите к **файл > Параметры сборки** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** кнопку, чтобы применить выбранные параметры.</span><span class="sxs-lookup"><span data-stu-id="3490b-440">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![переключение платформ](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="3490b-442">Оставаясь в **файл > Параметры сборки**, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="3490b-442">While still in **File > Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="3490b-443">**Целевое устройство** присваивается **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="3490b-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="3490b-444">Это приложение будет для рабочего стола, поэтому должны быть **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="3490b-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="3490b-445">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="3490b-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="3490b-446">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="3490b-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="3490b-447">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="3490b-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="3490b-448">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="3490b-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="3490b-449">Здесь стоит сохранение сцены и его добавления к сборке.</span><span class="sxs-lookup"><span data-stu-id="3490b-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="3490b-450">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="3490b-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="3490b-451">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="3490b-451">A save window will appear.</span></span>

            ![Добавление открытых сцен](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="3490b-453">Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="3490b-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Новая папка сцены](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="3490b-455">Откройте только что созданный **сцены** папку, а затем в **имя файла:** текстовое поле, тип **NH\_рабочего стола\_сцены**, нажмите клавишу **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="3490b-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![новый NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="3490b-457">Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="3490b-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="3490b-458">В одном окне щелкните **параметры проигрывателя** кнопки откроется панель связанных в пространстве где **инспектор** находится.</span><span class="sxs-lookup"><span data-stu-id="3490b-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="3490b-459">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="3490b-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="3490b-460">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="3490b-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="3490b-461">**Версия среды выполнения сценариев** должно быть **экспериментальная (эквивалент 4.6 .NET)**</span><span class="sxs-lookup"><span data-stu-id="3490b-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="3490b-462">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="3490b-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="3490b-463">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="3490b-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![версия 4.6 net](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="3490b-465">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="3490b-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="3490b-466">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="3490b-466">**InternetClient**</span></span>

            ![Интернет-клиент делений](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="3490b-468">Вернитесь в **параметры построения** *Unity C\# проекты* больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="3490b-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="3490b-469">Закрыть **параметры построения** окна.</span><span class="sxs-lookup"><span data-stu-id="3490b-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="3490b-470">Сохраните сцену и проекта \**файл > Сохранить сцену* / \* файл > Сохранить проект \*\*.</span><span class="sxs-lookup"><span data-stu-id="3490b-470">Save your Scene and Project \**File > Save Scene* / \*File > Save Project\*\*.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3490b-471">Если вы хотите пропустить *Настройка Unity* компонента для этого проекта (приложение рабочего стола) и по-прежнему непосредственно в код, вы можете [загрузить этот .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="3490b-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="3490b-472">По-прежнему необходимо будет добавить компонентов скрипта.</span><span class="sxs-lookup"><span data-stu-id="3490b-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="3490b-473">Глава 8 - импорт библиотеки DLL в Unity</span><span class="sxs-lookup"><span data-stu-id="3490b-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="3490b-474">Вы будете использовать службу хранилища Azure для Unity (который сам использует пакет SDK для Azure .net).</span><span class="sxs-lookup"><span data-stu-id="3490b-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="3490b-475">Дополнительные сведения по этой [ссылку о службе хранилища Azure для Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="3490b-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="3490b-476">В Unity, который требует подключаемых модулей, чтобы повторно настроить после импорта в настоящее время имеется известная проблема.</span><span class="sxs-lookup"><span data-stu-id="3490b-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="3490b-477">Эти шаги (4 – 7 в этом разделе), не будет обязательным после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="3490b-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="3490b-478">Чтобы импортировать пакет SDK в свой проект, убедитесь, что вы скачали последнюю версию [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) из GitHub.</span><span class="sxs-lookup"><span data-stu-id="3490b-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="3490b-479">Затем сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="3490b-479">Then, do the following:</span></span>

1.  <span data-ttu-id="3490b-480">Добавить **.unitypackage** к Unity с помощью **активы \> Импорт пакета \> пользовательского пакета** пункт меню.</span><span class="sxs-lookup"><span data-stu-id="3490b-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="3490b-481">В **Импорт пакета Unity** поле, отобразятся, вы сможете выбрать все данные \*\**подключаемый модуль* \> \* хранилища \*\*\*.</span><span class="sxs-lookup"><span data-stu-id="3490b-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="3490b-482">Снимите флажок, все остальное, так как он не требуется для этого курса.</span><span class="sxs-lookup"><span data-stu-id="3490b-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Импорт пакета](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="3490b-484">Нажмите кнопку ***импорта*** кнопку, чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="3490b-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="3490b-485">Перейдите к **хранения** папке **подключаемые модули** в проекте можно просматривать и выбирать следующие подключаемые модули *только*:</span><span class="sxs-lookup"><span data-stu-id="3490b-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="3490b-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="3490b-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="3490b-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="3490b-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="3490b-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="3490b-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="3490b-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="3490b-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="3490b-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="3490b-490">System.Spatial</span></span>

![Снимите флажок для любой платформы](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="3490b-492">С помощью *этих конкретных подключаемых модулей* выбран, **снимите** **Any платформы** и **снимите флажок** **WSAPlayer** Нажмите кнопку **применить**.</span><span class="sxs-lookup"><span data-stu-id="3490b-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![Применение платформы библиотек DLL](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="3490b-494">Мы отмечаем эти определенного подключаемые модули можно использовать только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="3490b-495">Это, так как существуют различные версии одной подключаемые модули в папку WSA, которая будет использоваться после проект будет экспортирован из Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="3490b-496">В **хранения** папку подключаемый модуль, выберите только:</span><span class="sxs-lookup"><span data-stu-id="3490b-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="3490b-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="3490b-497">Microsoft.Data.Services.Client</span></span>

        ![не обрабатывать набор библиотек DLL](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="3490b-499">Проверьте **процесса не** поле в разделе **параметры платформы** и нажмите кнопку ***применить***.</span><span class="sxs-lookup"><span data-stu-id="3490b-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![применить без обработки](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="3490b-501">Мы отмечаем этот подключаемый модуль «Не обрабатывать», так как средство исправления сборки Unity имеет сложности обработки этот подключаемый модуль.</span><span class="sxs-lookup"><span data-stu-id="3490b-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="3490b-502">Подключаемый модуль по-прежнему будет работать, несмотря на то, что он не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="3490b-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="3490b-503">Глава 9 — создать класс TableToScene в проекте Unity рабочего стола</span><span class="sxs-lookup"><span data-stu-id="3490b-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="3490b-504">Теперь необходимо создать скрипты, содержащий код для запуска этого приложения.</span><span class="sxs-lookup"><span data-stu-id="3490b-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="3490b-505">Первый скрипт, чтобы создать **TableToScene**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="3490b-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="3490b-506">Читать сущности таблицы Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="3490b-507">С помощью данных из таблицы, определить, какие объекты для создания и их расположение.</span><span class="sxs-lookup"><span data-stu-id="3490b-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="3490b-508">Второй сценарий, вам нужно создать — **CloudScene**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="3490b-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="3490b-509">Регистрация событий левой кнопкой мыши щелкните, чтобы разрешить пользователю перетаскивать объекты относительно сцены.</span><span class="sxs-lookup"><span data-stu-id="3490b-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="3490b-510">Сериализация данных объекта из этой сценой Unity и их отправки в приложение-функцию Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="3490b-511">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="3490b-511">To create this class:</span></span>

1.  <span data-ttu-id="3490b-512">Щелкните правой кнопкой мыши в **активов** папка находится в панели «проект» **Создать > Папка**.</span><span class="sxs-lookup"><span data-stu-id="3490b-512">Right-click in the **Asset** Folder located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="3490b-513">Назовите папку **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="3490b-513">Name the folder **Scripts**.</span></span>

    ![Создайте папку скриптов](images/AzureLabs-Lab8-66.png)

    ![Создайте папку сценарии 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="3490b-516">Дважды щелкните папку, только что создали, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="3490b-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="3490b-517">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать** **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="3490b-517">Right-click inside the **Scripts** folder, click **Create** **C\# Script**.</span></span> <span data-ttu-id="3490b-518">Назовите сценарий **TableToScene**.</span><span class="sxs-lookup"><span data-stu-id="3490b-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="3490b-519">![скрипт c#](images/AzureLabs-Lab8-68.png)
    ![TableToScene переименования](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="3490b-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="3490b-520">Дважды щелкните его, чтобы открыть его в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="3490b-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="3490b-521">Добавьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="3490b-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="3490b-522">К классу вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="3490b-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="3490b-523">Substitute **accountName** значение с именем вашей службы хранилища Azure и **accountKey** значение со значением ключа, имеющиеся в службе хранилища Azure, на портале Azure (см. рисунок ниже).</span><span class="sxs-lookup"><span data-stu-id="3490b-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![ключ учетной записи выборки](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="3490b-525">Теперь добавьте **Start()** и **Awake()** методы для инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="3490b-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="3490b-526">В рамках **TableToScene** добавьте метод, который будет извлекать значения из таблиц Azure и использовать их для создания соответствующих примитивы в сцене.</span><span class="sxs-lookup"><span data-stu-id="3490b-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="3490b-527">За пределами **TableToScene** класса, необходимо определить класс, используемый приложением для сериализации и десериализации **сущностей таблицы**.</span><span class="sxs-lookup"><span data-stu-id="3490b-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="3490b-528">Убедитесь, что **Сохранить** перед вернуться в редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="3490b-529">Нажмите кнопку **Main Camera** из **иерархии** панели, чтобы ее свойства появились на **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="3490b-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="3490b-530">С помощью **сценарии** папку открыт, выберите сценарий **файл TableToScene** и перетащите его на **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="3490b-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="3490b-531">Результат должен быть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3490b-531">The result should be as below:</span></span>

    ![Добавьте скрипт к главной камеры](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="3490b-533">Глава 10 — создать класс CloudScene в проекте Unity рабочего стола</span><span class="sxs-lookup"><span data-stu-id="3490b-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="3490b-534">Второй сценарий, вам нужно создать — **CloudScene**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="3490b-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="3490b-535">Регистрация событий левой кнопкой мыши щелкните, чтобы разрешить пользователю перетаскивать объекты относительно сцены.</span><span class="sxs-lookup"><span data-stu-id="3490b-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="3490b-536">Сериализация данных объекта из этой сценой Unity и их отправки в приложение-функцию Azure.</span><span class="sxs-lookup"><span data-stu-id="3490b-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="3490b-537">Чтобы создать второй скрипт:</span><span class="sxs-lookup"><span data-stu-id="3490b-537">To create the second script:</span></span>

1.  <span data-ttu-id="3490b-538">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**, **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="3490b-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="3490b-539">Назовите сценарий **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="3490b-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="3490b-540">![скрипт c#](images/AzureLabs-Lab8-72.png)
    ![переименовать CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="3490b-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="3490b-541">Добавьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="3490b-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="3490b-542">Вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="3490b-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="3490b-543">Substitute **azureFunctionEndpoint** значение URL приложения функции Azure, находится в службе приложений Azure функцию на портале Azure, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="3490b-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![получить URL-адрес функции](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="3490b-545">Теперь добавьте **Start()** и **Awake()** методы для инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="3490b-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="3490b-546">В рамках **Update()** метод, добавьте следующий код, который обнаруживает ввод от мыши и перетащите элемент, который в свою очередь будет переместить объекты Gameobject в сцене.</span><span class="sxs-lookup"><span data-stu-id="3490b-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="3490b-547">Если пользователь перетащен объекта, он передает названия и координат объекта метод **UpdateCloudScene()**, который будет вызывать службу приложения-функции Azure, которая обновит Azure таблицы и триггера уведомление.</span><span class="sxs-lookup"><span data-stu-id="3490b-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="3490b-548">Теперь добавьте **UpdateCloudScene()** метод, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="3490b-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="3490b-549">Сохраните код и вернуться к Unity</span><span class="sxs-lookup"><span data-stu-id="3490b-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="3490b-550">Перетащите **CloudScene** скрипт на **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="3490b-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="3490b-551">Нажмите кнопку **Main Camera** из **иерархии** панели, чтобы ее свойства появились на **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="3490b-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="3490b-552">С помощью **сценарии** открыт, выберите папку **CloudScene** сценариев и перетащите его на **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="3490b-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="3490b-553">Результат должен быть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3490b-553">The result should be as below:</span></span>

        > ![Перетащите скрипта cloud главной камеры](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="3490b-555">Глава 11 — построить проект для настольной системы для универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="3490b-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="3490b-556">Все необходимое для раздела этого проекта Unity теперь завершен.</span><span class="sxs-lookup"><span data-stu-id="3490b-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="3490b-557">Перейдите к **параметры сборки** (**файл > Параметры сборки**).</span><span class="sxs-lookup"><span data-stu-id="3490b-557">Navigate to **Build Settings** (**File > Build Settings**).</span></span>

2.  <span data-ttu-id="3490b-558">Из **параметры построения** окно, нажмите кнопку **построения**.</span><span class="sxs-lookup"><span data-stu-id="3490b-558">From the **Build Settings** window, click **Build**.</span></span>

    ![Сборка проекта](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="3490b-560">Объект **проводнике** будет контекстном меню окна, для расположения для сборки.</span><span class="sxs-lookup"><span data-stu-id="3490b-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="3490b-561">Создайте новую папку (щелкнув **новую папку** в левом верхнем углу) и назовите его **ПОСТРОЕНИЯ**.</span><span class="sxs-lookup"><span data-stu-id="3490b-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![новую папку для сборки](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="3490b-563">Откройте новый **ПОСТРОЕНИЯ** папки и создайте другую папку (с помощью **новую папку** еще раз) и назовите его **NH\_Desktop\_приложения**.</span><span class="sxs-lookup"><span data-stu-id="3490b-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![Имя папки NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="3490b-565">С помощью **NH\_Desktop\_приложения** выбранного.</span><span class="sxs-lookup"><span data-stu-id="3490b-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="3490b-566">Нажмите кнопку **выберите папку**.</span><span class="sxs-lookup"><span data-stu-id="3490b-566">click **Select Folder**.</span></span> <span data-ttu-id="3490b-567">Проекта займет около минуты для построения.</span><span class="sxs-lookup"><span data-stu-id="3490b-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="3490b-568">После построения **проводнике** появится расположение нового проекта.</span><span class="sxs-lookup"><span data-stu-id="3490b-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="3490b-569">Нет необходимости, чтобы открыть его, то, что, как вам нужно создать другой Unity project во-первых, в следующие несколько глав посвящены.</span><span class="sxs-lookup"><span data-stu-id="3490b-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="3490b-570">Глава 12 - Настройка проекта Unity смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="3490b-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="3490b-571">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="3490b-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="3490b-572">Откройте **Unity** и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="3490b-572">Open **Unity** and click **New**.</span></span>

    ![новый проект unity](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="3490b-574">Введите имя проекта Unity, теперь нужно вставить **UnityMRNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="3490b-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="3490b-575">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="3490b-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="3490b-576">Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="3490b-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="3490b-577">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="3490b-577">Then, click **Create project**.</span></span>

    ![Имя UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="3490b-579">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3490b-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="3490b-580">Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="3490b-580">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="3490b-581">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="3490b-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="3490b-582">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="3490b-582">Close the **Preferences** window.</span></span>

    ![набор внешний редактор в Visual STUDIO](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="3490b-584">Перейдите к **файл > Параметры сборки** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.</span><span class="sxs-lookup"><span data-stu-id="3490b-584">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![переключение платформ для универсальной платформы Windows](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="3490b-586">Перейдите к **файл > Параметры сборки** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="3490b-586">Go to **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="3490b-587">**Целевое устройство** присваивается **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="3490b-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="3490b-588">Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="3490b-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="3490b-589">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="3490b-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="3490b-590">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="3490b-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="3490b-591">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="3490b-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="3490b-592">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="3490b-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="3490b-593">Здесь стоит сохранение сцены и его добавления к сборке.</span><span class="sxs-lookup"><span data-stu-id="3490b-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="3490b-594">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="3490b-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="3490b-595">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="3490b-595">A save window will appear.</span></span>

            ![Добавление открытых сцен](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="3490b-597">Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="3490b-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Новая папка сцены](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="3490b-599">Откройте только что созданный **сцены** папку, а затем в **имя файла:** текстовое поле, тип **NH\_MR\_сцены**, нажмите клавишу  **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="3490b-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![создать сцену - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="3490b-601">Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="3490b-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="3490b-602">В одном окне щелкните **параметры проигрывателя** кнопки откроется панель связанных в пространстве где **инспектор** находится.</span><span class="sxs-lookup"><span data-stu-id="3490b-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![Открытие параметров проигрывателя](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="3490b-604">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="3490b-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="3490b-605">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="3490b-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="3490b-606">**Версия среды выполнения сценариев** должно быть **экспериментальные** (.NET 4.6 эквивалент)</span><span class="sxs-lookup"><span data-stu-id="3490b-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="3490b-607">**Создание сценариев серверной части** должно быть ***.NET***</span><span class="sxs-lookup"><span data-stu-id="3490b-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="3490b-608">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="3490b-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![совместимость API](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="3490b-610">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется</span><span class="sxs-lookup"><span data-stu-id="3490b-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Обновление параметров xr](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="3490b-612">В рамках **параметров публикации** в списке **возможности**, выполнить проверку:</span><span class="sxs-lookup"><span data-stu-id="3490b-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="3490b-613">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="3490b-613">**InternetClient**</span></span>           

            ![Интернет-клиент делений](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="3490b-615">Вернитесь в **параметры построения** *Unity C\# проекты* больше не отображается серым: установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="3490b-615">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="3490b-616">Эти изменения закрывайте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="3490b-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="3490b-617">Сохраните сцену и проекта \**файл* *сохранить сцену*/ *файл* \* сохранить проект \*\*.</span><span class="sxs-lookup"><span data-stu-id="3490b-617">Save your Scene and Project \**File* *Save Scene*/ *File* \*Save Project\*\*.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3490b-618">Если вы хотите пропустить *Настройка Unity* компонента для этого проекта (смешанной реальности приложения) и по-прежнему непосредственно в код, вы можете [загрузить этот .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="3490b-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="3490b-619">По-прежнему необходимо будет добавить компонентов скрипта.</span><span class="sxs-lookup"><span data-stu-id="3490b-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="3490b-620">Глава 13 - импорт библиотеки DLL в проекте Unity смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="3490b-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="3490b-621">Вы будете использовать службу хранилища Azure для библиотеки Unity (с использованием пакета SDK для .net для Azure).</span><span class="sxs-lookup"><span data-stu-id="3490b-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="3490b-622">Выполните инструкции из этого [ссылку на использование хранилища Azure с помощью Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="3490b-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="3490b-623">В Unity, который требует подключаемых модулей, чтобы повторно настроить после импорта в настоящее время имеется известная проблема.</span><span class="sxs-lookup"><span data-stu-id="3490b-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="3490b-624">Эти шаги (4 – 7 в этом разделе), не будет обязательным после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="3490b-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="3490b-625">Чтобы импортировать пакет SDK в свой проект, убедитесь, что вы скачали последнюю версию [.unitypackage](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="3490b-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="3490b-626">Затем сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="3490b-626">Then, do the following:</span></span>

1.  <span data-ttu-id="3490b-627">Добавление .unitypackage, загруженный из указанного выше, для Unity с помощью **ресурсы > Импорт пакета > Custom Package** пункт меню.</span><span class="sxs-lookup"><span data-stu-id="3490b-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="3490b-628">В **Импорт пакета Unity** поле, отобразятся, вы сможете выбрать все данные **подключаемый модуль > хранилища**.</span><span class="sxs-lookup"><span data-stu-id="3490b-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin > Storage**.</span></span>

    ![Импорт пакета](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="3490b-630">Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="3490b-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="3490b-631">Перейдите к **хранения** папке **подключаемые модули** в проекте можно просматривать и выбирать следующие подключаемые модули *только*:</span><span class="sxs-lookup"><span data-stu-id="3490b-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="3490b-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="3490b-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="3490b-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="3490b-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="3490b-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="3490b-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="3490b-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="3490b-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="3490b-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="3490b-636">System.Spatial</span></span>

    ![Выберите подключаемые модули](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="3490b-638">С помощью *этих конкретных подключаемых модулей* выбран, **снимите** **Any платформы** и **снимите флажок** **WSAPlayer** Нажмите кнопку **применить**.</span><span class="sxs-lookup"><span data-stu-id="3490b-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![применить изменения в платформе](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="3490b-640">Время разметки эти определенного подключаемые модули можно использовать только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="3490b-641">Это, так как существуют различные версии одной подключаемые модули в папку WSA, которая будет использоваться после проект будет экспортирован из Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="3490b-642">В **хранения** папку подключаемый модуль, выберите только:</span><span class="sxs-lookup"><span data-stu-id="3490b-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="3490b-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="3490b-643">Microsoft.Data.Services.Client</span></span>

        ![Выберите клиента служб данных](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="3490b-645">Проверьте **процесса не** поле в разделе **параметры платформы** и нажмите кнопку **применить**.</span><span class="sxs-lookup"><span data-stu-id="3490b-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![не обрабатывать](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="3490b-647">Время разметки этот подключаемый модуль «Не процесс» из-за сложности обработки этот подключаемый модуль средство исправления сборки Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="3490b-648">Подключаемый модуль по-прежнему будет работать, несмотря на то, что она не обработана.</span><span class="sxs-lookup"><span data-stu-id="3490b-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="3490b-649">Глава 14 - Создание TableToScene класса в проекте Unity смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="3490b-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="3490b-650">**TableToScene** совпадающее с тем, как описано в классе [Глава 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="3490b-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="3490b-651">Создание одного класса в смешанной реальности, проект Unity таким же способом, как описано в [Глава 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="3490b-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="3490b-652">После завершения этой главы, оба вашей **проектов Unity** будет иметь этот класс на Main Camera.</span><span class="sxs-lookup"><span data-stu-id="3490b-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="3490b-653">Глава 15 - Создание NotificationReceiver класса в проекте Unity смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="3490b-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="3490b-654">Второй сценарий, вам нужно создать — **NotificationReceiver**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="3490b-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="3490b-655">Регистрация приложения в центре уведомлений при инициализации.</span><span class="sxs-lookup"><span data-stu-id="3490b-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="3490b-656">Прослушивает уведомления, поступающие от концентратора уведомлений.</span><span class="sxs-lookup"><span data-stu-id="3490b-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="3490b-657">Десериализация данных объекта из полученного уведомления.</span><span class="sxs-lookup"><span data-stu-id="3490b-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="3490b-658">Переместите объекты Gameobject в сцене в зависимости от десериализованные данные.</span><span class="sxs-lookup"><span data-stu-id="3490b-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="3490b-659">Чтобы создать **NotificationReceiver** сценария:</span><span class="sxs-lookup"><span data-stu-id="3490b-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="3490b-660">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**, **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="3490b-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="3490b-661">Назовите сценарий **NotificationReceiver**.</span><span class="sxs-lookup"><span data-stu-id="3490b-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="3490b-662">![создать новый скрипт c#](images/AzureLabs-Lab8-95.png)
    ![назовите его NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="3490b-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="3490b-663">Дважды щелкните сценарий, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="3490b-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="3490b-664">Добавьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="3490b-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="3490b-665">Вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="3490b-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="3490b-666">Substitute **hubName** значение именем своего служб концентратора уведомлений и **hubListenEndpoint** значения со значением конечной точки, найти на вкладке политики доступа к службе центра уведомлений Azure, в Портал Azure (см. рисунок ниже).</span><span class="sxs-lookup"><span data-stu-id="3490b-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Вставка конечной точке политики концентраторов уведомлений](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="3490b-668">Теперь добавьте **Start()** и **Awake()** методы для инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="3490b-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="3490b-669">Добавить **WaitForNotification** метод, чтобы разрешить приложению получать уведомления из библиотеки концентратора уведомлений без конфликтов с основной поток:</span><span class="sxs-lookup"><span data-stu-id="3490b-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="3490b-670">Следующий метод, **InitNotificationAsync()**, будет зарегистрировать приложение в службе центра уведомлений при инициализации.</span><span class="sxs-lookup"><span data-stu-id="3490b-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="3490b-671">Код закомментирован, как Unity, не смогут сборки проекта.</span><span class="sxs-lookup"><span data-stu-id="3490b-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="3490b-672">Комментарии будут удалены при импорте пакета Nuget для обмена сообщениями Azure в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3490b-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="3490b-673">Следующий обработчик **канал\_PushNotificationReceived()**, будут создаваться каждый раз при получении уведомления.</span><span class="sxs-lookup"><span data-stu-id="3490b-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="3490b-674">Он десериализует уведомление, которое будет сущность таблицы Azure, который был перемещен в классическое приложение, а затем переместите соответствующий объект GameObject в сцене MR в той же позиции.</span><span class="sxs-lookup"><span data-stu-id="3490b-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="3490b-675">Код закомментирован, так как код ссылается на библиотеку обмена сообщениями Azure, которая будет добавлен после создания проекта Unity, используя диспетчер пакетов Nuget в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3490b-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="3490b-676">Таким образом проект Unity невозможна для построения, если только он закомментирован. Имейте в виду, что следует построить проект и затем хотите вернуться к Unity, необходимо будет **повторно комментарий** этого кода.</span><span class="sxs-lookup"><span data-stu-id="3490b-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="3490b-677">Не забудьте сохранить изменения перед вернуться в редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="3490b-678">Нажмите кнопку **Main Camera** из **иерархии** панели, чтобы ее свойства появились на **инспектор**.</span><span class="sxs-lookup"><span data-stu-id="3490b-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="3490b-679">С помощью **сценарии** открыт, выберите папку **NotificationReceiver** сценариев и перетащите его на **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="3490b-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="3490b-680">Результат должен быть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3490b-680">The result should be as below:</span></span>

    ![Перетащите сценарий получателя уведомлений к камере](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="3490b-682">Если вы разрабатываете для Microsoft HoloLens, необходимо обновить **Main Camera** *камеры* компонента, таким образом, чтобы:</span><span class="sxs-lookup"><span data-stu-id="3490b-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="3490b-683">Очистите флаги: Сплошным цветом</span><span class="sxs-lookup"><span data-stu-id="3490b-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="3490b-684">Фон: Черный</span><span class="sxs-lookup"><span data-stu-id="3490b-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="3490b-685">Глава 16 — построение проекта смешанной реальности для универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="3490b-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="3490b-686">В этой главе идентична процесс для предыдущий проект сборки.</span><span class="sxs-lookup"><span data-stu-id="3490b-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="3490b-687">Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.</span><span class="sxs-lookup"><span data-stu-id="3490b-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="3490b-688">Перейдите к **параметры сборки** ( **файл > Параметры сборки...**  ).</span><span class="sxs-lookup"><span data-stu-id="3490b-688">Navigate to **Build Settings** ( **File > Build Settings...** ).</span></span>

2.  <span data-ttu-id="3490b-689">Из **параметры построения** меню, убедитесь, **Unity C# проекты**\* установлен (что позволит редактировать сценарии в этом проекте, после сборки).</span><span class="sxs-lookup"><span data-stu-id="3490b-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="3490b-690">После этого нажмите кнопку **построения**.</span><span class="sxs-lookup"><span data-stu-id="3490b-690">After this is done, click **Build**.</span></span>

    ![Сборка проекта](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="3490b-692">Объект **проводнике** будет контекстном меню окна, для расположения для сборки.</span><span class="sxs-lookup"><span data-stu-id="3490b-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="3490b-693">Создайте новую папку (щелкнув **новую папку** в левом верхнем углу) и назовите его **ПОСТРОЕНИЯ**.</span><span class="sxs-lookup"><span data-stu-id="3490b-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Создайте папку builds](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="3490b-695">Откройте новый **ПОСТРОЕНИЯ** папки и создайте другую папку (с помощью **новую папку** еще раз) и назовите его **NH\_MR\_приложения**.</span><span class="sxs-lookup"><span data-stu-id="3490b-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![Создайте папку NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="3490b-697">С помощью **NH\_MR\_приложения** выбранного.</span><span class="sxs-lookup"><span data-stu-id="3490b-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="3490b-698">Нажмите кнопку **выберите папку**.</span><span class="sxs-lookup"><span data-stu-id="3490b-698">click **Select Folder**.</span></span> <span data-ttu-id="3490b-699">Проекта займет около минуты для построения.</span><span class="sxs-lookup"><span data-stu-id="3490b-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="3490b-700">После построения, **проводнике** в расположение нового проекта откроется окно.</span><span class="sxs-lookup"><span data-stu-id="3490b-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="3490b-701">Глава 17 - добавить пакеты NuGet в решение UnityMRNotifHub</span><span class="sxs-lookup"><span data-stu-id="3490b-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="3490b-702">Обратите внимание, добавив следующие пакеты NuGet (и раскомментируйте код в следующем [глава](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class)), код, при повторном открытии в проекте Unity, представит ошибки.</span><span class="sxs-lookup"><span data-stu-id="3490b-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="3490b-703">Если вы хотите вернуться назад и продолжить редактирование в редакторе Unity, вам необходимо комментарий errosome кода и затем раскомментируйте позже, когда вы снова находитесь в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3490b-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="3490b-704">После завершения построения смешанной реальности, перейдите к проекту смешанной реальности, который вы создали, и дважды щелкните файл решения (SLN) в этой папке, чтобы открыть решение в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="3490b-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="3490b-705">Теперь необходимо добавить **WindowsAzure.Messaging.managed** пакета NuGet; это библиотека, которая используется для получения уведомлений из центра уведомлений.</span><span class="sxs-lookup"><span data-stu-id="3490b-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="3490b-706">Чтобы импортировать пакет NuGet:</span><span class="sxs-lookup"><span data-stu-id="3490b-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="3490b-707">В **обозревателе решений**, щелкнуть правой кнопкой мыши решение</span><span class="sxs-lookup"><span data-stu-id="3490b-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="3490b-708">Щелкните **управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3490b-708">Click on **Manage NuGet Packages**.</span></span>

    ![Откройте диспетчер nuget](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="3490b-710">Выберите ***Обзор*** вкладку и выполните поиск **WindowsAzure.Messaging.managed**.</span><span class="sxs-lookup"><span data-stu-id="3490b-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![найти обмена сообщениями пакета windows azure](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="3490b-712">Выберите результат (как показано ниже), а в окне справа установите флажок рядом с полем **проекта**.</span><span class="sxs-lookup"><span data-stu-id="3490b-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="3490b-713">Это будет помещать такт в флажок рядом с полем **проекта**, вместе с флажок рядом с полем **сборки-CSharp** и **UnityMRNotifHub** проекта.</span><span class="sxs-lookup"><span data-stu-id="3490b-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![Установка флажка все проекты](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="3490b-715">Версия, указанная изначально **может не** совместимы с этим проектом.</span><span class="sxs-lookup"><span data-stu-id="3490b-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="3490b-716">Таким образом, щелкните раскрывающееся меню рядом **версии**и нажмите кнопку **версии 0.1.7.9**, затем нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="3490b-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="3490b-717">Вы завершили установки пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="3490b-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="3490b-718">Найти закомментированный код, введенный в **NotificationReceiver** класса и удалить комментарии...</span><span class="sxs-lookup"><span data-stu-id="3490b-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="3490b-719">Глава 18 - UnityMRNotifHub изменить приложение, класс NotificationReceiver</span><span class="sxs-lookup"><span data-stu-id="3490b-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="3490b-720">Следуя после добавления **пакеты NuGet**, вам нужно будет *раскомментируйте* часть кода в **NotificationReceiver** класса.</span><span class="sxs-lookup"><span data-stu-id="3490b-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="3490b-721">Сюда входят следующие возможности.</span><span class="sxs-lookup"><span data-stu-id="3490b-721">This includes:</span></span>

1. <span data-ttu-id="3490b-722">Пространство имен, верхней:</span><span class="sxs-lookup"><span data-stu-id="3490b-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="3490b-723">Весь код внутри **InitNotificationsAsync()** метод:</span><span class="sxs-lookup"><span data-stu-id="3490b-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="3490b-724">Приведенный выше код имеет комментарий в: Убедитесь, что не случайно *раскомментируется* , комментарий (как код не будет компилироваться при наличии!).</span><span class="sxs-lookup"><span data-stu-id="3490b-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="3490b-725">И, наконец **Channel_PushNotificationReceived** событий:</span><span class="sxs-lookup"><span data-stu-id="3490b-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="3490b-726">С помощью этих Раскомментировать области кода убедитесь, что сохранить и затем перейти к следующей главе.</span><span class="sxs-lookup"><span data-stu-id="3490b-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="3490b-727">Глава 19 - связать проект смешанной реальности в приложение Store</span><span class="sxs-lookup"><span data-stu-id="3490b-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="3490b-728">Теперь необходимо связать **смешанной реальности** проекта в приложение Store, созданную в начале лаборатории.</span><span class="sxs-lookup"><span data-stu-id="3490b-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="3490b-729">Откройте решение.</span><span class="sxs-lookup"><span data-stu-id="3490b-729">Open the solution.</span></span>

2.  <span data-ttu-id="3490b-730">Щелкните правой кнопкой проект приложения UWP на панели обозревателя решений, перейдите к **Store**, и **связать приложение с Store...** .</span><span class="sxs-lookup"><span data-stu-id="3490b-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![Откройте связи с магазином](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="3490b-732">Новое окно будет отображаться вызываемой **связь приложений с Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="3490b-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="3490b-733">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="3490b-733">Click **Next**.</span></span>

    ![Перейдите к следующему экрану](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="3490b-735">Он загрузит все приложения, связанные с учетной записью, в котором был выполнен вход.</span><span class="sxs-lookup"><span data-stu-id="3490b-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="3490b-736">Если вы не вошли в учетную запись, вы можете **вход** на этой странице.</span><span class="sxs-lookup"><span data-stu-id="3490b-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="3490b-737">Найти **Store имя_приложения** , созданного в начале работы с этим руководством и выберите его.</span><span class="sxs-lookup"><span data-stu-id="3490b-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="3490b-738">Затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="3490b-738">Then click **Next**.</span></span>

    ![Найдите и выберите имя хранилища](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="3490b-740">Нажмите кнопку **связать**.</span><span class="sxs-lookup"><span data-stu-id="3490b-740">Click **Associate**.</span></span>

    ![связать приложение](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="3490b-742">Создание приложения **связанные** с приложением Store.</span><span class="sxs-lookup"><span data-stu-id="3490b-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="3490b-743">Это необходимо для включения уведомлений.</span><span class="sxs-lookup"><span data-stu-id="3490b-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="3490b-744">Глава 20 - развертывание приложений UnityMRNotifHub и UnityDesktopNotifHub</span><span class="sxs-lookup"><span data-stu-id="3490b-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="3490b-745">В этой главе может быть проще, используя два человека, как результат будет включать как приложения, работающие, один работающий на компьютере рабочего стола, а другой в пределах вашей иммерсивных гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="3490b-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="3490b-746">Приложение иммерсивных гарнитура ожидает изменений в сцену (позиция изменения из локального объекты Gameobject) и классическое приложение будет вносить изменения в их локальной сцены (позиция изменения), которая будет общей для него MR.</span><span class="sxs-lookup"><span data-stu-id="3490b-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="3490b-747">Имеет смысл для развертывания приложения на MR во-первых, следуют классическое приложение, чтобы получатель может начать прослушивание.</span><span class="sxs-lookup"><span data-stu-id="3490b-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="3490b-748">Чтобы развернуть **UnityMRNotifHub** приложения на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="3490b-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="3490b-749">Откройте файл решения вашей **UnityMRNotifHub** приложения в **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="3490b-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="3490b-750">В **платформа решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="3490b-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="3490b-751">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="3490b-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![Настройка проекта](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="3490b-753">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на компьютер.</span><span class="sxs-lookup"><span data-stu-id="3490b-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="3490b-754">Приложения появятся в списке установленных приложений, Готово к запуску.</span><span class="sxs-lookup"><span data-stu-id="3490b-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="3490b-755">Чтобы развернуть **UnityDesktopNotifHub** приложения на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="3490b-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="3490b-756">Откройте файл решения вашей **UnityDesktopNotifHub** приложения в **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="3490b-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="3490b-757">В **платформа решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="3490b-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="3490b-758">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="3490b-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![Настройка проекта](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="3490b-760">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на компьютер.</span><span class="sxs-lookup"><span data-stu-id="3490b-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="3490b-761">Приложения появятся в списке установленных приложений, Готово к запуску.</span><span class="sxs-lookup"><span data-stu-id="3490b-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="3490b-762">Запустите приложение смешанной реальности, следуют настольного приложения.</span><span class="sxs-lookup"><span data-stu-id="3490b-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="3490b-763">Благодаря выполнению обоих приложений переместите объект в сцене настольных систем (с помощью левой кнопки мыши).</span><span class="sxs-lookup"><span data-stu-id="3490b-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="3490b-764">Эти изменения расположения, применяемые будет внесенных локально, сериализовать и отправить службе приложения-функции.</span><span class="sxs-lookup"><span data-stu-id="3490b-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="3490b-765">Служба приложения-функции, затем обновит таблицы, а также в центре уведомлений.</span><span class="sxs-lookup"><span data-stu-id="3490b-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="3490b-766">Получение обновления, центра уведомлений будет отправлять обновленные данные непосредственно на все зарегистрированные приложения (в данном случае приложение иммерсивных гарнитуры), которые затем будут десериализации входящих данных и применяют новые данные позиционными для локальных объектов, переместить их в сцене.</span><span class="sxs-lookup"><span data-stu-id="3490b-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="3490b-767">Ваш завершения приложения центров уведомлений Azure</span><span class="sxs-lookup"><span data-stu-id="3490b-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="3490b-768">Поздравляем, вы создали приложение смешанной реальности, использует службу концентраторов уведомлений Azure и Разрешить взаимодействие между приложениями.</span><span class="sxs-lookup"><span data-stu-id="3490b-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![конечный продукт-end](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="3490b-770">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="3490b-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="3490b-771">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="3490b-771">Exercise 1</span></span>

<span data-ttu-id="3490b-772">Можно работать как изменить цвет объекты Gameobject и отправки этого уведомления в другие приложения, просмотр сцены?</span><span class="sxs-lookup"><span data-stu-id="3490b-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="3490b-773">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="3490b-773">Exercise 2</span></span>

<span data-ttu-id="3490b-774">Можно добавить в приложение MR перемещение объекты Gameobject и см. в разделе обновленные сцены в свое приложение?</span><span class="sxs-lookup"><span data-stu-id="3490b-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
